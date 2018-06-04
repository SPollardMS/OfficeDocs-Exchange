---
title: "Exchange 2016 storage configuration options"
ms.author: dmaguire
author: msdmaguire
manager: serdars
ms.date: 4/25/2018
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 37cdeacf-74f9-4399-9860-4d1dbec12bb1
description: "Summary: Learn about storage options in Exchange Server 2016."
---

# Exchange 2016 storage configuration options

 **Summary**: Learn about storage options in Exchange Server 2016.
  
Understanding storage options and requirements for the Mailbox server role in Microsoft Exchange Server 2016 is an important part of your Mailbox server storage design solution.
  
## Storage architectures
<a name="Stor"> </a>

The following table describes supported storage architectures and provides best practice guidance for each type of storage architecture where appropriate.
  
**Supported storage architectures**

|**Storage architecture**|**Description**|**Best practice**|
|:-----|:-----|:-----|
|Direct-attached storage (DAS)  <br/> |DAS is a digital storage system directly attached to a server or workstation, without a storage network in between. For example, DAS transports include Serial Attached Small Computer System Interface (SCSI) and Serial Attached Advanced Technology Attachment (ATA).  <br/> |Not available.  <br/> |
|Storage area network (SAN): Internet Small Computer System Interface (iSCSI)  <br/> |SAN is an architecture to attach remote computer storage devices (such as disk arrays and tape libraries) to servers in such a way that the devices appear as locally attached to the operating system (for example, block storage). iSCSI SANs encapsulate SCSI commands within IP packets and use standard networking infrastructure as the storage transport (for example, Ethernet).  <br/> |Don't share physical disks backing up Exchange data with other applications.  <br/> Use dedicated storage networks.  <br/> Use multiple network paths for stand-alone configurations.  <br/> |
|SAN: Fibre Channel  <br/> |Fibre Channel SANs encapsulate SCSI commands within Fibre Channel packets and generally utilize specialized Fibre Channel networks as the storage transport.  <br/> |Don't share physical disks backing up Exchange data with other applications.  <br/> Use multiple Fibre Channel network paths for stand-alone configurations.  <br/> Follow storage vendor's best practices for tuning Fibre Channel host bus adapters (HBAs), for example, Queue Depth and Queue Target.  <br/> |
   
A network-attached storage (NAS) unit is a self-contained computer connected to a network, with the sole purpose of supplying file-based data storage services to other devices on the network. The operating system and other software on the NAS unit provide the functionality of data storage, file systems, and access to files, and the management of these functions (for example, file storage).
  
All storage used by Exchange for storage of Exchange data must be block-level storage because Exchange 2016 doesn't support the use of NAS volumes, other than in the SMB 3.0 scenario outlined in the topic [Exchange 2016 virtualization](../../plan-and-deploy/virtualization.md). Also, in a virtualized environment, NAS storage that's presented to the guest as block-level storage via the hypervisor isn't supported.
  
Using storage tiers is not recommended, as it could adversely affect system performance. For this reason, do not allow the storage controller to automatically move the most accessed files to "faster" storage.
  
[Storage architectures](storage-configuration.md#Stor)
  
## Physical disk types
<a name="Phys"> </a>

The following table provides a list of supported physical disk types and provides best practice guidance for each physical disk type where appropriate.
  
**Supported physical disk types**

|**Physical disk type**|**Description**|**Supported or best practice**|
|:-----|:-----|:-----|
|Serial ATA (SATA)  <br/> | SATA is a serial interface for ATA and integrated device electronics (IDE) disks. SATA disks are available in a variety of form factors, speeds, and capacities.  <br/>  In general, choose SATA disks for Exchange 2016 mailbox storage when you have the following design requirements:  <br/>  High capacity  <br/>  Moderate performance  <br/>  Moderate power utilization  <br/> | Supported: 512-byte sector disks for Windows Server 2008 and Windows Server 2008 R2. In addition, 512e disks are supported for Windows Server 2008 R2 with the following:  <br/>  The hotfix described in [Microsoft Knowledge Base article 982018](http://go.microsoft.com/fwlink/p/?linkid=3052&amp;kbid=982018). An update that improves the compatibility of Windows 7 and Windows Server 2008 R2 with Advanced Format Disks is available.  <br/>  Windows Server 2008 R2 with Service Pack 1 (SP1) and Exchange Server 2010 SP1.  <br/>  Exchange 2013 and later supports native 4-kilobyte (KB) sector disks and 512e disks. Support requires that all copies of a database reside on the same physical disk type. For example, it is not a supported configuration to host one copy of a given database on a 512-byte sector disk and another copy of that same database on a 512e disk or 4K disk.  <br/>  Best practice: Consider enterprise class SATA disks, which generally have better heat, vibration, and reliability characteristics.  <br/> |
|Serial Attached SCSI  <br/> | Serial Attached SCSI is a serial interface for SCSI disks. Serial Attached SCSI disks are available in a variety of form factors, speeds, and capacities.  <br/>  In general, choose Serial Attached SCSI disks for Exchange 2016 mailbox storage when you have the following design requirements:  <br/>  Moderate capacity  <br/>  High performance  <br/>  Moderate power utilization  <br/> | Supported: 512-byte sector disks for Windows Server 2008 and Windows Server 2008 R2. In addition, 512e disks are supported for Windows Server 2008 R2 with the following:  <br/>  The hotfix described in [Microsoft Knowledge Base article 982018](http://go.microsoft.com/fwlink/p/?linkid=3052&amp;kbid=982018). An update that improves the compatibility of Windows 7 and Windows Server 2008 R2 with Advanced Format Disks is available.  <br/>  Windows Server 2008 R2 with Service Pack 1 (SP1) and Exchange Server 2010 SP1.  <br/>  Exchange 2013 and later supports native 4-kilobyte (KB) sector disks and 512e disks. Support requires that all copies of a database reside on the same physical disk type. For example, it is not a supported configuration to host one copy of a given database on a 512-byte sector disk and another copy of that same database on a 512e disk or 4K disk.  <br/>  Best practice: Physical disk-write caching must be disabled when used without a UPS.  <br/> |
|Fibre Channel  <br/> | Fibre Channel is an electrical interface used to connect disks to Fibre Channel-based SANs. Fibre Channel disks are available in a variety of speeds and capacities.  <br/>  In general, choose Fibre Channel disks for Exchange 2016 mailbox storage when you have the following design requirements:  <br/>  Moderate capacity  <br/>  High performance  <br/>  SAN connectivity  <br/> | Supported: 512-byte sector disks for Windows Server 2008 and Windows Server 2008 R2. In addition, 512e disks are supported for Windows Server 2008 R2 with the following:  <br/>  The hotfix described in [Microsoft Knowledge Base article 982018](http://go.microsoft.com/fwlink/p/?linkid=3052&amp;kbid=982018). An update that improves the compatibility of Windows 7 and Windows Server 2008 R2 with Advanced Format Disks is available.  <br/>  Windows Server 2008 R2 with Service Pack 1 (SP1) and Exchange Server 2010 SP1.  <br/>  Exchange 2013 and later supports native 4-kilobyte (KB) sector disks and 512e disks. Support requires that all copies of a database reside on the same physical disk type. For example, it is not a supported configuration to host one copy of a given database on a 512-byte sector disk and another copy of that same database on a 512e disk or 4K disk.  <br/>  Best practice: Physical disk-write caching must be disabled when used without a UPS.  <br/> |
|Solid-state drive (SSD) (flash disk)  <br/> | An SSD is a data storage device that uses solid-state memory to store persistent data. An SSD emulates a hard disk drive interface. SSD disks are available in a variety of speeds (different I/O performance capabilities) and capacities.  <br/>  In general, choose SSD disks for Exchange 2016 mailbox storage when you have the following design requirements:  <br/>  Low capacity  <br/>  Extremely high performance  <br/> | Supported: 512-byte sector disks for Windows Server 2008 and Windows Server 2008 R2. In addition, 512e disks are supported for Windows Server 2008 R2 with the following:  <br/>  The hotfix described in [Microsoft Knowledge Base article 982018](http://go.microsoft.com/fwlink/p/?linkid=3052&amp;kbid=982018). An update that improves the compatibility of Windows 7 and Windows Server 2008 R2 with Advanced Format Disks is available.  <br/>  Windows Server 2008 R2 with Service Pack 1 (SP1) and Exchange Server 2010 SP1.  <br/>  Exchange 2013 and later supports native 4-kilobyte (KB) sector disks and 512e disks. Support requires that all copies of a database reside on the same physical disk type. For example, it is not a supported configuration to host one copy of a given database on a 512-byte sector disk and another copy of that same database on a 512e disk or 4K disk.  <br/>  Best practice: Physical disk-write caching must be disabled when used without a UPS.  <br/>  In general, Exchange 2016 Mailbox servers don't require the performance characteristics of SSD storage.  <br/> |
   
### Factors to consider when choosing disk types

There are several trade-offs when choosing disk types for Exchange 2016 storage. The correct disk is one that balances performance (both sequential and random) with capacity, reliability, power utilization, and capital cost. The following table of supported physical disk types provides information to help you when considering these factors.
  
From a performance perspective, using large, slower disks for Exchange storage is okay, provided the disks can maintain an average read and write latency of 20ms or less under load.
  
**Factors in disk type choice**

|**Disk speed (RPM)**|**Disk form factor**|**Interface or transport**|**Capacity**|**Random I/O performance**|**Sequential I/O performance**|**Power utilization**|
|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
|5,400  <br/> |2.5-inch  <br/> |SATA  <br/> |Average  <br/> |Poor  <br/> |Poor  <br/> |Excellent  <br/> |
|5,400  <br/> |3.5-inch  <br/> |SATA  <br/> |Excellent  <br/> |Poor  <br/> |Poor  <br/> |Above average  <br/> |
|7,200  <br/> |2.5-inch  <br/> |SATA  <br/> |Average  <br/> |Average  <br/> |Average  <br/> |Excellent  <br/> |
|7,200  <br/> |2.5-inch  <br/> |Serial Attached SCSI  <br/> |Average  <br/> |Average  <br/> |Above average  <br/> |Excellent  <br/> |
|7,200  <br/> |3.5-inch  <br/> |SATA  <br/> |Excellent  <br/> |Average  <br/> |Above average  <br/> |Above average  <br/> |
|7,200  <br/> |3.5-inch  <br/> |Serial Attached SCSI  <br/> |Excellent  <br/> |Average  <br/> |Above average  <br/> |Above average  <br/> |
|7,200  <br/> |3.5-inch  <br/> |Fibre Channel  <br/> |Excellent  <br/> |Average  <br/> |Above average  <br/> |Average  <br/> |
|10,000  <br/> |2.5-inch  <br/> |Serial Attached SCSI  <br/> |Below average  <br/> |Excellent  <br/> |Above average  <br/> |Above average  <br/> |
|10,000  <br/> |3.5-inch  <br/> |SATA  <br/> |Average  <br/> |Average  <br/> |Above average  <br/> |Above average  <br/> |
|10,000  <br/> |3.5-inch  <br/> |Serial Attached SCSI  <br/> |Average  <br/> |Above average  <br/> |Above average  <br/> |Below average  <br/> |
|10,000  <br/> |3.5-inch  <br/> |Fibre Channel  <br/> |Average  <br/> |Above average  <br/> |Above average  <br/> |Below average  <br/> |
|15,000  <br/> |2.5-inch  <br/> |Serial Attached SCSI  <br/> |Poor  <br/> |Excellent  <br/> |Excellent  <br/> |Average  <br/> |
|15,000  <br/> |3.5-inch  <br/> |Serial Attached SCSI  <br/> |Average  <br/> |Excellent  <br/> |Excellent  <br/> |Below average  <br/> |
|15,000  <br/> |3.5-inch  <br/> |Fibre Channel  <br/> |Average  <br/> |Excellent  <br/> |Excellent  <br/> |Poor  <br/> |
|SSD: enterprise class  <br/> |Not applicable  <br/> |SATA, Serial Attached SCSI, Fibre Channel  <br/> |Poor  <br/> |Excellent  <br/> |Excellent  <br/> |Excellent  <br/> |
   
[Storage architectures](storage-configuration.md#Stor)
  
## Best practices for supported storage configurations
<a name="Best"> </a>

This section provides best practice information about supported disk and array controller configurations. In addition to the commonly used Redundant Array of Indepentdent Disks (RAID), there is also just a bunch of disks (or drives), or JBOD, which refers to a collection of hard disks that have not been configured to act as a redundant array.
  
RAID is often used to both improve the performance characteristics of individual disks (by striping data across several disks) as well as to provide protection from individual disk failures. With the advancements in Exchange 2016 high availability, RAID is not a required component for Exchange 2016 storage design. However, RAID is still an essential component of Exchange 2016 storage design for standalone servers as well as solutions that require storage fault tolerance.
  
 **Operating System, System, or Pagefile Volume**
  
The recommended configuration for an operating system, system or pagefile volume is to utilize RAID technology to protect this data type. The recommended RAID configuration is either RAID-1 or RAID-1/0, however all RAID types are supported.
  
 **Separated Mailbox Database and Log Volumes**
  
If you are deploying a standalone Mailbox server role architecture, RAID technology is required for the mailbox database and log volumes. The recommended RAID configuration for mailbox volumes is RAID-1/0 (especially if you are using 5.4K or 7.2K disks); however all RAID types are supported. For log volumes, RAID-1 or RAID-1/0 is the recommended RAID configuration.
  
When using RAID-5 or RAID-6 configurations for the operating system, pagefile, or Exchange data volumes, note the following:
  
- RAID-5 configurations, including variations such as RAID-50 and RAID-51, should have no more than 7 disks per array group and array controller high-priority scrubbing and surface scanning enabled.
    
- RAID-6 configurations should have array controller high-priority scrubbing and surface scanning enabled.
    
Although JBOD is supported in high availability architectures that have 3 or more highly available database copies, because the log and mailbox database volumes are separated, JBOD is not recommended as a solution.
  
 **Mailbox Database and Log Volume Co-Location**
  
Mailbox database and log volume co-location is not recommended in standalone architectures. In high availability architectures, there are two possibilities for this scenario:
  
1. Single database per volume
    
2. Multiple databases per volume
    
 **Single Database Per Volume**
  
In an Exchange environment, a JBOD storage solution involves having both the database and its associated logs stored on a single disk. To deploy a JBOD solution, you must deploy a minimum of three highly available database copies. Utilizing a single disk is a single point of failure, because when the disk fails, the database copy residing on that disk is lost. Having a minimum of three database copies ensures fault tolerance by having two additional copies in the event that one copy (or one disk) fails. However, placement of three highly available database copies, as well as the use of lagged database copies, can affect storage design. The following table shows guidelines for RAID or JBOD considerations.
  
**RAID or JBOD Considerations**

|**Datacenter servers**|**Two highly available copies (total)**|**Three highly available copies (total)**|**Two or more highly available copies per datacenter**|**One lagged copy**|**Two or more lagged copies per datacenter**|
|:-----|:-----|:-----|:-----|:-----|:-----|
|Primary datacenter servers  <br/> |RAID  <br/> |RAID or JBOD (2 copies)  <br/> |RAID or JBOD  <br/> |RAID  <br/> |RAID or JBOD  <br/> |
|Secondary datacenter servers  <br/> |RAID  <br/> |RAID (1 copy)  <br/> |RAID or JBOD  <br/> |RAID  <br/> |RAID or JBOD  <br/> |
   
To deploy on JBOD with the primary datacenter servers, you need three or more highly available database copies within the DAG. If mixing lagged copies on the same server hosting highly available database copies (for example, not using dedicated lagged database copy servers), you need at least two lagged database copies.
  
For the secondary datacenter servers to use JBOD, you should have at least two highly available database copies in the secondary datacenter. The loss of a copy in the secondary datacenter won't result in requiring a reseed across the WAN or having a single point of failure in the event the secondary datacenter is activated. If mixing lagged database copies on the same server hosting highly available database copies (for example, not using dedicated lagged database copy servers), you need at least two lagged database copies.
  
For dedicated lagged database copy servers, you should have at least two lagged database copies within a datacenter to use JBOD. Otherwise, the loss of disk results in the loss of the lagged database copy, as well as the loss of the protection mechanism.
  
 **Multiple Databases Per Volume**
  
Multiple databases per volume is a new JBOD scenario available in Exchange 2016 that allows for active and passive copies (including lagged copies) to be mixed on a single disk, enabling better disk utilization. However, to deploy lagged copies in this manner, automatic lagged copy log file play down must be enabled. The following table shows guidelines for JBOD considerations for multiple databases per volume.
  
**JBOD Considerations**

|**Datacenter Servers**|**3 or more copies (total)**|**Two or more copies per datacenter**|
|:-----|:-----|:-----|
|Primary datacenter servers  <br/> |JBOD  <br/> |JBOD  <br/> |
|Secondary datacenter servers  <br/> |N/A  <br/> |JBOD  <br/> |
   
The following table provides guidance about storage array configurations for Exchange 2016.
  
**Supported RAID types for the Exchange 2016 Mailbox server role**

|**RAID type**|**Description**|**Supported or best practice**|
|:-----|:-----|:-----|
|Disk array RAID stripe size (KB)  <br/> |The stripe size is the per disk unit of data distribution within a RAID set. Stripe size is also referred to as block size.  <br/> |Best practice: 256 KB or greater. Follow storage vendor best practices.  <br/> |
|Storage array cache settings  <br/> |The cache settings are provided by a battery-backed caching array controller.  <br/> |Best practice: 100 percent write cache (battery or flash backed cache) for DAS storage controllers in either a RAID or JBOD configuration. 75 percent write cache, 25 percent read cache (battery or flash backed cache) for other types of storage solutions such as SAN. If your SAN vendor has different best practices for cache configuration on their platform, follow the guidance of your SAN vendor.  <br/> |
|Physical disk write caching  <br/> |The settings for the cache are on each individual disk.  <br/> |Supported: Physical disk write caching must be disabled when used without a UPS.  <br/> |
   
The following table provides guidance about database and log file choices.
  
**Database and log file choices for the Exchange 2016 Mailbox server role**

|**Database and log file options**|**Description**|**Stand-alone: supported or best practice**|**High availability: supported or best practice**|
|:-----|:-----|:-----|:-----|
|File placement: database per log isolation  <br/> |Database per log isolation refers to placing the database file and logs from the same mailbox database onto different volumes backed by different physical disks.  <br/> |Best practice: For recoverability, move database (.edb) file and logs from the same database to different volumes backed by different physical disks.  <br/> |Supported: Isolation of logs and databases isn't required.  <br/> |
|File placement: database files per volume  <br/> |Database files per volume refers to how you distribute database files within or across disk volumes.  <br/> |Best practice: Based on your backup methodology.  <br/> |Supported: When using JBOD, create a single volume with separate directories for database(s) and for log files.  <br/> |
|File placement: log streams per volume  <br/> |Log streams per volume refers to how you distribute database log files within or across disk volumes.  <br/> |Best practice: Based on your backup methodology.  <br/> |Supported: When using JBOD, create a single volume with separate directories for database(s) and for log files.  <br/> Best practice: When using JBOD, leverage multiple databases per volume.  <br/> |
|Database size  <br/> |Database size refers to the disk database (.edb) file size.  <br/> | Supported: Approximately 16 terabytes.  <br/>  Best practice:  <br/>  200 gigabytes (GB) or less.  <br/>  Provision for 120 percent of calculated maximum database size.  <br/> | Supported: Approximately 16 terabytes.  <br/>  Best practice:  <br/>  2 terabytes or less.  <br/>  Provision for 120 percent of calculated maximum database size.  <br/> |
|Log truncation method  <br/> | Log truncation method is the process for truncating and deleting old database log files. There are two mechanisms:  <br/>  Circular logging, in which Exchange deletes the logs.  <br/>  Log truncation, which occurs after a successful full or incremental Volume Shadow Copy Service (VSS) backup.  <br/> | Best practice:  <br/>  Use backups for log truncation (for example, circular logging disabled).  <br/>  Provision for three days of log generation capacity.  <br/> | Best practice:  <br/>  Enable circular logging for deployments that use Exchange native data protection features.  <br/>  Provision for three days beyond replay lag setting of log generation capacity.  <br/> |
   
The following table provides guidance about Windows disk types.
  
**Windows disk types for the Exchange 2016 Mailbox server role**

|**Windows disk type**|**Description**|**Stand-alone: supported or best practice**|**High availability: supported or best practice**|
|:-----|:-----|:-----|:-----|
|Basic disk  <br/> |A disk initialized for basic storage is called a basic disk. A basic disk contains basic volumes, such as primary partitions, extended partitions, and logical drives.  <br/> |Supported.  <br/> Best practice: Use basic disks.  <br/> |Supported.  <br/> Best practice: Use basic disks.  <br/> |
|Dynamic disk  <br/> |A disk initialized for dynamic storage is called a dynamic disk. A dynamic disk contains dynamic volumes, such as simple volumes, spanned volumes, striped volumes, mirrored volumes, and RAID-5 volumes.  <br/> |Supported.  <br/> |Supported.  <br/> |
   
The following table provides guidance on volume configurations.
  
**Volume configurations for the Exchange 2016 Mailbox server role**

|**Volume configuration**|**Description**|**Stand-alone: supported or best practice**|**High availability: supported or best practice**|
|:-----|:-----|:-----|:-----|
|GUID partition table (GPT)  <br/> |GPT is a disk architecture that expands on the older master boot record (MBR) partitioning scheme. The maximum NTFS formatted partition size is 256 terabytes.  <br/> |Supported.  <br/> Best practice: Use GPT partitions.  <br/> |Supported.  <br/> Best practice: Use GPT partitions.  <br/> |
|MBR  <br/> |An MBR, or partition sector, is the 512-byte boot sector that is the first sector (LBA Sector 0) of a partitioned data storage device such as a hard disk. The maximum NTFS formatted partition size is 2 terabytes.  <br/> |Supported.  <br/> |Supported.  <br/> |
|Partition alignment  <br/> |Partition alignment refers to aligning partitions on sector boundaries for optimal performance.  <br/> |Supported: The Windows Server 2008 R2 and Windows Server 2012 default is 1 megabyte (MB).  <br/> |Supported: The Windows Server 2008 R2 and Windows Server 2012 default is 1 MB.  <br/> |
|Volume path  <br/> |Volume path refers to how a volume is accessed.  <br/> |Supported: Drive letter or mount point.  <br/> Best practice: Mount point host volume must be RAID enabled.  <br/> |Supported: Drive letter or mount point.  <br/> Best practice: Mount point host volume must be RAID-enabled.  <br/> |
|File system  <br/> |File system is a method for storing and organizing computer files and the data they contain to make it easy to find and access the files.  <br/> |Supported: NTFS and ReFS.  <br/> |Supported: NTFS and ReFS.  <br/> |
|NTFS defragmentation  <br/> |NTFS defragmentation is a process that reduces the amount of fragmentation in Windows file systems. It does this by physically organizing the contents of the disk to store the pieces of each file close together and contiguously.  <br/> |Supported.  <br/> Best practice: Not required and not recommended. On Windows Server 2012, we also recommend disabling the automatic disk optimization and defragmentation feature.  <br/> |Supported.  <br/> Best practice: Not required and not recommended. On Windows Server 2012, we also recommend disabling the automatic disk optimization and defragmentation feature.  <br/> |
|NTFS allocation unit size  <br/> |NTFS allocation unit size represents the smallest amount of disk space that can be allocated to hold a file.  <br/> |Supported: All allocation unit sizes.  <br/> Best practice: 64 KB for both .edb and log file volumes.  <br/> |Supported: All allocation unit sizes.  <br/> Best practice: 64 KB for both .edb and log file volumes.  <br/> |
|NTFS compression  <br/> |NTFS compression is the process of reducing the actual size of a file stored on the hard disk.  <br/> |Supported: Not supported for Exchange database or log files.  <br/> |Supported: Not supported for Exchange database or log files.  <br/> |
|NTFS Encrypting File System (EFS)  <br/> |EFS enables users to encrypt individual files, folders, or entire data drives. Because EFS provides strong encryption through industry-standard algorithms and public key cryptography, encrypted files are confidential even if an attacker bypasses system security.  <br/> |Supported: Not supported for Exchange database or log files.  <br/> |Not supported for Exchange database or log files.  <br/> |
|Windows BitLocker (volume encryption)  <br/> |Windows BitLocker is a data protection feature in Windows Server 2008. BitLocker protects against data theft or exposure on computers that are lost or stolen, and it offers more secure data deletion when computers are decommissioned.  <br/> |Supported: All Exchange database and log files.  <br/> |Supported: All Exchange database and log files. Windows failover clusters require Windows Server 2008 R2 or Windows Server 2008 R2 SP1 and the following hotfix: [You cannot enable BitLocker on a disk volume in Windows Server 2008 R2 if the computer is a failover cluster node](http://go.microsoft.com/fwlink/p/?linkid=3052&amp;kbid=2446607). Exchange volumes with Bitlocker enabled are not supported on Windows failover clusters running earlier versions of Windows.  <br/> For more information about Windows 7 BitLocker encryption, see [BitLocker Drive Encryption in Windows 7: Frequently Asked Questions](https://go.microsoft.com/fwlink/p/?linkId=220898).  <br/> |
|Server Message Block (SMB) 3.0  <br/> | The Server Message Block (SMB) protocol is a network file sharing protocol (on top of TCP/IP or other network protocols) that allows applications on a computer to access files and resources on a remote server. It also allows applications to communicate with any server program that is set up to receive an SMB client request. Windows Server 2012 introduces the new 3.0 version of the SMB protocol with the following features:  <br/>  SMB Transparent failover  <br/>  SMB Scaleout  <br/>  SMB Multichannel  <br/>  SMB Direct  <br/>  SMB Encryption  <br/>  VSS for SMB file shares  <br/>  SMB Directory Leasing  <br/>  SMB PowerShell  <br/> |Limited Support. Supported scenario is a hardware virtualized deployment where the disks are hosted on VHDs on an SMB 3.0 share. These VHDs are presented to the host via a hypervisor. For more information, see [Exchange 2016 virtualization](../../plan-and-deploy/virtualization.md).  <br/> |Limited Support. Supported scenario is a hardware virtualized deployment where the disks are hosted on VHDs on an SMB 3.0 share. These VHDs are presented to the host via a hypervisor. For more information, see [Exchange 2016 virtualization](../../plan-and-deploy/virtualization.md).  <br/> |
|Storage Spaces  <br/> |Storage Spaces is a new storage solution that delivers virtualization capabilities for Windows Server 2012. Storage Spaces allow you to organize physical disks into storage pools, which can be easily expanded by simply adding disks. These disks can be connected either through USB, SATA or SAS. It also utilizes virtual disks (spaces), which behave just like physical disks, with associated powerful capabilities such as thin provisioning, as well as resiliency to failures of underlying physical media. For more information on Storage Spaces, see [Storage Spaces Overview](https://technet.microsoft.com/en-us/library/hh831739.aspx).  <br/> |Supported. Same restrictions as for physical disk types outlined in this topic.  <br/> |Supported. Same restrictions as for physical disk types outlined in this topic.  <br/> |
|Resilient File System (ReFS)  <br/> |ReFS is a newly engineered file system forWindows Server 2012 that is built on the foundations of NTFS. ReFS maintains high degree of compatibility with NTFS while providing enhanced data verification and auto-correction techniques as well as an integrated end-to-end resiliency to corruptions especially when used in conjunction with the storage spaces feature. For more information on ReFS, see [Resilient File System (ReFS) overview: Supported Deployments](https://docs.microsoft.com/windows-server/storage/refs/refs-overview#supported-deployments).  <br/> |Supported for volumes containing Exchange database files, log files and content indexing files, provided that the following hotfix is installed: [Exchange Server 2013 databases become fragmented in Windows Server 2012](https://support.microsoft.com/kb/2853418). Not supported for volumes containing Exchange binaries.  <br/> Best practice: Data integrity features must be disabled for the Exchange database (.edb) files or the volume that hosts these files. Integrity features can be enabled for volumes containing the content index catalog, provided that the volume does not contain any databases or log files.  <br/> |Supported for volumes containing Exchange database files, log files and content indexing files, provided that the following hotfix is installed: [Exchange Server 2013 databases become fragmented in Windows Server 2012](https://support.microsoft.com/kb/2853418). Not supported for volumes containing Exchange binaries.  <br/> Best practice: Data integrity features must be disabled for the Exchange database (.edb) files or the volume that hosts these files. Integrity features can be enabled for volumes containing the content index catalog, provided that the volume does not contain any databases or log files.  <br/> |
|Data De-Duplication  <br/> |Data deduplication is a new technique to optimize storage utilization for Windows Server 2012. It is a method of finding and removing duplication within data without compromising its fidelity or integrity. The goal is to store more data in less space by segmenting files into small variable-sized chunks, identifying duplicate chunks, and maintaining a single copy of each chunk. Redundant copies of the chunk are replaced by a reference to the single copy, the chunks are organized into container files, and the containers are compressed for further space optimization.  <br/> |Not Supported for Exchange database files. Note: Can be used for Exchange database files that are completely offline (used as backups or archives).  <br/> |Not Supported for Exchange database files. Note: Can be used for Exchange database files that are completely offline (used as backups or archives).  <br/> |
   
[Storage architectures](storage-configuration.md#Stor)
  

