---
title: "Enable or disable sending voice messages to users"
ms.author: tonysmit
author: tonysmit
manager: scotv
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.service: exchange-online
localization_priority: Normal
ms.assetid: faa300d8-2534-40db-8ef9-428be8bb7934
description: "You can enable callers to send voice messages to users from a Unified Messaging (UM) auto attendant, or prevent them from doing so. By default, this option is enabled and lets callers send voice messages to users in the UM dial plan that's associated with the UM auto attendant. If you disable this option, the auto attendant won't invite callers to send a voice message during a system prompt."
---

# Enable or disable sending voice messages to users

You can enable callers to send voice messages to users from a Unified Messaging (UM) auto attendant, or prevent them from doing so. By default, this option is enabled and lets callers send voice messages to users in the UM dial plan that's associated with the UM auto attendant. If you disable this option, the auto attendant won't invite callers to send a voice message during a system prompt.
  
For additional management tasks related to UM auto attendants, see [UM auto attendant procedures](um-auto-attendant-procedures.md).
  
## What do you need to know before you begin?

- Estimated time to complete: Less than 1 minute.
    
- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "UM auto attendants" entry in the [Unified Messaging Permissions](http://technet.microsoft.com/library/d326c3bc-8f33-434a-bf02-a83cc26a5498.aspx) topic. 
    
- Before you perform these procedures, confirm that a UM dial plan has been created. For detailed steps, see [Create a UM dial plan](../../voice-mail-unified-messaging/connect-voice-mail-system/create-um-dial-plan.md).
    
- Before you perform these procedures, confirm that a UM auto attendant has been created. For detailed steps, see [Create a UM auto attendant](create-a-um-auto-attendant.md).
    
- For information about keyboard shortcuts that may apply to the procedures in this topic, see **Keyboard shortcuts in the Exchange admin center**.
    
> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612),[Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351).. 
  
## What do you want to do?

### Use the EAC to enable callers to send voice messages or prevent them from doing so

1. In the EAC, navigate to **Unified Messaging** \> **UM dial plans**. In the list view, select the UM dial plan you want to change, and then click **Edit**![Edit icon](../../media/ITPro_EAC_EditIcon.gif).
    
2. On the **UM Dial Plan** page, under **UM Auto Attendants**, select the UM auto attendant you want to manage, and then click **Edit**![Edit icon](../../media/ITPro_EAC_EditIcon.gif).
    
3. On the **UM Auto Attendant** page \> **Address book and operator access**, under **Options for contacting users**, select the check box next to **Allow callers to leave voice messages for users** to enable callers to leave voice messages. To prevent callers from leaving voice messages, clear the check box. 
    
4. Click **Save**.
    
> [!NOTE]
> If you disable this option and also disable the **Allow callers to dial users** option, the **Options for searching the address book** are also disabled. 
  
### Use the Shell to enable callers to send voice messages or prevent them from doing so

This example prevents callers who call in to a UM auto attendant named  `MyUMAutoAttendant` from sending voice messages. 
  
```
Set-UMAutoAttendant -Identity MyUMAutoAttendant -SendVoiceMsgEnabled $false
```

This example enables callers who call in to a UM auto attendant named  `MyUMAutoAttendant` to send voice messages. 
  
```
Set-UMAutoAttendant -Identity MyUMAutoAttendant -SendVoiceMsgEnabled $true
```


