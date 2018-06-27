---
title: "Review the voice mail calls for a user"
ms.author: tonysmit
author: tonysmit
manager: scotv
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.service: exchange-online
localization_priority: Normal
ms.assetid: 95768fe3-3ae2-43bd-9cbf-18c3b85c4592
description: "User call logs are used to view the following information about specific Unified Messaging (UM) users:"
---

# Review the voice mail calls for a user

User call logs are used to view the following information about specific Unified Messaging (UM) users:
  
- Details about the UM calls for a user over the last 90 days.
    
- Audio quality of each call. Audio quality metrics might not be available for all calls, because the metrics depend on several factors, such as the type and length of the call. 
    
For additional tasks related to UM reporting, see [UM reports procedures](um-reports-procedures.md).
  
## How do I get call logs for a UM-enabled user?

1. In the Exchange Administration Center (EAC), select **Unified messaging** \> **More options**![More Options Icon](../../media/ITPro_EAC_MoreOptionsIcon.gif) \> **User call logs**.
    
2. Click **Select a user**, and then select the user you want data for. 
    
3. To get more details about the audio quality for a row in the report, select the row and click **Audio Quality Details**. For more information about how to interpret audio quality, see [Investigate the audio quality of voice calls for a user](audio-quality-of-voice-calls-for-user.md).
    
4. To copy the report to the Clipboard, click **Copy all rows to the clipboard.**
    
## How do I interpret the UM user call log?

The user call log includes the following information for each call:
  
- **DATE AND TIME** The date and time of the call, in the time zone that the selected user has set in Microsoft Outlook Web App. 
    
- **DURATION** How long the call lasted in minutes (MM) and seconds (SS), in the following format: MM:SS. 
    
- **CALL TYPE ** The type of call: 
    
  - **Call Answering** The call wasn't answered and was forwarded to the Mailbox servers, and the caller left a voice message. 
    
  - **Call Answering Missed Call** The call wasn't answered and was forwarded to the Mailbox servers, and the caller didn't leave a voice message. 
    
  - **Subscriber Access** A call was made to the subscriber access number. The caller signed in and was authenticated to UM with their extension and password to access email messages, calendars, and voice messages over the phone. 
    
  - **Auto Attendant** The call was answered by a UM auto attendant. These calls are typically calls in which the caller dialed your organization's main phone number. 
    
  - **Fax** A call was received in which a fax tone was detected. If you've configured fax partners, this call was sent to the partner. 
    
  - **PlayonPhone** A call was placed by UM because the user clicked the Play on Phone button in a voice message in Microsoft Outlook Web App or Outlook. 
    
  - **FindMe** An outbound call was placed by UM as a result of a Find Me rule in a call answering rule. 
    
  - **Unauthenticated Pilot Number** A call was placed to the Outlook Voice Access number. The caller didn't sign in and wasn't authenticated. 
    
  - **Greetings Recording** A call was placed by UM to record personal greetings for a user. 
    
  - **None** A call was placed but the type wasn't defined. 
    
- **CALLING NUMBER** The phone number or SIP address of the caller. 
    
- **CALLED NUMBER** The phone number or SIP address (for users in SIP dial plans, such as Microsoft Office Communications Server 2007 R2 or Microsoft Lync Server users) of the intended recipient of the call. 
    
- **UM IP GATEWAY** The UM IP gateway that took the call. 
    
- **AUDIO QUALITY** The overall audio quality of the call. For more details about audio quality, select the row and click **Audio Quality Details**.
    

