---
title: "Message retry, resubmit, and expiration intervals"
ms.author: chrisda
author: chrisda
manager: serdars
ms.date: 6/8/2018
ms.audience: ITPro
ms.topic: article
ms.prod: exchange-server-itpro
localization_priority: Normal
ms.assetid: 03020e6f-4c01-4c6e-ae47-fd74d4c4f96a
description: "Summary: Learn about the time intervals and settings in Exchange 2016 for messages that can't be successfully delivered."
---

# Message retry, resubmit, and expiration intervals

 **Summary**: Learn about the time intervals and settings in Exchange 2016 for messages that can't be successfully delivered.
  
In Exchange 2016, messages that can't be successfully delivered are subject to various retry, resubmit, and expiration deadlines based on the message's source and destination. *Retry* is a renewed connection attempt with the destination. *Resubmit* is the act of sending messages back to the Submission queue for the categorizer to reprocess. The message *expires* after all delivery efforts have failed over a specified period of time. After a message expires, the sender is notified of the delivery failure, and the message is deleted from the queue.
  
In all three cases of retry, resubmit, or expire, you can manually intervene before the automatic actions are performed on the messages.
  
For instructions on how to configure these intervals, see [Configure message retry, resubmit, and expiration intervals](configure-message-intervals.md).
  
## Configuration options for message retry

When a the Transport service on a Mailbox server or an Edge Transport server can't connect to the next hop, the queue is put in a status of Retry. Connection attempts continue until the queue expires or a connection is made.
  
### Configuration options for automatic message retry in the EdgeTransport.exe.config file

The automatic message retry interval settings that are available in the `%ExchangeInstallPath%Bin\EdgeTransport.exe.config` XML application configuration file are described in the following table.
  
> [!NOTE]
> Any customized per-server Exchange or Internet Information Server settings you make in Exchange XML application configuration files (for example, web.config files or the EdgeTransport.exe.config file) will be overwritten when you install an Exchange Cumulative Update (CU). Make sure that you save this information so that you can easily re-configure your server after the install. You must re-configure these settings after you install an Exchange CU.
  
****

|**Automatic message retry key name**|**Default value**|**Description**|
|:-----|:-----|:-----|
| _MailboxDeliveryQueueRetryInterval_ <br/> | `00:05:00` (5 minutes)  <br/> |How frequently the queues try to connect to the Mailbox Transport Delivery service for a destination mailbox database that can't be successfully reached.  <br/> To specify a value, enter it as a time span: `dd.hh:mm:ss` where `dd` = days, `hh` = hours, `mm` = minutes, and `ss` = seconds.  <br/> A valid value is a timespan from `00:00:01` (one second) through `1.00:00:00` (one day).  <br/> |
| _QueueGlitchRetryCount_ <br/> |4  <br/> |The number of connection attempts that are immediately tried when a transport server has trouble connecting with the destination server. Such connection problems are typically caused by very brief network outages.  <br/> A valid value is an integer from 0 through 15.  <br/> Typically, you don't need to modify this key unless the network is unreliable and continues to experience many accidentally dropped connections.  <br/> |
| _QueueGlitchRetryInterval_ <br/> | `00:01:00` (1 minute)  <br/> |The connection interval between each connection attempt that's specified by the _QueueGlitchRetryCount_ key.  <br/> Typically, you don't need to modify this parameter unless the network is unreliable and continues to experience many accidentally dropped connections.  <br/> |
   
### Configuration options for automatic message retry in the Exchange admin center and the Exchange Management Shell

The automatic message retry interval settings that are available in the Exchange admin center (EAC) and the Exchange Management Shell are described in the following table.
  
|**Automatic message retry setting**|**Default value**|**Exchange Management Shell configuration**|**Exchange admin center configuration on Mailbox servers**|
|:-----|:-----|:-----|:-----|
|**Message retry interval**: The retry interval for individual messages that have a status of Retry.  <br/> |15 minutes (`00:15:00`)  <br/> We recommend that you don't modify the default value unless you're directed to do so by Microsoft Customer Service and Support, or specific product documentation.  <br/> |Cmdlet: **Set-TransportService** cmdlet  <br/> Parameter: _MessageRetryInterval_ <br/> |n/a  <br/> |
|**Outbound connection failure retry interval**: The retry interval for outbound connection attempts that have previously failed. The previously failed connection attempts are controlled by the transient failure retry count and interval values.  <br/> |Transport service on Mailbox servers: 10 minutes (`00:10:00`)  <br/> Edge Transport Servers: 30 minutes (`00:30:00`)  <br/> |Cmdlet: **Set-TransportService** <br/> Parameter: _OutboundConnectionFailureRetryInterval_ <br/> |**Servers** \> select server \> **Edit** (![Edit icon](../../media/ITPro_EAC_EditIcon.png)) \> **Transport limits** \> **Retry** section \> **Outbound connection failure retry interval (seconds)** <br/> |
|**Transient failure retry count**: The number of connection attempts that are tried after the queue glitch retry count and interval values have failed. These failures can be caused by server restarts or cached DNS lookup failures.  <br/> A valid value is an integer from 0 through 15. The value 0 means the next connection attempt is controlled by the outbound connection failure retry interval.  <br/> |6  <br/> |Cmdlet: **Set-TransportService** <br/> Parameter: _TransientFailureRetryCount_ <br/> |**Servers** \> select server \> **Edit** (![Edit icon](../../media/ITPro_EAC_EditIcon.png)) \> **Transport limits** \> **Retries** section \> **Transient failure retry attempts** <br/> |
|**Transient failure retry interval**: The connection interval between each connection attempt that's specified by the transient failure retry count value.  <br/> |Transport service on Mailbox servers: 5 minutes (`00:05:00`)  <br/> Edge Transport servers: 10 minutes (`00:10:00`)  <br/> |Cmdlet: **Set-TransportService** <br/> Parameter: _TransientFailureRetryInterval_ <br/> |**Servers** \> select server \> **Edit** (![Edit icon](../../media/ITPro_EAC_EditIcon.png)) \> **Transport limits** \> **Retries** section \> **Transient failure retry interval (minutes)** <br/> |
   
### Configuration options for manual message retry

When a delivery queue is in the status of Retry, you can manually force an immediate connection attempt by using Queue Viewer in the Exchange Toolbox or the **Retry-Queue** cmdlet in the Exchange Management Shell. The manual retry attempt overrides the next scheduled retry time. If the connection isn't successful, the retry interval timer is reset. The delivery queue must be in a status of Retry for this action to have any effect. For more information, see [Retry queues](queue-procedures.md#Retry).
  
### Configuration options for delay DSN messages

After each message delivery failure, the Transport service on the Edge Transport server or the Mailbox server generates a delay delivery status notification (DSN) message and queues it for delivery to the sender of the undeliverable message. This delay DSN message is sent only after a delay notification interval has passed (the default is 4 hours), and only if the message wasn't successfully delivered during that time. This delay prevents the sending of unnecessary delay DSN messages due to temporary message transmission failures that are ultimately resolved. You can selectively enable or disable the sending of delay DSN notification messages for messages that originate inside or outside the Exchange organization.
  
The configuration options that are available for delay DSN notification messages are described in the following table.
  
|**Delay DSN setting**|**Default value**|**Exchange Management Shell configuration**|**Exchange admin center configuration on Mailbox servers**|
|:-----|:-----|:-----|:-----|
|**Delay notification timeout**: How long the server waits before it sends a delay DSN message to the sender.  <br/> This value should always be greater than the transient failure retry count multiplied by the transient failure retry interval (the default total is 30 minutes on a Mailbox server, and one hour on an Edge Transport server).  <br/> |4 hours (`4:00:00`)  <br/> |Cmdlet: **Set-TransportService** <br/> Parameter: _DelayNotificationTimeOut_ <br/> |**Servers** \> select server \> **Edit** (![Edit icon](../../media/ITPro_EAC_EditIcon.png)) \> **Transport limits** \> **Notifications** section \> **Notify sender when message is delayed after (hours)** <br/> |
|**External delay DSN enabled**: Specifies whether delay DSN messages can be sent to external message senders (senders who are outside the Exchange organization).  <br/> _ExternalDelayDSNEnabled_ <br/> | `$true` <br/> |Cmdlet: **Set-TransportConfig** <br/> Parameter: _ExternalDelayDSNEnabled_ <br/> |Not available  <br/> |
|**Internal delay DSN enabled**: Specifies whether delay DSN messages can be sent to internal message senders (message senders who are inside the Exchange organization).  <br/> | `$true` <br/> |Cmdlet: **Set-TransportConfig** <br/> Parameter: _InternalDelayDSNEnabled_ <br/> |Not available  <br/> |
   
## Configuration options for message resubmission

Message resubmission sends undelivered messages back to the Submission queue to be reprocessed by the categorizer. For more information about the categorizer and the Submission queue, see [Understanding the Transport service on Mailbox servers](../../mail-flow/mail-flow.md#TransportService).
  
### Automatic message resubmission

Undelivered messages in delivery queues are automatically resubmitted if the delivery queue is in the status of Retry and has been unable to successfully deliver any messages for a specified period of time. That period of time is controlled by the _MaxIdleTimeBeforeResubmit_ key in the `%ExchangeInstallPath%Bin\EdgeTransport.exe.config` XML application configuration file. The default value is `12:00:00` or 12 hours.
  
> [!NOTE]
> Any customized per-server Exchange or Internet Information Server settings you make in Exchange XML application configuration files (for example, web.config files or the EdgeTransport.exe.config file) will be overwritten when you install an Exchange Cumulative Update (CU). Make sure that you save this information so that you can easily re-configure your server after the install. You must re-configure these settings after you install an Exchange CU.
  
### Manual Message Resubmission

You can manually resubmit messages by using the following methods:
  
- Resubmit a delivery queue that has the status of Retry, or resubmit the Unreachable queue. For more information, see [Resubmit queues](queue-procedures.md#Resubmit).
    
- Resubmit messages in the poison message queue. For more information, see [Resubmit messages in the poison message queue](queue-procedures.md#PoisonResubmit).
    
- Suspend a queue, suspend the messages in the queue, export the messages to files, and copy the files to the Replay directory on any Mailbox server or Edge Transport server. For more information, see [Export messages from queues](export-messages.md).
    
## Configuration options for message expiration

The *message expiration timeout interval* specifies the maximum length of time that an Edge Transport server or Mailbox server (the Transport service) tries to deliver a failed message. If the message can't be successfully delivered before the expiration timeout interval has passed, a non-delivery report (also known as an NDR or bounce message) that contains the original message or the message headers is delivered to the sender.
  
### Automatic message expiration

The message expiration timeout interval is described in the following table.
  
|**Default value**|**Exchange Management Shell configuration**|**Exchange admin center configuration on Mailbox servers**|
|:-----|:-----|:-----|
|2 days (`2.00:00:00`)  <br/> |Cmdlet: **Set-TransportService** <br/> Parameter: _MessageExpirationTimeOut_ <br/> |**Servers** \> select server \> **Edit** (![Edit icon](../../media/ITPro_EAC_EditIcon.png)) \> **Transport limits** \> **Message expiration** section \> **Maximum time since submission (days)** <br/> |
   
### Manual Message Expiration

Although you can't manually force messages to expire, you can manually remove messages from any queue (except the Submission queue) with or without an NDR. For more information, see [Remove messages from queues](message-procedures.md#Remove).
  

