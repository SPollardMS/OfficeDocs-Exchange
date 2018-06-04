---
title: "Installation on domain controllers is not supported with Active Directory split permissions [InstallOnDCInADSplitPermissionMode]"
ms.author: dstrome
author: dstrome
manager: serdars
ms.date: 7/22/2015
ms.audience: ITPro
ms.topic: reference
f1_keywords:
- 'ms.exch.setupreadiness.InstallOnDCInADSplitPermissionMode'
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 977e3758-5e09-40a2-80c1-fe344b1d8a2a
description: "Microsoft Exchange Server 2016 Setup has detected that you're attempting to run Setup on an Active Directory domain controller and one of the following is true:"
---

# Installation on domain controllers is not supported with Active Directory split permissions [InstallOnDCInADSplitPermissionMode]

Microsoft Exchange Server 2016 Setup has detected that you're attempting to run Setup on an Active Directory domain controller and one of the following is true:
  
- The Exchange organization is already configured for Active Directory split permissions.
    
- You selected the Active Directory split permissions option in Exchange 2016 Setup.
    
The installation of Exchange 2016 on domain controllers isn't supported when the Exchange organization is configured for Active Directory split permissions.
  
If you want to install Exchange 2016 on a domain controller, you must configure the Exchange organization for Role Based Access Control (RBAC) split permissions or shared permissions.
  
> [!IMPORTANT]
> We don't recommend installing Exchange 2016 on Active Directory domain controllers. For more information, see [Installing Exchange on a domain controller is not recommended [WarningInstallExchangeRolesOnDomainController]](ms-exch-setupreadiness-warninginstallexchangerolesondomaincontroller.md). 
  
If you want to continue using Active Directory split permissions, you must install Exchange 2016 on a member server.
  
For more information about split and shared permissions in Exchange 2016 , see the following topics:
  
[Understanding Split Permissions](http://technet.microsoft.com/library/2b709e15-63a2-4841-94bc-b289b71166d0.aspx)
  
[Configure Exchange 2013 for Split Permissions](http://technet.microsoft.com/library/8c74f893-a6f3-4869-8571-3bc0f662cc87.aspx)
  
[Configure Exchange 2013 for Shared Permissions](http://technet.microsoft.com/library/7d119977-b420-4b66-acf0-0a978b188cdd.aspx)
  
Having problems? Ask for help in the Exchange forums. Visit the forums at: [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351).
  
Did you find what you're looking for? Please take a minute to [send us feedback](mailto:ExchangeHelpFeedback@microsoft.com&amp;subject=Exchange%202016%20help%20feedback&amp;Body=Thanks%20for%20taking%20the%20time%20to%20send%20us%20feedback!%20We%20strive%20to%20respond%20to%20every%20message%20we%20receive,%20even%20though%20it%20might%20take%20us%20a%20while.%20Let%20us%20know%20what%20you%20think%20about%20Exchange%20content:%20What%20are%20we%20doing%20right%3F%20How%20can%20we%20make%20help%20better%3F%0APlease%20note%20that%20we're%20unable%20to%20respond%20to%20requests%20for%20support%20submitted%20via%20this%20email%20address.%20If%20you%20need%20help,%20please%20contact%20Exchange%20Server%20support%20at%20http://go.microsoft.com/fwlink/p/%3FLinkId=402506.%0AThanks!%0AThe%20Exchange%20Server%20Content%20Publishing%20team) about the information you were hoping to find. 
  

