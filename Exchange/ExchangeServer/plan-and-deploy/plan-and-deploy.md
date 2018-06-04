---
title: "Planning and deployment"
ms.author: dstrome
author: dstrome
manager: serdars
ms.date: 5/23/2018
ms.audience: ITPro
ms.topic: hub-page
ms.prod: office-online-server
localization_priority: Normal
ms.collection: Strat_EX_Admin
ms.assetid: 692c59e3-f0b0-4cef-a66e-751aa740abae
description: "Guidance for planning and deploying Exchange 2016."
---

# Planning and deployment

Guidance for planning and deploying Exchange 2016.
  
The following sections contain links to information about planning for and then deploying Microsoft Exchange Server 2016.
  
> [!IMPORTANT]
> Make sure you read the [Release notes for Exchange 2016](../release-notes.md) topic before you begin your deployment. The release notes contain important information on issues you might encounter during and after your deployment. 
  
## Planning for Exchange 2016
<a name="Planning"> </a>

 Use the following links to access information to help you plan the deployment of Exchange Server 2016 into your organization. 
  
> [!IMPORTANT]
> See [Establish a Test Environment](#test.md) later in this topic about installing Exchange 2016 in a test environment. 
  
[Exchange 2016 architecture](../architecture/architecture.md)
  
> Learn about the Mailbox and Edge Transport server roles, architecture improvements, and more, in Exchange 2016.
    
[Exchange 2016 system requirements](system-requirements.md)
  
> Understand the system requirements that need to be satisfied in your organization before you can install Exchange 2016.
    
[Exchange 2016 prerequisites](prerequisites.md)
  
> Learn which Windows Server 2012 R2 or Windows Server 2012 features and the other software that needs to be installed to perform a successful installation of Exchange 2016.
    
[Exchange Server Deployment Assistant](http://go.microsoft.com/fwlink/p/?LinkId=626978)
  
> Use this tool to generate a customized checklist for planning, installing, or upgrading to Exchange 2016. Guidance is available for multiple scenarios, including an on-premises, hybrid, or cloud deployment.
    
[Active Directory](active-directory/active-directory.md)
  
> Read this topic to learn about how Exchange 2016 uses Active Directory and how your Active Directory deployment affects your Exchange deployment.
    
[Antispam and antimalware protection in Exchange 2016](../antispam-and-antimalware/antispam-and-antimalware.md)
  
> Read this topic to understand anti-malware protection options for Exchange 2016.
    
[Exchange Server Hybrid Deployments](http://technet.microsoft.com/library/59e32000-4fcf-417f-a491-f1d8f9aeef9b.aspx)
  
> Read this topic to help you with planning a hybrid deployment with Microsoft Office 365 and your on-premises Exchange 2016 organization.
    
[Exchange 2016 virtualization](virtualization.md)
  
> Read this topic to learn more about how you can deploy Exchange 2016 in a virtualized environment.
    
[Exchange Development Technologies](http://go.microsoft.com/fwlink/p/?LinkId=268448)
  
> This topic contains important information about Application Programming Interfaces (APIs) that are available for applications that use Exchange 2016.
    
### Establish a test environment
<a name="Test"> </a>

Before installing Exchange 2016 for the first time, we recommend that you install it in an isolated test environment. This approach reduces the risk of end-user downtime and negative ramifications to the production environment. 
  
The test environment will act as your "proof of concept" for your new Exchange 2016 design and make it possible to move forward or roll back any implementations before deploying into your production environments. Having an exclusive test environment for validation and testing allows you to do pre-installation checks for your future production environments. By installing in a test environment first, we believe that your organization will have a better likelihood of success in a full production implementation. 
  
For many organizations, the costs of building a test lab may be high because of the need to duplicate the production environment. To reduce the hardware costs associated with a prototype lab, we recommend the use of virtualization by using Windows Server 2012 R2 or Windows Server 2012 Hyper-V technologies. Hyper-V enables server virtualization, allowing multiple virtual operating systems to run on a single physical machine.
  
For more detailed information about Hyper-V, see [Server Virtualization](https://go.microsoft.com/fwlink/p/?LinkId=117704). For information about Microsoft support of Exchange 2016 in production on hardware virtualization software, see "Hardware virtualization" in [Exchange 2016 system requirements](system-requirements.md).
  
## Deploying Exchange 2016
<a name="Deployment"> </a>

The deployment phase is the period during which you install Exchange 2016 into your organization. Before you begin the deployment phase, you should plan your Exchange organization. For more information, see the [Planning for Exchange 2016](#Planning.md) section earlier in this topic. 
  
Use the following links to access the information you need to help you with deploying Exchange 2016.
  
[Prepare Active Directory and domains](prepare-ad-and-domains.md)
  
> Learn about the steps you need to take to prepare your Active Directory forest for Exchange 2016 and the changes Exchange makes to your forest.
    
[Install the Exchange 2016 Mailbox role using the Setup wizard](deploy-new-installations/install-mailbox-role.md)
  
> Follow the steps in this topic to use the Exchange 2016 Setup wizard to install Exchange 2016 into a new Exchange organization.
    
[Install Exchange 2016 using unattended mode](deploy-new-installations/unattended-installs.md)
  
> Follow the steps in this topic to use Exchange 2016 unattended setup to install Exchange 2016 into a new Exchange organization.
    
[Install the Exchange 2016 Edge Transport role using the Setup wizard](deploy-new-installations/install-edge-transport-role.md)
  
> Follow the steps in this topic to use the Exchange 2016 Setup wizard to install the Exchange 2016 Edge Transport role into a perimeter network.
    
[Upgrade Exchange 2016 to the latest cumulative update](install-cumulative-updates.md)
  
> Follow the steps in this topic to apply the latest cumulative update or service pack to Exchange 2016 servers in your organization.
    
[Exchange Server Hybrid Deployments](http://technet.microsoft.com/library/cbbe558d-1ae2-49ed-bd97-2013349fef35.aspx)
  
> Read this topic for information that will help you deploy Exchange in an existing hybrid deployment.
    
[Exchange 2016 post-installation tasks](post-installation-tasks/post-installation-tasks.md)
  
> Learn about post-installation tasks to complete your Exchange 2016 installation.
    
## Understanding Exchange 2016 Setup
<a name="Understand"> </a>

You can use different types and modes of Exchange 2016 Setup to install and maintain the various editions and versions of Exchange 2016.
  
### Exchange editions and versions

Exchange 2016 is available in two server editions: Standard Edition and Enterprise Edition. These are licensing editions that are defined by a product key. For more information, see [Exchange Server Licensing](https://go.microsoft.com/fwlink/p/?linkid=237292).
  
### Types of Exchange Setup

You have the following options for Exchange 2016 Setup:
  
- **Exchange Setup UI** Running Setup.exe without any command-line switches provides an interactive experience where you are guided by the Exchange 2016 Setup wizard. 
    
- **Exchange Unattended Setup** Running Setup.exe with command-line switches enables you to install Exchange from an interactive command line or through a script. 
    
### Modes of Exchange Setup
<a name="Modes"> </a>

Setup for Exchange 2016 includes several installation modes:
  
- **Install** Use this mode when you're installing a new server role or adding a server role to an existing installation (maintenance mode). You can use this mode from both the Exchange Setup wizard and the unattended install. 
    
- **Uninstall** Use this mode when you're removing the Exchange installation from a computer. You can use this mode from both the Exchange Setup wizard and the unattended install. 
    
- **Upgrade** Select this mode used when you have an existing installation of Exchange and you're installing a cumulative update or service pack. You can use this mode from both the Exchange Setup wizard and the unattended install. 
    
    > [!NOTE]
    > Exchange 2016 doesn't support in-place upgrades from previous versions of Exchange. This mode is used only to install cumulative updates or service packs. 
  
- **RecoverServer** Use this mode when there has been a catastrophic failure of a server, and you need to recover data. You must install a server using the same fully qualified domain name (FQDN) as the failed server, and then run Setup with the **/m:RecoverServer** switch. Don't specify the roles to restore. Setup detects the Exchange Server object in Active Directory and installs the corresponding files and configuration automatically. After you recover the server, you can restore databases and reconfigure any additional settings. To run in **RecoverServer** mode, you can't have Exchange installed on the server. The Exchange server object must exist in Active Directory. You can only use this mode during an unattended installation. 
    
> [!NOTE]
> You must complete one mode of Setup before you can use another mode. 
  

