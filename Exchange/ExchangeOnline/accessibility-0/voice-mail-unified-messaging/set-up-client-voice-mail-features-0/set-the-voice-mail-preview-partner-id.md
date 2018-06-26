---
title: "Set the Voice Mail Preview partner ID"
ms.author: tonysmit
author: tonysmit
manager: scotv
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: ab98c320-9952-47a7-b141-ddfc2c0ad419
description: "You can set a Voice Mail Preview partner ID on a Unified Messaging (UM) mailbox policy. After you've set the Voice Mail Preview partner ID on a UM mailbox policy, the setting will apply to all UM-enabled users who are linked with that mailbox policy."
---

# Set the Voice Mail Preview partner ID

You can set a Voice Mail Preview partner ID on a Unified Messaging (UM) mailbox policy. After you've set the Voice Mail Preview partner ID on a UM mailbox policy, the setting will apply to all UM-enabled users who are linked with that mailbox policy.
  
> [!NOTE]
> You must use the Shell to set the Voice Mail Preview partner ID. 
  
For more information about the Voice Mail Preview partner program, see [Voice Mail Preview advisor](voice-mail-preview-advisor.md).
  
For additional management tasks related to voice mail preview, see [Voice Mail Preview procedures](voice-mail-preview-procedures.md).
  
## What do you need to know before you begin?

- Estimated time to complete: 1 minute.
    
- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "UM mailbox policies" entry in the [Unified Messaging Permissions](http://technet.microsoft.com/library/d326c3bc-8f33-434a-bf02-a83cc26a5498.aspx) topic. 
    
- Before you perform these procedures, confirm that a UM dial plan has been created. For detailed steps, see [Create a UM dial plan](../../voice-mail-unified-messaging/connect-voice-mail-system/create-um-dial-plan.md).
    
- Before you perform these procedures, confirm that a UM dial plan has been created. For detailed steps, see [Create a UM mailbox policy](../../voice-mail-unified-messaging/set-up-voice-mail/create-um-mailbox-policy.md).
    
- For information about keyboard shortcuts that may apply to the procedures in this topic, see **Keyboard shortcuts in the Exchange admin center**.
    
> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612),[Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351).. 
  
## Use the Shell to set the Voice Mail Preview partner ID on a UM mailbox policy

This example sets the Voice Mail Preview partner ID to CON123-2010 on a UM mailbox policy named  _MyUMMailboxPolicy_.
  
```
Set-UMMailboxPolicy -identity MyUMMailboxPolicy 
-VoiceMailPreviewPartnerAssignedID CON123-2010
```


