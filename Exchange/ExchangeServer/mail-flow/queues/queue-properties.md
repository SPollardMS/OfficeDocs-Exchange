---
title: "Queue properties"
ms.author: chrisda
author: chrisda
manager: serdars
ms.date: 6/8/2018
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: fbfbdcab-e0d2-4ed9-8f7f-e5fa2c87360d
description: "Summary: Learn about queue properties to use in filters in Exchange 2016."
---

# Queue properties

 **Summary**: Learn about queue properties to use in filters in Exchange 2016.
  
Filtering queues by one or more queue properties in Exchange Server 2016 allows you to quickly find and take action on those queues. The following scenarios are examples of how you might use queue filtering to manage mail flow:
  
- You receive a message from System Center Operations Manager that indicates a queue length has exceeded the established threshold. You want to investigate whether a server-wide mail flow problem exists.
    
    You create a filter to view all the queues on a server whose message count exceeds what you consider to be typical. If a mail flow problem is indicated, you can select all the queues in the results and suspend the queues while you continue to investigate.
    
- You suspend several queues to investigate the cause of mail flow problems. You determine that the problem was caused by an incorrect connector configuration that is now fixed.
    
    You can create a filter to view all the queues that have a status of Suspended, and then select all the queues in the filter results and resume the queues.
    
You can create queue filters in Queue Viewer in the Exchange Toolbox, or by using the  _Filter_ parameter on the queue management cmdlets. Note that the queue management cmdlets support more filterable properties than Queue Viewer. 
  
For more information about Queue Viewer, see [Queue Viewer](queue-viewer.md). For more information about the queue management cmdlets, see [Procedures for queues](queue-procedures.md) and [Find queues and messages in queues in the Exchange Management Shell](queues-and-messages-in-powershell.md).
  
## Queue properties to use as filters

 The following table describes the queue properties that you can use as filters in Queue Viewer and the Exchange Management Shell. 
  
|**Queue Viewer**|**Exchange Management Shell**|**Comparison operators**|**Description**|
|:-----|:-----|:-----|:-----|
|n/a  <br/> | `DeferredMessageCount` <br/> |Equals ( `-eq`)  <br/> Does not equal ( `-ne`)  <br/> Greater than ( `-gt`)  <br/> Greater than or equal to ( `-ge`)  <br/> Less than ( `-lt`)  <br/> Less than or equal to ( `-le`)  <br/> |The number of messages returned to the Submission queue because of transient errors that were encountered during recipient resolution. For more information about deferred messages, see [Recipient resolution in Exchange 2016](../../mail-flow/mail-routing/recipient-resolution.md).  <br/> |
|n/a  <br/> | `DDeferredMessageCountsPerPriority` <br/> |Equals ( `-eq`)  <br/> Does Not Equal ( `-ne`)  <br/> Contains ( `-like`)  <br/> |An array that shows the number of deferred messages in the queue by priority (importance) value. The **MessageCountsPerPriority** property shows what each number means.  <br/> For example, the value  `{1, 5, 10, 0}` indicates the queue contains 1 deferred High priority message, 5 deferred Normal priority messages, 10 deferred Low priority messages, and no deferred messages that have the priority value None.  <br/> |
|**Delivery Type** <br/> | `DeliveryType` <br/> |**Equals** (  `-eq`)  <br/> **Does Not Equal** (  `-ne`)  <br/> |The results of the categorization of the message, and how the Transport service intends to transmit the message to the next hop. For a list of the available **DeliveryType** values, see [NextHopSolutionKey](queues.md#NextHopSolutionKey).  <br/> |
|n/a  <br/> | `FirstRetryTime` <br/> |Equals ( `-eq`)  <br/> Does not equal ( `-ne`)  <br/> Greater than ( `-gt`)  <br/> Greater than or equal to ( `-ge`)  <br/> Less than ( `-lt`)  <br/> Less than or equal to ( `-le`)  <br/> |The date/time of the first connection attempt for a queue that has a status of  `Retry`. For more information, see [Message retry, resubmit, and expiration intervals](message-intervals.md).  <br/> |
|n/a  <br/> | `Identity` <br/> |n/a  <br/> |The identity of the queue in the form of  _\<Server\>_\ _\<Queue\>_. For more information see [Queue identity](queues-and-messages-in-powershell.md#QueueIdentity).  <br/> |
| n/a  <br/> | `IncomingRate` <br/> |Equals ( `-eq`)  <br/> Does not equal ( `-ne`)  <br/> Greater than ( `-gt`)  <br/> Greater than or equal to ( `-ge`)  <br/> Less than ( `-lt`)  <br/> Less than or equal to ( `-le`)  <br/> |A calculated number that indicates how quickly messages are entering the queue. For more information, see [IncomingRate, OutgoingRate, and Velocity](queues.md#RatesAndVelocity).  <br/> |
|**Last Error** <br/> | `LastError` <br/> |**Equals** (  `-eq`)  <br/> **Does Not Equal** (  `-ne`)  <br/> **Contains** (  `-contains`)  <br/> **Is Present** <br/> **Is Not Present** <br/> |The last error that was recorded for the queue. For more information about SMTP error codes, see [DSNs and NDRs in Exchange 2016](../../mail-flow/non-delivery-reports-and-bounce-messages/non-delivery-reports-and-bounce-messages.md).  <br/> |
|**Last Retry Time** <br/> | `LastRetryTime` <br/> |**Greater Than** (  `-gt`)  <br/> **Greater Than or Equals** (  `-ge`)  <br/> **Less Than** (  `-lt`)  <br/> **Less Than or Equals** (  `-le`)  <br/> **Is Present** <br/> **Is Not Present** <br/> |The date/time of the last connection attempt for a queue that has a status of  `Retry`. For more information, see [Message retry, resubmit, and expiration intervals](message-intervals.md).  <br/> |
|n/a  <br/> | `LockedMessageCount` <br/> |n/a  <br/> |This property is reserved for internal Microsoft use, and isn't used in on-premises Exchange organizations.  <br/> |
|**Message Count** <br/> | `MessageCount` <br/> |**Equals** (  `-eq`)  <br/> **Does Not Equal** (  `-ne`)  <br/> **Greater Than** (  `-gt`)  <br/> **Greater Than or Equals** (  `-ge`)  <br/> **Less Than** (  `-lt`)  <br/> **Less Than or Equals** (  `-le`)  <br/> |The number of messages in the queue.  <br/> |
|n/a  <br/> | `MessageCountsPerPriority` <br/> |Equals ( `-eq`)  <br/> Does Not Equal ( `-ne`)  <br/> Contains ( `-like`)  <br/> |An array that shows the number of messages in the queue by priority (importance) value. The **MessageCountsPerPriority** property shows what each number means.  <br/> For example, the value  `{1, 100, 10, 0}` indicates the queue contains 1 High priority message, 100 Normal priority messages, 10 Low priority messages, and no messages that have the priority value None.  <br/> For more information about priority queuing, see [Priority Queuing](http://technet.microsoft.com/library/6edbd826-fe55-435b-9c63-48e6365c3d09.aspx).  <br/> |
| n/a  <br/> | `NextHopCategory` <br/> |Equals ( `-eq`)  <br/> Does Not Equal ( `-ne`)  <br/> |The value  `Internal` or  `External` for the next hop based on the value of the **DeliveryType** property. For more information, see [NextHopSolutionKey](queues.md#NextHopSolutionKey).  <br/> |
|n/a  <br/> | `NextHopConnector` <br/> |Equals ( `-eq`)  <br/> Does Not Equal ( `-ne`)  <br/> Contains ( `-like`)  <br/> |The GUID of the next hop based on the value of the **DeliveryType** property. For more information, see [NextHopSolutionKey](queues.md#NextHopSolutionKey).  <br/> |
|**Next Hop Domain** <br/> | `NextHopDomain` <br/> |**Equals** (  `-eq`)  <br/> **Does Not Equal** (  `-ne`)  <br/> **Contains** (  `-like`)  <br/> |The name of next hop based on the value of the **DeliveryType** property. For more information, see [NextHopSolutionKey](queues.md#NextHopSolutionKey).  <br/> |
|**Next Retry Time** <br/> | `NextRetryTime` <br/> |**Greater Than** (  `-gt`)  <br/> **Greater Than or Equals** (  `-ge`)  <br/> **Less Than** (  `-lt`)  <br/> **Less Than or Equals** (  `-le`)  <br/> **Is Present** <br/> **Is Not Present** <br/> |The date/time of the next connection attempt for a queue that has a status of  `Retry`. For more information, see [Message retry, resubmit, and expiration intervals](message-intervals.md).  <br/> |
|n/a  <br/> | `OutboundIPPool` <br/> |n/a  <br/> | This property is reserved for internal Microsoft use, and isn't used in on-premises Exchange organizations.  <br/> |
|n/a  <br/> | `OutgoingRate` <br/> |Equals ( `-eq`)  <br/> Does not equal ( `-ne`)  <br/> Greater than ( `-gt`)  <br/> Greater than or equal to ( `-ge`)  <br/> Less than ( `-lt`)  <br/> Less than or equal to ( `-le`)  <br/> |A calculated number that indicates how quickly messages are leaving the queue. For more information, see [IncomingRate, OutgoingRate, and Velocity](queues.md#RatesAndVelocity).  <br/> |
|n/a  <br/> | `OverrideSource` <br/> |n/a  <br/> | This property is reserved for internal Microsoft use, and isn't used in on-premises Exchange organizations.  <br/> |
|n/a  <br/> | `PriorityDescriptions` <br/> |n/a  <br/> |The value descriptions in the **DeferredMessageCountsPerPriority** and **MessageCountsPerPriority** properties. The value of this property is  `{High, Normal, Low, None}`.  <br/> Because the value of this property is always the same, it won't make a good filter.  <br/> |
|n/a  <br/> | `RetryCount` <br/> |Equals ( `-eq`)  <br/> Does not equal ( `-ne`)  <br/> Greater than ( `-gt`)  <br/> Greater than or equal to ( `-ge`)  <br/> Less than ( `-lt`)  <br/> Less than or equal to ( `-le`)  <br/> |The number connection attempts for a queue that has a status of  `Retry`. For more information, see [Message retry, resubmit, and expiration intervals](message-intervals.md).  <br/> |
| n/a  <br/> | `RiskLevel` <br/> |n/a  <br/> | This property is reserved for internal Microsoft use, and isn't used in on-premises Exchange organizations.  <br/> |
|**Status** <br/> | `Status` <br/> |**Equals** (  `-eq`)  <br/> **Does Not Equal** (  `-ne`)  <br/> |The current queue status. A queue can have one of the following status values: Active, Connecting, Suspended, Ready, or Retry. For more information, see [Queue status](queues.md#QueueStatus).  <br/> |
|n/a  <br/> | `TlsDomain` <br/> |Equals ( `-eq`)  <br/> Does Not Equal ( `-ne`)  <br/> Contains ( `-like`)  <br/> |The FQDN of the destination domain if the domain is configured for Domain Security (mutual TLS authentication).  <br/> |
|n/a  <br/> | `Velocity` <br/> |Equals ( `-eq`)  <br/> Does not equal ( `-ne`)  <br/> Greater than ( `-gt`)  <br/> Greater than or equal to ( `-ge`)  <br/> Less than ( `-lt`)  <br/> Less than or equal to ( `-le`)  <br/> |A calculated number that indicates how effectively the queue is draining. For more information, see [IncomingRate, OutgoingRate, and Velocity](queues.md#RatesAndVelocity) <br/> |
   

