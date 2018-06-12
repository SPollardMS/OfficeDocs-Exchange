---
title: "Delivery reports for administrators"
ms.author: chrisda
author: chrisda
manager: serdars
ms.date: 6/7/2018
ms.audience: ITPro
ms.topic: overview
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: d98623d3-e0b7-4cb9-93fb-6351b4a06137
description: "Summary: Learn how administrators can track delivery information about messages sent or received from any mailbox in the organization."
---

# Delivery reports for administrators

 **Summary**: Learn how administrators can track delivery information about messages sent or received from any mailbox in the organization.
  
With delivery reports for administrators, you can track delivery information about messages sent by or received from any specific mailbox in your organization. Specifically, delivery reports for administrators uses the Exchange admin center (EAC) to perform a targeted search of the message tracking logs. The search is always scoped to a specific mailbox. You can search for messages sent by the mailbox, or sent to the mailbox, and you can filter the search results by the message subject.
  
The content of the message body isn't returned in a delivery report, but the subject line is displayed in the results. If you want to search the mailboxes in your organization for specific email messages based on message content, see [In-Place eDiscovery in Exchange 2016](../../policy-and-compliance/ediscovery/ediscovery.md).
  
You may find delivery report searches useful in the following situations:
  
- A manager gives a poor review for a trainee because the trainee didn't turn in an assignment on time. The trainee insists he sent a message with the assignment attached. The manager asks you to verify the status of the message.
    
- A security bulletin has been sent to users asking that they reply immediately, but no one has replied. Are they ignoring the message or did they just not receive it?
    
- Users complain that no one is receiving their messages. They check delivery status for their mail but can't figure out what is going on. This may be because a rule is being applied to messages at the organization level.
    
After you create a delivery report search, the resulting delivery report will show the following information: Who the message was sent from and to, the subject line, and when the message was sent. The delivery report also shows message delivery status and reasons why delivery may be delayed or failed.
  
## More about delivery reports

- Here's how administrators in on-premises Exchange organizations create delivery reports: [Track messages with delivery reports](track-messages-with-delivery-reports.md).
    
- Ordinary users can use a targeted version of delivery reports to track their own messages. For more information, see [Delivery Reports for Users](https://go.microsoft.com/fwlink/p/?LinkId=279920).
    
- A more powerful option for administrators in on-premises Exchange organizations is to use the Exchange Management Shell to query the message tracking logs directly. For more information, see [Search message tracking logs](search-message-tracking-logs.md).
    
- Exchange 2016 delivery reports can track messages across Exchange 2016 and Exchange 2013 servers in the same Active Directory site.
    

