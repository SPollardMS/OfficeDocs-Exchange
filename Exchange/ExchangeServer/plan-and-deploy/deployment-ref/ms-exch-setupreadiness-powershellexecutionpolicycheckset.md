---
title: "ExecutionPolicy GPO is defined [PowerShellExecutionPolicyCheckSet]"
ms.author: dstrome
author: dstrome
manager: serdars
ms.date: 7/22/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- 'ms.exch.setupreadiness.PowerShellExecutionPolicyCheckSet'
ms.prod: exchange-server-itpro
localization_priority: Normal
ms.assetid: 63de83e2-9a6b-4f57-85b9-df445bea18dd
description: "Microsoft Exchange Server 2016 Setup can't continue because it detected that the ExecutionPolicy Group Policy Object (GPO) defines one or both of the following policies:"
---

# ExecutionPolicy GPO is defined [PowerShellExecutionPolicyCheckSet]

Microsoft Exchange Server 2016 Setup can't continue because it detected that the **ExecutionPolicy** Group Policy Object (GPO) defines one or both of the following policies: 
  
- **MachinePolicy**
    
- **UserPolicy**
    
It doesn't matter how the policies have been defined. It only matters that they have been defined.
  
When you run Exchange 2016 Setup, Exchange stops and disables the Windows Management Instrumentation (WMI) service. When either of these policies are defined, the WMI service needs to be enabled to run a Windows PowerShell script. If the policies are defined and the WMI service is stopped, Setup will fail and the server will be left in an inconsistent state.
  
To allow Setup to continue, you need to temporarily remove any definition of **MachinePolicy** or **UserPolicy** in the **ExecutionPolicy** GPO.
  
For information on how to remove any definitions of **MachinePolicy** or **UserPolicy** in the **ExecutionPolicy** GPO, see [Knowledge Base article KB981474](http://go.microsoft.com/fwlink/?linkid=3052&kbid=981474).
  
> [!NOTE]
> Even though this Knowledge Base article was written for Exchange 2010, it also applies to Exchange 2016 cumulative updates and service packs.
  
Having problems? Ask for help in the Exchange forums. Visit the forums at: [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351).
  
Did you find what you're looking for? Please take a minute to [send us feedback](mailto:ExchangeHelpFeedback@microsoft.com&subject=Exchange%202016%20help%20feedback&Body=Thanks%20for%20taking%20the%20time%20to%20send%20us%20feedback!%20We%20strive%20to%20respond%20to%20every%20message%20we%20receive,%20even%20though%20it%20might%20take%20us%20a%20while.%20Let%20us%20know%20what%20you%20think%20about%20Exchange%20content:%20What%20are%20we%20doing%20right%3F%20How%20can%20we%20make%20help%20better%3F%0APlease%20note%20that%20we're%20unable%20to%20respond%20to%20requests%20for%20support%20submitted%20via%20this%20email%20address.%20If%20you%20need%20help,%20please%20contact%20Exchange%20Server%20support%20at%20http://go.microsoft.com/fwlink/p/%3FLinkId=402506.%0AThanks!%0AThe%20Exchange%20Server%20Content%20Publishing%20team) about the information you were hoping to find.
  

