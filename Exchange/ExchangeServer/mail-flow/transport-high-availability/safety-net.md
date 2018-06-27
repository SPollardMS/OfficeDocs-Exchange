---
title: "Safety Net in Exchange 2016"
ms.author: chrisda
author: chrisda
manager: serdars
ms.date: 6/8/2018
ms.audience: ITPro
ms.topic: article
ms.prod: exchange-server-itpro
localization_priority: Normal
ms.assetid: d0abb807-3b12-4c7d-bc7e-769b87c84ccb
description: "Summary: Learn how Safety Net is used in Exchange 2016 to protect against data loss by maintaining a queue of successfully delivered messages that have not replicated to the passive mailbox database copies."
---

# Safety Net in Exchange 2016

 **Summary**: Learn how Safety Net is used in Exchange 2016 to protect against data loss by maintaining a queue of successfully delivered messages that have not replicated to the passive mailbox database copies.
  
In Exchange 2010, the *transport dumpster* helped protect against data loss by maintaining a queue of successfully delivered messages that hadn't replicated to the passive mailbox database copies in the database availability group (DAG). When a mailbox database or server failure required the promotion of an out-of-date copy of the mailbox database, the messages in the transport dumpster were automatically resubmitted to the new active copy of the mailbox database.
  
The transport dumpster was improved in Exchange 2013 and is now called *Safety Net*. Exchange 2016 has these same improvements.
  
Here's how Safety Net is similar to the transport dumpster in Exchange 2010:
  
- Safety Net is a queue that's associated with the Transport service on a Mailbox server. This queue stores copies of messages that were successfully processed by the server.
    
- You can specify how long Safety Net stores copies of the successfully processed messages before they expire and are automatically deleted. The default is 2 days.
    
Here's how Safety Net is improved from the transport dumpster in Exchange 2010:
  
- **Safety Net doesn't require a DAG**: For Mailbox servers that don't belong to a DAG, Safety Net stores copies of the delivered messages on other Mailbox servers in the local Active Directory site.
    
- **Safety Net itself isn't a single point of failure**: Redundancy is provided by using a *Primary Safety Net* and a *Shadow Safety Net*. If the Primary Safety Net is unavailable for more than 12 hours, resubmit requests become shadow resubmit requests, and messages are re-delivered from the Shadow Safety Net.
    
- **Safety Net takes over some responsibility from shadow redundancy in DAG environments**: hadow redundancy doesn't need to keep another copy of the delivered message in a shadow queue while it waits for the delivered message to replicate to the passive copies of mailbox database. The copy of the delivered message is already stored in Safety Net, so the message can be resubmitted from Safety Net if necessary.
    
- **Safety Net tries to guarantee message redundancy**: Safety Net is more than just a best effort for message redundancy, so you can't specify a maximum size limit for Safety Net. You can only specify how long Safety Net stores messages before they're automatically deleted.
    
For more information about transport high availability features in Exchange 2016, see [Transport high availability](transport-high-availability.md). For more information about message redundancy for messages in transit, see [Shadow redundancy in Exchange 2016](shadow-redundancy.md).
  
## How Safety Net works
<a name="How"> </a>

Shadow redundancy keeps a redundant copy of the message while the message is in transit. Safety Net keeps a redundant copy of a message after the message is successfully processed. So, Safety Net begins where shadow redundancy ends. concepts in shadow redundancy, including the transport high availability boundary, primary messages, primary servers, shadow messages and shadow servers also apply to Safety Net. For more information, see [Shadow redundancy in Exchange 2016](shadow-redundancy.md).
  
The Primary Safety Net exists on the Mailbox server that held the primary message before the message was successfully processed by the Transport service. This could mean the message was delivered to the Mailbox Transport Delivery service on the destination Mailbox server. Or, the message could have been relayed through the Mailbox server in an Active Directory site that's designated as a hub site on the way to the destination DAG or Active Directory site. After the primary server processes the primary message, the message is moved from the active delivery queue into the Primary Safety Net on the same server.
  
The Shadow Safety Net exists on the Mailbox server that held the shadow message. After the shadow server determines the primary server has successfully processed the primary message, the shadow server moves the shadow message from the shadow queue into the Shadow Safety Net on the same server. Although it may seem obvious, the existence of the Shadow Safety Net requires shadow redundancy to be enabled (it's is enabled by default).
  
This table describes the parameters that are used by Safety Net.
  
|**Parameter**|**Default value**|**Description**|
|:-----|:-----|:-----|
| _SafetyNetHoldTime_ on **Set-TransportConfig** <br/> |2 days  <br/> |The length of time successfully processed primary messages are stored in Primary Safety Net, and acknowledged shadow messages are stored in Shadow Safety Net.  <br/> You can also specify this value in the Exchange admin center (EAC) at **Mail flow** \> **Receive connectors** \> **More options** ![More Options icon](../../media/ITPro_EAC_MoreOptionsIcon.png) \> **Organization transport settings** \> **Safety Net** \> **Safety Net hold time**.  <br/> Unacknowledged shadow messages eventually expire from Shadow Safety Net after the sum of _SafetyNetHoldTime_ and _MessageExpirationTimeout_ parameter values.  <br/> To avoid data loss during Safety Net resubmits, the value of this parameter must be greater than or equal to the value of _ReplayLagTime_ on **Set-MailboxDatabaseCopy** for the lagged copy of the mailbox database.  <br/> |
| _ReplayLagTime_ on **Set-MailboxDatabaseCopy** <br/> |Not configured  <br/> |The amount of time that the Microsoft Exchange Replication service should wait before replaying log files that have been copied to the passive database copy. Setting this parameter to a value greater than 0 creates a lagged copy of the mailbox database. The maximum value is 14 days.  <br/> To avoid data loss during Safety Net resubmits, the value of this parameter for the lagged copy of the mailbox database must be less than or equal to the value of _SafetyNetHoldTime_ on **Set-TransportConfig**.  <br/> |
| _MessageExpirationTimeout_ on **Set-TransportService** <br/> |2 days  <br/> |How long a message can remain in a queue before it expires.  <br/> |
| _ShadowRedundancyEnabled_ on **Set-TransportConfig** <br/> | `$true` <br/> | `$true`: Shadow redundancy is enabled on all Mailbox servers in the organization.  <br/> `$false`: Shadow redundancy is disabled on all transport servers in the organization.  <br/> Redundancy for Safety Net requires shadow redundancy to be enabled.  <br/> |
   
## Message resubmission from Safety Net
<a name="PrimaryResubmit"> </a>

The Active Manager component of the Microsoft Exchange Replication service (MRS) manages DAGs and mailbox database copies. Message resubmissions from Safety Net require no manual actions, and are initiated by the Active Manager. For more information about Active Manager, see [Active Manager](../../high-availability/database-availability-groups/active-manager.md).
  
There are two basic Safety Net message resubmission scenarios:
  
- After the automatic or manual failover of a mailbox database in a DAG.
    
- After you activate a lagged copy of a mailbox database.
    
A *lagged mailbox database copy* or *lagged copy* is a passive copy of a mailbox database where updates to the database are intentionally delayed to protect against logical corruption of the mailbox database. For more information, see [Manage mailbox database copies](../../high-availability/manage-ha/manage-database-copies.md).
  
The only significant difference between the two scenarios is how far back in time to go to resubmit messages from Safety Net. Typically, for database failover in a DAG, the new active copy of the mailbox database is anywhere from several minutes to several hours behind the old active copy. A lagged copy of a mailbox database is typically several days behind the old active copy.
  
The main requirement for successful message resubmission from Safety Net for a lagged copy is: the length of time messages are stored in Safety Net must be greater than or equal to the lag time of the lagged copy. In other words, the value of _SafetyNetHoldTime_ on **Set-TransportConfig** must be greater than or equal to the value of the _ReplayLagTime_ on **Set-MailboxDatabaseCopy** for the lagged copy.
  
## Message resubmission from Shadow Safety Net
<a name="ShadowResubmit"> </a>

Message resubmission from Shadow Safety Net (like message resubmission from Primary Safety Net), is fully automated, and requires no manual intervention. This scenario describes the interaction of Primary Safety Net and Shadow Safety Net during message resubmission:
  
1. Active Manager requests message resubmission from Safety Net for a mailbox database for the specified time interval (for example, 5:00 to 9:00). However, the Mailbox server that holds the Primary Safety Net has crashed due to a hardware failure. Active Manager unsuccessfully tries to contact the Primary Safety Net for the next 12 hours.
    
2. After 12 hours, Active Manager sends a broadcast message to the Transport service on all Mailbox servers in the transport high availability boundary (the DAG or Active Directory site in non-DAG environments) looking for other Safety Nets that contain messages for the target mailbox database for the specified time interval. The Shadow Safety Net responds and resubmits messages for the mailbox database for the time interval 5:00 to 9:00.
    
When a Shadow Safety Net responds, it only resubmits the messages for the required mailbox database during the required time interval. This restriction by mailbox database and time interval helps reduce these potential issues:
  
- Resubmitting messages from Safety Net could result in duplicate deliveries. This isn't an issue for mailboxes in the Exchange organization, because duplicate message detection prevents mailbox users from seeing the duplicate messages. But, duplicate message delivery to external recipients could result in duplicate copies of messages that the recipient would see.
    
- Shadow messages resubmitted from Shadow Safety Net require full categorization and processing through the Transport service on the Mailbox server. Resubmission of a large number of shadow messages can be expensive in terms of Mailbox server system resources.
    
These are some important considerations for the shadow messages that are stored in Shadow Safety Net:
  
- Shadow Safety Net doesn't know where the primary server transmitted the primary message.
    
- The shadow messages in Shadow Safety Net only contain original message envelope recipients, not the actual recipients where the primary message was delivered (for example, the message envelope recipient might be a distribution group that requires expansion).
    
- The messages in Shadow Safety net don't contain any message updates that occurred after the primary server processed the message (for example, message encoding or content conversion).
    
This scenario describes what happens if the Primary Safety Net is offline during part of the requested resubmit interval:
  
1. The queue database on the Mailbox server that holds the Primary Safety Net is corrupt, and a new queue database is created at 7:00. All of the primary messages stored in the Primary Safety Net from 1:00 to 7:00 are lost, but the server is able to store copies of successfully delivered messages in Safety Net starting at 7:00.
    
2. Active Manager requests a resubmission of messages from Safety Net for a mailbox database for the time interval 1:00 to 9:00.
    
3. The Primary Safety Net resubmits messages for the time interval 7:00 to 9:00.
    
4. Because the Primary Safety Net doesn't have the required messages for 1:00 to 7:00. the Primary Safety Net sends a broadcast message to the Transport service on all Mailbox servers in the transport high availability boundary looking for other Safety Nets that contain the required messages. The Shadow Safety Net generates a second resubmit request on behalf of the Primary Safety Net to resubmit the shadow messages for the target mailbox database for the time interval 1:00 to 7:00.
    
These are some other issues to consider when messages are resubmitted from Safety Net:
  
- **All delivery status notifications (also known as DSNs, non-delivery reports, NDRs or bounce messages) are suppressed for Safety Net message resubmissions**: For example, if the primary message resulted in an NDR, the NDR for the resubmitted message won't be delivered.
    
- **Users removed from a distribution group may not receive a resubmitted message when the Shadow Safety Net resubmits the message**: For example, a message is sent to a group containing User A and User B, and both recipients receive the message. User B is subsequently removed from the group. Later, a resubmit request from Primary Safety Net is made for the mailbox database that holds User B's mailbox. However, the Primary Safety Net is unavailable for more than 12 hours, so the Shadow Safety Net server responds and resubmits the affected message. During message resubmission when the distribution group is expanded, User B is no longer a member of the group, and won't receive a copy of the resubmitted message.
    
- **New Users added to a distribution group may receive an old resubmitted message when the Shadow Safety Net resubmits the message**: For example, a message is sent to a group containing User A and User B, and both recipients receive the message. User C is subsequently added to the group. Later, a resubmit request from Primary Safety Net is made for the mailbox database that holds User C's mailbox. However, the Primary Safety Net server is unavailable for more than 12 hours, so the Shadow Safety Net server responds and resubmits the affected messages. During message resubmission when the distribution group is expanded, User C is now a member of the group, and will receive a copy of the resubmitted message.
    

