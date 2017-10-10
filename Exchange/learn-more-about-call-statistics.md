---
title: Learn more about call statistics
ms.prod: EXCHANGE
ms.assetid: 581afd8f-7082-48a2-adbc-566c874df102
---


# Learn more about call statistics

Use the UM Call Statistics report to view information about the type and status of incoming calls handled by Mailbox servers in your organization that are running the Microsoft Exchange Unified Messaging (UM) service. The report provides statistical information about the calls forwarded to or placed by UM. You can use this information to monitor and troubleshoot the availability and audio quality of UM in your organization, track usage for capacity planning, and troubleshoot audio quality and failed calls. 
  
    
    


> [!NOTE]
> Microsoft Office Communications Server 2007 R2 and Microsoft Lync Server notifications about missed calls—where the caller hangs up before the call is redirected to UM—aren't included in this report because they're handled directly by the servers running Communications Server 2007 R2 and Lync Server. 
  
    
    

This topic explains the following:
-  [How do I get call statistics for UM?](#howto)
    
  
-  [How do I interpret UM call statistics?](#interpret)
    
  

## How do I get call statistics for UM?
<a name="howto"> </a>


1. In the EAC, click **Unified messaging** >
  
    
    
![More Options icon](images/ITPro_EAC_MoreOptionsIcon.png)
  
    
    
 > **Call statistics**.
    
  
2. Choose what information to include in the report. The report automatically updates as you select any of the following options:
    
  - **Show** Choose what type of call statistics to view:
    
    • **Daily (90 days)** Select Daily to see details for all calls in the past 90 days.
    
    • **Monthly (12 months)** Select Monthly to see a summary of calls by month for the last 12 months.
    
    • **All** Select All to see the combined statistics for all calls received since UM started handling calls.
    
  
  - **UM dial plan** If you want to limit the data in the report to only calls in a specific UM dial plan, select that dial plan.
    
  
  - **UM IP gateway** If you want to limit the data in the report to only calls in a specific UM IP gateway, select that gateway. If you select a UM dial plan first, only the UM IP gateways associated with the selected UM dial plan are available in the list.
    
  
3. To get more details about the audio quality for a row in the report, select the row and click **Audio Quality Details**. 
    
  
4. To copy the report to the Clipboard, click **Copy**.
    
  
5. For daily reports, you can export the details for a specific day to a .csv file.
    
1. Select the day and click **Export Day**.
    
  
2. In the **File Download** confirmation, click **Open** or **Save**.
    
  

    The exported file will be named um_cdr_ _YYYY-MM-DD_.csv, where  _YYYY-MM-DD_ is the year, month, and day the report was run.
    
    > [!NOTE]
      > On the report page, you can download a Microsoft Excel template to use to import the .csv file for a specific day. 
 [Return to top](#Introduction)
  
    
    

## How do I interpret UM call statistics?
<a name="interpret"> </a>

The UM Call Statistics report includes the following information:
  
    
    

- **DATE** The UTC date for the call data. The date format depends on the type of report you've chosen and your locale settings:
    
  - **---** All calls are shown.
    
  
  - **MMM/YY** The month of the calls. For example, Jan/10.
    
  
  - **MM/DD/YY** The day of the calls. For example, 6/23/10.
    
  
- **TOTAL** The total number of calls for the selected UM dial plan or UM IP gateway for that date.
    
  
- **VOICE MESSAGE** The percentage of incoming calls answered by UM on behalf of users in which callers left a voice message.
    
  
- **MISSED** The percentage of incoming calls answered by UM on behalf of users in which the callers didn't leave a voice message, resulting in a missed call notification.
    
  
-     > [!CAUTION]
      > Missed call notifications aren't available to users who have a mailbox located on an Exchange 2007 or Exchange 2010 Mailbox server when you're integrating Unified Messaging and Lync Server. 
- **OUTLOOK VOICE ACCESS** The percentage of incoming calls where users signed in to UM to access their email, calendars, and voice messages (and were authenticated).
    
  
- **OUTGOING** The percentage of calls that were placed or transferred by UM on behalf of authenticated or unauthenticated users. This statistic includes Find Me, Play On Phone, and Play On Phone Greetings call types.
    
  
- **AUTO ATTENDANT** The percentage of incoming calls that were answered by UM auto attendants.
    
  
- **FAX** The percentage of incoming calls that were redirected to a fax partner.
    
  
- **OTHER** The percentage of incoming or placed calls that don't fall in any of the categories mentioned earlier. These include calls made to Outlook Voice Access numbers where the users didn't sign in and weren't authenticated.
    
  
- **FAILED OR REJECTED** The percentage of calls that either failed or were rejected by UM. Note that failed calls aren't counted twice. For example, if a call to Outlook Voice Access fails, it's counted only as a failed call, and not also as an Outlook Voice Access call.
    
  
- **AUDIO QUALITY** A graphical representation of the overall audio quality for the selected period of time for the organization.
    
  
 [Return to top](#Introduction)
  
    
    

