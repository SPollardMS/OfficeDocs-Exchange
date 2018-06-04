---
title: "MAPI over HTTP isn't enabled [WarnMapiHttpNotEnabled]"
ms.author: dstrome
author: dstrome
manager: serdars
ms.date: 7/22/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- 'ms.exch.setupreadiness.WarnMapiHttpNotEnabled'
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 8c7e2b60-2973-47b1-ac1c-3c3e96824aee
description: "Microsoft Exchange Server 2016 Setup displayed this warning because there are servers running Exchange 2016 or later in this organization and MAPI over HTTP isn't enabled."
---

# MAPI over HTTP isn't enabled [WarnMapiHttpNotEnabled]

Microsoft Exchange Server 2016 Setup displayed this warning because there are servers running Exchange 2016 or later in this organization and MAPI over HTTP isn't enabled.
  
MAPI over HTTP is the preferred Outlook connectivity method when connecting to servers running Exchange 2016 or later. MAPI over HTTP improves the reliability and stability of the Outlook and Exchange connections by moving the transport layer to the industry-standard HTTP model. This allows a higher level of visibility of transport errors and enhanced recoverability. Additional functionality includes support for an explicit pause-and-resume function. This enables supported clients to change networks or resume from hibernation while maintaining the same server context.
  
Exchange Setup won't automatically enable MAPI over HTTP to avoid making unexpected changes to client connectivity. However, we recommend that you enable MAPI over HTTP as soon as possible to receive the benefits it provides. 
  
For more information about MAPI over HTTP and how to enable it, see [MAPI over HTTP in Exchange 2016](../../clients/mapi-over-http/mapi-over-http.md). 
  
Having problems? Ask for help in the Exchange forums. Visit the forums at: [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351).
  
Did you find what you're looking for? Please take a minute to [send us feedback](mailto:ExchangeHelpFeedback@microsoft.com&amp;subject=Exchange%202016%20help%20feedback&amp;Body=Thanks%20for%20taking%20the%20time%20to%20send%20us%20feedback!%20We%20strive%20to%20respond%20to%20every%20message%20we%20receive,%20even%20though%20it%20might%20take%20us%20a%20while.%20Let%20us%20know%20what%20you%20think%20about%20Exchange%20content:%20What%20are%20we%20doing%20right%3F%20How%20can%20we%20make%20help%20better%3F%0APlease%20note%20that%20we're%20unable%20to%20respond%20to%20requests%20for%20support%20submitted%20via%20this%20email%20address.%20If%20you%20need%20help,%20please%20contact%20Exchange%20Server%20support%20at%20http://go.microsoft.com/fwlink/p/%3FLinkId=402506.%0AThanks!%0AThe%20Exchange%20Server%20Content%20Publishing%20team) about the information you were hoping to find. 
  

