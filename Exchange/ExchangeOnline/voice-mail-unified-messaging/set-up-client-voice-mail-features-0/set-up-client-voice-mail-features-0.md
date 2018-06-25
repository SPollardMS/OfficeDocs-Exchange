---
title: "Set up client voice mail features in Exchange Online"
ms.author: tonysmit
author: tonysmit
manager: scotv
ms.date: 6/24/2018
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 58493d02-0f66-4ea0-9686-ece51828f9f9
description: "This topic describes the client features that give users who are enabled for Exchange Unified Messaging (UM) access to the email and voice mail messages in their mailbox. These features let you offer your users simplified access to voice mail and email and an improved overall user experience."
---

# Set up client voice mail features in Exchange Online

This topic describes the client features that give users who are enabled for Exchange Unified Messaging (UM) access to the email and voice mail messages in their mailbox. These features let you offer your users simplified access to voice mail and email and an improved overall user experience.
  
## Voice mail client support
<a name="clientsupport"> </a>

 **Exchange ActiveSync clients** The Microsoft Exchange ActiveSync protocol is used to connect mobile clients, such as those found on Internet-capable mobile devices, to an Exchange mailbox. Users can use mobile devices to access their mailbox and view email messages, view and change calendar and contact information, and listen to their voice mail messages. They can also synchronize email, voice mail, calendar items, and contact information with other devices. 
  
 **Integration with Outlook** Microsoft Outlook enables users to access their Exchange mailbox and view email messages in their Inbox, view and change calendar information, and listen to voice messages by using Microsoft Windows Media Player, which is embedded inside the email messages. By using a supported email client, users gain additional features, such as the Play on Phone functionality. 
  
 **Integration with Outlook Web App** Microsoft Outlook Web App provides users with a set of UM interfaces and tools comparable to a full-featured email client like Outlook. With Outlook Web App, users can access their Exchange mailbox by using a compliant web browser. Like Outlook, Outlook Web App provides Windows Media Player embedded in email messages so that users can listen to voice messages, and enables users to access other features such as Play on Phone. 
  
## Outlook Voice Access
<a name="OutlookVoiceAccess"> </a>

In Exchange UM, a UM-enabled user can call in to an internal or external telephone number that's configured on a UM dial plan to access their mailbox and use the Outlook Voice Access menu system. Using this menu, UM-enabled users can read email, listen to voice messages, interact with their Outlook calendar, access their personal contacts, and perform tasks such as configuring their Outlook Voice Access PIN or recording their voice mail greetings. For details, see [Setting up Outlook Voice Access](set-up-outlook-voice-access.md).
  
## Forwarding calls
<a name="forwardingcalls"> </a>

A UM-enabled user can create and configure call answering rules using Outlook or Outlook Web App. Call answering rules let users control how their incoming calls should be handled. The rules are applied to incoming calls similar to the way Inbox rules are applied to incoming email messages, and are stored along with other voice settings in the user's mailbox. Up to nine call answering rules can be set up for each UM-enabled mailbox. These rules are independent of the Inbox rules and don't take up part of the user's Inbox rules storage quota. For details, see [Allow voice mail users to forward calls](allow-voice-mail-users-to-forward-calls.md).
  
## Voice Mail Preview
<a name="VoiceMailPreview"> </a>

Voice Mail Preview is a feature that's available to users who receive their voice mail messages from the UM voice mail system. Voice Mail Preview enhances the voice mail experience by providing a text version of audio recordings. For details, see [Allow users to see a voice mail transcript](allow-users-to-see-a-voice-mail-transcript.md).
  
## Receiving faxes
<a name="receivingfaxes"> </a>

UM forwards incoming fax calls for a UM-enabled user to a dedicated fax partner solution, which establishes the fax call with the fax sender and receives the fax on behalf of the user. Before your UM-enabled users can receive fax messages in their mailbox, you must do the following: 
  
- Enable inbound faxing on the UM dial plan linked to the users by setting the  _FaxEnabled_ parameter to  `$true`.
    
- Enable inbound faxing on the UM dial plan linked to the users by setting the  _Allowfax_ parameter to  `$true`.
    
- Enable inbound faxing for the users by setting the  _FaxEnabled_ parameter to  `$true`.
    
- Set the partner fax server URI to allow inbound faxing.
    
- Configure authentication between the Mailbox server and the fax partner server.
    

