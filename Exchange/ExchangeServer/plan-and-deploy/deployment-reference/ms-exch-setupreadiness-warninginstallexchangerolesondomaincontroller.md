---
title: "Installing Exchange on a domain controller is not recommended [WarningInstallExchangeRolesOnDomainController]"
ms.author: dstrome
author: dstrome
manager: serdars
ms.date: 7/22/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- 'ms.exch.setupreadiness.WarningInstallExchangeRolesOnDomainController'
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 48922de2-a68c-4092-96a5-d38c8e5f49f5
description: "Microsoft Exchange Server 2016 Setup has detected that the computer you're attempting to install Exchange 2016 on is an Active Directory domain controller. Installing Exchange 2016 on a domain controller isn't recommended."
---

# Installing Exchange on a domain controller is not recommended [WarningInstallExchangeRolesOnDomainController]

Microsoft Exchange Server 2016 Setup has detected that the computer you're attempting to install Exchange 2016 on is an Active Directory domain controller. Installing Exchange 2016 on a domain controller isn't recommended.
  
If you install Exchange 2016 on a domain controller, be aware of the following issues:
  
- Configuring Exchange 2016 for Active Directory split permissions isn't supported.
    
- The Exchange Trusted Subsystem universal security group (USG) is added to the Domain Admins group when Exchange is installed on a domain controller. When this occurs, all Exchange servers in the domain are granted domain administrator rights in that domain.
    
- Exchange Server and Active Directory are both resource-intensive applications. There are performance implications to be considered when both are running on the same computer.
    
- You must make sure that the domain controller Exchange 2016 is installed on is a global catalog server.
    
- Exchange services may not start correctly when the domain controller is also a global catalog server.
    
- System shutdown will take considerably longer if Exchange services aren't stopped before shutting down or restarting the server.
    
- Demoting a domain controller to a member server isn't supported.
    
- Running Exchange 2016 on a clustered node that is also an Active Directory domain controller isn't supported.
    
We recommend that you install Exchange 2016 on a member server.
  
Having problems? Ask for help in the Exchange forums. Visit the forums at: [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351).
  
Did you find what you're looking for? Please take a minute to [send us feedback](mailto:ExchangeHelpFeedback@microsoft.com&amp;subject=Exchange%202016%20help%20feedback&amp;Body=Thanks%20for%20taking%20the%20time%20to%20send%20us%20feedback!%20We%20strive%20to%20respond%20to%20every%20message%20we%20receive,%20even%20though%20it%20might%20take%20us%20a%20while.%20Let%20us%20know%20what%20you%20think%20about%20Exchange%20content:%20What%20are%20we%20doing%20right%3F%20How%20can%20we%20make%20help%20better%3F%0APlease%20note%20that%20we're%20unable%20to%20respond%20to%20requests%20for%20support%20submitted%20via%20this%20email%20address.%20If%20you%20need%20help,%20please%20contact%20Exchange%20Server%20support%20at%20http://go.microsoft.com/fwlink/p/%3FLinkId=402506.%0AThanks!%0AThe%20Exchange%20Server%20Content%20Publishing%20team) about the information you were hoping to find. 
  

