---
title: "Disable selected features for Outlook Voice Access users"
ms.author: tonysmit
author: tonysmit
manager: scotv
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.service: exchange-online
localization_priority: Normal
ms.assetid: 37421edf-af60-4ca9-9e8b-262b8b851607
description: "Outlook Voice Access contains two interfaces: the telephone user interface (TUI) and the voice user interface (VUI). By default, when users dial in to Outlook Voice Access, they can access their calendar, email, and personal contacts, and search the directory. You can use the Shell to prevent users from accessing one or more of these features when they use Outlook Voice Access to access their mailbox. When you modify Outlook Voice Access features on a Unified Messaging (UM) mailbox policy, your changes affect all users who are associated with the UM mailbox policy."
---

# Disable selected features for Outlook Voice Access users

Outlook Voice Access contains two interfaces: the telephone user interface (TUI) and the voice user interface (VUI). By default, when users dial in to Outlook Voice Access, they can access their calendar, email, and personal contacts, and search the directory. You can use the Shell to prevent users from accessing one or more of these features when they use Outlook Voice Access to access their mailbox. When you modify Outlook Voice Access features on a Unified Messaging (UM) mailbox policy, your changes affect all users who are associated with the UM mailbox policy. 
  
You can disable users' access to the following Outlook Voice Access features on a UM mailbox policy:
  
- Calendar
    
- Directory
    
- Email
    
- Personal contacts
    
For additional management tasks related to UM mailbox policies, see [UM mailbox policy procedures](../../voice-mail-unified-messaging/set-up-voice-mail/um-mailbox-policy-procedures.md).
  
You can also use the Shell to disable Outlook Voice Access features on the mailbox of a single UM-enabled user. When you do this, the features will be disabled only for that user. Although you can't disable all the Outlook Voice Access features that are found on a UM mailbox policy for a single user, you can disable access to their calendar and to their email.
  
For additional management tasks related to UM mailboxes, see [Voice mail for users](../../voice-mail-unified-messaging/set-up-voice-mail/voice-mail-for-users.md).
  
> [!NOTE]
> You can use only the Shell to modify the Outlook Voice Access features for UM-enabled users on a UM mailbox policy or on the mailbox of a single UM-enabled user. 
  
## What do you need to know before you begin?

- Estimated time to complete each procedure: 5 minutes.
    
- Procedures in this topic require specific permissions. See each procedure for its permissions information.
    
- Before you perform these procedures, confirm that a UM dial plan has been created. For detailed steps, see [Create a UM dial plan](../../voice-mail-unified-messaging/connect-voice-mail-system/create-um-dial-plan.md).
    
- Before you perform these procedures, confirm that a UM mailbox policy has been created. For detailed steps, see [Create a UM mailbox policy](../../voice-mail-unified-messaging/set-up-voice-mail/create-um-mailbox-policy.md).
    
- Before you perform these procedures, confirm that a user has been enabled for UM. For detailed steps, see [Enable a user for voice mail](../../voice-mail-unified-messaging/set-up-voice-mail/enable-a-user-for-voice-mail.md).
    
- For information about keyboard shortcuts that may apply to the procedures in this topic, see **Keyboard shortcuts in the Exchange admin center**.
    
> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612),[Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351).. 
  
## What do you want to do?

### Use the Shell to disable selected Outlook Voice Access features for UM-enabled users on a UM mailbox policy

You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "UM mailbox policies" entry in the [Unified Messaging Permissions](http://technet.microsoft.com/library/d326c3bc-8f33-434a-bf02-a83cc26a5498.aspx) topic. 
  
This example prevents users associated with a UM mailbox policy named  `MyUMMailboxPolicy` from accessing their calendar when they dial in to Outlook Voice Access. 
  
```
Set-UMMailboxPolicy -id MyUMMailboxPolicy -AllowTUIAccessToCalendar $false
```

This example prevents users associated with the UM mailbox policy named  `MyUMMailboxPolicy` from accessing the directory when they dial in to Outlook Voice Access. 
  
```
Set-UMMailboxPolicy -id MyUMMailboxPolicy -AllowTUIAccessToDirectory $false
```

This example prevents users associated with the UM mailbox policy named  `MyUMMailboxPolicy` from accessing their email when they dial in to Outlook Voice Access. 
  
```
Set-UMMailboxPolicy -id MyUMMailboxPolicy -AllowTUIAccessToEmail -$false
```

This example prevents users associated with the UM mailbox policy named  `MyUMMailboxPolicy` from accessing personal contacts when they dial in to Outlook Voice Access. 
  
```
Set-UMMailboxPolicy -id MyUMMailboxPolicy -AllowTUIAccessToPersonalContacts $false
```

### Use the Shell to disable selected Outlook Voice Access features on the mailbox of a single UM-enabled user

You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "UM mailboxes" entry in the [Unified Messaging Permissions](http://technet.microsoft.com/library/d326c3bc-8f33-434a-bf02-a83cc26a5498.aspx) topic. 
  
This example disables access to the calendar on a UM mailbox named tony@contoso.com when the user dials in to Outlook Voice Access. 
  
```
Set-UMMailbox -id tony@contoso.com -TUIAccessToCalendarEnabled $false
```

This example disables access to email on a UM mailbox named tony@contoso.com when the user dials in to Outlook Voice Access. 
  
```
Set-UMMailbox -id tony@contoso.com -TUIAccessToEmailEnabled $false
```


