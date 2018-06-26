---
title: "Disable voice mail for a user"
ms.author: tonysmit
author: tonysmit
manager: scotv
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: cecc9c0d-377d-489e-9db4-d487e9c0b552
description: "You can disable Unified Messaging (UM) for a UM-enabled user. When you do this, the user can no longer use the voice mail features found in Unified Messaging. If you prefer, when you disable UM for a user, you can keep the UM settings for the user."
---

# Disable voice mail for a user

You can disable Unified Messaging (UM) for a UM-enabled user. When you do this, the user can no longer use the voice mail features found in Unified Messaging. If you prefer, when you disable UM for a user, you can keep the UM settings for the user. 
  
For additional management tasks related to users who are enabled for voice mail, see [Voice mail-enabled user procedures](voice-mail-enabled-user-procedures.md).
  
## What do you need to know before you begin?

- Estimated time to complete: Less than 1 minute.
    
- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "UM mailboxes" entry in the [Unified Messaging Permissions](http://technet.microsoft.com/library/d326c3bc-8f33-434a-bf02-a83cc26a5498.aspx) topic. 
    
- Before you perform this procedure, confirm that a UM dial plan has been created. For detailed steps, see [Create a UM dial plan](../../voice-mail-unified-messaging/connect-voice-mail-system/create-um-dial-plan.md).
    
- Before you perform this procedure, confirm that a UM mailbox policy has been created. For detailed steps, see [Create a UM mailbox policy](create-um-mailbox-policy.md).
    
- Before you perform these procedures, confirm that the existing user is currently enabled for Unified Messaging. For detailed steps, see [Enable a user for voice mail](enable-a-user-for-voice-mail.md).
    
- For information about keyboard shortcuts that may apply to the procedures in this topic, see **Keyboard shortcuts in the Exchange admin center**.
    
> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612),[Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351).. 
  
## What do you want to do?

### Use the EAC to disable Unified Messaging and voice mail for a user

1. In the EAC, click **Recipients**.
    
2. In the list view, select the user whose mailbox you want to disable for Unified Messaging.
    
3. In the Details pane, under **Phone and Voice Features**, under **Unified Messaging**, click **Disable**.
    
4. In the **Warning** box, click **Yes** to confirm that Unified Messaging will be disabled for the user. 
    
### Use the Shell to disable Unified Messaging and voice mail for a user

This example disables Unified Messaging and voice mail for the user tonysmith@contoso.com, but keeps the UM mailbox settings.
  
```
Disable-UMMailbox -Identity tonysmith@contoso.com -KeepProperties $True
```


