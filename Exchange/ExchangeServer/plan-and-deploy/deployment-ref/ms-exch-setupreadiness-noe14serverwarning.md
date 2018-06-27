---
title: "No Exchange 2010 servers detected [NoE14ServerWarning]"
ms.author: dstrome
author: dstrome
manager: serdars
ms.date: 6/12/2018
ms.audience: ITPro
ms.topic: reference
f1_keywords:
- 'ms.exch.setupreadiness.NoE14ServerWarning'
ms.prod: exchange-server-itpro
localization_priority: Normal
ms.assetid: 789cabab-c769-4a16-a6c8-3db82cff8861
description: "Microsoft Exchange Server 2016 Setup displayed this warning because no Exchange Server 2010 server roles exist in the organization."
---

# No Exchange 2010 servers detected [NoE14ServerWarning]

Microsoft Exchange Server 2016 Setup displayed this warning because no Exchange Server 2010 server roles exist in the organization.
  
> [!CAUTION]
> If you continue with Exchange Server 2016 installation, you won't be able to add Exchange 2010 servers to the organization at a future date.
  
Before deploying Exchange 2016, consider the following factors that may require you to deploy Exchange 2010 servers prior to deploying Exchange 2016:
  
- **Third-party or in-house developed applications**: Applications developed for earlier versions of Exchange may not be compatible with Exchange 2016. You may need to maintain Exchange 2010 servers to support these applications.
    
- **Coexistence or migration requirements**: If you plan on migrating mailboxes into your organization, some solutions may require the use of Exchange 2010 servers.
    
If you decide that you need to deploy Exchange 2010 servers, you must do so before you deploy Exchange 2016. Active Directory must be prepared for each Exchange version in the following order:
  
1. Exchange 2010
    
2. Exchange 2013 (only required if you're planning to deploy Exchange 2013 at a later date)
    
3. Exchange 2016
    
Having problems? Ask for help in the Exchange forums. Visit the forums at: [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351).
  
Did you find what you're looking for? Please take a minute to [send us feedback](mailto:ExchangeHelpFeedback@microsoft.com&subject=Exchange%202016%20help%20feedback&Body=Thanks%20for%20taking%20the%20time%20to%20send%20us%20feedback!%20We%20strive%20to%20respond%20to%20every%20message%20we%20receive,%20even%20though%20it%20might%20take%20us%20a%20while.%20Let%20us%20know%20what%20you%20think%20about%20Exchange%20content:%20What%20are%20we%20doing%20right%3F%20How%20can%20we%20make%20help%20better%3F%0APlease%20note%20that%20we're%20unable%20to%20respond%20to%20requests%20for%20support%20submitted%20via%20this%20email%20address.%20If%20you%20need%20help,%20please%20contact%20Exchange%20Server%20support%20at%20http://go.microsoft.com/fwlink/p/%3FLinkId=402506.%0AThanks!%0AThe%20Exchange%20Server%20Content%20Publishing%20team) about the information you were hoping to find.
  

