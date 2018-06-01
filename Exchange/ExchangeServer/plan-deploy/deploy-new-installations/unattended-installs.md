---
title: "Install Exchange 2016 using unattended mode"
ms.author: dstrome
author: dstrome
manager: serdars
ms.date: 4/19/2018
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.collection: Strat_EX_Admin
ms.assetid: 386465e9-41da-4e26-9816-b3b69be1f8bf
description: "How to perform an unattended setup of Exchange Server 2016 from the command line."
---

# Install Exchange 2016 using unattended mode

How to perform an unattended setup of Exchange Server 2016 from the command line.
  
For more information about planning for Exchange 2016, see [Planning and deployment](../../plan-deploy/plan-deploy.md).
  
We recommend that the Edge Transport role be installed in a perimeter network outside of your organization's internal Active Directory forest. While you can install the Edge Transport server role on a domain-joined computer, doing so will only enable domain management of Windows features and settings. The Edge Transport role itself doesn't use Active Directory. Instead, it uses the Active Directory Lightweight Directory Services (AD LDS) Windows feature to store configuration and recipient information. For more information about the Edge Transport role, see [Edge Transport servers](../../architecture/edge-transport-servers/edge-transport-servers.md).
  
> [!NOTE]
> The Edge Transport role can't be installed on the same computer as the Mailbox server role. 
  
For information about tasks to complete after installation, see [Exchange 2016 post-installation tasks](../../plan-deploy/post-installation-tasks/post-installation-tasks.md).
  
## What do you need to know before you begin?

The following information applies to both the Mailbox and Edge Transport server roles.
  
- Make sure you've read the release notes prior to installing Exchange 2016. For more information, see [Release notes for Exchange 2016](../../release-notes.md).
    
- The computer you install Exchange 2016 on needs to have a supported operating system, have enough disk space, and satisfy other requirements. For information about system requirements, see [Exchange 2016 system requirements](../../plan-deploy/system-requirements.md).
    
- To run Exchange 2016 setup, you need to install various Windows roles and features, .NET Framework 4.5.2 or later, and other required software. To understand the prerequisites for all server roles, see [Exchange 2016 prerequisites](../../plan-deploy/prerequisites.md).
    
- For information about keyboard shortcuts that may apply to the procedures in this topic, see [Keyboard shortcuts in the Exchange admin center](../../about-documentation/eac-keyboard-shortcuts.md).
    
> [!CAUTION]
> After you install Exchange 2016 on a server, you must not change the server name. Renaming a server after you have installed an Exchange 2016 server role is not supported. 
  
The following information applies to the Exchange 2016 Mailbox server role.
  
- Estimated time to complete: 60 minutes
    
- The computer you install Exchange 2016 on must be a member of an Active Directory domain.
    
- If you're installing the first Exchange 2016 server in the organization, the account you use needs to be a member of the Enterprise Admins group.
    
- If you haven't previously prepared the Active Directory schema, the account you use also needs to be a member of the Schema Admins group. 
    
- If you've already prepared the schema and aren't installing the first Exchange 2016 server in the organization, the account you use needs to be a member of the Exchange 2016 Organization Management role group.
    
    Administrators who are members of the Delegated Setup role group can deploy Exchange 2016 servers that have been previously provisioned by a member of the Organization Management role group.
    
The following information applies to the Exchange 2016 Edge Transport server role.
  
- Estimated time to complete: 40 minutes
    
- You need to configure the primary DNS suffix on the computer. For example, if the fully qualified domain name of your computer is edge.contoso.com, the DNS suffix for the computer is contoso.com. For more information, see [Primary DNS Suffix is missing [ms.exch.setupreadiness.FqdnMissing]](../../plan-deploy/deployment-ref/ms-exch-setupreadiness-fqdnmissing.md).
    
- Exchange 2010 Hub Transport servers need an update before you can create an EdgeSync Subscription between them and an Exchange 2016 Edge Transport server. If you don't install this update, the EdgeSync Subscription won't work correctly. For more information, see the "Supported coexistence scenarios" section in [Exchange 2016 system requirements](../../plan-deploy/system-requirements.md).
    
- Make sure the account you use is a member of the local Administrators group on the computer you're installing the Edge Transport role.
    
## Use Setup.exe to install Exchange 2016 in unattended mode

1. Log on to the computer on which you want to install Exchange 2016.
    
2. Download the Exchange 2016 installation files from the [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=627251).
    
3. Navigate to the network location of the Exchange 2016 installation files.
    
4. At the command prompt, run the applicable command for your organization.
    
    > [!IMPORTANT]
    > If you have User Access Control (UAC) enabled, you must run  `Setup.exe` from an elevated command prompt. 
  
  ```
  Setup.exe [/Mode:<setup mode>] [/IAcceptExchangeServerLicenseTerms]
  [/Role:<server role to install>] [/InstallWindowsComponents] 
  [/OrganizationName:<name for the new Exchange organization>] 
  [/TargetDir:<target directory>] [/SourceDir:<source directory>]
  [/UpdatesDir:<directory from which to install updates>] 
  [/DomainController:<FQDN of domain controller>] [/DisableAMFiltering]
  [/AnswerFile:<filename>] [/DoNotStartTransport] 
  [/EnableErrorReporting] [/CustomerFeedbackEnabled:<True | False>] 
  [/AddUmLanguagePack:<UM language pack name>] 
  [/RemoveUmLanguagePack:<UM language pack name>] 
  [/NewProvisionedServer:<server>] [/RemoveProvisionedServer:<server>] 
  [/MdbName:<mailbox database name>] [/DbFilePath:<Edb file path>] 
  [/LogFolderPath:<log folder path>] [/ActiveDirectorySplitPermissions:<True | False>]
  [/TenantOrganizationConfig:<path>]
  ```

5. Setup copies the setup files locally to the computer on which you're installing Exchange 2016.
    
6. Setup checks the prerequisites, including all prerequisites specific to the server roles that you're installing. If you haven't met all the prerequisites, Setup fails and returns an error message that explains the reason for the failure. If you've met all the prerequisites, Setup installs Exchange 2016.
    
7. Restart the computer after Exchange 2016 has completed.
    
8. Complete your deployment by performing the tasks provided in [Exchange 2016 post-installation tasks](../../plan-deploy/post-installation-tasks/post-installation-tasks.md).
    
## Examples

The following are examples of using Setup.exe:
  
- **Setup.exe /mode:Install /role:Mailbox /OrganizationName:MyOrg /IAcceptExchangeServerLicenseTerms**
    
    This command creates an Exchange 2016 organization in Active Directory called MyOrg, installs the Mailbox server role and the management tools, and also accepts the Exchange 2016 licensing terms.
    
- **Setup.exe /mode:Install /role:Mailbox /TargetDir:"C:\Exchange Server" /IAcceptExchangeServerLicenseTerms**
    
    This command installs the Mailbox server role and the management tools in the "C:\Exchange Server" directory. This command assumes an Exchange 2016 organization has already been prepared.
    
- **Setup.exe /mode:Install /r:MB /IAcceptExchangeServerLicenseTerms**
    
    This command installs the Mailbox server role and the management tools in the default installation location.
    
- **Setup.exe /mode:Install /r:EdgeTransport /IAcceptExchangeServerLicenseTerms**
    
    This command installs the Edge Transport server role and the management tools in the default installation location.
    
- **Setup.exe /mode:Install /r:ET /IAcceptExchangeServerLicenseTerms**
    
    This command installs the Edge Transport server role and the management tools in the default installation location.
    
- **Setup.exe /mode:Uninstall /IAcceptExchangeServerLicenseTerms**
    
    This command completely removes Exchange 2016 from the server and removes this server's Exchange configuration from Active Directory.
    
- **Setup.exe /PrepareAD /on:"My Org" /IAcceptExchangeServerLicenseTerms**
    
    This command creates an Exchange organization called My Org and prepares Active Directory for Exchange 2016.
    
- **Setup.exe /role:Mailbox /UpdatesDir:"C:\ExchangeServer\New Patches" /IAcceptExchangeServerLicenseTerms**
    
    This command updates ExchangeServer.msi with patches from the specified directory, and then installs the Mailbox server role and the management tools. If a language pack bundle is included in this directory, the language pack is also installed.
    
- **Setup.exe /mode:Install /role:Mailbox /DomainController:DC01 /IAcceptExchangeServerLicenseTerms**
    
    This command uses the domain controller DC01 to query and make changes to Active Directory while installing Mailbox server role and the management tools.
    
- **Setup.exe /mode:Install /role:Mailbox /AnswerFile:c:\ExchangeConfig.txt /IAcceptExchangeServerLicenseTerms**
    
    This command installs the Mailbox server role by using the settings in the ExchangeConfig.txt file.
    
- **Setup.exe /rprs:Exchange03 /IAcceptExchangeServerLicenseTerms**
    
    This command removes the object Exchange03 from Active Directory.
    
- **Setup.exe /AddUmLanguagePack:ko-KR /IAcceptExchangeServerLicenseTerms**
    
    This command installs the Korean Unified Messaging language pack from the %ExchangeSourceDir%\ServerRoles\UnifiedMessaging directory.
    
## How do you know this worked?

To verify that you've successfully installed Exchange 2016, see [Verify an Exchange 2016 installation](../../plan-deploy/post-installation-tasks/verify-installation.md).
  
Having problems? Ask for help in the Exchange forums. Visit the forums at: [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351).
  
Did you find what you're looking for? Please take a minute to [send us feedback](mailto:ExchangeHelpFeedback@microsoft.com&amp;subject=Exchange%202016%20help%20feedback&amp;Body=Thanks%20for%20taking%20the%20time%20to%20send%20us%20feedback!%20We%20strive%20to%20respond%20to%20every%20message%20we%20receive,%20even%20though%20it%20might%20take%20us%20a%20while.%20Let%20us%20know%20what%20you%20think%20about%20Exchange%20content:%20What%20are%20we%20doing%20right%3F%20How%20can%20we%20make%20help%20better%3F%0APlease%20note%20that%20we're%20unable%20to%20respond%20to%20requests%20for%20support%20submitted%20via%20this%20email%20address.%20If%20you%20need%20help,%20please%20contact%20Exchange%20Server%20support%20at%20http://go.microsoft.com/fwlink/p/%3FLinkId=402506.%0AThanks!%0AThe%20Exchange%20Server%20Content%20Publishing%20team) about the information you were hoping to find. 
  

