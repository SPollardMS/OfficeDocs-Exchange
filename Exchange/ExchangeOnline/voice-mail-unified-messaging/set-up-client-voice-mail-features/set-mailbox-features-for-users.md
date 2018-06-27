---
title: "Set mailbox features for Outlook Voice Access users"
ms.author: tonysmit
author: tonysmit
manager: scotv
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.service: exchange-online
localization_priority: Normal
ms.assetid: 10960bf0-65cf-4d0b-bae5-d203c53662db
description: "Outlook Voice Access contains two interfaces: a telephone user interface (TUI) and a voice user interface (VUI). You can configure a UM-enabled user's TUI settings when the user accesses a mailbox using the Unified Messaging (UM) system in Exchange 2013. When you modify a UM-enabled user's TUI settings on a UM mailbox policy, the changes affect all users who are associated with the UM mailbox policy. You can modify the following TUI settings on a UM mailbox policy:"
---

# Set mailbox features for Outlook Voice Access users

Outlook Voice Access contains two interfaces: a telephone user interface (TUI) and a voice user interface (VUI). You can configure a UM-enabled user's TUI settings when the user accesses a mailbox using the Unified Messaging (UM) system in Exchange 2013. When you modify a UM-enabled user's TUI settings on a UM mailbox policy, the changes affect all users who are associated with the UM mailbox policy. You can modify the following TUI settings on a UM mailbox policy:
  
- PIN-less access to voice mail
    
- Voice responses to other messages
    
- TUI access to their calendar
    
- TUI access to the directory
    
- TUI access to their email
    
- TUI access to their personal contacts
    
> [!NOTE]
> You can use only the Shell to modify the Outlook Voice Access TUI settings for UM-enabled users. 
  
For additional management tasks related to UM mailbox policies, see [UM mailbox policy procedures](../../voice-mail-unified-messaging/set-up-voice-mail/um-mailbox-policy-procedures.md).
  
## What do you need to know before you begin?

- Estimated time to complete: 5 minutes.
    
- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "UM mailbox policies" entry in the [Unified Messaging Permissions](http://technet.microsoft.com/library/d326c3bc-8f33-434a-bf02-a83cc26a5498.aspx) topic. 
    
- Before you perform this procedure, confirm that a UM dial plan has been created. For detailed steps, see [Create a UM dial plan](../../voice-mail-unified-messaging/connect-voice-mail-system/create-um-dial-plan.md).
    
- Before you perform this procedure, confirm that a UM mailbox policy has been created. For detailed steps, see [Create a UM mailbox policy](../../voice-mail-unified-messaging/set-up-voice-mail/create-um-mailbox-policy.md).
    
- For information about keyboard shortcuts that may apply to the procedures in this topic, see **Keyboard shortcuts in the Exchange admin center**.
    
> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612),[Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351).. 
  
## Use the Shell to modify TUI settings on a UM mailbox policy

This example sets TUI-related settings on a UM mailbox policy named  `MyUMMailboxPolicy`.
  
```
Set-UMMailbox -identity MyUMMailboxPolicy -AllowSubscriberAccess $true -AllowTUIAccessToCalendar $false -AllowTUIAccessToDirectory $false -AllowTUIAccessToEmail -$true -AllowTUIAccessToPersonalContacts $true
```


