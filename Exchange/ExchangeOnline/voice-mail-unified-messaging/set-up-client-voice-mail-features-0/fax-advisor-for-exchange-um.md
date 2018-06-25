---
title: "Fax advisor for Exchange UM"
ms.author: tonysmit
author: tonysmit
manager: scotv
ms.date: 12/9/2016
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 928a466d-cc0c-4160-bd4c-f0fc76b038d4
description: "Microsoft Unified Messaging (UM) relies on certified fax partner solutions for enhanced fax functionality such as outbound fax or fax routing. By default, users aren't configured to allow incoming fax messages to be delivered to a UM-enabled user. Exchange servers send the fax requests to a certified fax partner solution. The fax partner's server receives the fax data and then sends it to the recipient's mailbox in an email message with the fax included as a .tif attachment. For details, see Enable Voice Mail Users to Receive Faxes."
---

# Fax advisor for Exchange UM

Microsoft Unified Messaging (UM) relies on certified fax partner solutions for enhanced fax functionality such as outbound fax or fax routing. By default, users aren't configured to allow incoming fax messages to be delivered to a UM-enabled user. Exchange servers send the fax requests to a certified fax partner solution. The fax partner's server receives the fax data and then sends it to the recipient's mailbox in an email message with the fax included as a .tif attachment. For details, see [Enable Voice Mail Users to Receive Faxes](http://technet.microsoft.com/library/451ab0ea-21e1-4c1f-ae62-4ba7cdfd1e4d.aspx).
  
> [!IMPORTANT]
> We recommend that all customers who plan to deploy Unified Messaging obtain the assistance of a Unified Messaging specialist. A Unified Messaging specialist helps you ensure that there's a smooth transition to Unified Messaging from a legacy voice mail system. Performing a new deployment or upgrading a legacy voice mail system requires significant knowledge about PBXs and Unified Messaging. For more information about how to contact a Unified Messaging specialist, see the [Microsoft Exchange Server 2013 Unified Messaging (UM) Specialists](http://go.microsoft.com/fwlink/p/?LinkId=262708) or [Microsoft Pinpoint for Unified Messaging](https://go.microsoft.com/fwlink/p/?LinkId=261951). 
  
## Exchange Unified Messaging Fax Partner Program

To become a fax partner certified for interoperability with Exchange UM, the partner must implement the requirements contained in the Fax Partner Interoperability Specification and the fax solution must be certified by an independent certification vendor. For more information about certifying a fax product to work with Exchange Unified Messaging, submit a request to [Fax Partners for Unified Messaging](mailto:fax-part@microsoft.com).
  
## Fax partner solutions certified as interoperable with Unified Messaging

If you've already deployed Exchange Unified Messaging and are looking for a fax partner that can enable incoming faxes for your organization, see [Microsoft Pinpoint for Fax Partners](https://go.microsoft.com/fwlink/p/?linkId=190238). These software vendors have been certified as interoperable with Exchange Server and include certified software solutions for Unified Messaging.
  
## VoIP, media gateway, and IP PBX support

Correctly configuring VoIP gateways for your organization is a difficult deployment task that must be completed to successfully deploy Exchange Unified Messaging with incoming faxing. To help answer questions and get the most up-to-date VoIP gateway configuration information, see [Telephony advisor for Exchange 2013](../../voice-mail-unified-messaging/telephone-system-integration-with-um/telephony-advisor-for-exchange-2013.md). [Configuration notes for supported VoIP gateways, IP PBXs, and PBXs](../../voice-mail-unified-messaging/telephone-system-integration-with-um/configuration-notes-for-voip-gateways.md) provides VoIP gateway configuration notes and files that you must have to correctly configure your organization's VoIP gateways, IP PBXs, and SBCs to work with Exchange Unified Messaging. 
  
Interoperability testing of Exchange Unified Messaging with VoIP gateways is now integrated with the Microsoft Unified Communications Open Interoperability Program. For more information, see [Microsoft Unified Communications Open Interoperability Program](http://go.microsoft.com/fwlink/p/?linkId=140722).
  
The [Microsoft Unified Communications Open Interoperability Program](http://go.microsoft.com/fwlink/p/?linkId=140722) qualification program for VoIP gateways and IP PBXs ensures that customers have a seamless setup and support experience when they're using qualified telephony gateways and IP PBXs with Microsoft Unified Communications software. 
  
> [!IMPORTANT]
> Sending and receiving faxes using T.38 or G.711 isn't supported in an environment where Unified Messaging and Communications Server 2007 R2 or Microsoft Lync Server are integrated. 
  
## Deploying and configuring faxing

UM forwards incoming fax calls to a dedicated fax partner solution, which then establishes the fax call with the fax sender and receives the fax on behalf of the UM-enabled user. However, to allow UM-enabled users to receive fax messages in their mailbox, you must configure the fax partner server, and then configure the UM dial plans, UM mailbox policies, and enable UM-enabled users to receive faxes. For details, see [Setting up incoming faxing](set-up-incoming-faxing.md).
  

