---
title: "Monitor database availability groups"
ms.author: dmaguire
author: msdmaguire
manager: serdars
ms.date: 4/19/2018
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: f5bdfd6e-e93c-4d96-8bc2-548750d51930
description: "Summary: Resources and methods for monitoring the health and status of DAGs in Exchange 2016."
---

# Monitor database availability groups

 **Summary**: Resources and methods for monitoring the health and status of DAGs in Exchange 2016.
  
You can use the details in this topic for monitoring mailbox database copies for database availability groups (DAGs), for gathering diagnostic information, and for configuring the low disk space monitoring threshold.
  
## Get-MailboxDatabaseCopyStatus cmdlet
<a name="Get"> </a>

Use the [Get-MailboxDatabaseCopyStatus](http://technet.microsoft.com/library/6ad690fb-3a23-41d4-b19d-666b34e62b26.aspx) cmdlet to view status information about mailbox database copies. This cmdlet enables you to view information about all copies of a particular database, information about a specific copy of a database on a specific server, or information about all database copies on a server. The following table describes possible values for the copy status of a mailbox database copy. 
  
**Database copy status**

|**Database copy status**|**Description**|
|:-----|:-----|
|Failed  <br/> |The mailbox database copy is in a Failed state because it isn't suspended, and it isn't able to copy or replay log files. While in a Failed state and not suspended, the system will periodically check whether the problem that caused the copy status to change to Failed has been resolved. After the system has detected that the problem is resolved, and barring no other issues, the copy status will automatically change to Healthy.  <br/> |
|Seeding  <br/> |The mailbox database copy is being seeded, the content index for the mailbox database copy is being seeded, or both are being seeded. Upon successful completion of seeding, the copy status should change to Initializing.  <br/> |
|SeedingSource  <br/> |The mailbox database copy is being used as a source for a database copy seeding operation.  <br/> |
|Suspended  <br/> |The mailbox database copy is in a Suspended state as a result of an administrator manually suspending the database copy by running the **Suspend-MailboxDatabaseCopy** cmdlet.  <br/> |
|Healthy  <br/> |The mailbox database copy is successfully copying and replaying log files, or it has successfully copied and replayed all available log files.  <br/> |
|ServiceDown  <br/> |The Microsoft Exchange Replication service isn't available or running on the server that hosts the mailbox database copy.  <br/> |
|Initializing  <br/> |The mailbox database copy is in an Initializing state when a database copy has been created, when the Microsoft Exchange Replication service is starting or has just been started, and during transitions from Suspended, ServiceDown, Failed, Seeding, or SinglePageRestore to another state. While in this state, the system is verifying that the database and log stream are in a consistent state. In most cases, the copy status will remain in the Initializing state for about 15 seconds, but in all cases, it should generally not be in this state for longer than 30 seconds.  <br/> |
|Resynchronizing  <br/> |The mailbox database copy and its log files are being compared with the active copy of the database to check for any divergence between the two copies. The copy status will remain in this state until any divergence is detected and resolved.  <br/> |
|Mounted  <br/> |The active copy is online and accepting client connections. Only the active copy of the mailbox database copy can have a copy status of Mounted.  <br/> |
|Dismounted  <br/> |The active copy is offline and not accepting client connections. Only the active copy of the mailbox database copy can have a copy status of Dismounted.  <br/> |
|Mounting  <br/> |The active copy is coming online and not yet accepting client connections. Only the active copy of the mailbox database copy can have a copy status of Mounting.  <br/> |
|Dismounting  <br/> |The active copy is going offline and terminating client connections. Only the active copy of the mailbox database copy can have a copy status of Dismounting.  <br/> |
|DisconnectedAndHealthy  <br/> |The mailbox database copy is no longer connected to the active database copy, and it was in the Healthy state when the loss of connection occurred. This state represents the database copy with respect to connectivity to its source database copy. It may be reported during DAG network failures between the source copy and the target database copy.  <br/> |
|DisconnectedAndResynchronizing  <br/> |The mailbox database copy is no longer connected to the active database copy, and it was in the Resynchronizing state when the loss of connection occurred. This state represents the database copy with respect to connectivity to its source database copy. It may be reported during DAG network failures between the source copy and the target database copy.  <br/> |
|FailedAndSuspended  <br/> |The Failed and Suspended states have been set simultaneously by the system because a failure was detected, and because resolution of the failure explicitly requires administrator intervention. An example is if the system detects unrecoverable divergence between the active mailbox database and a database copy. Unlike the Failed state, the system won't periodically check whether the problem has been resolved, and automatically recover. Instead, an administrator must intervene to resolve the underlying cause of the failure before the database copy can be transitioned to a healthy state.  <br/> |
|SinglePageRestore  <br/> |This state indicates that a single page restore operation is occurring on the mailbox database copy.  <br/> |
   
The **Get-MailboxDatabaseCopyStatus** cmdlet also returns details about the in-use replication networks, including  _IncomingLogCopyingNetwork_, which is returned for passive database copies, and  _OutgoingConnections_, which is returned for active databases that have more than one copy, as well as any database copy being used as a source for a database seeding operation. Outgoing connection information is provided for database copies that are in file mode replication. Outgoing connection information is not provided for database copies that are in block mode replication.
  
### Get-MailboxDatabaseCopyStatus examples
<a name="RTT"> </a>

The following examples use the **Get-MailboxDatabaseCopyStatus** cmdlet. Each example pipes the results to the **Format-List** cmdlet to display the output in list format. 
  
This example returns status information for all copies of the database DB2.
  
```
Get-MailboxDatabaseCopyStatus -Identity DB2 | Format-List
```

This example returns the status for all database copies on the Mailbox server MBX2.
  
```
Get-MailboxDatabaseCopyStatus -Server MBX2 | Format-List
```

This example returns the status for all database copies on the local Mailbox server.
  
```
Get-MailboxDatabaseCopyStatus -Local | Format-List
```

For more information about using the **Get-MailboxDatabaseCopyStatus** cmdlet, see [Get-MailboxDatabaseCopyStatus](http://technet.microsoft.com/library/6ad690fb-3a23-41d4-b19d-666b34e62b26.aspx).
  
## Test-ReplicationHealth cmdlet
<a name="Test"> </a>

You can use the [Test-ReplicationHealth](http://technet.microsoft.com/library/da55fa0f-e100-44b1-b9b4-bf14e55a5b4d.aspx) cmdlet to view continuous replication status information about mailbox database copies. This cmdlet can be used to check all aspects of the replication and replay status to provide a complete overview of a specific Mailbox server in a DAG. 
  
The **Test-ReplicationHealth** cmdlet is designed for the proactive monitoring of continuous replication and the continuous replication pipeline, the availability of Active Manager, and the health and status of the underlying cluster service, quorum, and network components. It can be run locally on or remotely against any Mailbox server in a DAG. The **Test-ReplicationHealth** cmdlet performs the tests listed in the following table. 
  
**Test-ReplicationHealth cmdlet tests**

|**Test name**|**Description**|
|:-----|:-----|
|ClusterService  <br/> |Verifies that the Cluster service is running and reachable on the specified DAG member, or if no DAG member is specified, on the local server.  <br/> |
|ReplayService  <br/> |Verifies that the Microsoft Exchange Replication service is running and reachable on the specified DAG member, or if no DAG member is specified, on the local server.  <br/> |
|ActiveManager  <br/> |Verifies that the instance of Active Manager running on the specified DAG member, or if no DAG member is specified, the local server, is in a valid role (primary, secondary, or stand-alone).  <br/> |
|TasksRpcListener  <br/> |Verifies that the tasks remote procedure call (RPC) server is running and reachable on the specified DAG member, or if no DAG member is specified, on the local server.  <br/> |
|TcpListener  <br/> |Verifies that the TCP log copy listener is running and reachable on the specified DAG member, or if no DAG member is specified, on the local server.  <br/> |
|ServerLocatorService  <br/> |Verifies the Active Manager client/server processes on DAG members and on the Client Access Server that perform lookups in Active Directory and Active Manager to determine where a user's mailbox database is active.  <br/> |
|DagMembersUp  <br/> |Verifies that all DAG members are available, running, and reachable.  <br/> |
|ClusterNetwork  <br/> |Verifies that all cluster-managed networks on the specified DAG member, or if no DAG member is specified, the local server, are available.  <br/> |
|QuorumGroup  <br/> |Verifies that the default cluster group (quorum group) is in a healthy and online state.  <br/> |
|FileShareQuorum  <br/> |Verifies that the witness server and witness directory and share configured for the DAG are reachable.  <br/> |
|DatabaseRedundancy  <br/> |Verifies that there is at least one healthy copy available of the databases on the specified DAG member, or if no DAG member is specified, on the local server.  <br/> |
|DatabaseAvailability  <br/> |Verifies that the databases have sufficient availability on the specified DAG member, or if no DAG member is specified, on the local server.  <br/> |
|DBCopySuspended  <br/> |Checks whether any mailbox database copies are in a state of Suspended on the specified DAG member, or if no DAG member is specified, on the local server.  <br/> |
|DBCopyFailed  <br/> |Checks whether any mailbox database copies are in a state of Failed on the specified DAG member, or if no DAG member is specified, on the local server.  <br/> |
|DBInitializing  <br/> |Checks whether any mailbox database copies are in a state of Initializing on the specified DAG member, or if no DAG member is specified, on the local server.  <br/> |
|DBDisconnected  <br/> |Checks whether any mailbox database copies are in a state of Disconnected on the specified DAG member, or if no DAG member is specified, on the local server.  <br/> |
|DBLogCopyKeepingUp  <br/> |Verifies that log copying and inspection by the passive copies of databases on the specified DAG member, or if no DAG member is specified, on the local server, are able to keep up with log generation activity on the active copy.  <br/> |
|DBLogReplayKeepingUp  <br/> |Verifies that replay activity for the passive copies of databases on the specified DAG member, or if no DAG member is specified, on the local server, is able to keep up with log copying and inspection activity.  <br/> |
   
### Test-ReplicationHealth example

This example uses the **Test-ReplicationHealth** cmdlet to test the health of replication for the Mailbox server MBX1. 
  
```
Test-ReplicationHealth -Identity MBX1
```

## Crimson channel event logging
<a name="Crimson"> </a>

Windows includes two categories of event logs: Windows logs, and Applications and Services logs. The Windows logs category includes the event logs available in previous versions of Windows: Application, Security, and System event logs. It also includes two new logs: the Setup log and the ForwardedEvents log. Windows logs are intended to store events from legacy applications and events that apply to the entire system.
  
Applications and Services logs are a new category of event logs. These logs store events from a single application or component rather than events that might have system-wide impact. This new category of event logs is referred to as an application's crimson channel.
  
The Applications and Services logs category includes four subtypes: Admin, Operational, Analytic, and Debug logs. Events in Admin logs are of particular interest if you use event log records to troubleshoot problems. Events in the Admin log should provide you with guidance about how to respond to the events. Events in the Operational log are also useful, but may require more interpretation. Admin and Debug logs aren't as user friendly. Analytic logs (which by default are hidden and disabled) store events that trace an issue, and often a high volume of events are logged. Debug logs are used by developers when debugging applications.
  
Exchange 2016 logs events to crimson channels in the Applications and Services logs area. You can view these channels by performing these steps:
  
1. Open Event Viewer.
    
2. In the console tree, navigate to **Applications and Services Logs** > **Microsoft** > **Exchange**.
    
3. Under **Exchange**, select a crimson channel, such as **HighAvailability** or **MailboxDatabaseFailureItems** to see DAG and database copy-related events, or **ActiveMontoring** or **ManagedAvailability** to see events related to Managed Availability. 
    
The HighAvailability channel contains events related to startup and shutdown of the Microsoft Exchange Replication service, and the various components that run within the Microsoft Exchange Replication service, such as Active Manager, the third-party synchronous replication API, the tasks RPC server, TCP listener, and Volume Shadow Copy Service (VSS) writer. The HighAvailability channel is also used by Active Manager to log events related to Active Manager role monitoring and database action events, such as a database mount operation and log truncation, and to record events related to the DAG's underlying cluster.
  
The MailboxDatabaseFailureItems channel is used to log events associated with any failures that affect a replicated mailbox database.
  
The ActiveMonitoring channel contains definition and result events for Managed Availability probes, monitors and responders.
  
The ManagedAvailability channel contains recovery action logs and results and related events.
  
## Low Disk Space Monitor
<a name="Crimson"> </a>

Exchange 2016 Managed Availability monitors hundreds of system metrics and components every minute, including the amount of free disk space on volumes used by the Mailbox server role. Prior to Exchange 2013 Service Pack 1 (SP1), Exchange monitored available space on all local volumes, including volumes that don't contain any databases or log files. In Exchange 2016, only volumes that contain Exchange databases and log files are monitored. The default threshold for the low volume space monitor is 180 GB. You can configure the threshold by adding the following DWORD registry value (in MB) on each Mailbox server that you want to customize:
  
Path: **HKEY_LOCAL_MACHINE\Software\Microsoft\ExchangeServer\v15\Replay\Parameters**
  
Value:  _SpaceMonitorLowSpaceThresholdInMB_
  
For example to configure the threshold to 100 GB, you would configure the following registry value:
  
 **REG_DWORD 186a0 (100000)**
  
After configuring or modifying the above registry value, you must restart the Microsoft Exchange DAG Management service for the change to take effect.
  
## CollectOverMetrics.ps1 script
<a name="CollectOver"> </a>

Exchange 2016 includes a script called CollectOverMetrics.ps1, which can be found in the Scripts folder. CollectOverMetrics.ps1 reads DAG member event logs to gather information about database operations (such as database mounts, moves, and failovers) over a specific time period. For each operation, the script records the following information:
  
- Identity of the database
    
- Time at which the operation began and ended
    
- Servers on which the database was mounted at the start and finish of the operation
    
- Reason for the operation
    
- Whether the operation was successful, and if the operation failed, the error details
    
The script writes this information to .csv files with one operation per row. It writes a separate .csv file for each DAG.
  
The script supports parameters that allow you to customize the script's behavior and output. For example, the results can be restricted to a specified subset by using the  _Database_ or  _ReportFilter_ parameters. Only the operations that match these filters will be included in the summary HTML report. The available parameters are listed in the following table. 
  
**CollectOverMetrics.ps1 script parameters**

|**Parameter**|**Description**|
|:-----|:-----|
| _DatabaseAvailabilityGroup_ <br/> |Specifies the name of the DAG from which you want to collect metrics. If this parameter is omitted, the DAG of which the local server is a member will be used. Wildcard characters can be used to collect information from and report on multiple DAGs.  <br/> |
| _Database_ <br/> |Provides a list of databases for which the report needs to be generated. Wildcard characters are supported, for example,  `-Database:"DB1","DB2"` or  `-Database:"DB*"`.  <br/> |
| _StartTime_ <br/> |Specifies the duration of the time period to report on. The script gathers only the events logged during this period. As a result, the script may capture partial operation records (for example, only the end of an operation at the start of the period or vice-versa). If neither  _StartTime_ nor  _EndTime_ is specified, the script defaults to the past 24 hours. If only one parameter is specified, the period will be 24 hours, either beginning or ending at the specified time.  <br/> |
| _EndTime_ <br/> |Specifies the duration of the time period to report on. The script gathers only the events logged during this period. As a result, the script may capture partial operation records (for example, only the end of an operation at the start of the period or vice-versa). If neither  _StartTime_ nor  _EndTime_ is specified, the script defaults to the past 24 hours If only one parameter is specified, the period will be 24 hours, either beginning or ending at the specified time.  <br/> |
| _ReportPath_ <br/> |Specifies the folder used to store the results of event processing. If this parameter is omitted, the Scripts folder will be used. When specified, the script takes a list of .csv files generated by the script and uses them as the source data to generate a summary HTML report. The report is the same one that's generated with the -GenerateHtmlReport option. The files can be generated across multiple DAGs at many different times, or even with overlapping times, and the script will merge all of their data together.  <br/> |
| _GenerateHtmlReport_ <br/> |Specifies that the script gather all the information it has recorded, group the data by the operation type, and then generate an HTML file that includes statistics for each of these groups. The report includes the total number of operations in each group, the number of operations that failed, and statistics for the time taken within each group. The report also contains a breakdown of the types of errors that resulted in failed operations.  <br/> |
| _ShowHtmlReport_ <br/> |Specifies that the HTML-generated report should be displayed in a Web browser after it's generated.  <br/> |
| _SummariseCsvFiles_ <br/> |Specifies that the script read the data from existing .csv files that were previously generated by the script. This data is then used to generate a summary report similar to the report generated by the  _GenerateHtmlReport_ parameter.  <br/> |
| _ActionType_ <br/> |Specifies the type of operational actions the script should collect. The values for this parameter are  `Move`,  `Mount`,  `Dismount`, and  `Remount`. The  `Move` value refers to any time that the database changes its active server, whether by controlled moves or by failovers. The  `Mount`,  `Dismount`, and  `Remount` values refer to times that the database changes its mounted status without moving to another computer.  <br/> |
| _ActionTrigger_ <br/> |Specifies which administrative operations should be collected by the script. The values for this parameter are  `Admin` or  `Automatic`. Automatic actions are those performed automatically by the system (for example, a failover when a server goes offline). Admin actions are any actions that were performed by an administrator using either the Exchange Management Shell or the Exchange Administration Center.  <br/> |
| _RawOutput_ <br/> |Specifies that the script writes the results that would have been written to .csv files directly to the output stream, as would happen with write-output. This information can then be piped to other commands.  <br/> |
| _IncludedExtendedEvents_ <br/> |Specifies that the script collects the events that provide diagnostic details of times spent mounting databases. This can be a time-consuming stage if the Application event log on the servers is large.  <br/> |
| _MergeCSVFiles_ <br/> |Specifies that the script takes all the .csv files containing data about each operation and merges them into a single .csv file.  <br/> |
| _ReportFilter_ <br/> |Specifies that a filter should be applied to the operations using the fields as they appear in the .csv files. This parameter uses the same format as a  `Where` operation, with each element set to  `$_` and returning a Boolean value. For example:  `{$_DatabaseName -notlike "Mailbox Database*"}` can be used to exclude the default databases from the report.  <br/> |
   
### CollectOverMetrics.ps1 examples

The following example collects metrics for all databases that match DB\* (which includes a wildcard character) in the DAG DAG1. After the metrics are collected, an HTML report is generated and displayed.
  
```
CollectOverMetrics.ps1 -DatabaseAvailabilityGroup DAG1 -Database:"DB*" -GenerateHTMLReport -ShowHTMLReport
```

The following examples demonstrate ways that the summary HTML report may be filtered. The first uses the  _Database_ parameter, which takes a list of database names. The summary report then contains data only about those databases. The next two examples use the  _ReportFilter_ option. The last example filters out all the default databases. 
  
```
CollectOverMetrics.ps1 -SummariseCsvFiles (dir *.csv) -Database MailboxDatabase123,MailboxDatabase456
CollectOverMetrics.ps1 -SummariseCsvFiles (dir *.csv) -ReportFilter { $_.DatabaseName -notlike "Mailbox Database*" }
CollectOverMetrics.ps1 -SummariseCsvFiles (dir *.csv) -ReportFilter { ($_.ActiveOnStart -like "ServerXYZ*") -and ($_.ActiveOnEnd -notlike "ServerXYZ*") }
```

## CollectReplicationMetrics.ps1 script
<a name="CollectRep"> </a>

CollectReplicationMetrics.ps1 is another health metric script included in Exchange 2016. This script provides an active form of monitoring because it collects metrics in real time, while the script is running. CollectReplicationMetrics.ps1 collects data from performance counters related to database replication. The script gathers counter data from multiple Mailbox servers, writes each server's data to a .csv file, and then reports various statistics across all of this data (for example, the amount of time each copy was failed or suspended, the average copy or replay queue length, or the amount of time that copies were outside of their failover criteria).
  
You can either specify the servers individually, or you can specify entire DAGs. You can either run the script to first collect the data and then generate the report, or you can run it to just gather the data or to only report on data that's already been collected. You can specify the frequency at which data should be sampled and the total duration to gather data.
  
The data collected from each server is written to a file named **CounterData.\<ServerName\>.\<TimeStamp\>.csv**. The summary report will be written to a file named **HaReplPerfReport.\<DAGName\>.\<TimeStamp\>.csv**, or **HaReplPerfReport.\<TimeStamp\>.csv** if you didn't run the script with the  _DagName_ parameter. 
  
The script starts Windows PowerShell jobs to collect the data from each server. These jobs run for the full period in which data is being collected. If you specify a large number of servers, this process can use a considerable amount of memory. The final stage of the process, when data is processed into a summary report, can also be quite time consuming for large amounts of data. It's possible to run the collection stage on one computer, and then copy the data elsewhere for processing.
  
The CollectReplicationMetrics.ps1 script supports parameters that allow you to customize the script's behavior and output. The available parameters are listed in the following table.
  
**CollectReplicationMetrics.ps1 script parameters**

|**Parameter**|**Description**|
|:-----|:-----|
| _DagName_ <br/> |Specifies the name of the DAG from which you want to collect metrics. If this parameter is omitted, the DAG of which the local server is a member will be used.  <br/> |
| _DatabaseNames_ <br/> |Provides a list of databases for which the report needs to be generated. Wildcard characters are supported for use, for example,  `-DatabaseNames:"DB1","DB2"` or  `-DatabaseNames:"DB*"`.  <br/> |
| _ReportPath_ <br/> |Specifies the folder used to store the results of event processing. If this parameter is omitted, the Scripts folder will be used.  <br/> |
| _Duration_ <br/> |Specifies the amount of time the collection process should run. Typical values would be one to three hours. Longer durations should be used only with long intervals between each sample or as a series of shorter jobs run by scheduled tasks.  <br/> |
| _Frequency_ <br/> |Specifies the frequency at which data metrics are collected. Typical values would be 30 seconds, one minute, or five minutes. Under normal circumstances, intervals that are shorter than these won't show significant changes between each sample.  <br/> |
| _Servers_ <br/> |Specifies the identity of the servers from which to collect statistics. You can specify any value, including wildcard characters or GUIDs.  <br/> |
| _SummariseFiles_ <br/> |Specifies a list of .csv files to generate a summary report. These files are the files named **CounterData.\<CounterData\>\*** and are generated by the CollectReplicationMetrics.ps1 script.  <br/> |
| _Mode_ <br/> | Specifies the processing stages that the script executes. You can use the following values:  <br/>  `CollectAndReport` This is the default value. This value signifies that the script should both collect the data from the servers and then process them to produce the summary report.  <br/>  `CollectOnly` This value signifies that the script should just collect the data and not produce the report.  <br/>  `ProcessOnly` This value signifies that the script should import data from a set of .csv files and process them to produce the summary report. The  _SummariseFiles_ parameter is used to provide the script with the list of files to process.  <br/> |
| _MoveFilestoArchive_ <br/> |Specifies that the script should move the files to a compressed folder after processing.  <br/> |
| _LoadExchangeSnapin_ <br/> |Specifies that the script should load the Exchange Management Shell commands. This parameter is useful when the script needs to run from outside the Exchange Management Shell, such as in a scheduled task.  <br/> |
   
### CollectReplicationMetrics.ps1 example

The following example gathers one hour's worth of data from all the servers in the DAG DAG1, sampled at one minute intervals, and then generates a summary report. In addition, the  _ReportPath_ parameter is used, which causes the script to place all the files in the current directory. 
  
```
CollectReplicationMetrics.ps1 -DagName DAG1 -Duration "01:00:00" -Frequency "00:01:00" -ReportPath
```

The following example reads the data from all the files matching CounterData\* and then generates a summary report.
  
```
CollectReplicationMetrics.ps1 -SummariseFiles (dir CounterData*) -Mode ProcessOnly -ReportPath
```


