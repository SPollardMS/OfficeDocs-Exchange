---
title: Install the Exchange 2016 Edge Transport role using the Setup wizard
ms.prod: EXCHANGE
ms.assetid: b8e51b0b-201e-4c64-92c8-3ac0db04b6e2
---


# Install the Exchange 2016 Edge Transport role using the Setup wizard
 **Summary**: How to use the Exchange Server 2016 Setup wizard to install the Exchange 2016 Edge Transport server role on a computer.
For more information about planning and deploying Exchange 2016, see  [Planning and deployment](planning-and-deployment.md).
  
    
    

We recommend that the Edge Transport role be installed in a perimeter network outside of your organization's internal Active Directory forest. While you can install the Edge Transport server role on a domain-joined computer, doing so will only enable domain management of Windows features and settings. The Edge Transport role itself doesn't use Active Directory. Instead, it uses the Active Directory Lightweight Directory Services (AD LDS) Windows feature to store configuration and recipient information. For more information about the Edge Transport role, see  [Edge Transport servers](edge-transport-servers.md).
If you want to install the Exchange 2016 Mailbox role on a computer, see  [Install the Exchange 2016 Mailbox role using the Setup wizard](install-the-exchange-2016-mailbox-role-using-the-setup-wizard.md). The Edge Transport role can't be installed on the same computer as the Mailbox server role.
  
    
    

For information about tasks to complete after installation, see  [Exchange 2016 post-installation tasks](exchange-2016-post-installation-tasks.md).
## What do you need to know before you begin?


- Estimated time to complete: 40 minutes
    
  
- Make sure you've read the release notes prior to installing Exchange 2016. For more information, see  [Release notes for Exchange 2016](release-notes-for-exchange-2016.md).
    
  
- The computer you install Exchange 2016 on must have a supported operating system, have enough disk space, and satisfy other requirements. For information about system requirements, see  [Exchange 2016 system requirements](exchange-2016-system-requirements.md).
    
  
- To run Exchange 2016 setup, you must install Microsoft .NET Framework 4.5.2 or later, and other required software. To understand the prerequisites for all server roles, see  [Exchange 2016 prerequisites](exchange-2016-prerequisites.md).
    
  
- You need to configure the primary DNS suffix on the computer. For example, if the fully qualified domain name of your computer is edge.contoso.com, the DNS suffix for the computer is contoso.com. For more information, see  [Primary DNS Suffix is missing [ms.exch.setupreadiness.FqdnMissing]](primary-dns-suffix-is-missing-ms-exch-setupreadiness-fqdnmissing.md).
    
  
-  Exchange 2010 Hub Transport servers need an update before you can create an EdgeSync Subscription between them and an Exchange 2016 Edge Transport server. If you don't install this update, the EdgeSync Subscription won't work correctly. For more information, see the "Supported coexistence scenarios" section in [Exchange 2016 system requirements](exchange-2016-system-requirements.md).
    
  
- Make sure the account you use is a member of the local Administrators group on the computer you're installing the Edge Transport role.
    
  
- For information about keyboard shortcuts that may apply to the procedures in this topic, see  [Keyboard shortcuts in the Exchange admin center](keyboard-shortcuts-in-the-exchange-admin-center.md).
    
  

> [!CAUTION]
> After you install Exchange 2016 on a server, you must not change the server name. Renaming a server after you have installed an Exchange 2016 server role is not supported. 
  
    
    


## Install Exchange Server 2016


1. Log on to the computer on which you want to install Exchange 2016. 
    
  
2. Download the Exchange 2016 installation files from the  [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=627251).
    
  
3. Navigate to the network location of the Exchange 2016 installation files.
    
  
4. Start Exchange 2016 Setup by double-clicking  `Setup.exe`
    
    > [!IMPORTANT]
      > If you have User Access Control (UAC) enabled, you must right-click  `Setup.exe` and select **Run as administrator**. 
5. On the **Check for Updates?** page, choose whether you want Setup to connect to the Internet and download product and security updates for Exchange 2016. If you select **Connect to the Internet and check for updates**, Setup will download updates and apply them prior to continuing. If you select **Don't check for updates right now**, you can download and install updates manually later. We recommend that you download and install updates now. Click **Next** to continue.
    
  
6. The **Introduction** page begins the process of installing Exchange into your organization. It will guide you through the installation. Several links to helpful deployment content are listed. We recommend that you visit these links prior to continuing setup. Click **Next** to continue.
    
  
7. On the **License Agreement** page, review the software license terms. If you agree to the terms, select **I accept the terms in the license agreement**, and then click **Next**.
    
  
8. On the **Recommended settings** page, select whether you want to use the recommended settings. If you select **Use recommended settings**, Exchange will automatically send error reports and information about your computer hardware and how you use Exchange to Microsoft. If you select **Don't use recommended settings**, these settings remain disabled but you can enable them at any time after Setup completes. For more information about these settings and how information sent to Microsoft is used, click **?**.
    
  
9. On the **Server Role Selection** page, select **Edge Transport**. Remember, you can't add the Mailbox server role to a computer that has the Edge Transport role installed. The management tools are installed automatically if you install any server role. 
    
    Select **Automatically install Windows Server roles and features that are required to install Exchange Server** to have the Setup wizard install required Windows prerequisites. You may need to reboot the computer to complete the installation of some Windows features. If you don't select this option, you must install the Windows features manually.
    
    > [!NOTE]
      > This option installs only the Windows features required by Exchange. You must manually install other prerequisites manually. For more information, see  [Exchange 2016 prerequisites](exchange-2016-prerequisites.md). 

    Click **Next** to continue.
    
  
10. On the **Installation Space and Location** page, either accept the default installation location or click **Browse** to choose a new location. Make sure that you have enough disk space available in the location where you want to install Exchange. Click **Next** to continue.
    
  
11. On the **Readiness Checks** page, view the status to determine if the organization and server role prerequisite checks completed successfully. If they haven't completed successfully, you must resolve any reported errors before you can install Exchange 2016. You don't need to exit Setup when resolving some of the prerequisite errors. After resolving a reported error, click **back** and then click **Next** to run the prerequisite check again. Be sure to also review any warnings that are reported. If all readiness checks have completed successfully, click **Next** to install Exchange 2016.
    
  
12. On the **Completion** page, click **Finish**.
    
  
13. Restart the computer after Exchange 2016 has completed.
    
  
14. Complete your deployment by performing the tasks provided in  [Exchange 2016 post-installation tasks](exchange-2016-post-installation-tasks.md).
    
  

## How do you know this worked?

To verify that you've successfully installed Exchange 2016, see  [Verify an Exchange 2016 installation](verify-an-exchange-2016-installation.md).
  
    
    
Having problems? Ask for help in the Exchange forums. Visit the forums at:  [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612),  [Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or  [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351).
  
    
    
Did you find what you're looking for? Please take a minute to  [send us feedback](mailto:ExchangeHelpFeedback@microsoft.com&amp;subject=Exchange%202016%20help%20feedback&amp;Body=Thanks%20for%20taking%20the%20time%20to%20send%20us%20feedback!%20We%20strive%20to%20respond%20to%20every%20message%20we%20receive,%20even%20though%20it%20might%20take%20us%20a%20while.%20Let%20us%20know%20what%20you%20think%20about%20Exchange%20content:%20What%20are%20we%20doing%20right%3F%20How%20can%20we%20make%20help%20better%3F%0APlease%20note%20that%20we're%20unable%20to%20respond%20to%20requests%20for%20support%20submitted%20via%20this%20email%20address.%20If%20you%20need%20help,%20please%20contact%20Exchange%20Server%20support%20at%20http://go.microsoft.com/fwlink/p/%3FLinkId=402506.%0AThanks!%0AThe%20Exchange%20Server%20Content%20Publishing%20team) about the information you were hoping to find.
  
    
    

