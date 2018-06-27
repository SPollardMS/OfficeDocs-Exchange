---
title: "What changes in Active Directory when Exchange 2016 is installed?"
ms.author: dstrome
author: dstrome
manager: serdars
ms.date: 6/7/2018
ms.audience: ITPro
ms.topic: conceptual
ms.prod: exchange-server-itpro
localization_priority: Normal
ms.collection: Strat_EX_Admin
ms.assetid: 07386078-6103-49a2-8698-2d41db9cec95
description: "Summary: How Exchange 2016 affects Active Directory."
---

# What changes in Active Directory when Exchange 2016 is installed?

 **Summary**: How Exchange 2016 affects Active Directory.
  
When you install Exchange 2016, changes are made to your Active Directory forest and domains. Exchange does this so that it can store information about the Exchange servers, mailboxes, and other objects related to Exchange in your organization. These changes are made for you when you run the Exchange 2016 Setup wizard or when you run the _PrepareSchema_, _PrepareAD_, and _PrepareDomains_ commands (see how to use these commands in [Prepare Active Directory and domains](../../plan-and-deploy/prepare-ad-and-domains.md)) during Exchange 2016 command-line Setup. If you're curious about the changes that Exchange makes to Active Directory, this topic is for you. It explains what Exchange does at each step of Active Directory preparation.
  
There are three steps that need to be done to prepare Active Directory for Exchange:
  
- [Extend the Active Directory schema](ad-changes.md#Extend)
    
- [Prepare Active Directory containers, objects, and other items](ad-changes.md#PrepAD)
    
- [Prepare Active Directory domains](ad-changes.md#PrepDomains)
    
After all three steps are done, your Active Directory forest is ready for Exchange 2016. You can find out more about how to install Exchange 2016 by reading [Install the Exchange 2016 Mailbox role using the Setup wizard](../../plan-and-deploy/deploy-new-installations/install-mailbox-role.md).
  
## Extend the Active Directory schema
<a name="Extend"> </a>

Extending the Active Directory schema adds and updates classes, attributes, and other items. These changes are needed so that Exchange can create containers and objects to store information about the Exchange organization. Because Exchange makes a lot of changes to the Active Directory schema, there's a topic dedicated to this step. To see all of the changes made to the schema, see [Exchange 2016 Active Directory schema changes](ad-schema-changes.md).
  
This step is done automatically when you run the Exchange 2016 Setup wizard on the first Exchange 2016 server in the Active Directory forest. It's also done when you run Exchange 2016 command line Setup with the _PrepareSchema_ command (or optionally with the _PrepareAD_ command) on the first Exchange 2016 server in the forest. If you want to find out more information about how to extend the schema, see [1. Extend the Active Directory schema](../../plan-and-deploy/prepare-ad-and-domains.md#Step1) in [Prepare Active Directory and domains](../../plan-and-deploy/prepare-ad-and-domains.md).
  
After Exchange is finished extending the schema, it sets the schema version, which is stored in the **ms-Exch-Schema-Version-Pt** attribute. If you want to make sure that the Active Directory schema was extended successfully, you can check the value stored in this attribute. If the value in the attribute matches the schema version listed for the release of Exchange 2016 you installed, extending the schema was successful. For a list of Exchange releases and how to check the value of this attribute, check out the [How do you know this worked?](../../plan-and-deploy/prepare-ad-and-domains.md#Verify) section in [Prepare Active Directory and domains](../../plan-and-deploy/prepare-ad-and-domains.md).
  
## Prepare Active Directory containers, objects, and other items
<a name="PrepAD"> </a>

With the schema extended, the next step is to add all of the containers, objects, attributes, and other items that Exchange uses to store information in Active Directory. Most of the changes made in this step are applied to the entire Active Directory forest. A smaller set of changes are made to the local Active Directory domain where the _PrepareAD_ command was run during Setup.
  
These are the changes that are made to the Active Directory forest:
  
- The Microsoft Exchange container is created under CN=Services,CN=Configuration,DC=\< _root domain_\> if it doesn't already exist.
    
- The following containers and objects are created under CN=\< _organization name_\>,CN=Microsoft Exchange,CN=Services,CN=Configuration,DC=\< _root domain_\> if they don't already exist:
    
  - CN=Address Lists Container
    
  - CN=AddressBook Mailbox Policies
    
  - CN=Addressing
    
  - CN=Administrative Groups
    
  - CN=Approval Applications
    
  - CN=Auth Configuration
    
  - CN=Availability Configuration
    
  - CN=Client Access
    
  - CN=Connections
    
  - CN=ELC Folders Container
    
  - CN=ELC Mailbox Policies
    
  - CN=ExchangeAssistance
    
  - CN=Federation
    
  - CN=Federation Trusts
    
  - CN=Global Settings
    
  - CN=Hybrid Configuration
    
  - CN=Mobile Mailbox Policies
    
  - CN=Mobile Mailbox Settings
    
  - CN=Monitoring Settings
    
  - CN=OWA Mailbox Policies
    
  - CN=Provisioning Policy Container
    
  - CN=Push Notification Settings
    
  - CN=RBAC
    
  - CN=Recipient Policies
    
  - CN=Remote Accounts Policies Container
    
  - CN=Retention Policies Container
    
  - CN=Retention Policy Tag Container
    
  - CN=ServiceEndpoints
    
  - CN=System Policies
    
  - CN=Team Mailbox Provisioning Policies
    
  - CN=Transport Settings
    
  - CN=UM AutoAttendant Container
    
  - CN=UM DialPlan Container
    
  - CN=UM IPGateway Container
    
  - CN=UM Mailbox Policies
    
  - CN=Workload Management Settings
    
- The following containers and objects are created under CN=Transport Settings,CN=\< _Organization Name_\>,CN=Microsoft Exchange,CN=Services,CN=Configuration,DC=\< _root domain_\> if they don't already exist:
    
  - CN=Accepted Domains
    
  - CN=ControlPoint Config
    
  - CN=DNS Customization
    
  - CN=Interceptor Rules
    
  - CN=Malware Filter
    
  - CN=Message Classifications
    
  - CN=Message Hygiene
    
  - CN=Rules
    
  - CN=MicrosoftExchange329e71ec88ae4615bbc36ab6ce41109e
    
- Permissions are set throughout the configuration partition in Active Directory.
    
- The Rights.ldf file is imported. This file adds permissions that are needed to install Exchange and configure Active Directory.
    
- The Microsoft Exchange Security Groups organizational unit (OU) is created in the root domain of the forest, and permissions are assigned to it.
    
- The following groups are created within the Microsoft Exchange Security Groups OU if they don't already exist:
    
  - Compliance Management
    
  - Delegated Setup
    
  - Discovery Management
    
  - Exchange Servers
    
  - Exchange Trusted Subsystem
    
  - Exchange Windows Permissions
    
  - ExchangeLegacyInterop
    
  - Help Desk
    
  - Hygiene Management
    
  - Managed Availability Servers
    
  - Organization Management
    
  - Public Folder Management
    
  - Recipient Management
    
  - Records Management
    
  - Server Management
    
  - UM Management
    
  - View-Only Organization Management
    
- The new management role groups (which appear as universal security groups (USGs) in Active Directory) that were created in the Microsoft Exchange Security Groups OU are added to the **otherWellKnownObjects** attribute stored on the CN=Microsoft Exchange,CN=Services,CN=Configuration,DC=\< _root domain_\> container.
    
- The Unified Messaging Voice Originator contact is created in the Microsoft Exchange System Objects container of the root domain.
    
- The domain where the _PrepareAD_ command was run is prepared for Exchange 2016. For information about what's done to prepare the Active Directory domain for Exchange, check out [Prepare Active Directory domains](ad-changes.md#PrepDomains).
    
## Prepare Active Directory domains
<a name="PrepDomains"> </a>

The final step of preparing Active Directory for Exchange is to prepare all of the Active Directory domains where Exchange servers will be installed or where mailbox-enabled users will be located. This step is done automatically in the domain where the _PrepareAD_ command was run.
  
These are the changes that are made to the Active Directory domains:
  
- The Microsoft Exchange System Objects container is created in the root domain partition in Active Directory if it doesn't already exist.
    
- Permissions are set on the Microsoft Exchange System Objects container for the Exchange Servers, Organization Management, and Authenticated Users security groups.
    
- The Exchange Install Domain Servers domain global group is created in the current domain and placed in the Microsoft Exchange System Objects container.
    
- The Exchange Install Domain Servers group is added to the Exchange Servers USG in the root domain.
    
- Permissions are assigned at the domain level for the Exchange Servers USG and the Organization Management USG.
    
- The **objectVersion** property in the Microsoft Exchange System Objects container under DC=\< _root domain_\> is set. If you want to make sure that the Active Directory schema was extended successfully, you can check the value stored in this property. If the value in the property matches the schema version listed for the release of Exchange 2016 you installed, extending the schema was successful. For a list of Exchange releases and how to check the value of this property, check out the [How do you know this worked?](../../plan-and-deploy/prepare-ad-and-domains.md#Verify) section in [Prepare Active Directory and domains](../../plan-and-deploy/prepare-ad-and-domains.md).
    

