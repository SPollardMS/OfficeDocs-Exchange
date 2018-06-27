---
title: "Review the voice mail calls in your organization"
ms.author: tonysmit
author: tonysmit
manager: scotv
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.service: exchange-online
localization_priority: Normal
ms.assetid: f6fdbe17-d1d2-442a-aa13-06b908d9c33a

---

# Review the voice mail calls in your organization
You can use the Call Statistics report to view information about the type and status of incoming calls handled by the Exchange servers in your organization. The report provides statistical information about the calls forwarded to or placed by Unified Messaging (UM) for your organization. You can use this information to track usage for capacity planning, monitor and troubleshoot the availability and audio quality of UM, and to troubleshoot failed calls. 
  
This topic answers these questions:
  
- [How do I get call statistics for UM?](#howto.md)
    
- [How do I interpret UM call statistics?](#interpret.md)
    
For additional tasks related to UM reporting, see [UM reports procedures](um-reports-procedures.md).
  
## How do I get call statistics for UM?
<a name="howto"> </a>

1. In the Exchange admin center (EAC), click **Unified messaging** \> **More options**![More Options Icon](../../media/ITPro_EAC_MoreOptionsIcon.gif) \> **Call statistics**.
    
2. Choose the information you want to include in the report. The report automatically updates as you select any of the following options:
    
  - **Show** Choose what type of call statistics to view: 
    
  - **Daily (90 days)** Select Daily to see details for all calls in the past 90 days. 
    
  - **Monthly (12 months)** Select Monthly to see a summary of calls by month for the last 12 months. 
    
  - **All** Select All to see the combined statistics for all calls received since UM started handling calls. 
    
  - **UM dial plan** If you want to limit the data in the report to only calls in a specific UM dial plan, select that dial plan. 
    
  - **UM IP gateway** If you want to limit the data in the report to only calls in a specific UM IP gateway, select that gateway. If you select a UM dial plan first, only the UM IP gateways associated with the selected UM dial plan are available in the list. 
    
3. To get more details about the audio quality for a row in the report, select the row and click **Audio Quality Details**. For more information about how to interpret audio quality, see [Investigate the audio quality of voice calls in your organization](audio-quality-of-voice-calls-in-organization.md).
    
4. To copy the report to the Clipboard, click **Copy**.
    
5. For Daily reports, you can export the details for a specific day to a .csv file.
    
1. Select the day and click **Export day**.
    
2. In the **File Download** confirmation box, click **Open** or **Save**.
    
    The exported file will be named um_cdr_ _YYYY-MM-DD_.csv, where  _YYYY-MM-DD_ is the year, month, and day the report was run. For more information, see [Interpret voice mail call records](interpret-voice-mail-call-records.md).
    
    > [!NOTE]
    > On the report page, you can download a Microsoft Excel template that you can use to import the .csv file for a specific day. 
  
[Return to top](#Introduction.md)
  
## How do I interpret UM call statistics?
<a name="interpret"> </a>

The UM Call Statistics report includes the following information:
  
- **DATE** The UTC date for the call data. The date format depends on the type of report you've chosen and your locale settings. You can choose from the following options: 
    
  - **---** All calls are shown. 
    
  - **MMM/YY** The month of the calls. For example, Jan/13. 
    
  - **MM/DD/YY** The day of the calls. For example, 6/23/13. 
    
- **TOTAL** The total number of calls for the selected UM dial plan or UM IP gateway for that date. 
    
- **VOICE MESSAGE** The percentage of incoming calls answered by UM on behalf of users in which callers left a voice message. 
    
- **MISSED** The percentage of incoming calls answered by UM on behalf of users in which callers didn't leave a voice message, resulting in a missed call notification. 
    
- **OUTLOOK VOICE ACCESS** The percentage of incoming calls where users signed in to UM (and were authenticated) to access their email messages, calendars, and voice messages. 
    
- **OUTGOING** The percentage of calls that were placed or transferred by UM on behalf of authenticated or unauthenticated users. This statistic includes Find Me, Play on Phone, and Play on Phone Greetings call types. 
    
- **AUTO ATTENDANT** The percentage of incoming calls that were answered by UM auto attendants. 
    
- **FAX** The percentage of incoming calls that were redirected to a fax partner. 
    
- **OTHER** The percentage of any other incoming or placed calls that do not fall in any of the above categories. These calls include calls made to Outlook Voice Access numbers where the users didn't sign in and weren't authenticated. 
    
- **FAILED OR REJECTED** The percentage of calls that either failed or were rejected by UM. Note that failed calls aren't counted twice. For example, if a call to Outlook Voice Access fails, it is only counted as a Failed call, and not also as an Outlook Voice Access call. 
    
- **AUDIO QUALITY** A graphical representation of the overall audio quality for the selected period of time for the organization. 
    
[Return to top](#Introduction.md)
  
## For more information
<a name="fmi"> </a>

[Investigate the audio quality of voice calls in your organization](audio-quality-of-voice-calls-in-organization.md)
  
[Interpret voice mail call records](interpret-voice-mail-call-records.md)
  

