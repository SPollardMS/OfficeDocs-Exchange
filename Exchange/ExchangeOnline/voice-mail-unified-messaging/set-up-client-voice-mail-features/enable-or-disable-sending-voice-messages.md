---
title: "Enable or disable sending voice messages from Outlook Voice Access"
ms.author: tonysmit
author: tonysmit
manager: scotv
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.service: exchange-online
localization_priority: Normal
ms.assetid: 63544ae2-6a28-40b2-82fc-3df83e93ee56
description: "You can enable Outlook Voice Access users to send voice mail messages to other UM-enabled users who are associated with the same dial plan, or prevent them from doing so."
---

# Enable or disable sending voice messages from Outlook Voice Access

You can enable Outlook Voice Access users to send voice mail messages to other UM-enabled users who are associated with the same dial plan, or prevent them from doing so. 
  
By default, this setting is enabled. If you disable this setting, Outlook Voice Access users that call into an Outlook Voice Access number won't be able to send voice messages to users within the same dial plan.
  
For additional tasks related to UM dial plans, see [UM Dial Plan Procedures](http://technet.microsoft.com/library/1bda77c8-c4e2-4ae0-a001-76ae029bf843.aspx).
  
## What do you need to know before you begin?

- Estimated time to complete: Less than 1 minute.
    
- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "UM dial plans" entry in the [Unified Messaging Permissions](http://technet.microsoft.com/library/d326c3bc-8f33-434a-bf02-a83cc26a5498.aspx) topic. 
    
- Before you perform these procedures, confirm that a UM dial plan has been created. For detailed steps, see [Create a UM dial plan](../../voice-mail-unified-messaging/connect-voice-mail-system/create-um-dial-plan.md).
    
- For information about keyboard shortcuts that may apply to the procedures in this topic, see **Keyboard shortcuts in the Exchange admin center**.
    
> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612),[Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351).. 
  
## What do you want to do?

### Use the EAC to enable or prevent Outlook Voice Access users sending voice messages to users in the same dial plan

1. In the EAC, navigate to **Unified Messaging** \> **UM dial plans**.
    
2. In the list view, select the UM dial plan you want to change, and then click **Edit**![Edit icon](../../media/ITPro_EAC_EditIcon.gif).
    
3. On the **UM dial plan** page, click **Configure**.
    
4. In **Transfer &amp; search**, under **Allow callers to**, select **Leave voice messages without ringing a user's phone** to allow sending voice messages. If you want to prevent sending voice messages for users, clear this setting. 
    
5. Click **Save**.
    
### Use the Shell to enable or prevent Outlook Voice Access users sending voice messages to users in the same dial plan

This example enables Outlook Voice Access users associated with the UM dial plan named  `MyUMDialPlan` to send voice messages to users associated with the same dial plan. 
  
```
Set-UMDialPlan -identity MyUMDialPlan -SendVoiceMsgEnabled $true
```

This example prevents Outlook Voice Access users associated with the UM dial plan named  `MyUMDialPlan` from sending voice messages to users associated with the same dial plan. 
  
```
Set-UMDialPlan -identity MyUMDialPlan -SendVoiceMsgEnabled $false
```


