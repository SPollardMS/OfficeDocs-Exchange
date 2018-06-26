---
title: "Message Trace FAQ"
ms.author: tirich
author: tirich
manager: scotv
ms.date: 6/25/2018
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: aa49e3f9-a5b1-4410-aac2-ddbbf3f5bfb2
description: "This topic presents messaging questions that a user may have, along with possible answers. It also describes how to use the message trace tool in order to get those answers and troubleshoot specific mail delivery issues."
---

# Message Trace FAQ

This topic presents messaging questions that a user may have, along with possible answers. It also describes how to use the message trace tool in order to get those answers and troubleshoot specific mail delivery issues.
  
## How long does it take to see results when running a message trace? And how long does it take when a message is sent for it to be available to search in the message trace?
<a name="BKMB_Howlongdoesittakewhenamessageissentforittoappear"> </a>

When you run a message trace for messages less than 7 days old, the search results appear immediately. When such a message is sent to a recipient, it should take between 5-10 minutes to appear in the message trace data.
  
When you run a message trace for messages greater than 7 days old, the search results may take up to a few hours.
  
## Can I run a message trace via remote Windows PowerShell rather than the user interface?
<a name="CanIrunamessagetraceviaremoteWindowsPowerShell"> </a>

You can use the following remote Windows PowerShell cmdlets to run a message trace:
  
[Get-MessageTrace](http://technet.microsoft.com/library/5e5134f2-b887-4840-9dff-cea9ec8fde72.aspx) - Use this cmdlet to trace messages that are less than 7 days old. 
  
[Get-MessageTraceDetail](http://technet.microsoft.com/library/27e9b80c-66db-4038-b93e-edd68fe86a12.aspx) - Use this cmdlet to view the message trace event details for a specific message. 
  
[Get-HistoricalSearch](http://technet.microsoft.com/library/70f2ec73-2733-4f87-ac89-1665d575a4dc.aspx) Use this cmdlet to view information about historical searches that have been performed within the last ten days. 
  
[Start-HistoricalSearch](http://technet.microsoft.com/library/9688689c-2953-49de-bb38-eeea10b7f08e.aspx) - Use this cmdlet to start a new historical search. 
  
[Stop-HistoricalSearch](http://technet.microsoft.com/library/8868372f-842b-417d-acb2-8c08a914a779.aspx)- Use this cmdlet to stop an existing historical search that has a status value of NotStarted.
  
To learn how to use Windows PowerShell to connect to Exchange Online Protection, see [Connect to Exchange Online Protection Using Remote PowerShell](http://technet.microsoft.com/library/054e0fd7-d465-4572-93f8-a00a9136e4d1.aspx). To learn how to use Windows PowerShell to connect to Exchange Online, see [Connect to Exchange Online Using Remote PowerShell](http://technet.microsoft.com/library/c8bea338-6c1a-4bdf-8de0-7895d427ee5b.aspx).
  
## Why am I getting a timeout error when running a message trace in the user interface?
<a name="BKMB_WhyamIgettingatimeouterror"> </a>

The likely cause of a timeout error is that the query is taking too long to process. Consider simplifying your search criteria. You may want to consider using remote PowerShell, which has more liberal timeout requirements. 
  
## Why didn't I receive an expected email message?
<a name="BKMB_WhydidntIreceiveanexpectedemailmessage"> </a>

Possible reasons include the following:
  
- The message was detected as spam.
    
- The message was sent to quarantine due to a rule match.
    
- The message was rejected
    
  - By the malware filter
    
  - Because a file attached to the message contained malware
    
  - Because the message body contained malware
    
  - By a rule
    
  - Because the action was Reject
    
  - Because the action was Force TLS and TLS failed to be established
    
  - By a connector because TLS was required and failed to be established
    
- The message was sent for moderation and is awaiting approval or was rejected by the moderator.
    
- The message was never sent.
    
- The message is still being processed because there was a previous failure and the service is re-attempting delivery.
    
- The message failed to be delivered to your mailboxes
    
  - Because the destination is not reachable
    
  - Because the destination rejected the message
    
  - Because the message timed out during the delivery attempt
    
To find out what happened, run the message trace (see [Run a message trace](run-a-message-trace-and-view-results.md#BKMK_Runamessagetrace)). Try to specify parameter values in a manner that will best narrow down your search results. For example, you should know the sender and the intended recipient or recipients of the message, and the general time period during which it was sent. View the results, locate the message, and then view specific details about the message (see [View message trace results for messages that are less than 7 days old](run-a-message-trace-and-view-results.md#BKMK_Viewmessagetracefesultsformessagesthatarelessthan7daysold) or [View message trace results for messages that are more than 7 days old](run-a-message-trace-and-view-results.md#BKMK_Viewmessagetracefesultsformessagesthataregreaterthan7daysold)). Look for a delivery status of **Failed** or **Pending** to explain why the message was not received. Confirm that the message was sent, that it was successfully received by the service, that it was not filtered, redirected, or sent for moderation, and that it did not experience any delivery failures or delays. 
  
## Why did I receive an unexpected message?
<a name="BKMB_WhydidIreceiveanunexpectedmessage"> </a>

Possible reasons include the following:
  
- The message was released from quarantine.
    
- The message was awaiting moderator approval and was released.
    
- The message was spam that was not detected.
    
- The message matched a rule that added you to the message.
    
- The message was sent to a distribution list of which you are a member.
    
To find out what happened, run the message trace (see [Run a message trace](run-a-message-trace-and-view-results.md#BKMK_Runamessagetrace)). Try to specify parameter values in a manner that will best narrow down your search results. For example, specify the recipient who received the message, set the delivery status to **Delivered**, and set the time period based on when the message was received. View the results, locate the message, and then view specific details about the message (see [View message trace results for messages that are less than 7 days old](run-a-message-trace-and-view-results.md#BKMK_Viewmessagetracefesultsformessagesthatarelessthan7daysold) or [View message trace results for messages that are more than 7 days old](run-a-message-trace-and-view-results.md#BKMK_Viewmessagetracefesultsformessagesthataregreaterthan7daysold)) One of the above-listed unforeseen events is likely the cause of your receiving the message.
  
## Why didn't someone receive my message or why did I get this non-delivery report (NDR)?
<a name="BKMB_Whydidntsomeonereceivemymessage"> </a>

Possible reasons include the following:
  
- The message was detected as spam.
    
- The message was sent to quarantine due to a rule match.
    
- The message was re-routed because a connector sent it to another destination.
    
- The message was rejected
    
  - By the malware filter
    
  - Because a file attached to the message contained malware
    
  - Because the message body contained malware
    
  - By a rule
    
  - Because the action was Reject
    
  - Because the action was Force TLS and TLS failed to be established
    
  - By a connector because TLS was required and failed to be established
    
- The message was sent for moderation and is awaiting approval or was rejected by the moderator.
    
- The message was never sent.
    
- The message is still being processed because there was a previous failure and the service is re-attempting delivery.
    
- The message failed to be delivered to the destination
    
  - Because the destination is not reachable
    
  - Because the destination rejected the message
    
  - Because the message timed out during the delivery attempt
    
- The message was delivered to the destination but it was deleted before it was accessed (perhaps because it matched a rule).
    
To find out what happened, run the message trace (see [Run a message trace](run-a-message-trace-and-view-results.md#BKMK_Runamessagetrace)). Try to specify parameter values in a manner that will best narrow down your search results. For example, you should know the sender and the intended recipient or recipients of the message, and the general time period during which it was sent. View the results, locate the message, and then view specific details about the message (see [View message trace results for messages that are less than 7 days old](run-a-message-trace-and-view-results.md#BKMK_Viewmessagetracefesultsformessagesthatarelessthan7daysold) or [View message trace results for messages that are more than 7 days old](run-a-message-trace-and-view-results.md#BKMK_Viewmessagetracefesultsformessagesthataregreaterthan7daysold)) Look for a delivery status of **Failed** or **Pending** to explain why the message was not delivered. Confirm that the message was sent, that it was successfully received by the service, that it was not filtered, redirected, or sent for moderation, and that it did not experience any delivery failures or delays. If the destination is not reachable, you can use the **To IP** to help troubleshoot connectivity issues. 
  
## Why is my message taking so long to arrive to its destination? Where is it in the pipeline?
<a name="BKMB_Whyismymessagetakingsolong"> </a>

Possible reasons include the following:
  
- The intended destination is not responsive. This is the most likely scenario.
    
- It may be a large message that is taking a long time to process
    
- Latency in the service may be causing delays
    
- The message may have been blocked, in which case you should refer to [Why didn't someone receive my message or why did I get this non-delivery report (NDR)?](message-trace-faq.md#BKMB_Whydidntsomeonereceivemymessage)
    
To find out what happened, run the message trace (see [Run a message trace](run-a-message-trace-and-view-results.md#BKMK_Runamessagetrace)). Try to specify parameter values in a manner that will best narrow down your search results. For example, you should know the sender and the intended recipient or recipients of the message, and the general time period during which it was sent. View the results, locate the message, and then view specific details about the message (see [View message trace results for messages that are less than 7 days old](run-a-message-trace-and-view-results.md#BKMK_Viewmessagetracefesultsformessagesthatarelessthan7daysold) or [View message trace results for messages that are more than 7 days old](run-a-message-trace-and-view-results.md#BKMK_Viewmessagetracefesultsformessagesthataregreaterthan7daysold)) The events section will tell you why the message was not yet delivered. When viewing the events, the timestamp information will let you follow the message through the messaging pipeline, and tell you how long the service takes to process each event. The event details will also inform you if the message being delivered is extremely large or if the destination is not responsive.
  
## Was a message marked as spam?
<a name="BKMB_Whywasamessagemarkedasspam"> </a>

Messages can be marked as spam for several reasons. For example, the sending IP address may appear on one of the service's IP Block lists. A message can be marked as spam due to the content of the actual message, such as when it matches a rule in the spam content filter. The message trace tool only tracks spam content filter events; connection filter events (such as blocked IP addresses) are not traceable. For more information about spam filtering, including spam content filtering, see [Anti-Spam Protection](http://technet.microsoft.com/library/d5c58b9d-c9a2-4f2e-b4aa-b202aa4d5e7d.aspx). 
  
To find out why a message was marked as spam, run the message trace (see [Run a message trace](run-a-message-trace-and-view-results.md#BKMK_Runamessagetrace)), locate the message in the results, and then view specific details about the message (see [View message trace results for messages that are less than 7 days old](run-a-message-trace-and-view-results.md#BKMK_Viewmessagetracefesultsformessagesthatarelessthan7daysold) or [View message trace results for messages that are more than 7 days old](run-a-message-trace-and-view-results.md#BKMK_Viewmessagetracefesultsformessagesthataregreaterthan7daysold)). When the content filter marks a message as spam, if it is sent to the Junk Email folder or the quarantine, it will have a status of **Delivered**. You can view the event details in order to see how the message arrived at its destination. For example, it may inform you that the message was determined to have a high spam confidence level, or that an advanced spam filtering option was matched. You will also be informed of the action that occurred as a result of the message being marked as spam, for example if it was sent to quarantine, stamped with an X-header, or if it was sent through the high risk delivery pool.
  
## Was a message detected to contain malware?
<a name="BKMB_Whywasamessagedetectedtocontainmalware"> </a>

Messages are detected as malware when its properties, either in the message body or in an attachment, match a malware definition in of one of the anti-malware engines. For more detailed information about malware filtering, see [Anti-Malware Protection](http://technet.microsoft.com/library/0e39a0ce-ab8b-4820-8b5e-93fbe1cc11e8.aspx). 
  
To find out why a message was detected to contain malware, run the message trace (see [Run a message trace](run-a-message-trace-and-view-results.md#BKMK_Runamessagetrace)). Try to specify parameter values in a manner that will best narrow down your search results. Set the delivery status to **Failed**. View the results, locate the message, and then view specific details about the message (see [View message trace results for messages that are less than 7 days old](run-a-message-trace-and-view-results.md#BKMK_Viewmessagetracefesultsformessagesthatarelessthan7daysold) or [View message trace results for messages that are more than 7 days old](run-a-message-trace-and-view-results.md#BKMK_Viewmessagetracefesultsformessagesthataregreaterthan7daysold)) If the message was not delivered because it was determined to contain malware, this information will be provided in the events section. For example, the following is a sample **Detail**: Malware: " *ZipBomb*  " was detected in attachment  *file*  .  *zip*  . You will also be informed of the action that occurred as a result of the message containing malware, for example if the entire message was blocked or if all attachments were deleted and replaced with an alert text file. 
  
## Which transport rule or DLP policy was applied to a message?
<a name="BKMB_Whichtransportruleordlppolicy"> </a>

To find out which transport rule (custom policy rule) or Data Loss Prevention (DLP) policy (Exchange Online customers only) was applied to a message, run the message trace (see [Run a message trace](run-a-message-trace-and-view-results.md#BKMK_Runamessagetrace)). Try to specify parameter values in a manner that will best narrow down your search results. Set the delivery status to **Failed**. View the results, locate the message, and then view specific details about the message (see [View message trace results for messages that are less than 7 days old](run-a-message-trace-and-view-results.md#BKMK_Viewmessagetracefesultsformessagesthatarelessthan7daysold) or [View message trace results for messages that are more than 7 days old](run-a-message-trace-and-view-results.md#BKMK_Viewmessagetracefesultsformessagesthataregreaterthan7daysold)) If the message was not delivered because its contents matched a rule, the events section will let you know the name of the transport rule that was matched. You will also be informed of the action that occurred as a result of the transport rule match, for example if the message was quarantined, rejected, redirected, sent for moderation, decrypted, or any number of other possible options. For information about how to create Exchange transport rules and set actions for them, see [Mail flow rules (transport rules) in Exchange Online](../../security-and-compliance/mail-flow-rules/mail-flow-rules.md). 
  
## When I run a message trace it returns rule ID-1. What does this mean?
<a name="BKMB_WhenIrunamessagetraceitreturnsfuleID1"> </a>

Rule ID-1 is returned when the message trace encounters a transport rule that no longer exists. (The transport rule could have been modified or deleted after the original message was sent.)
  
## Are there any known limitations or behavior clarifications that I should be aware of when using the message trace tool?
<a name="BKMB_Arethereanyknownlimitations"> </a>

You should be aware of the following when using the message trace tool: 
  
- **IP-blocked messages:** Messages blocked by IP reputation block lists will be included in the spam data for real time reports, but you cannot perform a message trace on these messages. 
    
- **Redirected messages:** If a recipient is rewritten by a transport rule or because the spam action for the domain is set to **Redirect to email address**, the message is not traceable in a single search. The original message can be traced until to the point when the recipient is changed. After that, the message is not traceable under the original recipient. You can trace the message again using the new recipient.
    
- **MAIL FROM:** The message trace tool uses the MAIL FROM value presented at the initiation of the SMTP conversation as the Sender in a search, regardless of what the DATA section of the message shows. The message may show a Reply-to address or different From: or Sender values. If the email message was sent by a process and not by an email client, there is an increased likelihood that the sender in the MAIL FROM will not match the sender in the actual message. 
    
- **Transport rule updates:** When a message matches a transport rule, the rule ID is stored in the message trace and real time reporting databases. If you trace one of these messages, or drill down on rule details in a report, the message trace and real time reporting user interfaces dynamically pull the current rule information from the hosted services network based on the rule ID in the reporting database. If you have changed the attributes of that particular rule since the message was processed (changed it from Reject to Allow, for example), the rule ID stays the same in the message trace and real time reporting returned results, but the Exchange admin center will show the new transport rule properties. You can use the auditing reports feature in order to determine when the rule was changed and the properties that were changed. 
    
- **Spam-filtered messages**: When the content filter marks a message as spam, if it is sent to the Junk Email folder or the quarantine, it will have a status of **Delivered**. Drill down to the event details in order to see how the message arrived at its destination. 
    
## For more information
<a name="BKMB_Arethereanyknownlimitations"> </a>

[Trace an email message](trace-an-email-message.md)
  
[Help and Support for EOP](http://technet.microsoft.com/library/64535a0a-1044-413f-8bc2-ed8e8a0bc54c.aspx)
  

