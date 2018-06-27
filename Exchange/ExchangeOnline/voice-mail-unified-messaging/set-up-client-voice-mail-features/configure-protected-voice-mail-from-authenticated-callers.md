---
title: "Configure Protected Voice Mail from authenticated callers"
ms.author: tonysmit
author: tonysmit
manager: scotv
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.service: exchange-online
localization_priority: Normal
ms.assetid: f69e94a7-9768-4445-9ded-e78d732bd623
description: "You can configure Unified Messaging to answer an incoming call, and then determine whether it will apply protection to voice mail messages by using encryption. When a voice message is protected:"
---

# Configure Protected Voice Mail from authenticated callers

You can configure Unified Messaging to answer an incoming call, and then determine whether it will apply protection to voice mail messages by using encryption. When a voice message is protected:
  
- The message is marked as Private in Microsoft Outlook and Outlook Web App. 
    
- The voice message can be opened only by the intended recipient of the voice message.
    
- The recipient can reply to the voice message, but can't forward it to someone who wasn't included on the original voice message.
    
This setting applies to voice messages sent to UM-enabled users when they don't answer their phone. This setting also applies when callers sign in to their mailbox using Outlook Voice Access, and then create and send a voice message. 
  
For additional management tasks related to Protected Voice Mail procedures, see [Protected Voice Mail procedures](protected-voice-mail-procedures.md).
  
## What do you need to know before you begin?

- Estimated time to complete: Less than 1 minute.
    
- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "UM mailbox policies" entry in the [Unified Messaging Permissions](http://technet.microsoft.com/library/d326c3bc-8f33-434a-bf02-a83cc26a5498.aspx) topic. 
    
- Before you perform these procedures, confirm that a UM dial plan has been created. For detailed steps, see [Create a UM dial plan](../../voice-mail-unified-messaging/connect-voice-mail-system/create-um-dial-plan.md).
    
- Before you perform these procedures, confirm that a UM mailbox policy has been created. For detailed steps, see [Create a UM mailbox policy](../../voice-mail-unified-messaging/set-up-voice-mail/create-um-mailbox-policy.md).
    
- For information about keyboard shortcuts that may apply to the procedures in this topic, see **Keyboard shortcuts in the Exchange admin center**.
    
> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612),[Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351).. 
  
## What do you want to do?

### Use the EAC to configure Protected Voice Mail from authenticated callers

1. In the EAC, navigate to **Unified Messaging** \> **UM dial plans**. In the list view, select the UM dial plan you want to modify, and then click **Edit**![Edit icon](../../media/ITPro_EAC_EditIcon.gif).
    
2. On the **UM Dial Plan** page, under **UM Mailbox Policies**, select the UM mailbox policy you want to manage, and then click **Edit**![Edit icon](../../media/ITPro_EAC_EditIcon.gif). 
    
3. On the **UM Mailbox Policy** page \> **Protected voice mail**, under **Protect voice message from authenticated callers**, select one of the following options:
    
  - **None** Use this setting when you don't want protection applied to any voice messages sent to UM-enabled users. 
    
  - **Private** Use this setting when you want Unified Messaging to apply protection only to voice messages that have been marked as private by the caller. 
    
  - **All** Use this setting when you want Unified Messaging to apply protection to all voice messages, including those not marked as private. 
    
4. Click **Save**.
    
### Use the Shell to configure Protected Voice Mail from authenticated callers

This example protects voice messages from all authenticated callers on the UM mailbox policy  `MyUMMailboxPolicy`.
  
```
Set-UMMailboxPolicy -identity MyUMMailboxPolicy ProtectAuthenticatedVoiceMail -All
```


