---
title: "Interpret voice mail call records"
ms.author: tonysmit
author: tonysmit
manager: scotv
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.service: exchange-online
localization_priority: Normal
ms.assetid: 368d9c58-61a2-43d5-8189-d3469a9e2a8d
description: "To view detailed information about calls handled by the Exchange servers on a specific day, export the call data for that day from the Call Statistics report. Daily call data, which is available for the past 90 days, can help you diagnose problems with audio quality or rejected calls, and provide information for audits or reports on Exchange servers in your organization."
---

# Interpret voice mail call records

To view detailed information about calls handled by the Exchange servers on a specific day, export the call data for that day from the Call Statistics report. Daily call data, which is available for the past 90 days, can help you diagnose problems with audio quality or rejected calls, and provide information for audits or reports on Exchange servers in your organization. 
  
For additional tasks related to UM reporting, see [UM reports procedures](um-reports-procedures.md).
  
## Use the EAC to export daily UM call records

1. In the EAC, navigate to **Unified messaging** \> **More options**![More Options Icon](../../media/ITPro_EAC_MoreOptionsIcon.gif) \> **Call statistics**.
    
2. Under **Show**, click **Daily (90 days)**, and then choose the UM dial plan or UM IP gateway, or both, if you want. The report automatically updates as you choose options.
    
3. Select the day for which you want to export call records, and then click **Export day**.
    
4. In the **File Download** confirmation box, click **Open** or **Save**.
    
    The exported file will be named um_cdr_ _YYYY-MM-DD_.csv, where  _YYYY-MM-DD_ is the year, month, and day the report was run. 
    
    > [!NOTE]
    > On the report page, you can download a Microsoft Excel template that you can use to import the .csv file for a specific day. 
  
5. Use an application such as Excel to process the .csv file and build your own custom reports. 
    
## Interpret UM call data

The UM call data that you export includes the following detailed information about each call that UM handled on that day.
  
> [!NOTE]
> In the Call Statistics report, the days are in UTC time. 
  
- **CallStartTime ** The date and time that UM handled the call, in UTC. The UTC time and date is represented in the following format:  _YYYY-MM-DD hh:mm:SSZ_, where  _YYYY_ = year,  _MM_ = month,  _DD_ = day,  _hh_ = hour, in 24-hour time,  _mm_ = minutes, ss = seconds. Z signifies Zulu, which is a way to denote UTC (like +  _hh_: _mm_ or -  _hh_: _mm_, which gives the time offset from UTC). Because all call times in this report are in UTC time, this will always be Z.
    
    For example, for a call placed on June 23, 2013 at 2:23pm, the call start time is shown as 2013-06-23 14:23:11Z.
    
- **Call Type ** The type of call: 
    
  - **Call Answering Voice Message** The call wasn't answered and was forwarded to the Exchange servers, and the caller left a voice message. 
    
  - **Call Answering Missed Call** The call wasn't answered and was forwarded to the Exchange servers, and the caller didn't leave a voice message. 
    
  - **Subscriber Access** A call was made to the subscriber access number. The caller signed in and was authenticated to UM with their extension and password to access email messages, calendars, and voice messages over the phone. 
    
  - **Auto Attendant** The call was answered by a UM auto attendant. These calls are typically calls in which the caller dialed your organization's main phone number. 
    
  - **Fax** A call was received in which a fax tone was detected. If you've configured fax partners, this call was sent to the fax partner. 
    
  - **PlayOnPhone** A call was placed by UM because the user clicked the Play on Phone button in a voice message in either Microsoft Outlook Web App or Outlook. 
    
  - **Find Me** An outbound call was placed by UM as a result of a Find Me rule in a call answering rule. 
    
  - **Unauthenticated Pilot Number** A call was placed to the Outlook Voice Access number. The caller didn't sign in and wasn't authenticated. 
    
  - **Greetings Recording** A call was placed by UM to record personal greetings for a user. 
    
  - **None** A call was placed but the type wasn't defined. 
    
- **CallIdentity** The SIP call identity, as provided by the UM IP gateway. 
    
- **ParentCallIdentity** The SIP Session Identity of the session that originated this call. This box is used when using the Call Answering Rules Find Me feature or call transfer calls, including call transfers between UM auto attendants. 
    
- **UMServerName** The name of the Mailbox server handling the call, if any. This information is provided only when you have an on-premises Mailbox server. 
    
- **DialPlanName** The UM dial plan that handled the call. 
    
- **Call Duration** The total duration of the call. 
    
- **IPGatewayAddress** The fully qualified domain name (FQDN) of the IP gateway that handled the call. 
    
- **CalledPhoneNumber** The phone number or SIP address of the intended recipient of the call (for users in SIP dial plans with Microsoft Office Communications Server 2007 R2 or Microsoft Lync Server) . 
    
- **CallerPhoneNumber** The phone number or SIP address of the caller. 
    
- **OfferResult** The status of the call: 
    
  - **Answer** UM successfully answered or placed a call. The call was neither transferred nor redirected. These calls include completed calls to Outlook Voice Access, Play on Phone, or UM auto attendants, and calls that UM handled when the called extension didn't answer the phone. 
    
  - **Failed** UM accepted or placed a call, but the call failed. These calls include calls where the called number or address is busy, doesn't answer, or doesn't exist; where the caller hung up before the call was connected; where the UM dial plan or UM mailbox policy settings prevented the call; or where the VoIP gateway or IP PBX on your telephone system couldn't be reached. 
    
  - **Rejected** UM rejected the call, usually because of a configuration error. These calls include calls where the UM IP gateway isn't associated with a UM dial plan, or where there are incompatibility issues. 
    
  - **Redirected** UM accepted the call, but redirected it to another Mailbox server. These calls include calls where the caller used the UM menu to call a contact in the directory or personal contacts, or where the caller called an Outlook Voice Access number using a phone number that isn't associated with the user's mailbox. In these cases, UM transfers the call to the Exchange server that's associated with that user's account. 
    
  - **None** The call status is unknown. 
    
- **DropCallReason** The reason the call was disconnected, if UM was able to determine the reason. For example, if the caller hung up, this shows Graceful Hangup. 
    
- **ReasonForCall** How the call was connected: 
    
  - **Direct** The caller dialed the called number directly. 
    
  - **DivertForward** The caller dialed a number, and the person being called redirected the call to UM voice mail. 
    
  - **DivertBusy** The caller dialed a number, and the phone was busy, so the call was redirected to UM voice mail. 
    
  - **DivertNoAnswer** The caller dialed a number, and the person didn't answer, so the call was redirected to UM voice mail. 
    
  - **Outbound** The call was placed by UM, for example, to play a voice message using Play on Phone. 
    
  - **None** No reason was reported for the call. 
    
- **DialedString** The address or phone number of the person to whom this call was either referred or transferred. This value also refers to the address or phone number called for Play on Phone calls. 
    
- **CallerMailboxAlias** The mailbox alias (the portion of the email address that precedes the @ symbol) of the caller. This value is only available if the caller signed in to Outlook Voice Access. 
    
- **CallerMailboxAlias** The mailbox alias of the intended recipient of the call, if the intended recipient is a UM-enabled user. 
    
- **Auto Attendant Name** The name of the auto attendant related to this call. 
    
- **NMOS Score** The Network Mean Opinion Score (NMOS) for the call. The NMOS indicates how good the audio quality was on the call as a number on a scale from 1 to 5, with 5 being excellent. 
    
    > [!NOTE]
    > **Note** The maximum NMOS possible for a call depends on the audio codec being used. The NMOS may not be available for very short calls that are less than 10 seconds long. 
  
- **NMOSDegradation** The amount of audio degradation of the NMOS from the top value possible for the audio codec being used. For example, if the NMOS degradation value for a call was 1.2 and the NMOS reported for the call was 3.3, the maximum NMOS for that particular call would be 4.5 (1.2 + 3.3). 
    
- **NMOSDegradation Jitter** The total NMOS degradation due to jitter. 
    
- **NMOSDegradation PacketLoss** The total NMOS degradation because of packet loss. 
    
- **Jitter** The average variation in the arrival of data packets for the call. 
    
- **PacketLoss** The average percentage of data packet loss for the selected call. Packet loss is an indication of the reliability of the connection. 
    
- **Round Trip** The average round trip, in milliseconds, for audio on the selected call. The round-trip score measures latency on the connection. 
    
- **BurstDensity** The percentage of packets lost and discarded within a burst (high loss rate) period. 
    
- **Burst Gap duration** The average duration of packet loss during bursts of losses for the selected call. 
    
- **Audio Codec** The audio codec used during the call. 
    

