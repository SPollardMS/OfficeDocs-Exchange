---
title: "Install the Exchange 2016 management tools"
ms.author: dstrome
author: dstrome
manager: serdars
ms.date: 4/19/2018
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.collection: Strat_EX_Admin
ms.assetid: 71fcbe4c-783b-4f77-aabb-a21aa7a4ef23
description: "Summary: Learn how to install the Exchange 2016 management tools on other computers."
---

# Install the Exchange 2016 management tools

 **Summary**: Learn how to install the Exchange 2016 management tools on other computers.
  
The management tools in Exchange Server 2016 include the Exchange Management Shell and the Exchange Toolbox. You can install the management tools on other client computers or servers in the Active Directory domain to help you manage your Exchange organization. The management tools have similar operating system, .NET Framework, and Windows Management Framework (Windows PowerShell) requirements as an Exchange server. The notable exception is: you can install the management tools on client versions of Windows. For more information, see [Exchange 2016 system requirements](../../plan-and-deploy/system-requirements.md) and [Exchange 2016 prerequisites](../../plan-and-deploy/prerequisites.md)..
  
> [!NOTE]
> The management tools don't include the Exchange admin center (EAC). The EAC is a web-based console that's hosted on Exchange 2016 Mailbox servers, and like any web site, you can access the EAC from other computers. For more information about the EAC, see [Exchange admin center in Exchange 2016](../../architecture/client-access-services/eac.md). 
  
For more information about the Exchange Management Shell and the Exchange Toolbox, see [Using Powershell with Exchange 2016 (Exchange Management Shell)](http://technet.microsoft.com/library/925ad66f-2f05-4269-9923-c353d9c19312.aspx) and [Exchange Toolbox](http://technet.microsoft.com/library/b4a2e942-ea90-4a80-963d-d336cd6411d9.aspx).
  
## What do you need to know before you begin?

- Estimated time to complete: 20 minutes
    
- For information about keyboard shortcuts that may apply to the procedures in this topic, see [Keyboard shortcuts in the Exchange admin center](../../about-documentation/keyboard-shortcuts-in-eac.md).
    
> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at: [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351). 
  
## Use the Exchange 2016 Setup wizard to install the management tools

1. Use the information in [Updates for Exchange 2016](../../what-s-new/updates.md) to download the latest version of Exchange 2016. You can download the ISO image file locally on the computer where you want to install the management tools, or to a central network location. 
    
2. On the computer where you want to install the management tools:
    
1. Open File Explorer, right-click on the Exchange ISO image file that you downloaded, and then select **Mount**.
    
2. In the resulting virtual DVD drive that appears, start Exchange 2016 Setup by double-clicking  `Setup.exe`.
    
3. The Exchange Server 2016 Setup wizard opens. On the **Check for Updates?** page, choose one of the following options, and then click **Next** to continue: 
    
  - **Connect to the Internet and check for updates** We recommend this option, which searches for updates to the version of Exchange 2016 that you're installing (it doesn't detect newer Exchange 2016 Cumulative Updates). This option takes you to the **Downloading Updates** page that searches for updates. 
    
  - **Don't check for updates right now**
    
![Exchange 2016 Setup, Check for Updates page](../../media/f0ca225e-b88f-45e9-a8cb-21adaabe984e.png)
  
4. The **Copying Files** page shows the progress of copying files to the local hard drive. Typically, the files are copied to  `%WinDir%\Temp\ExchangeSetup`, but you can confirm the location in the Exchange Setup log at  `C:\ExchangeSetupLogs\ExchangeSetup.log`.
    ![Exchange 2016 Setup, Copying Files page](../../media/78813be2-745d-4a58-8da8-883c43aa2650.png)
  
5. On the **Introduction** page, click **Next** to continue. 
    ![Exchange 2016 Setup, Introduction page](../../media/9f605305-979a-4667-a042-38854677cf0b.png)
  
6. On the **License Agreement** page, review the software license terms, select **I accept the terms in the license agreement**, and then click **Next** to continue. 
    ![Exchange 2016 Setup, License Agreement page](../../media/2bb6bfaa-1b39-4052-9420-a7a053b07d58.png)
  
7. On the **Recommended Settings** page, choose one of the following settings: 
    
  - **Use recommended settings** Exchange automatically sends error reports and information about your computer hardware and how you use Exchange to Microsoft. For information about what's sent to Microsoft and how it's used, click **?** or the help links on the page. 
    
  - **Don't use recommended settings** These settings are disabled, but you can enable them at any time after Setup completes. 
    
    Click **Next** to continue. 
    ![Exchange 2016 Setup, Recommended Settings page](../../media/26af58f0-52ab-4482-8710-9a7cd2e7a6c3.png)
  
8. On the **Server Role Selection** page, configure the following settings: 
    
  - Select **Management tools**.
    
  - **Automatically install Windows Server roles and features that are required to install Exchange** Select this option to have the Setup wizard install the required Windows prerequisites. You might need to reboot the computer to complete the installation of some Windows features. If you don't select this option, you need to install the Windows features manually. 
    
    **Note**: Selecting this option installs only the Windows features that are required by Exchange. You need to install other prerequisites manually. For more information, see [Exchange 2016 prerequisites](../../plan-and-deploy/prerequisites.md).
    
    Click **Next** to continue. 
    ![Exchange 2016 Setup, Server Role Selection page, Management tools selection](../../media/9675432c-9b46-4f95-841d-1cea632a93a9.png)
  
9. On the **Installation Space and Location** page, either accept the default installation location (  `C:\Program Files\Microsoft\Exchange Server\V15`), or click **Browse** to choose a new location. Make sure that you have enough disk space available in the location where you want to install the management tools. Click **Next** to continue. 
    ![Exchange 2016 Setup, Installation Space and Location page](../../media/7ae7f248-3cdc-4453-9d7d-e99edc300d16.png)
  
10. If this is the first installation of Exchange in your organization (Exchange server or the management tools), you arrive on the **Exchange Organization** page. On this page, configure the following settings: 
    
  - **Specify the name for this Exchange organization** The default value is **First Organization**, but you typically use the company name for this value. The organization name is used internally by Exchange, isn't typically seen by users, doesn't affect the functionality of Exchange, and doesn't determine what you can use for email addresses.
    
  - The organization name can't contain more than 64 characters, and can't be blank.
    
  - Valid characters are A to Z, a to z, 0 to 9, hyphen or dash (-), and space, but leading or trailing spaces aren't allowed.
    
  - You can't change the organization name after it's set.
    
  - **Apply Active Directory split permission security model to the Exchange organization** Most organizations don't need to select this option. If you need to separate management of Active Directory security principals and the Exchange configuration, split permissions might work for you. For more information, click **?**.
    
    Click **Next** to continue. 
    ![Exchange 2016 Setup, Exchange Organization page](../../media/acdba072-f4bb-4fb8-acae-c6b43cb32044.png)
  
11. On the **Readiness Checks** page, verify that the organization and server role prerequisite checks completed successfully. If they haven't, the only option on the page is **Retry**, so you need to resolve the errors before you can continue.
    ![Exchange 2016 Setup, Readiness Check page with errors detected](../../media/d4ee435a-a383-4be6-8233-da4cc2a19eea.png)
  
    After you resolve the errors, click **Retry** to run the prerequisite checks again. You can fix some errors without exiting Setup, while the fix for other errors requires you to restart the computer. If you restart the computer, you need to start over at Step 2. 
    
    When no more errors are detected on the **Readiness Checks** page, the **Retry** button changes to **Install** so you can continue. Be sure to review any warnings, and then click **Install** to install the management tools. 
    ![Exchange 2016 Setup, Readiness Check page with errors resolved](../../media/a9aca4d0-19ac-4783-8071-cdd435b1658d.png)
  
12. On the **Setup Completed** page, click **Finish**, and then restart the computer.
    ![Exchange 2016 Setup, Setup Completed page](../../media/6019a9d8-33d8-4ceb-9b4f-63bff3c105dd.png)
  
## Use Exchange 2016 unattended Setup mode to install the management tools

1. Use the information in [Updates for Exchange 2016](../../what-s-new/updates.md) to download the latest version of Exchange 2016. You can download the ISO image file locally on the computer where you want to install the management tools, or to a central network location. 
    
2. On the computer where you want to install the management tools:
    
1. Open File Explorer, right-click on the Exchange ISO image file that you downloaded, and then select **Mount**.
    
2. Open an elevated command prompt (a Command Prompt window you open by selecting **Run as administrator**), and go to the resulting virtual DVD drive that appears. For example, if the virtual drive letter is E:, type  `E:` in the command prompt, and then press Enter. 
    
3. To install the management tools, use the following syntax:
    
  ```
  Setup.exe /Role:ManagementTools /IAcceptExchangeServerLicenseTerms [/EnableErrorReporting] [/CustomerFeedbackEnabled:<True | False>] [/InstallWindowsComponents] [/TargetDir:<Target folder>] [/OrganizationName:<Name>]
  ```

    This example installs the management tools on the local computer with the default settings.
    
  ```
  Setup.exe /Role:ManagementTools /IAcceptExchangeServerLicenseTerms
  ```

For more information, see [Install Exchange 2016 using unattended mode](../../plan-and-deploy/deploy-new-install/install-exchange-server-in-unattended-mode.md).
  

