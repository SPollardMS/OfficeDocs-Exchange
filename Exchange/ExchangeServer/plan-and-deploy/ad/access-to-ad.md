---
title: "Access to Active Directory"
ms.author: dstrome
author: dstrome
manager: serdars
ms.date: 4/19/2018
ms.audience: ITPro
ms.topic: conceptual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 61080b45-8bce-4c23-b744-ed264d5f0b7d
description: "Summary: How Exchange 2016 retrieves data from Active Directory, and how to recover deleted objects."
---

# Access to Active Directory

 **Summary**: How Exchange 2016 retrieves data from Active Directory, and how to recover deleted objects.
  
Microsoft Exchange Server 2016 stores all configuration and recipient information in the Active Directory directory service database. When a computer running Exchange 2016 requires information about recipients and information about the configuration of the Exchange organization, it must query Active Directory to access the information. Active Directory servers must be available for Exchange 2016 to function correctly.
  
This topic explains how Exchange 2016 stores and retrieves information in Active Directory so that you can plan access to Active Directory. This topic also discusses issues you should be aware of if you try to recover deleted Exchange 2016 Active Directory objects.
  
## Exchange information stored in Active Directory

The Active Directory database stores information in three types of logical partitions that are described in the following sections:
  
- Schema partition
    
- Configuration partition
    
- Domain partition
    
### Schema partition

The schema partition stores the following two types of information:
  
- **Schema classes** define all the types of objects that can be created and stored in Active Directory. 
    
- **Schema attributes** define all the properties that can be used to describe the objects that are stored in Active Directory. 
    
When you install the first Exchange 2016 server role in the forest or run the Active Directory preparation process, the Active Directory preparation process adds many classes and attributes to the Active Directory schema. The classes that are added to the schema are used to create Exchange-specific objects, such as agents and connectors. The attributes that are added to the schema are used to configure the Exchange-specific objects and the mail-enabled users and groups. These attributes include properties, such as Office Outlook Web Access settings and Exchange Unified Messaging (UM) settings. Every domain controller and global catalog server in the forest contains a complete replica of the schema partition.
  
For more information about schema modifications in Exchange 2016, see [Exchange 2016 Active Directory schema changes](ad-schema-changes.md).
  
### Configuration partition

The configuration partition stores information about the forest-wide configuration. This configuration information includes the configuration of Active Directory sites, Exchange global settings, transport settings, and mailbox policies. Each type of configuration information is stored in a container in the configuration partition. Exchange configuration information is stored in a subfolder under the configuration partition's Services container. The information that is stored in this container includes the following:
  
- Address lists
    
- Address book mailbox policies
    
- Administrative groups
    
- Client access settings
    
- Connections
    
- Mobile Mailbox Settings
    
- Global settings
    
- Monitoring Settings
    
- System policies
    
- Retention policies container
    
- Transport settings
    
Every domain controller and global catalog server in the forest contains a complete replica of the configuration partition.
  
### Domain partition

The domain partition stores information in default containers and in organizational units that are created by the Active Directory administrator. These containers hold the domain-specific objects. This data includes Exchange system objects and information about the computers, users, and groups in that domain. When Exchange 2016 is installed, Exchange updates the objects in this partition to support Exchange functionality. This functionality affects how recipient information is stored and accessed.
  
Each domain controller contains a complete replica of the domain partition for the domain for which it is authoritative. Every global catalog server in the forest contains a subset of the information in every domain partition in the forest.
  
## How Exchange 2016 accesses information in Active Directory

Exchange 2016 uses an Active Directory API to access information that is stored in Active Directory. This service reads information from all Active Directory partitions. The data that is retrieved is cached and is used by Exchange 2016 servers to discover the Active Directory site location of all Exchange services in the organization.
  
For more information about topology and service discovery, see [Planning to Use Active Directory Sites for Routing Mail](http://technet.microsoft.com/library/0f697cee-bcaa-4c69-b80c-7a2afd1817d2.aspx).
  
Exchange 2016 is an Active Directory site-aware application that prefers to communicate with the directory servers that are located in the same site as the Exchange server to optimize network traffic. Each Exchange 2016 server must communicate with Active Directory to retrieve information about recipients and information about the other Exchange 2016 servers. The Mailbox server role stores configuration information about mailbox users and mailbox stores in Active Directory. Additionally, the Mailbox server stores information in Active Directory for the Client Access protocols, Transport service, Mailbox databases,Unified Messaging, and so on. The Mailbox server handles all activity for the active mailboxes on that server.
  
By default, whenever an Exchange 2016 server starts, it binds to a randomly selected domain controller and global catalog server in its own site. You can view the selected directory servers by using the **Get-ExchangeServer** cmdlet in the Exchange Management Shell. You can also use the **Set-ExchangeServer** cmdlet to configure a static list of domain controllers to which an Exchange 2016 server should bind or a list of domain controllers that should be excluded. 
  
> [!IMPORTANT]
> You can't deploy an Exchange 2016 server in any site that contains only read-only directory servers. 
  
## Recovery of deleted Exchange objects

Active Directory Recycle Bin helps minimize directory service downtime by enhancing your ability to preserve and recover accidentally deleted Active Directory objects without restoring Active Directory data from backups, restarting Active Directory Domain Services (AD DS), or rebooting domain controllers.
  
The most important thing to understand about recovering deleted Exchange-related Active Directory objects is that Exchange objects don't exist in isolation. For example, when you mail-enable a user, several different policies and links are calculated for the user based on your current Exchange configuration. Two problems that may arise when you restore a deleted Exchange configuration or recipient object are:
  
- **Collisions** Some Exchange attributes must be unique across a forest. For example, proxy (email) addresses must not be the same for two different users. Active Directory doesn't enforce proxy address uniqueness—Exchange administrative tools check for uniqueness. Exchange email address policies also automatically resolve possible conflicts in proxy address assignment based on deterministic rules. Therefore, it's possible to restore an Exchange user object and, as a result, create a collision with proxy addresses or other attributes that should be unique. 
    
- **Misconfigurations** Exchange has automated rules that assign various policies or settings. If you delete a recipient, and then change the rules or policies, restoring an Exchange user object may result in a user being assigned to the wrong policy (or even to a policy that no longer exists). 
    
The following guidelines will help you minimize problems or issues when you recover deleted Exchange-related objects:
  
- If you deleted an Exchange configuration object using Exchange management tools, don't restore the object. Instead, create the object again using the Exchange management tools (Exchange admin center or Exchange Management Shell).
    
- If you deleted an Exchange configuration object without using the Exchange management tools, recover the object as soon as possible. The more administrative and configuration changes that have been made in the system since the deletion, the more likely it is that restoring the objects will result in misconfiguration.
    
- If you recover deleted Exchange recipients (contacts, users, or distribution groups), monitor closely for collisions and errors relating to the recovered objects. If Exchange policies or other configuration relating to recipients may have been modified since the deletion, re-apply current policies to the restored recipients to ensure that they're configured correctly.
    
## For more information

[Active Directory Recycle Bin Step-by-Step Guide](https://go.microsoft.com/fwlink/p/?linkId=178720)
  
[Introduction to Active Directory Administrative Center Enhancements (Level 100)](https://go.microsoft.com/fwlink/p/?linkId=267641)
  
[Advanced AD DS Management Using Active Directory Administrative Center (Level 200)](https://go.microsoft.com/fwlink/p/?LinkId=267642)
  

