---
title: "Exchange 2016 system requirements"
ms.author: dstrome
author: dstrome
manager: serdars
ms.date: 6/8/2018
ms.audience: ITPro
ms.topic: conceptual
ms.prod: exchange-server-itpro
localization_priority: Critical
ms.collection: Strat_EX_Admin
ms.assetid: 1e80857c-b870-4a6d-a0f4-ff7b3a7be037
description: "Summary: Learn about what you need to have in your environment before installing Exchange 2016."
---

# Exchange 2016 system requirements

 **Summary**: Learn about what you need to have in your environment before installing Exchange 2016.

> [!TIP]
> Coming from the Exchange Deployment Assistant? Click [Exchange 2013 system requirements](https://technet.microsoft.com/library/aa996719%28v=exchg.150%29.aspx). 

Before you install Exchange 2016, we recommend that you review this topic to ensure that your network, hardware, software, clients, and other elements meet the requirements for Exchange 2016. In addition, make sure you understand the coexistence scenarios that are supported for Exchange 2016 and earlier versions of Exchange.

## Supported coexistence scenarios

The following table lists the scenarios in which coexistence between Exchange 2016 and earlier versions of Exchange is supported.

**Coexistence of Exchange 2016 with earlier versions of Exchange Server**

|**Exchange version**|**Exchange organization coexistence**|
|:-----|:-----|
|Exchange 2007 and earlier versions  <br/> |Not supported  <br/> |
|Exchange 2010  <br/> |Supported with Update Rollup 11 for Exchange 2010 SP3 or later on all Exchange 2010 servers in the organization, including Edge Transport servers.  <br/> |
|Exchange 2013  <br/> |Supported with Exchange 2013 Cumulative Update 10 or later on all Exchange 2013 servers in the organization, including Edge Transport servers.  <br/> |
|Mixed Exchange 2010 and Exchange 2013 organization  <br/> |Supported with the following minimum versions of Exchange:  <br/> Update Rollup 11 Exchange 2010 SP3 or later on all Exchange 2010 servers in the organization, including Edge Transport servers.  <br/> Exchange 2013 Cumulative Update 10 or later on all Exchange 2013 servers in the organization, including Edge Transport servers.  <br/> |
 
## Supported hybrid deployment scenarios

Exchange 2016 supports hybrid deployments with Office 365 tenants that have been upgraded to the latest version of Office 365. For more information about specific hybrid deployments, see [Hybrid Deployment Prerequisites](http://technet.microsoft.com/library/e7454db0-fed4-4662-8890-9501126b1ba2.aspx).

## Network and directory servers

The following table lists the requirements for the network and the directory servers in your Exchange 2016 organization.

 **Network and directory server requirements for Exchange 2016**

|**Component**|**Requirement**|
|:-----|:-----|
|Domain controllers  <br/> |All domain controllers in the forest need to be running one of the following:  <br/> Windows Server 2016 Standard or Datacenter  <br/> Windows Server 2012 R2 Standard or Datacenter  <br/> Windows Server 2012 Standard or Datacenter  <br/> Windows Server 2008 R2 Standard or Enterprise  <br/> Windows Server 2008 R2 Datacenter RTM or later  <br/> |
|Active Directory forest  <br/> |The Active Directory forest functionality level needs to be at Windows Server 2008 R2 or higher.  <br/> |
|DNS namespace support  <br/> |Exchange 2016 supports the following domain name system (DNS) namespaces:  <br/> • Contiguous  <br/> • Noncontiguous  <br/> • Single label domains  <br/> • Disjoint  <br/> For more information about DNS namespaces supported by Exchange, see Microsoft Knowledge Base article 2269838, [Microsoft Exchange compatibility with Single Label Domains, Disjoined Namespaces, and Discontiguous Namespaces](https://go.microsoft.com/fwlink/p/?linkid=3052&kbid=2269838).  <br/> |
|IPv6 support  <br/> |In Exchange 2016, IPv6 is supported only when IPv4 is also installed and enabled. If Exchange 2016 is deployed in this configuration, and the network supports IPv4 and IPv6, all Exchange servers can send data to and receive data from devices, servers, and clients that use IPv6 addresses. For more information, see [IPv6 Support in Exchange 2013](http://technet.microsoft.com/library/33543023-eb9a-4102-b990-84a818a52814.aspx).  <br/> |
 
## Directory server architecture

The use of 64-bit Active Directory domain controllers increases directory service performance for Exchange 2016.

> [!NOTE]
> In multi-domain environments, on Windows Server 2008 domain controllers that have the Active Directory language locale set to Japanese (ja-jp), your servers may not receive some attributes that are stored on an object during inbound replication. For more information, see Microsoft Knowledge Base article 949189, [A Windows Server 2008 domain controller that is configured with the Japanese language locale may not apply updates to attributes on an object during inbound replication](https://go.microsoft.com/fwlink/p/?linkid=3052&kbid=949189). 

### Installing Exchange 2016 on directory servers

For security and performance reasons, we recommend that you install Exchange 2016 only on member servers and not on Active Directory directory servers. To learn about the issues you can face when installing Exchange 2016 on a directory server, see [Installing Exchange on a domain controller is not recommended [WarningInstallExchangeRolesOnDomainController]](deployment-ref/ms-exch-setupreadiness-warninginstallexchangerolesondomaincontroller.md)After Exchange 2016 is installed, changing its role from a member server to a directory server, or vice versa, isn't supported.

## Hardware

For information about deploying Exchange in a virtualized environment, see [Exchange 2016 virtualization](virtualization.md).

 **Hardware requirements for Exchange 2016**

|**Component**|**Requirement**|**Notes**|
|:-----|:-----|:-----|
|Processor  <br/> |x64 architecture-based computer with Intel processor that supports Intel 64 architecture (formerly known as Intel EM64T).  <br/> AMD processor that supports the AMD64 platform.  <br/> **Note**: Intel Itanium IA64 processors not supported.  <br/> |For more information, see [Sizing Exchange 2016 Deployments](https://blogs.technet.microsoft.com/exchange/2015/10/15/ask-the-perf-guy-sizing-exchange-2016-deployments/).  <br/> See the "Operating system" section later in this topic for supported operating systems.  <br/> |
|Memory  <br/> |Varies depending on Exchange roles that are installed:  <br/> **Mailbox**: 8GB minimum  <br/> **Edge Transport**: 4GB minimum  <br/> |For more information, see [Sizing Exchange 2016 Deployments](https://blogs.technet.microsoft.com/exchange/2015/10/15/ask-the-perf-guy-sizing-exchange-2016-deployments/).  <br/> |
|Paging file size  <br/> |The page file size minimum and maximum must be set to physical RAM plus 10MB, to a maximum size of 32,778MB (32GB) if you're using more than 32GB of RAM.  <br/> |None  <br/> |
|Disk space  <br/> |At least 30 GB on the drive on which you install Exchange.  <br/> An additional 500 MB of available disk space for each Unified Messaging (UM) language pack that you plan to install.  <br/> 200 MB of available disk space on the system drive.  <br/> A hard disk that stores the message queue database on with at least 500 MB of free space.  <br/> |For more information, see [Sizing Exchange 2016 Deployments](https://blogs.technet.microsoft.com/exchange/2015/10/15/ask-the-perf-guy-sizing-exchange-2016-deployments/).  <br/> |
|Drive  <br/> |DVD-ROM drive, local or network accessible.  <br/> |None  <br/> |
|Screen resolution  <br/> |1024 x 768 pixels or higher  <br/> |None  <br/> |
|File format  <br/> |Disk partitions formatted as NTFS file systems, which applies to the following partitions:  <br/> • System partition  <br/> • Partitions that store Exchange binary files or files generated by Exchange diagnostic logging  <br/> • Database files, such as mailbox and transport databases  <br/> Disk partitions containing only the following types of files can optionally be formatted as ReFS:  <br/> • Partitions containing transaction log files  <br/> • Partitions containing mailbox database files  <br/> • Partitions containing content indexing files  <br/> |None  <br/> |
 
## Operating system

The following table lists the supported operating systems for Exchange 2016.

 **Important**: We don't support the installation of Exchange 2016 on a computer that's running Windows Server Core or Nano Server. The Windows Server Desktop Experience feature needs to be installed. To install Exchange 2016, you need to do one of the following to install the Desktop Experience on Windows Server prior to starting Exchange 2016 Setup:

- **Windows Server 2012 and Windows Server 2012 R2**: Run the following command in Windows PowerShell

  ```
  Install-WindowsFeature Server-Gui-Mgmt-Infra, Server-Gui-Shell -Restart
  ```

- **Windows Server 2016**: Install Windows Server 2016 and choose the **Desktop Experience** installation option. If a computer is running Windows Server 2016 Core mode and you want to install Exchange 2016 on it, you'll need to reinstall the operating system and choose the **Desktop Experience** installation option. 

 **Supported operating systems for Exchange 2016**

|**Component**|**Requirement**|
|:-----|:-----|
|Mailbox and Edge Transport server roles  <br/> |Windows Server 2016 Standard or Datacenter<sup>\*</sup> <br/> Windows Server 2012 R2 Standard or Datacenter  <br/> Windows Server 2012 Standard or Datacenter  <br/> |
|Management tools  <br/> |One of the following:  <br/> Windows Server 2016 Standard or Datacenter<sup>\*</sup> <br/> Windows Server 2012 R2 Standard or Datacenter  <br/> Windows Server 2012 Standard or Datacenter  <br/> 64-bit edition of Windows 10  <br/> 64-bit edition of Windows 8.1  <br/> |
 
<sup>\*</sup> Requires Exchange Server 2016 Cumulative Update 3 or later. 

 **Supported Windows Management Framework versions for Exchange 2016**

Exchange 2016 only supports the version of Windows Management Framework that's built in to the release of Windows that you're installing Exchange on. Don't install versions of Windows Management Framework that are made available as stand-alone downloads on servers running Exchange.

 **Installing other software on an Exchange 2016 server**

We don't support the installation of Office client or Office server software, such as SharePoint Server; Skype for Business Server; Office Online Server; or Project Server, on Exchange 2016 servers. Other software that you want to install on Exchange 2016 servers needs to be designed to run on the same computer as Exchange.

## .NET Framework

We strongly recommend that you use the latest version of .NET Framework that's supported by the release of Exchange you're installing.

> [!IMPORTANT]
> **Releases of .NET Framework that aren't listed in the table below are not supported on any release of Exchange 2016**. This includes minor and patch-level releases of .NET Framework. 

|**Exchange version**|**.NET Framework 4.7.1**|**.NET Framework 4.6.2**|**.NET Framework 4.6.1**|**.NET Framework 4.5.2**|
|:-----|:-----|:-----|:-----|:-----|
|Exchange 2016 CU8  <br/> |X  <br/> |X  <br/> |||
|Exchange 2016 CU5 - CU7  <br/> ||X  <br/> |||
|Exchange 2016 CU4  <br/> ||X  <br/> |X<sup>3</sup> <br/> |X<sup>3</sup> <br/> |
|Exchange 2016 CU3  <br/> ||X  <br/> |X  <br/> |X<br/> |
|Exchange 2016 CU2<br/> |||X<sup>1,2</sup> <br/> |X<br/> |
|Exchange 2016 RTM or CU1<br/> ||||X<br/> |
 
<sup>1</sup>.NET Framework 4.6.1 requires post-release fixes if you want to install it on a server running Exchange 2016 CU2. For more information. see [Exchange 2016 prerequisites](prerequisites.md).

<sup>2</sup> If you're upgrading to Exchange 2016 CU4 from Exchange 2016 RTM, CU1, or CU2, we strongly recommend that you install Exchange 2016 CU4 before .NET Framework 4.6.2 or .NET Framework 4.6.1 and its related post-release fixes. 

<sup>3</sup> Starting with Exchange 2016 CU5, .NET Framework 4.6.1 and 4.5.2 will no longer be supported with Exchange 2016. While those versions of .NET Framework are supported by Exchange 2016 CU4, we strongly recommend that you upgrade servers running Exchange 2016 to .NET Framework 4.6.2. 

## Supported clients

- Outlook 2016

- Outlook 2013

- Outlook 2010 SP2 and updates KB2956191 and KB2965295

- Outlook for Mac for Office 365

## Exchange 2016 third-party clients

Exchange Server offers several well-known protocols, and publishes APIs that third-party vendors often write clients for.

Microsoft makes no warranties, expressed or implied, as to the overall suitability, fitness, compatibility, or security of clients that are created by third-party developers.

If you want to use a third-party client that uses our protocols or APIs, we recommend that you thoroughly review and test all considerations (functionality, security, maintenance, management, and so on) before you deploy the client in the enterprise workspace. We also recommend that you make sure that the third-party vendor offers an appropriate Enterprise Support Agreement (ESA).
  

