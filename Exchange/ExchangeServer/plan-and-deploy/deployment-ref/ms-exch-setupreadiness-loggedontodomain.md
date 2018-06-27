---
title: "The current account isn't logged into an Active Directory domain [LoggedOntoDomain]"
ms.author: dstrome
author: dstrome
manager: serdars
ms.date: 7/22/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- 'ms.exch.setupreadiness.LoggedOntoDomain'
ms.prod: exchange-server-itpro
localization_priority: Normal
ms.assetid: 0e229d10-605a-420f-bf8b-58a7fcb5b259
description: "Microsoft Exchange Server 2016 Setup can't continue because it detected that the current account isn't logged on to an Active Directory domain. You must log in using an Active Directory account that has the permissions required to install Exchange Server 2016."
---

# The current account isn't logged into an Active Directory domain [LoggedOntoDomain]

Microsoft Exchange Server 2016 Setup can't continue because it detected that the current account isn't logged on to an Active Directory domain. You must log in using an Active Directory account that has the permissions required to install Exchange Server 2016.
  
Setup requires that the user who is logged on when Exchange 2016 is installed has permission to create and modify objects in Active Directory. If you're running Exchange 2016 Setup in your organization for the first time, the account you use must be a member of the Schema Admins and Enterprise Admins groups. These permissions are required because Active Directory is prepared for Exchange 2016 the first time Setup is run. After Active Directory is prepared, the account you use to install additional Exchange 2016 servers must be a member of the Organization Management management role group.
  
To resolve this issue, grant the logged-on user the appropriate permissions, or log on with an account that has those permissions and run Exchange 2016 Setup again.
  
> [!IMPORTANT]
> Cross-forest installation of Exchange 2016 isn't supported. Use an account that is a member of the Active Directory forest where you're installing Exchange 2016.
  
Having problems? Ask for help in the Exchange forums. Visit the forums at: [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351).
  
Did you find what you're looking for? Please take a minute to [send us feedback](mailto:ExchangeHelpFeedback@microsoft.com&subject=Exchange%202016%20help%20feedback&Body=Thanks%20for%20taking%20the%20time%20to%20send%20us%20feedback!%20We%20strive%20to%20respond%20to%20every%20message%20we%20receive,%20even%20though%20it%20might%20take%20us%20a%20while.%20Let%20us%20know%20what%20you%20think%20about%20Exchange%20content:%20What%20are%20we%20doing%20right%3F%20How%20can%20we%20make%20help%20better%3F%0APlease%20note%20that%20we're%20unable%20to%20respond%20to%20requests%20for%20support%20submitted%20via%20this%20email%20address.%20If%20you%20need%20help,%20please%20contact%20Exchange%20Server%20support%20at%20http://go.microsoft.com/fwlink/p/%3FLinkId=402506.%0AThanks!%0AThe%20Exchange%20Server%20Content%20Publishing%20team) about the information you were hoping to find.
  

