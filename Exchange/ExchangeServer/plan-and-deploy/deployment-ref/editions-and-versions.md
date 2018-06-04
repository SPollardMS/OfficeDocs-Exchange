---
title: "Exchange 2016 editions and versions"
ms.author: dstrome
author: dstrome
manager: serdars
ms.date: 4/19/2018
ms.audience: ITPro
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: b563b543-fb3f-4465-9a54-cbfd680aee1f
description: "Microsoft Exchange Server 2016 is available in two server editions: Standard Edition and Enterprise Edition. Enterprise Edition can scale to 100 mounted databases per server; Standard Edition is limited to 5 mounted databases per server. A mounted database is a database that is in use. A mounted database can be an active mailbox database that is mounted for use by clients, or a passive mailbox database that is mounted in recovery for log replication and replay. While you can create more databases than the limits described above, you can only mount the maximum number specified above. The recovery database does not count towards this limit."
---

# Exchange 2016 editions and versions

Microsoft Exchange Server 2016 is available in two server editions: Standard Edition and Enterprise Edition. Enterprise Edition can scale to 100 mounted databases per server; Standard Edition is limited to 5 mounted databases per server. A mounted database is a database that is in use. A mounted database can be an active mailbox database that is mounted for use by clients, or a passive mailbox database that is mounted in recovery for log replication and replay. While you can create more databases than the limits described above, you can only mount the maximum number specified above. The recovery database does not count towards this limit.
  
These licensing editions are defined by a product key. When you enter a valid license product key, the supported edition for the server is established. Product keys can be used for the same edition key swaps and upgrades only; they can't be used for downgrades. You can use a valid product key to move from the evaluation version (Trial Edition) of Exchange 2016 to either Standard Edition or Enterprise Edition. You can also use a valid product key to move from Standard Edition to Enterprise Edition.
  
No loss of functionality will occur when the Trial Edition expires, so you can maintain lab, demo, training, and other non-production environments beyond 120 days without having to reinstall the Trial Edition of Exchange 2016.
  
As mentioned earlier, you can't use product keys to downgrade from Enterprise Edition to Standard Edition, nor can you use them to revert to the Trial Edition. These types of downgrades can only be done by uninstalling Exchange 2016, reinstalling Exchange 2016, and entering the correct product key.
  
## Exchange 2016 versions

For a list of Exchange 2016 versions and information on how to download and upgrade to the latest version of Exchange 2016, see the following topics:
  
- [Exchange 2016 Build Numbers and Release Dates](http://technet.microsoft.com/library/6a8091d0-4f19-4ae7-9e44-fd1c9f5fbe19.aspx)
    
- [Install the Exchange 2016 Mailbox role using the Setup wizard](../../plan-and-deploy/deploy-new-installations/install-mailbox-role.md)
    
To view the build number for the version of Exchange 2016 that you're running, run the following command in the Exchange Management Shell.
  
```
Get-ExchangeServer | fl name,edition,admindisplayversion
```

## Exchange 2016 license types

Exchange 2016 is licensed in the Server/Client Access License (CAL) model similar to how Exchange 2010 was licensed. Following are the types of licenses:
  
- **Server licenses** A license must be assigned for each instance of the server software that is being run. The Server license is sold in two server editions: Standard Edition and Enterprise Edition. 
    
- **Client Access licenses (CALs)** Exchange 2016 also comes in two client access license (CAL) editions, which are referred to as a Standard CAL and an Enterprise CAL. You can mix and match the server editions with the CAL types. For example, you can use Enterprise CALs with Exchange 2016 Standard Edition. Similarly, you can use Standard CALs with Exchange 2016 Enterprise Edition. 
    
For more information about Exchange license types, see [Licensing](https://go.microsoft.com/fwlink/p/?LinkId=392675).
  

