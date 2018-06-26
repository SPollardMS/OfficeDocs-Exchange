---
title: "Running 'dir' on an ReFS-formatted disk could cause the computer to freeze [Win2k12RefsUpdateNotInstalled]"
ms.author: dstrome
author: dstrome
manager: serdars
ms.date: 12/20/2016
ms.audience: Developer
ms.topic: reference
f1_keywords:
- 'ms.exch.setupreadiness.Win2k12RefsUpdateNotInstalled'
ms.prod: exchange-server-itpro
localization_priority: Normal
ms.assetid: 50b23c15-53b8-46ee-a334-94534bd76e2c
description: "Microsoft Exchange Server 2016 Setup has detected that the computer you're attempting to install Exchange 2016 on doesn't have a recommended Windows update installed. We strongly recommend that you install this Windows update before installing Exchange 2016 to avoid any issues resolved by the update."
---

# Running "dir" on an ReFS-formatted disk could cause the computer to freeze [Win2k12RefsUpdateNotInstalled]

Microsoft Exchange Server 2016 Setup has detected that the computer you're attempting to install Exchange 2016 on doesn't have a recommended Windows update installed. We strongly recommend that you install this Windows update before installing Exchange 2016 to avoid any issues resolved by the update.
  
Computers running Windows Server 2012 and later support the Resilient File System (ReFS). An issue exists that could cause computers to freeze when the " **dir** " command is run on disks formatted with ReFS. 
  
Download and install the 64-bit update from the following URL, and then click **retry** on the **Readiness Checks** page. 
  
> [!NOTE]
> If this update requires a reboot to complete installation, you'll need to exit Exchange 2016 Setup, reboot, and then start Setup again. 
  
Microsoft Knowledge Base article KB2894875, [ Windows 8-based or Windows Server 2012-based computer freezes when you run the "dir" command on an ReFS volume ](http://go.microsoft.com/fwlink/?linkid=3052&kbid=2894875)
  
Having problems? Ask for help in the Exchange forums. Visit the forums at: [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351).
  
Did you find what you're looking for? Please take a minute to [send us feedback](mailto:ExchangeHelpFeedback@microsoft.com&subject=Exchange%202016%20help%20feedback&Body=Thanks%20for%20taking%20the%20time%20to%20send%20us%20feedback!%20We%20strive%20to%20respond%20to%20every%20message%20we%20receive,%20even%20though%20it%20might%20take%20us%20a%20while.%20Let%20us%20know%20what%20you%20think%20about%20Exchange%20content:%20What%20are%20we%20doing%20right%3F%20How%20can%20we%20make%20help%20better%3F%0APlease%20note%20that%20we're%20unable%20to%20respond%20to%20requests%20for%20support%20submitted%20via%20this%20email%20address.%20If%20you%20need%20help,%20please%20contact%20Exchange%20Server%20support%20at%20http://go.microsoft.com/fwlink/p/%3FLinkId=402506.%0AThanks!%0AThe%20Exchange%20Server%20Content%20Publishing%20team) about the information you were hoping to find. 
  

