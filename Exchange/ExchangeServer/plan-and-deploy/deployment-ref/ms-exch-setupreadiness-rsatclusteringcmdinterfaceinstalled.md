---
title: "Failover Cluster Command Interface Windows feature not installed [RsatClusteringCmdInterfaceInstalled]"
ms.author: dstrome
author: dstrome
manager: serdars
ms.date: 7/22/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- 'ms.exch.setupreadiness.RsatClusteringCmdInterfaceInstalled'
ms.prod: exchange-server-itpro
localization_priority: Normal
ms.assetid: 0d839514-5ab7-497d-8945-41392b4c3980
description: "Microsoft Exchange Server 2016 Setup can't continue because the local computer is missing a required Windows feature. You'll need to install this Windows feature before Exchange 2016 can continue."
---

# Failover Cluster Command Interface Windows feature not installed [RsatClusteringCmdInterfaceInstalled]

Microsoft Exchange Server 2016 Setup can't continue because the local computer is missing a required Windows feature. You'll need to install this Windows feature before Exchange 2016 can continue.
  
Exchange 2016 Setup requires that the **Failover Cluster Command Interface** Windows feature be installed on the computer before installation can continue.
  
Do the following to install the Windows feature on this computer. If the feature requires a reboot to complete installation, you'll need to exit Exchange 2016 Setup, reboot, and then start Setup again.
  
> [!NOTE]
> Additional Windows features or updates might need to be installed before Exchange 2016 Setup can continue. For a complete list of required Windows features and updates, check out [Exchange 2016 prerequisites](../../plan-and-deploy/prerequisites.md).
  
1. Open Windows PowerShell on the local computer.
    
2. Run the following command to install the required Windows feature.
    
  ```
  Install-WindowsFeature RSAT-Clustering-CmdInterface
  ```

Having problems? Ask for help in the Exchange forums. Visit the forums at: [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351).
  
Did you find what you're looking for? Please take a minute to [send us feedback](mailto:ExchangeHelpFeedback@microsoft.com&subject=Exchange%202016%20help%20feedback&Body=Thanks%20for%20taking%20the%20time%20to%20send%20us%20feedback!%20We%20strive%20to%20respond%20to%20every%20message%20we%20receive,%20even%20though%20it%20might%20take%20us%20a%20while.%20Let%20us%20know%20what%20you%20think%20about%20Exchange%20content:%20What%20are%20we%20doing%20right%3F%20How%20can%20we%20make%20help%20better%3F%0APlease%20note%20that%20we're%20unable%20to%20respond%20to%20requests%20for%20support%20submitted%20via%20this%20email%20address.%20If%20you%20need%20help,%20please%20contact%20Exchange%20Server%20support%20at%20http://go.microsoft.com/fwlink/p/%3FLinkId=402506.%0AThanks!%0AThe%20Exchange%20Server%20Content%20Publishing%20team) about the information you were hoping to find.
  

