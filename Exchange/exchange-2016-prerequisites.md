---
title: Exchange 2016 prerequisites
ms.prod: EXCHANGE
ms.assetid: e21cf744-7813-48b3-9293-5cecd89a6c25
---


# Exchange 2016 prerequisites
 **Summary**: Windows operating system prerequisites for Exchange 2016 and Exchange management tools.
> [!TIP]
> Coming from the Exchange Deployment Assistant? Click  [Exchange 2013 prerequisites](https://technet.microsoft.com/en-us/library/bb691354%28v=exchg.150%29.aspx). 
  
    
    

This topic provides the steps for installing the necessary Windows Server 2012, Windows Server 2012 R2, and Windows Server 2016 operating system prerequisites for the Exchange 2016 Mailbox and Edge Transport server roles. It also provides the prerequisites required to install the Exchange 2016 management tools on Windows 8.1 and Windows 10 client computers.
-  [What do you need to know before you begin?](#prereq)
    
  
-  [Active Directory preparation](#ADPrep)
    
  
-  [Windows Server 2012 and Windows Server 2012 R2 prerequisites](#WS2012)
    
  -  [Mailbox server role](exchange-2016-prerequisites.md#WS2012MBX)
    
  
  -  [Edge Transport server role](#WS2012Edge)
    
  
-  [Windows Server 2016 prerequisites](#WS2016)
    
  -  [Mailbox server role](exchange-2016-prerequisites.md#WS2016MBX)
    
  
  -  [Edge Transport server role](#WS2016Edge)
    
  
-  [ Windows 8.1 and Windows 10 prerequisites (admin tools only)](exchange-2016-prerequisites.md#Windows8) (admin tools only)
    
  

## What do you need to know before you begin?
<a name="prereq"> </a>


> [!TIP]
> Have you heard about the Exchange Server Deployment Assistant? It's a free online tool that helps you quickly deploy Exchange 2016 in your organization by asking you a few questions and creating a customized deployment checklist just for you. If you want to learn more about it, go to **Exchange Server Deployment Assistant**. 
  
    
    


- Make sure that the functional level of your forest is at least Windows Server 2008, and that the schema master is running Windows Server 2008 or later. For more information about the Windows functional level, see  [Understanding Active Directory Domain Services (AD DS) Functional Levels](https://go.microsoft.com/fwlink/p/?linkId=137037).
    
  
- The full installation option of Windows Server 2012 and Windows Server 2012 R2 must be used for all servers running Exchange 2016 server roles or management tools.
    
  
- You must first join the computer to the appropriate internal Active Directory forest and domain.
    
  
- Some prerequisites require you to reboot the server to complete installation.
    
  
- Install the latest Windows updates on your computer. For more information, see  [Deployment Security Checklist](http://technet.microsoft.com/library/0cbfad59-f503-48a0-8184-6ca999d89e61.aspx).
    
    > [!NOTE]
      > You can't upgrade Windows from one version to another, or from Standard to Datacenter, when Exchange is installed on the server. 

> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at:  [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612),  [Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or  [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351). 
  
    
    

The following sections describe how to prepare your environment for Exchange 2016. Once your environment is prepared, use the Exchange Deployment Assistant for next steps on your actual deployment. For information on hybrid deployments, see  [Exchange Server Hybrid Deployments](https://technet.microsoft.com/en-us/library/jj200581%28v=exchg.150%29.aspx).
  
    
    

## Active Directory preparation
<a name="ADPrep"> </a>

The computer you want to use to prepare Active Directory for Exchange 2016 has specific prerequisites that must be met.
  
    
    
First, install  [.NET Framework 4.6.2 ](https://go.microsoft.com/fwlink/p/?linkid=808659) on the computer that will be used to prepare Active Directory.
  
    
    
After you've installed the software listed above, complete the following steps to install the Remote Tools Administration Pack. After you've installed the Remote Tools Administration Pack you'll be able to use the computer to prepare Active Directory. For more information about preparing Active Directory, see  [Prepare Active Directory and domains](prepare-active-directory-and-domains.md).
  
    
    

1. Open Windows PowerShell.
    
  
2. Install the Remote Tools Administration Pack using the following command.
    
  ```
  
Install-WindowsFeature RSAT-ADDS
  ```


## Windows Server 2012 and Windows Server 2012 R2 prerequisites
<a name="WS2012"> </a>

The prerequisites that are needed to install Exchange 2016 on computers running Windows Server 2012 or Windows Server 2012 R2 depends on which Exchange role you want to install. Read the section below that matches the role you want to install.
  
    
    

### Mailbox server role
<a name="WS2012MBX"> </a>

Follow the instructions in this section to install the prerequisites on computers running Windows Server 2012 or Windows Server 2012 R2 where you want to install the Mailbox server role.
  
    
    
Do the following to install the required Windows roles and features:
  
    
    

1. Open Windows PowerShell.
    
  
2. Run the following command to install the required Windows components.
    
  ```
  Install-WindowsFeature AS-HTTP-Activation, Server-Media-Foundation, NET-Framework-45-Features, RPC-over-HTTP-proxy, RSAT-Clustering, RSAT-Clustering-CmdInterface, RSAT-Clustering-Mgmt, RSAT-Clustering-PowerShell, Web-Mgmt-Console, WAS-Process-Model, Web-Asp-Net45, Web-Basic-Auth, Web-Client-Auth, Web-Digest-Auth, Web-Dir-Browsing, Web-Dyn-Compression, Web-Http-Errors, Web-Http-Logging, Web-Http-Redirect, Web-Http-Tracing, Web-ISAPI-Ext, Web-ISAPI-Filter, Web-Lgcy-Mgmt-Console, Web-Metabase, Web-Mgmt-Console, Web-Mgmt-Service, Web-Net-Ext45, Web-Request-Monitor, Web-Server, Web-Stat-Compression, Web-Static-Content, Web-Windows-Auth, Web-WMI, Windows-Identity-Foundation, RSAT-ADDS
  ```

After you've installed the operating system roles and features, install the following software in the order shown:
  
    
    

1.  [.NET Framework 4.6.2 ](https://go.microsoft.com/fwlink/p/?linkid=808659)
    
    > [!IMPORTANT]
      > Exchange 2016 CU5 and later **require**.NET Framework 4.6.2. Upgrade your servers to .NET Framework 4.6.2 before you install Exchange 2016 CU5 or you'll receive an error. If .NET Framework 4.5.2 is installed on your Exchange servers, upgrade your servers to Exchange 2016 CU4 before installing .NET Framework 4.6.2.
2.  [Microsoft Unified Communications Managed API 4.0, Core Runtime 64-bit](https://go.microsoft.com/fwlink/p/?linkId=258269)
    
  

### Edge Transport server role
<a name="WS2012Edge"> </a>

Follow the instructions in this section to install the prerequisites on computers running Windows Server 2012 or Windows Server 2012 R2 where you want to install the Edge Transport server role.
  
    
    
Do the following to install the required Windows roles and features:
  
    
    

1. Open Windows PowerShell.
    
  
2. Run the following command to install the required Windows components.
    
  ```
  Install-WindowsFeature ADLDS
  ```

After you've installed the operating system roles and features, install  [.NET Framework 4.6.2 ](https://go.microsoft.com/fwlink/?linkid=808659)
  
    
    

> [!IMPORTANT]
> Exchange 2016 CU5 and later **require**.NET Framework 4.6.2. Upgrade your servers to .NET Framework 4.6.2 before you install Exchange 2016 CU5 or you'll receive an error. If .NET Framework 4.5.2 is installed on your Exchange servers, upgrade your servers to Exchange 2016 CU4 before installing .NET Framework 4.6.2.
  
    
    


## Windows Server 2016 prerequisites
<a name="WS2016"> </a>

The prerequisites that are needed to install Exchange 2016 on computers running Windows Server 2016 depends on which Exchange role you want to install. Read the section below that matches the role you want to install.
  
    
    

> [!IMPORTANT]
> Exchange 2016 Cumulative Update 3 or later is required if you want to install Exchange on Windows Server 2016. 
  
    
    


### Mailbox server role
<a name="WS2016MBX"> </a>

Follow the instructions in this section to install the prerequisites on computers running Windows Server 2016 where you want to install the Mailbox server role.
  
    
    
Do the following to install the required Windows roles and features:
  
    
    

1. Open Windows PowerShell.
    
  
2. Run the following command to install the required Windows components.
    
  ```
  Install-WindowsFeature NET-Framework-45-Features, RPC-over-HTTP-proxy, RSAT-Clustering, RSAT-Clustering-CmdInterface, RSAT-Clustering-Mgmt, RSAT-Clustering-PowerShell, Web-Mgmt-Console, WAS-Process-Model, Web-Asp-Net45, Web-Basic-Auth, Web-Client-Auth, Web-Digest-Auth, Web-Dir-Browsing, Web-Dyn-Compression, Web-Http-Errors, Web-Http-Logging, Web-Http-Redirect, Web-Http-Tracing, Web-ISAPI-Ext, Web-ISAPI-Filter, Web-Lgcy-Mgmt-Console, Web-Metabase, Web-Mgmt-Console, Web-Mgmt-Service, Web-Net-Ext45, Web-Request-Monitor, Web-Server, Web-Stat-Compression, Web-Static-Content, Web-Windows-Auth, Web-WMI, Windows-Identity-Foundation, RSAT-ADDS
  ```

After you've installed the operating system roles and features, install the following software in the order shown:
  
    
    

1.  [Microsoft Knowledge Base article KB3206632](https://go.microsoft.com/fwlink/p/?linkid=837748)
    
  
2.  [Microsoft Unified Communications Managed API 4.0, Core Runtime 64-bit](https://go.microsoft.com/fwlink/p/?linkId=258269)
    
  

### Edge Transport server role
<a name="WS2016Edge"> </a>

Follow the instructions in this section to install the prerequisites on computers running Windows Server 2016 where you want to install the Edge Transport server role.
  
    
    
Do the following to install the required Windows roles and features:
  
    
    

1. Open Windows PowerShell.
    
  
2. Run the following command to install the required Windows components.
    
  ```
  Install-WindowsFeature ADLDS
  ```


## Windows 8.1 and Windows 10 prerequisites (admin tools only)
<a name="Windows8"> </a>

Follow the instructions in this section to install the prerequisites on computers running Windows 8.1 or Windows 10 where you want to install the Exchange 2016 Admin Tools.
  
    
    
On Windows 8.1 computers, install  [.NET Framework 4.6.2 ](https://go.microsoft.com/fwlink/p/?linkid=808659).
  
    
    
On Windows 8.1 and Windows 10 computers, run the following command from an elevated Windows PowerShell session.
  
    
    



```
Enable-WindowsOptionalFeature -Online -FeatureName IIS-ManagementScriptingTools,IIS-ManagementScriptingTools,IIS-IIS6ManagementCompatibility,IIS-LegacySnapIn,IIS-ManagementConsole,IIS-Metabase,IIS-WebServerManagementTools,IIS-WebServerRole
```


