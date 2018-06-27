---
title: "Set mailbox features for an Outlook Voice Access user"
ms.author: tonysmit
author: tonysmit
manager: scotv
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.service: exchange-online
localization_priority: Normal
ms.assetid: a56bfd75-7bc5-49b9-b098-06855a720dcd
description: "Telephone user interface (TUI) settings are used when a user accesses the Unified Messaging (UM) system by using Outlook Voice Access. When you modify a UM-enabled user's TUI configuration settings, you modify properties and their values on the UM-enabled user's mailbox."
---

# Set mailbox features for an Outlook Voice Access user

Telephone user interface (TUI) settings are used when a user accesses the Unified Messaging (UM) system by using Outlook Voice Access. When you modify a UM-enabled user's TUI configuration settings, you modify properties and their values on the UM-enabled user's mailbox.
  
You can change the following TUI settings for a UM-enabled user:
  
- Allow subscriber access 
    
- Allow TUI access to the calendar
    
- Allow TUI access to email
    
- Allow Automatic Speech Recognition 
    
For additional management tasks related to UM users, see [Set mailbox features for an Outlook Voice Access user](set-mailbox-features-for-a-user.md).
  
## What do you need to know before you begin?

- Estimated time to complete: 5 minutes.
    
- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "UM mailboxes" entry in the [Unified Messaging Permissions](http://technet.microsoft.com/library/d326c3bc-8f33-434a-bf02-a83cc26a5498.aspx) topic. 
    
- Before you perform these procedures, confirm that the existing Exchange recipient is enabled for Unified Messaging and voice mail. For detailed steps, see [Enable a user for voice mail](../../voice-mail-unified-messaging/set-up-voice-mail/enable-a-user-for-voice-mail.md).
    
- Before you perform these procedures, confirm that a UM dial plan has been created. For detailed steps, see [Create a UM dial plan](../../voice-mail-unified-messaging/connect-voice-mail-system/create-um-dial-plan.md).
    
- Before you perform these procedures, confirm that a UM mailbox policy has been created. For detailed steps, see [Create a UM mailbox policy](../../voice-mail-unified-messaging/set-up-voice-mail/create-um-mailbox-policy.md).
    
- For information about keyboard shortcuts that may apply to the procedures in this topic, see **Keyboard shortcuts in the Exchange admin center**.
    
> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612),[Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351).. 
  
## Use the Shell to modify a single UM-enabled user's TUI settings

This example enables calendar and email access using the TUI for a UM-enabled user named Tony Smith.
  
```
Set-UMMailbox -Identity tony@contoso.com TUIAccessToCal True -TUIAccessToEmail True -OperatorNumber 111111 -DisableMissedCallNotification False -AnonCallBlock True
```

> [!NOTE]
> TUI settings for users are also available on UM mailbox policies. Modifying TUI settings on a UM mailbox policy affects all users who are associated with the UM mailbox policy. For more information about how to modify TUI settings on a UM mailbox policy, see [Set mailbox features for Outlook Voice Access users](set-mailbox-features-for-users.md). 
  

