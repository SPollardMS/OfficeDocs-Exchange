---
title: "Installation of the first Exchange server in the organization can't be delegated [DelegatedMailboxFirstInstall]"
ms.author: dstrome
author: dstrome
manager: serdars
ms.date: 11/17/2014
ms.audience: Developer
ms.topic: reference
f1_keywords:
- 'ms.exch.setupreadiness.DelegatedMailboxFirstInstall'
ms.prod: exchange-server-itpro
localization_priority: Normal
ms.assetid: d451581b-6161-4e95-99f1-03dac8313fae
description: "Microsoft Exchange Server 2016 Setup can't continue because the logged-on user doesn't have the account permissions that are required to install the first Exchange 2016 server in the organization."
---

# Installation of the first Exchange server in the organization can't be delegated [DelegatedMailboxFirstInstall]

Microsoft Exchange Server 2016 Setup can't continue because the logged-on user doesn't have the account permissions that are required to install the first Exchange 2016 server in the organization.
  
Although Exchange 2016 Setup allows using delegation to install successive server roles, Setup requires that the user who is logged on is a member of the Enterprise Admins Windows security group when the first Exchange 2016 server in the organization is installed. This is required because Exchange 2016 Setup creates and configures objects in the Exchange Organization container in Active Directory during installation.
  
> [!NOTE]
> If you haven't prepared the Active Directory schema for Exchange 2016, the logged-on user must also be a member of the Schema Admins Windows security group. Alternately, another user who's a member of the Schema Admins Windows group can prepare the Active Directory schema before Exchange 2016 is installed.
  
To resolve this issue, add the logged-on user as a member of the Enterprise Admins security group. Or, log on to an account that's a member of the Enterprise Admins security group. Then run Exchange 2016 Setup again.
  
Having problems? Ask for help in the Exchange forums. Visit the forums at: [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351).
  
Did you find what you're looking for? Please take a minute to [send us feedback](mailto:ExchangeHelpFeedback@microsoft.com&subject=Exchange%202016%20help%20feedback&Body=Thanks%20for%20taking%20the%20time%20to%20send%20us%20feedback!%20We%20strive%20to%20respond%20to%20every%20message%20we%20receive,%20even%20though%20it%20might%20take%20us%20a%20while.%20Let%20us%20know%20what%20you%20think%20about%20Exchange%20content:%20What%20are%20we%20doing%20right%3F%20How%20can%20we%20make%20help%20better%3F%0APlease%20note%20that%20we're%20unable%20to%20respond%20to%20requests%20for%20support%20submitted%20via%20this%20email%20address.%20If%20you%20need%20help,%20please%20contact%20Exchange%20Server%20support%20at%20http://go.microsoft.com/fwlink/p/%3FLinkId=402506.%0AThanks!%0AThe%20Exchange%20Server%20Content%20Publishing%20team) about the information you were hoping to find.
  

