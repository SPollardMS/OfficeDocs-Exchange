---
title: "Upgrade Exchange 2016 to the latest cumulative update"
ms.author: dstrome
author: dstrome
manager: serdars
ms.date: 3/28/2016
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.collection: Strat_EX_Admin
ms.assetid: 928a4a0b-0082-4d50-a696-bfaf2782f42d
description: "Summary: How to install cumulative updates in Exchange 2016."
---

# Upgrade Exchange 2016 to the latest cumulative update

 **Summary**: How to install cumulative updates in Exchange 2016.
  
If you have Microsoft Exchange Server 2016 installed, you can upgrade it to the latest Exchange 2016 cumulative update. You can use the Exchange 2016 Setup wizard to upgrade your current version of Exchange 2016. For more information about the latest Exchange 2016 cumulative update, see [Updates for Exchange 2016](../what-s-new/updates.md). To learn more about Exchange 2016, see [What's new in Exchange 2016](../what-s-new/what-s-new.md).
  
> [!CAUTION]
> After you upgrade Exchange 2016 to a newer cumulative update, you can't uninstall the new version to revert to the previous version. If you uninstall the new version, you remove Exchange from the server. 
  
## What do you need to know before you begin?

- Estimated time to complete: 60 minutes
    
- Make sure you read the release notes before you install Exchange 2016. For more information, see [Release notes for Exchange 2016](../release-notes.md).
    
- Make sure that any server on which you plan to install the cumulative update or service pack meets the system requirements and prerequisites. For more information, see [Exchange 2016 system requirements](system-requirements.md) and [Exchange 2016 prerequisites](prerequisites.md).
    
    > [!CAUTION]
    > Any customized per-server Exchange or Internet Information Server settings you make in Exchange XML application configuration files (for example, web.config files or the EdgeTransport.exe.config file) will be overwritten when you install an Exchange Cumulative Update (CU). Make sure that you save this information so that you can easily re-configure your server after the install. You must re-configure these settings after you install an Exchange CU. 
  
- After you install a cumulative update or service pack, you must restart the computer so that changes can be made to the registry and operating system.
    
> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at: [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351). 
  
## Install the Exchange 2016 cumulative update or service pack

You can install the cumulative update or service pack for Exchange 2016 by using either the Setup wizard or via unattended mode. For specific instructions, see the following topics:
  
- [Install the Exchange 2016 Mailbox role using the Setup wizard](deploy-new-install/install-mailbox-role-using-setup-wizard.md)
    
- [Install Exchange 2016 using unattended mode](deploy-new-install/install-exchange-server-in-unattended-mode.md)
    

