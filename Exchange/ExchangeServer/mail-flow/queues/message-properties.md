---
title: "Properties of messages in queues"
ms.author: chrisda
author: chrisda
manager: serdars
ms.date: 6/8/2018
ms.audience: ITPro
ms.topic: article
ms.prod: exchange-server-itpro
localization_priority: Normal
ms.assetid: 8e6187c1-76f0-49da-bc24-2ab57cfb3c2c
description: "Summary: Learn about the filterable properties for messages in queues in Exchange 2016."
---

# Properties of messages in queues

 **Summary**: Learn about the filterable properties for messages in queues in Exchange 2016.
  
Filtering messages in queues by one or more message properties in Exchange Server 2016 allows you to quickly locate messages and take action on them. When an email message is sent to multiple recipients, the message might be located in multiple queues on the server. When you filter messages in queues by message properties, you can locate messages across all queues. The following scenarios are examples of how you might use message filtering to manage mail flow:
  
- The Submission queue on the Mailbox server or Edge Transport server that receives email from the Internet has a high volume of messages that are queued for delivery. Many of the messages have the same subject. Therefore, you suspect that spam is being sent to your organization. You can create a filter to view all the messages that meet the subject criteria. If you determine that the messages are spam, you can select them all and delete them from the delivery queue without sending an NDR.
    
- A user reports that mail flow is slow. You examine the queues and see that many messages with random subjects appear to be coming from a single domain. You can create a filter to view all the queued messages from that domain. If you determine that the messages are spam, you can select them all and delete them from the queues without sending an NDR.
    
You can create message filters in Queue Viewer in the Exchange Toolbox, or by using the _Filter_ parameter on the message management cmdlets. Note that the message management cmdlets support more filterable properties than Queue Viewer.
  
For more information about Queue Viewer, see [Queue Viewer](queue-viewer.md). For more information about the message management cmdlets, see [Procedures for messages in queues](message-procedures.md) and [Find queues and messages in queues in the Exchange Management Shell](queues-and-messages-in-powershell.md).
  
## Message properties to use as filters

The following table describes the message properties that you can use as filters in Queue Viewer and the Exchange Management Shell.
  
|**Queue Viewer**|**Exchange Management Shell**|**Comparison operators**|**Description**|
|:-----|:-----|:-----|:-----|
|n/a  <br/> | `AccountForest` <br/> |n/a  <br/> |This property is reserved for internal Microsoft use, and isn't used in on-premises Exchange organizations.  <br/> In on-premises Exchange, this property is the forest root domain where the mailbox resides (for example, contoso.com).  <br/> |
|n/a  <br/> | `ComponentLatency` <br/> |n/a  <br/> |This property is reserved for internal Microsoft use, and isn't used in on-premises Exchange organizations.  <br/> |
|**Date Received** <br/> | `DateReceived` <br/> |**Greater Than** (`-gt`)  <br/> **Greater Than or Equals** (`-ge`)  <br/> **Less Than** (`-lt`)  <br/> **Less Than or Equals** (`-le`)  <br/> |The date/time when the message was placed in the queue.  <br/> |
|n/a  <br/> | `DeferReason` <br/> |Equals (`-eq`)  <br/> Does not equal (`-ne`)  <br/> Contains (`-like`)  <br/> |Indicates why the message was deferred. If the message wasn't deferred, this property has the value `None`. A deferred message is returned to the Submission queue because of transient errors that were encountered during recipient resolution. For more information about deferred messages, see [Recipient resolution in Exchange 2016](../../mail-flow/mail-routing/recipient-resolution.md). The possible values are:  <br/> `AD Transient Failure During Content Conversion` <br/> `AD Transient Failure During Resolve` <br/> `Agent` <br/> `Ambiguous Recipient` <br/> `Config Update` <br/> `Loop Detected` <br/> `Marked As Retry Delivery If Rejected` <br/> `Recipient does not have a mailbox database` <br/> `Recipient Thread Limit Exceeded` <br/> `Rerouted By Store Driver` <br/> `Storage Transient Failure During Content Conversion` <br/> `Target Site Inbound Mail Disabled` <br/> `Transient Accepted Domains Load Failure` <br/> `Transient Attribution Failure` <br/> `Transient Failure` <br/> |
|n/a  <br/> | `Directionality` <br/> |Equals (`-eq`)  <br/> Does Not Equal (`-ne`)  <br/> |Valid values are `Incoming`, `Originating`, and `Undefined`.  <br/> |
|**Expiration Time** <br/> | `ExpirationTime` <br/> |**Greater Than** (`-gt`)  <br/> **Greater Than or Equals** (`-ge`)  <br/> **Less Than** (`-lt`)  <br/> **Less Than or Equals** (`-le`)  <br/> |The date/time when the message will expire and be deleted from the queue if the message can't be delivered.  <br/> |
|n/a  <br/> | `ExternalDirectoryOrganizationId` <br/> |n/a  <br/> |This property is reserved for internal Microsoft use, and isn't used in on-premises Exchange organizations.  <br/> In on-premises Exchange, the value is `00000000-0000-0000-0000-000000000000`.  <br/> |
|**From Address** <br/> | `FromAddress` <br/> |**Equals** (`-eq`)  <br/> **Does Not Equal** (`-ne`)  <br/> **Contains** (`-contains`)  <br/> |The SMTP address of the sender.  <br/> |
|n/a  <br/> | `Identity` <br/> |n/a  <br/> |The identity of the message in the form of _\<Server\>_\ _\<Queue\>_\ _\<MessageInteger\>_. For more information see [Message identity](queues-and-messages-in-powershell.md#MessageIdentity).  <br/> |
|**Internet Message ID** <br/> | `InternetMessageId` <br/> |**Equals** (`-eq`)  <br/> **Does Not Equal** (`-ne`)  <br/> **Contains** (`-contains`)  <br/> |The value of the **Message-Id:** header field in the message header. This value is constant for the lifetime of the message. For messages created in Exchange, the value is in the format `<GUID@ServerFQDN>`, including the angle brackets (\< \>). For example, `<4867a3d78a50438bad95c0f6d072fca5@mailbox01.contoso.com>`.  <br/> |
|**Last Error** <br/> | `LastError` <br/> |**Equals** (`-eq`)  <br/> **Does Not Equal** (`-ne`)  <br/> **Contains** (`-contains`)  <br/> **Is Present** <br/> **Is Not Present** <br/> |The last error that was recorded for a message. For example, `A matching connector cannot be found to route the external recipient`.  <br/> |
|n/a  <br/> | `LockReason` <br/> |n/a  <br/> |This property is reserved for internal Microsoft use, and isn't used in on-premises Exchange organizations.  <br/> |
|n/a  <br/> | `MessageLatency` <br/> |Equals (`-eq`)  <br/> Does not equal (`-ne`)  <br/> Greater than (`-gt`)  <br/> Greater than or equal to (`-ge` <br/> Less than (`-lt` <br/> Less than or equal to (`-le` <br/> |The amount of time that elapsed between when the message first entered the Submission queue on the server, and when the message was placed in the queue. The value uses the syntax _hh:mm:ss.ff_, where _hh_ = hour, _mm_ = minute, _ss_ = second, and _ff_ = fractions of a second.  <br/> |
|**Message Source Name** <br/> | `MessageSourceName` <br/> |**Equals** (`-eq`)  <br/> **Does Not Equal** (`-ne`)  <br/> **Contains** (`-contains`)  <br/> |The name of the transport component that submitted the message to the queue. For example, if the message came in through a Receive connector, the value is: `SMTP:` _\<ConnectorName\>_. If the message is a delivery status notification (DSN), the value is `DSN`.  <br/> |
|n/a  <br/> | `OriginalFromAddress` <br/> |Equals (`-eq`)  <br/> Does not equal (`-ne`)  <br/> Contains (`-like`)  <br/> |The original sender's email address for any new side effect messages that are created during categorization (for example, journal rules, NDRs, or transport rules).  <br/> |
|n/a  <br/> | `Priority` <br/> |Equals (`-eq`)  <br/> Does not equal (`-ne`)  <br/> |The priority (importance) of the message that's assigned by the user in Microsoft Outlook or Outlook on the web. Valid values are `Low`, `Normal`, and `High`. For more information, see [Priority Queuing](http://technet.microsoft.com/library/6edbd826-fe55-435b-9c63-48e6365c3d09.aspx).  <br/> |
|**Queue ID** <br/> | `Queue` <br/> |**Equals** (`-eq`)  <br/> **Does Not Equal** (`-ne`)  <br/> **Contains** (`-contains`)  <br/> |The queue that holds the message. The queue identity uses the syntax _\<Server\>\\<Queue\>_. For more information, see [Queue identity](queues-and-messages-in-powershell.md#QueueIdentity).  <br/> |
|n/a  <br/> | `Recipients` <br/> |Contains (`-like`)  <br/> |An array that contains details about the recipient and the Send connector that will be used, or any errors that were encountered. For example:  <br/> `{chris@contoso.com;2;2;A matching connector cannot be found to route the external recipient;16;<No Matching Connector>;0}` <br/> |
|n/a  <br/> | `RetryCount` <br/> |Equals (`-eq`)  <br/> Does not equal (`-ne`)  <br/> Greater than (`-gt`)  <br/> Greater than or equal to (`-ge` <br/> Less than (`-lt` <br/> Less than or equal to (`-le` <br/> |The number of times that delivery of the message to the destination was tried, either automatically or manually.  <br/> |
|**SCL** <br/> | `SCL` <br/> |**Equals** (`-eq`)  <br/> **Does Not Equal** (`-ne`)  <br/> **Greater Than** (`-gt`)  <br/> **Greater Than or Equals** (`-ge` <br/> **Less Than** (`-lt` <br/> **Less Than or Equals** (`-le` <br/> |The spam confidence level (SCL) rating of the message. Valid SCL entries are integers 0 through 9, or -1 for internal (authenticated) messages. For more information, see [Exchange spam confidence level (SCL) thresholds](../../antispam-and-antimalware/antispam-protection/scl.md).  <br/> |
|**Size (KB)** <br/> | `Size` <br/> |**Equals** (`-eq`)  <br/> **Does Not Equal** (`-ne`)  <br/> **Greater Than** (`-gt`)  <br/> **Greater Than or Equals** (`-ge` <br/> **Less Than** (`-lt` <br/> **Less Than or Equals** (`-le` <br/> |The size of the message. In Queue Viewer, you need to specify the message size in kilobytes (KB), but in the Exchange Management Shell, you can also specify other sizes, for example, bytes (B) or megabytes (MB).  <br/> |
|**Source IP** <br/> | `SourceIP` <br/> |**Equals** (`-eq`)  <br/> **Does Not Equal** (`-ne`)  <br/> |The IPv4 or IPv6 address of the server that submitted the message to the Exchange server that holds the message in the queue. The address could be the IP address of a remote SMTP server, or the IP address of the local Exchange server.  <br/> |
|**Status** <br/> | `Status` <br/> |**Equals** (`-eq`)  <br/> **Does Not Equal** (`-ne`)  <br/> |The current message status. Valid values are:  <br/> **Active** <br/> **Locked** <br/> **Pending Remove** (`PendingRemove`)  <br/> **Pending Suspend** (`PendingSuspend`)  <br/> **Ready** <br/> **Retry** <br/> **Suspended** <br/> For more information, see [Message status](queues.md#MessageStatus).  <br/> |
|**Subject** <br/> | `Subject` <br/> |**Equals** (`-eq`)  <br/> **Does Not Equal** (`-ne`)  <br/> **Contains** (`-contains`)  <br/> **Is Present** <br/> **Is Not Present** <br/> |The subject of the message (from the **Subject:** header field).  <br/> |
|n/a  <br/> | `TrafficType` <br/> |n/a  <br/> |This property is reserved for internal Microsoft use, and isn't used in on-premises Exchange organizations.  <br/> In on-premises Exchange, this property is blank or has the value `Email`.  <br/> |
|n/a  <br/> | `TrafficSubType` <br/> |n/a  <br/> |This property is reserved for internal Microsoft use, and isn't used in on-premises Exchange organizations.  <br/> |
   

