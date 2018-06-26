---
title: "Retrieve voice mail PIN information"
ms.author: tonysmit
author: tonysmit
manager: scotv
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 01517cca-99fe-46b2-b586-19e8d2707728
description: "You can retrieve PIN information for a user who is enabled for Unified Messaging (UM). After a user has been enabled for UM-enabled and a PIN is generated or created, the PIN is encrypted and stored in the user's mailbox."
---

# Retrieve voice mail PIN information

You can retrieve PIN information for a user who is enabled for Unified Messaging (UM). After a user has been enabled for UM-enabled and a PIN is generated or created, the PIN is encrypted and stored in the user's mailbox. 
  
When you retrieve PIN information for a UM-enabled user, the information returned to you is calculated by using the encrypted PIN data stored in the user's mailbox. This lets you view information from the user's mailbox and also indicates whether the user has been locked out of the mailbox.
  
For additional tasks related to PIN security, see [PIN security procedures](pin-security-procedures.md).
  
## What do you need to know before you begin?

- Estimated time to complete: Less than 1 minute.
    
- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "UM dial plans" entry in the [Unified Messaging Permissions](http://technet.microsoft.com/library/d326c3bc-8f33-434a-bf02-a83cc26a5498.aspx) topic. 
    
- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "UM mailboxes" entry in the [Unified Messaging Permissions](http://technet.microsoft.com/library/d326c3bc-8f33-434a-bf02-a83cc26a5498.aspx) topic. 
    
- Before you perform these procedures, confirm that a UM dial plan has been created. For detailed steps, see [Create a UM dial plan](../../voice-mail-unified-messaging/connect-voice-mail-system/create-um-dial-plan.md).
    
- Before you perform these procedures, confirm that a UM mailbox policy has been created. For detailed steps, see [Create a UM mailbox policy](../../voice-mail-unified-messaging/set-up-voice-mail/create-um-mailbox-policy.md).
    
- Before you perform these procedures, confirm that the user's mailbox has been UM-enabled. For detailed steps, see [Enable a user for voice mail](../../voice-mail-unified-messaging/set-up-voice-mail/enable-a-user-for-voice-mail.md).
    
- For information about keyboard shortcuts that may apply to the procedures in this topic, see **Keyboard shortcuts in the Exchange admin center**.
    
> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612),[Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351).. 
  
## What do you want to do?

### Use the EAC to retrieve PIN information for a UM-enabled user

1. In the EAC, navigate to **Recipients**. In the list view, select the user mailbox that you want to view.
    
2. In the details pane, under **Phone and Voice Features**, click **View details**. 
    
3. On the **UM Mailbox** page \> **UM mailbox settings**, view the **PIN status** for the user. On this page, you can also reset the voice mail PIN for the user. 
    
### Use the Shell to retrieve PIN information for a UM-enabled user

This example displays the user ID, whether a PIN is expired, whether the UM mailbox is locked out, and whether Tony is a first-time user.
  
```
Get-UMMailboxPIN -identity tony@contoso.com
```


