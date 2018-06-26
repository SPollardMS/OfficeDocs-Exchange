---
title: "Queues and messages in queues"
ms.author: chrisda
author: chrisda
manager: serdars
ms.date: 6/8/2018
ms.audience: ITPro
ms.topic: overview
ms.prod: exchange-server-itpro
localization_priority: Normal
ms.assetid: e7ad0ba5-3789-4a2b-9825-6bb1b321609c
description: "Summary: Learn about queues in Exchange 2016"
---

# Queues and messages in queues

 **Summary**: Learn about queues in Exchange 2016
  
A *queue* is a temporary holding location for messages that are waiting to enter the next stage of processing or delivery to a destination. Each queue represents a logical set of messages that the Exchange server processes in a specific order. In Exchange 2016, queues hold messages before, during and after delivery. Queues exist in the Transport service on Mailbox servers and on Edge Transport servers. Mailbox servers and Edge Transport servers are called *transport servers* throughout this topic. 
  
Like all previous versions of Exchange, Exchange 2016 uses a single Extensible Storage Engine (ESE) database for queue storage.
  
You can manage queues and messages in queues by using the Exchange Management Shell and Queue Viewer in the Exchange Toolbox. You can use these interfaces to view the status and contents of queues and detailed message properties. You can also perform actions that modify queues or the messages in queues. For more information, see [Procedures for queues](queue-procedures.md) and [Procedures for messages in queues](message-procedures.md).
  
## Types of queues
<a name="QueueTypes"> </a>

The following types of queues are used in Exchange 2016, which are the same as Exchange 2013:
  
****

|**Queue**|**Server role**|**Description**|
|:-----|:-----|:-----|
|Delivery queues  <br/> |Mailbox servers and Edge Transport servers  <br/> |Holds messages that are being delivered to all internal and external destinations.  <br/> Delivery queues are dynamically created when they're required, and are automatically deleted when the queue is empty and the expiration time has passed. The queue expiration time is controlled by the _QueueMaxIdleTime_ parameter on the **Set-TransportService** cmdlet. The default value is three minutes.  <br/> On Edge Transport servers, there's a queue for every unique destination SMTP domain or smart host.  <br/> On Mailbox servers, there's a queue for every unique destination as indicated by the **NextHopSolutionKey** property. For more information, see the [NextHopSolutionKey](queues.md#NextHopSolutionKey) section later in this topic.  <br/>  All messages are transmitted between Exchange 2016 and Exchange 2013 servers by using SMTP. Non-SMTP destinations also use delivery queues if the destination is serviced by a Delivery Agent connector. For more information, see [Delivery Agents and Delivery Agent Connectors](http://technet.microsoft.com/library/38c942ee-b59d-47ec-87eb-bebad441ada5.aspx).  <br/> |
|Poison message queue  <br/> |Mailbox servers and Edge Transport servers  <br/> |Isolates messages that contain errors and are determined to be harmful to Exchange after a server or service failure. The messages may be genuinely harmful in their content and format, or the messages might have been the victims of a poorly written transport agent or a software bug that crashed the Exchange server while it was processing the otherwise valid messages.  <br/> The poison message queue is typically empty. If the poison message queue contains no messages, then it doesn't appear in the queue management tools. Messages in the poison message queue are never automatically resumed or expired. Messages remain in the poison message queue until they're manually resumed or removed by an administrator.  <br/>  Every Mailbox server or Edge Transport server has only one poison message queue.  <br/> |
|Shadow queues  <br/> |Mailbox servers  <br/> |Shadow queues hold redundant copies of messages while the messages are in transit. For more information, see [Shadow redundancy in Exchange 2016](../../mail-flow/transport-high-availability/shadow-redundancy.md).  <br/> |
|Submission queue  <br/> |Mailbox servers and Edge Transport servers  <br/> |Holds messages that have been accepted by the Transport service, but haven't been processed. Messages in the Submission queue are either waiting to be processed, or are actively being processed.  <br/> On Mailbox servers, messages are received by a Receive connector, the Pickup or Replay directories, or the Mailbox Transport Submission service. On Edge Transport servers, messages are typically received by a Receive connector, but the Pickup and Replay directories are also available.  <br/> The categorizer retrieves messages from this queue and, among other things, determines the location of the recipient and the route to that location. After categorization, the message is moved to a delivery queue or to the Unreachable queue. For more information about the categorizer and the transport pipeline, see [Mail flow and the transport pipeline](../../mail-flow/mail-flow.md).  <br/>  Every Mailbox server or Edge Transport server has only one Submission queue.  <br/> |
|Unreachable queue  <br/> |Mailbox servers and Edge Transport servers  <br/> |Contains messages that can't be routed to their destinations. Typically, an unreachable destination is caused by configuration changes that have modified the routing path for delivery. Regardless of destination, all messages that have unreachable recipients reside in this queue.  <br/>  Every Mailbox server or Edge Transport server has only one Unreachable queue.  <br/> |
   
## Queue database files
<a name="QueueDBFiles"> </a>

All the different queues are stored in a single ESE database. By default, this queue database is located on the transport server at `%ExchangeInstallPath%TransportRoles\data\Queue`.
  
Like any ESE database, the queue database uses log files to accept, track, and maintain data. To enhance performance, all message transactions are written first to log files and memory, and then to the database file. The checkpoint file tracks the transaction log entries that have been committed to the database. During an ordinary shutdown of the Microsoft Exchange Transport service, uncommitted database changes that are found in the transaction logs are committed to the database.
  
Circular logging is used for the queue database. This means that transaction logs that are older than the current checkpoint are immediately and automatically deleted. Therefore, the transaction logs can't be replayed for queue database recovery from backup.
  
The following table lists the files that constitute the queue database.
  
|**File**|**Description**|
|:-----|:-----|
|Mail.que  <br/> |This queue database file stores all the queued messages.  <br/> |
|Tmp.edb  <br/> |This temporary database file is used to verify the queue database schema on startup.  <br/> |
|Trn\*.log  <br/> |Transaction logs record all changes to the queue database. Changes to the database are first written to the transaction log and then committed to the database. Trn.log is the current active transaction log file. Trntmp.log is the next provisioned transaction log file that's created in advance. If the existing Trn.log transaction log file reaches its maximum size, Trn.log is renamed to Trn _nnnn_.log, where _nnnn_ is a sequence number. Trntmp.log is then renamed Trn.log and becomes the current active transaction log file.  <br/> |
|Trn.chk  <br/> |This checkpoint file tracks the transaction log entries that have been committed to the database. This file is always in the same location as the mail.que file.  <br/> |
|Trnres00001.jrs  <br/> Trnres00002.jrs  <br/> |These reserve transaction log files act as placeholders. They're only used when the hard disk that contains the transaction log runs out of space to stop the queue database cleanly.  <br/> |
   
Exchange 2016 uses *generation tables* for storage and clean-up of messages in the queue database. Instead of processing and deleting individual message records from one large table, the queue database stores messages in time-based tables, and only deletes the entire table after all the messages in the table have been successfully processed. For example, consider the following example: 
  
- All messages queued from 1:00 PM to 2:00 PM, regardless of the queue or destination, are stored in the `1p-2p_msgs` table. 
    
- At 2:00 PM, new messages are stored in the `2p-3p_msgs` table. 
    
- At 4:00 PM, a new table named `4p-5p_msgs` is created. The entire `1p-2p_msgs` table is deleted, but only if all messages in the table have been successfully processed. 
    
This approach of deleting entire messages tables instead of individual messages helps improves the I/O performance of the drive that holds the queue database.
  
### Options for configuring the queue database

You configure the queue database by adding or modifying keys in the `%ExchangeInstallPath%Bin\EdgeTransport.exe.config` XML application configuration file. This file is associated with the Microsoft Exchange Transport service. Changes you make to the EdgeTransport.exe.config file take effect after you restart the Microsoft Exchange Transport service. 
  
> [!NOTE]
> Any customized per-server Exchange or Internet Information Server settings you make in exExchangeNoVersion XML application configuration files (for example, web.config files or the EdgeTransport.exe.config file) will be overwritten when you install an exExchangeNoVersion Cumulative Update (CU). Make sure that you save this information so that you can easily re-configure your server after the install. You must re-configure these settings after you install an exExchangeNoVersion CU. 
  
The `<appSettings>` section of the EdgeTransport.exe.config file is where you can add new keys or modify existing keys. If a specific key doesn't exist, you can add it manually to change its value. 
  
The keys for the queue database that are available in the EdgeTransport.exe.config file are described in the following table.
  
**Message queue database keys that are available in the EdgeTransport.exe.config file**

|**Key**|**Default value**|**Description**|
|:-----|:-----|:-----|
| _QueueDatabaseBatchSize_ <br/> |40  <br/> |Specifies the number of database I/O operations that can be grouped together before they're executed.  <br/>  By default, this key doesn't exist in the EdgeTransport.exe.config file.  <br/> |
| _QueueDatabaseBatchTimeout_ <br/> |100  <br/> |Specifies the maximum time in milliseconds that the database will wait for multiple database I/O operations to group before it executes them. The database I/O operations are executed without waiting for any more if the following conditions are true:  <br/> • The number of database I/O operations that's specified by the _QueueDatabaseBatchSize_ key hasn't been reached.  <br/> • The time specified by the _QueueDatabaseBatchTimeout_ key has passed.  <br/> By default, this key doesn't exist in the EdgeTransport.exe.config file.  <br/> |
| _QueueDatabaseMaxConnections_ <br/> |4  <br/> |Specifies the number of ESE database connections that can be open.  <br/> |
| _QueueDatabaseLoggingBufferSize_ <br/> |5MB  <br/> |Specifies the memory that's used to cache the transaction records before they're written to the transaction log file.  <br/> |
| _QueueDatabaseLoggingFileSize_ <br/> |5MB  <br/> |Specifies the maximum size of a transaction log file. When the maximum log file size is reached, a new log file is opened.  <br/> |
| _QueueDatabaseLoggingPath_ <br/> | `%ExchangeInstallPath%TransportRoles\data\Queue` <br/> |Specifies the default directory for the queue database log files. For instructions on how to change the location of the queue database, see [Change the location of the queue database](relocate-queue-database.md).  <br/> |
| _QueueDatabaseMaxBackgroundCleanupTasks_ <br/> |32  <br/> |Specifies the maximum number of background cleanup work items that can be queued to the database engine thread pool at any time.  <br/> |
| _QueueDatabaseOnlineDefragEnabled_ <br/> |True  <br/> |Enables or disables scheduled online defragmentation of the mail queue database.  <br/>  By default, this key doesn't exist in the EdgeTransport.exe.config file.  <br/> |
| _QueueDatabaseOnlineDefragSchedule_ <br/> | `1:00:00` or 1:00 A.M.  <br/> |Specifies the time of day in 24 hour format to start the online defragmentation of the mail queue database. To specify a value, enter the value as a time span: _hh:mm:ss_, where _h_ = hours, _m_ = minutes, and _s_ = seconds.  <br/> |
| _QueueDatabaseOnlineDefragTimeToRun_ <br/> | `3:00:00` or 3 hours  <br/> |Specifies the length of time the online defragmentation task is allowed to run. Even if the defragmentation task doesn't finish in the time specified, the queue database is left in a consistent state. To specify a value, enter the value as a time span: _hh:mm:ss_, where _h_ = hours, _m_ = minutes, and _s_ = seconds.  <br/> |
| _QueueDatabasePath_ <br/> | `%ExchangeInstallPath%TransportRoles\data\Queue` <br/> |Specifies the default directory for the queue database files. For instructions on how to change the location of the queue database, see [Change the location of the queue database](relocate-queue-database.md).  <br/> |
   
## Queue properties
<a name="QueueProperties"> </a>

A queue has many properties that describe the purpose and status of the queue. Some queue properties are applied to the queue when the queue is created, and don't change. Other properties contain status, size, time, or other indicators that are updated frequently.
  
### NextHopSolutionKey
<a name="NextHopSolutionKey"> </a>

The routing component of the categorizer in the Microsoft Exchange Transport service selects the destination for a message, and this destination is used to create the delivery queue. The destination is stamped on every recipient as the **NextHopSolutionKey** property. Every unique value of the **NextHopSolutionKey** property corresponds to a separate delivery queue. 
  
The **NextHopSolutionKey** property contains the following fields: 
  
- **DeliveryType**: Represents the results of the categorization of the message, and how the Transport service intends to transmit the message to the next hop, which could be the ultimate destination of the message, or an intermediate hop along the way. The Transport service uses a predefined list of values for **DeliveryType**. 
    
    Based on the value of **DeliveryType**, the **NextHopCategory** property is added to the queue. 
    
  - The value `External` indicates the next hop for the queue is outside the Exchange organization. 
    
  - The value `Internal` indicates the next hop for the queue is inside the Exchange organization. 
    
    Note that a message for an external recipient may require one or more internal hops before the message is delivered externally.
    
- **NextHopDomain**: Uses specific values based on the value of the **DeliveryType** field. For delivery queues, the value of this field is effectively the name of the queue. 
    
     The value of **NextHopDomain** isn't always a domain name. For example, the value could be the name of the target Active Directory site or database availability group (DAG). Think of this field as the *next hop name* . 
    
- **NextHopConnector**: Uses specific values based on the value of the **DeliveryType** field. The value is always expressed as a GUID. If this field isn't used, the value is a GUID with all zeroes. 
    
     The value of **NextHopConnector** isn't always the GUID of a connector. For example, the value could be the GUID of the target Active Directory site or DAG. Think of this field as the *next hop GUID* . 
    
The values of **DeliveryType**, **NextHopCategory**, **NextHopDomain** and **NextHopConnector** are described in the following table. 
  
|**Delivery Type in Queue Viewer**|**DeliveryType in the Exchange Management Shell**|**Description**|**NextHopCategory**|**NextHopDomain**|**NextHopConnector**|
|:-----|:-----|:-----|:-----|:-----|:-----|
|**Delivery Agent** <br/> | `DeliveryAgent` <br/> |The queue holds messages for delivery to recipients in a non-SMTP address space that's serviced by a delivery agent and a Delivery Agent connector. The connector has the local Mailbox server configured as a source server. For more information, see [Delivery Agents and Delivery Agent Connectors](http://technet.microsoft.com/library/38c942ee-b59d-47ec-87eb-bebad441ada5.aspx).  <br/> |External  <br/> |This value is the destination address space that's configured on the Delivery Agent connector. For example, `MOBILE`.  <br/> |This value is the GUID of the Delivery Agent connector. For example, `4520e633-d83d-411a-bbe4-6a84648674ee`.  <br/> |
|**DnsConnectorDelivery** <br/> | `DnsConnectorDelivery` <br/> |The queue holds messages for delivery to recipients in an SMTP domain. The Send connector that services the domain has the local transport server configured as source server, and the Send connector is configured to use DNS routing.  <br/> |External  <br/> |This value is the destination address space that's configured on the Send connector. For example, `contoso.com`.  <br/> |This value is the GUID of the Send connector. For example, `4520e633-d83d-411a-bbe4-6a84648674ee`.  <br/> |
|**Heartbeat** <br/> | `Heartbeat` <br/> |This value is reserved for internal Microsoft use. For more information about heartbeat, see [Shadow redundancy in Exchange 2016](../../mail-flow/transport-high-availability/shadow-redundancy.md).  <br/> |n/a  <br/> |n/a  <br/> |n/a  <br/> |
|**MapiDelivery** <br/> | `MapiDelivery` <br/> |**Note**: This value isn't used by Exchange 2016. It's included for backwards compatibility with Exchange 2010.  <br/> The queue holds messages for delivery by an Exchange 2010 Hub Transport server to a mailbox on an Exchange 2010 Mailbox server in the local Active Directory site.  <br/> |n/a  <br/> |n/a  <br/> |n/a  <br/> |
|**NonSmtpGatewayDelivery** <br/> | `NonSmtpGatewayDelivery` <br/> |The queue holds messages for delivery to recipients in a non-SMTP address space that's serviced by a Foreign connector. The connector has the local Mailbox server configured as a source server. For more information, see [Foreign Connectors](http://technet.microsoft.com/library/21c6a7a9-f4d2-4359-9ac9-930701b63a4e.aspx).  <br/> |External  <br/> |This value is the destination address space that's configured on the Foreign connector. For example, `FAX`.  <br/> |This value is the GUID of the Foreign connector. For example, `4520e633-d83d-411a-bbe4-6a84648674ee`.  <br/> |
|**Shadow Redundancy** <br/> | `ShadowRedundancy` <br/> |The queue holds messages in a shadow queue. A shadow queue holds redundant copies messages in transit in case the primary messages aren't successfully delivered. For more information, see [Shadow redundancy in Exchange 2016](../../mail-flow/transport-high-availability/shadow-redundancy.md).  <br/> |Internal  <br/> |This value is the FQDN of the primary transport server for which the shadow queue is holding redundant copies of the primary messages. For example, `mailbox01.contoso.com`.  <br/> |This value is `00000000-0000-0000-0000-000000000000`.  <br/> |
|**SmartHostConnectorDelivery** <br/> | `SmartHostConnectorDelivery` <br/> |The queue holds messages for delivery to recipients in an SMTP domain. The Send connector that services the domain has the local transport server configured as source server, and the Send connector is configured to use smart host routing.  <br/> |External  <br/> |This value is the list of smart hosts that are configured on the Send connector. Smart hosts can be configured as FQDNs, IP addresses or both. The values can be one of the following:  <br/> **FQDN**: The syntax is `<FQDN1,FQDN2,...>`. For example, `smarthost01.contoso.com` or `smarthost01.contoso.com,smarthost02.fabrikam.com`.  <br/> **IP address**: The syntax is `<[IPAddress1],[IPAddress2],...>`. For example, `[10.10.10.100]` or `[10.10.10.100],[10.10.10.101]`.  <br/> **FQDN and IP address**: The syntax is `<[IPAddress1],FQDN1,...>`, and depends on how the smart hosts are listed on the Send connector. For example, `[172.17.17.7],relay.tailspintoys.com` or `mail.contoso.com,[192.168.1.50]`.  <br/> |This value is the GUID of the Send connector. For example, `4520e633-d83d-411a-bbe4-6a84648674ee`.  <br/> |
|**SMTP Delivery to Ex Online** <br/> | `SmtpDeliveryToExo` <br/> |This value isn't used in on-premises Exchange.  <br/> |n/a  <br/> |n/a  <br/> |n/a  <br/> |
|**SMTP Delivery to Mailbox** <br/> | `SmtpDeliveryToMailbox` <br/> | The queue holds messages for delivery to Exchange 2016 or Exchange 2013 mailbox recipients. The destination mailbox database is in one of the following locations:  <br/>  The local Exchange 2016 Mailbox server or Exchange 2013 Mailbox server.  <br/>  An Exchange 2016 Mailbox server in the same Exchange 2016 DAG.  <br/>  An Exchange 2013 Mailbox server in the same Exchange 2013 DAG.  <br/>  An Exchange 2016 Mailbox server or an Exchange 2013 Mailbox server in the same Active Directory site in non-DAG environments.  <br/> |Internal  <br/> |This value is the name of the destination mailbox database. For example, `Mailbox Database 0471695037`.  <br/> |This value is the GUID of the target mailbox database. For example, `6dcb5a1e-0a88-4fc9-b8f9-634c34b1a123`.  <br/> |
|**SMTP Relay to Send Connector Source Servers** <br/> | `SmtpRelayToConnectorSourceServers` <br/> |The queue holds messages for delivery to an SMTP or non-SMTP address space that's serviced by a Send connector, Delivery Agent connector, or Foreign connector. The connector has a remote transport server configured as a source server.  <br/>  The remote transport server could be an Exchange 2016 Mailbox server, an Exchange 2013 Mailbox server, or an Exchange 2010 Hub Transport server.  <br/> The remote transport server could be located in the local Active Directory site, or in a remote Active Directory site.  <br/> |Internal  <br/> |This value is the name of the destination Send connector, Delivery Agent connector, or Foreign connector. For example, `Contoso.com Send Connector`.  <br/> |This value is the GUID of the destination Send connector, Delivery Agent connector, or Foreign connector. For example, `4520e633-d83d-411a-bbe4-6a84648674ee`.  <br/> |
|**SMTP Relay to Database Availability Group** <br/> | `SmtpRelayToDag` <br/> |The queue holds messages for delivery to Exchange 2016 or Exchange 2013 mailbox recipients, where the destination mailbox database is located in a remote DAG.  <br/> The remote DAG could be located in the local Active Directory site, or in a remote Active Directory site.  <br/> |Internal  <br/> |This value is the name of the destination DAG. For example, `DAG1`.  <br/> |This value is the GUID of the destination DAG. For example, `6dcb5a1e-0a88-4fc9-b8f9-634c34b1a123` <br/> |
|**SMTP Relay to Mailbox Delivery Group** <br/> | `SmtpRelayToMailboxDeliveryGroup` <br/> |The queue holds messages for delivery to legacy mailbox recipients, where the destination mailbox is on an Exchange 2010 Mailbox server. The message is related to an Exchange 2010 Hub Transport server.  <br/>  The destination Exchange 2010 Hub Transport server could be in the local Active Directory site, or a remote Active Directory site.  <br/> |Internal  <br/> |The queue name uses the syntax: `Site:<ADSiteName>;Version:<ExchangeVersion>`, where _\<ADSiteName\>_ is the name of the destination Active Directory site, and _\<ExchangeVersion\>_ is the version of Exchange 2010 on the Mailbox server.  <br/> |This value is blank.  <br/> |
|**SMTP Relay to Remote Active Directory Site** <br/> | `SmtpRelayToRemoteActiveDirectorySite` <br/> | The queue holds messages for delivery to a remote destination, and the routing topology requires the message to be routed through a specific Active Directory site. The site is an intermediate hop on the way to the final destination. This situation occurs under the following circumstances:  <br/>  The message needs to be routed through a hub site.  <br/>  The message requires delivery through a Send connector that's configured on an Edge Transport server that's subscribed to a remote Active Directory site.  <br/> |Internal  <br/> |This value is the target Active Directory site name. For example, `NorthAmericaSite`.  <br/> |This value is the GUID of the target Active Directory site. For example, `bfd6c3df-5b65-8bfb-53f1f2c0d55c`.  <br/> |
|**SMTP Relay to specified remote forest** <br/> | `SmtpRelayToRemoteForest` <br/> |This value isn't used in on-premises Exchange  <br/> |n/a  <br/> |n/a  <br/> |n/a  <br/> |
|**SMTP Relay to Specified Exchange Servers** <br/> | `SmtpRelayToServers` <br/> |The queue holds messages for delivery to a distribution group that's configured for a specific expansion server. The expansion server could be an Exchange 2016 Mailbox server, an Exchange 2013 Mailbox server, or an Exchange 2010 Hub Transport server.  <br/> The expansion server could be located in the local Active Directory site, or in a remote Active Directory site.  <br/> |Internal  <br/> |This value is the FQDN of the target expansion server. For example, `mailbox01.contoso.com`.  <br/> |This value is `0000000-0000-0000-0000-000000000000`.  <br/> |
|**SmtpRelayToTiRg** <br/> | `SmtpRelayToTiRg` <br/> |**Note**: This value isn't used by Exchange 2016. It's included for backwards compatibility with Exchange 2010.  <br/> The queue holds messages for delivery by an Exchange 2010 Hub Transport server to an Exchange 2003 routing group.  <br/> |n/a  <br/> |n/a  <br/> |n/a  <br/> |
|**Smtp Relay in Active Directory Site** <br/> | `SmtpRelayWithinAdSite` <br/> |**Note**: This value isn't used by Exchange 2016. It's included for backwards compatibility with Exchange 2010.  <br/> The queue holds messages for delivery by an Exchange 2010 Hub Transport server to another Hub Transport server in the same Active Directory site.  <br/> |n/a  <br/> |n/a  <br/> |n/a  <br/> |
|**SMTP Relay in Active Directory Site to Edge Transport Server** <br/> | `SmtpRelayWithinAdSiteToEdge` <br/> |The queue holds messages for delivery to an external SMTP domain that's serviced by a Send connector that's configured on an Edge Transport server. The Edge Transport server is subscribed to the local Active Directory site.  <br/> |Internal  <br/> |This value is the name of the Send connector that sends outbound Internet mail from the Edge Transport server to the Internet. This Send connector is automatically created by the Edge subscription, and is named EdgeSync - _\<ADSiteName\>_ to Internet.  <br/> |This value is the GUID of the Send connector. For example, `4520e633-d83d-411a-bbe4-6a84648674ee`.  <br/> |
|**Undefined** <br/> | `Undefined` <br/> |This value is used only on the Submission queue and the poison message queue.  <br/> |Internal  <br/> |For the Submission queue, this value is `Submisssion`. For the poison message queue, this value is `Poison Message`.  <br/> |This value is `00000000-0000-0000-0000-000000000000`.  <br/> |
|**Unreachable** <br/> | `Unreachable` <br/> |This value is used only on the Unreachable queue.  <br/> |Internal  <br/> |This value is `Unreachable Domain`.  <br/> |This value is `00000000-0000-0000-0000-000000000000`.  <br/> |
   
### IncomingRate, OutgoingRate, and Velocity
<a name="RatesAndVelocity"> </a>

Exchange 2016 measures the rate of messages entering and leaving a queue and stores these values in queue properties. You can use these rates as an indicator of queue and transport server health. The properties are described in the following table:
  
****

|**Property**|**Description**|
|:-----|:-----|
|**IncomingRate** <br/> |The rate that messages are entering the queue. The rate is the number of messages per second averaged over the last minute.  <br/> |
|**OutgoingRate** <br/> |The rate that messages are leaving the queue. The rate is the number of messages per second averaged over the last minute.  <br/> |
|**Velocity** <br/> | The drain rate of the queue, calculated by subtracting the value of **IncomingRate** from the value of **OutgoingRate**.  <br/>  If the value is greater than 0, messages are leaving the queue faster than they are entering the queue.  <br/>  If the value equals 0, messages are leaving the queue as fast as they are entering the queue. This is also the value you'll see when the queue is inactive.  <br/>  If the value is less than 0, messages are entering the queue faster than they are leaving the queue.  <br/>  The **Velocity** value is displayed in the results of **Get-Queue**.  <br/> |
   
At a basic level, a positive value of **Velocity** indicates a healthy queue that's efficiently draining, and a negative value of **Velocity** indicates a queue that isn't efficiently draining. However, you also need to consider the values of **IncomingRate**, **OutgoingRate**, and **MessageCount**, as well as the magnitude of **Velocity**. 
  
For example, consider a queue that has the following property values.
  
- **Velocity**: -50 
    
- **MessageCount**: 1000 
    
- **OutgoingRate**: 10 
    
- **IncomingRate**: 60 
    
 Based on the property values for this queue, the negative value for **Velocity** clearly indicates that the queue isn't draining properly. 
  
Now consider a queue that has the following property values.
  
- **Velocity**: -0.85 
    
- **MessageCount**: 2 
    
- **OutgoingRate**: 0.15 
    
- **IncomingRate**: 1 
    
 Although the value for **Velocity** is negative, it's very close to zero, and the values of the other properties are also very small. Therefore, a negative **Velocity** value for this queue doesn't indicate a problem with the queue. 
  
### Queue status
<a name="QueueStatus"> </a>

The current status of a queue is stored in the **Status** property of the queue. A queue can have one of the status values that's described in the following table: 
  
|**Queue status**|**Description**|
|:-----|:-----|
|Active  <br/> |The queue is actively transmitting messages.  <br/> |
|Connecting  <br/> |The queue is in the process of connecting to the next hop.  <br/> |
|Ready  <br/> |The queue recently transmitted messages, but the queue is now empty.  <br/> |
|Retry  <br/> |The last automatic or manual connection attempt failed, and the queue is waiting to retry the connection.  <br/> |
|Suspended  <br/> | The queue has been manually suspended by an administrator to prevent message delivery. New messages can enter the queue, and messages that are in the act of being transmitted to the next hop will finish delivery and leave the queue. Otherwise, messages won't leave the queue until the queue is manually resumed by an administrator.  <br/> **Notes:** <br/>  You can suspend the following queues:  <br/>  Delivery queues that have any status.  <br/>  The Unreachable queue. When you suspend this queue, messages are no longer automatically resubmitted to the categorizer when configuration updates are detected. To automatically resubmit these messages, you need to manually resume the queue.  <br/>  The Submission queue. When you suspend this queue, messages aren't picked up by the categorizer until the queue is resumed.  <br/>  Suspending a queue doesn't change the status of the messages in the queue.  <br/> |
   
### Other queue properties
<a name="OtherQueueProperties"> </a>

There are other queue properties that are self-explanatory. You can use most of the queue properties as filter options. By specifying filter criteria, you can quickly locate queues and take action on them. For a complete description of the filterable queue properties, see [Queue properties](queue-properties.md).
  
An important queue property that's also worth mentioning here is the **MessageCount** property that shows how many messages are in a queue. This property is an important indicator of queue health. For example, a delivery queue that contains a large number of messages that continues to grow and never decreases could indicate a routing or transport pipeline issue that requires your attention. 
  
## Message properties
<a name="MessageProperties"> </a>

A message in a queue has many properties. Many of the properties reflect the information that was used to create the message. Some of the messages status and information properties are heavily influenced by corresponding properties on the queue. However, an individual message may have a different value than the corresponding property of the queue. Other properties contain status, time, or other indicators that are updated frequently.
  
### Message status
<a name="MessageStatus"> </a>

The current status of a message is stored in the **Status** property of the message. A message can have one of the status values that's described in the following table: 
  
|**Message status**|**Description**|
|:-----|:-----|
|Active  <br/> |If the message is in a delivery queue, the message is being delivered to its destination. If the message is in the Submission queue, the message is being processed by the categorizer.  <br/> |
|Locked  <br/> |This value is reserved for internal Microsoft use, and isn't used in on-premises Exchange organizations.  <br/> |
|PendingRemove  <br/> |The message was deleted by the administrator, but the message was already in the act of being transmitted to the next hop. The message will be deleted if the delivery ends in an error that causes the message to reenter the queue. Otherwise, delivery will continue.  <br/> |
|PendingSuspend  <br/> |The message was suspended by the administrator, but the message was already in the act of being transmitted to the next hop. The message will be suspended if the delivery ends in an error that causes the message to reenter the queue. Otherwise, delivery will continue.  <br/> |
|Ready  <br/> |The message is waiting in the queue and is ready to be processed.  <br/> |
|Retry  <br/> |The last automatic or manual connection attempt fail for the queue that holds the message. The message is waiting for the next automatic queue connection retry.  <br/> |
|Suspended  <br/> |The message was manually suspended by an administrator.  <br/>  Any messages in the poison message queue are in a permanently suspended state.  <br/> |
   
### Other message properties
<a name="OtherMessageProperties"> </a>

There are other message properties that are self-explanatory. You can use most of the message properties as filter options. By specifying filter criteria, you can quickly locate messages and take action on them. For a complete description of the filterable message properties, see [Properties of messages in queues](message-properties.md).
  
## Manage queues and messages in queues
<a name="ManageQueuesAndMessages"> </a>

Queue Viewer and the historical queue and message management cmdlets in the Exchange Management Shell are restricted to a single Exchange server. You can view or operate on individual queues or messages, or multiple queues or messages, but only on a specific server.
  
Exchange 2016 use the **Get-QueueDigest** cmdlet that was introduced in Exchange 2013 to provides a high-level, aggregate view of the state of queues on all servers within a specific scope. The scope could be a DAG, an Active Directory site, a list of servers, or the entire Active Directory forest. Note that queues on a subscribed Edge Transport server in the perimeter network aren't included in the results. Also, **Get-QueueDigest** is available on Edge Transport servers, but the results are restricted to queues on the Edge Transport server. 
  
> [!NOTE]
> By default, the **Get-QueueDigest** cmdlet displays delivery queues that contain ten or more messages, and the results are between one and two minutes old. For instructions on how to change these default values, see **Configure Get-QueueDigest**. 
  
The following table describes the management tasks you can perform on queues or messages in queues.
  
|**Task**|**Description**|**Tool to use**|**Instructions**|
|:-----|:-----|:-----|:-----|
|View and filter queues on a server  <br/> |Displays one or more queues on a transport server. You can use the results to take action on the queues.  <br/> |Queue Viewer or the **Get-Queue** cmdlet.  <br/> |[Procedures for queues](queue-procedures.md) <br/> |
|View and filter queues on specific servers in specific DAGs, specific Active Directory sites, or in the whole Active Directory forest.  <br/> |Displays a summary list of queues.  <br/> |**Get-QueueDigest** cmdlet  <br/> |[Procedures for queues](queue-procedures.md) <br/> |
|Suspend queues  <br/> |Temporarily prevent delivery of messages that are currently in the queue. The queue continues to accept new messages, but no messages leave the queue.  <br/> |Queue Viewer or the **Suspend-Queue** cmdlet.  <br/> |[Procedures for queues](queue-procedures.md) <br/> |
|Resume queues  <br/> |Reverses the effect of the suspend queue action, and enables delivery of queued messages to resume.  <br/> |Queue Viewer or the **Resume-Queue** cmdlet.  <br/> |[Procedures for queues](queue-procedures.md) <br/> |
|Retry queues  <br/> |Immediately tries to connect to the next hop. Without manual intervention, when the connection to the next hop fails, the connection is attempted a specific number of times after a specific time interval between each attempt.  <br/> Whether the connection attempt is manual or automatic, any connection attempt resets the next retry time. For more information, see [Message retry, resubmit, and expiration intervals](message-intervals.md).  <br/> |Queue Viewer or the **Retry-Queue** cmdlet.  <br/> |[Procedures for queues](queue-procedures.md) <br/> |
|Resubmit messages in queues  <br/> |Causes messages in the queue to be resubmitted to the Submission queue and to go back through the categorization process.  <br/> |**Retry-Queue** with the _Resubmit_ parameter  <br/> Note that you can use Queue Viewer to resubmit messages, but only from the poison message queue. To resubmit a poison message, you first need to resume the message in Queue Viewer, or by using the **Resume-Message** cmdlet.  <br/> |[Procedures for queues](queue-procedures.md) <br/> |
|Suspend messages in queues  <br/> |Temporarily prevents delivery of a message. You can use the suspend message action to prevent delivery of a message to all the recipients in a specific queue or to all recipients in all queues.  <br/> |Queue Viewer or the **Suspend-Message** cmdlet.  <br/> |[Procedures for messages in queues](message-procedures.md) <br/> |
|Resume messages in queues  <br/> |Reverses the effect of the suspend message action, and enables the delivery of queued messages to resume. You can resume the delivery of a message to all recipients in a specific queue, or to all recipients in all queues.  <br/> |Queue Viewer or the **Resume-Message** cmdlet.  <br/> |[Procedures for messages in queues](message-procedures.md) <br/> |
|Remove messages from queues  <br/> |Permanently prevents the delivery of a message. You can prevent the delivery of a message to any recipients in a specific queue, or to all recipients in all queues. Optionally, you can send a non-delivery report (also known as an NDR, delivery status notification, DSN or bounce message) to the sender when the message is removed.  <br/> |Queue Viewer or the **Remove-Message** cmdlet.  <br/> |[Procedures for messages in queues](message-procedures.md) <br/> |
|Export messages from queues  <br/> |Copies a message to the location that you specify. The messages aren't deleted from the queue, but a copy of the message is saved as a file in the specified location. This enables administrators or officials in an organization to later examine the messages. Before you export a message, you need to temporarily suspend the message.  <br/> |**Export-Message** cmdlet only.  <br/> |[Export messages from queues](export-messages.md) <br/> |
   

