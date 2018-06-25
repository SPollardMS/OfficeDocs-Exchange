---
title: "Remove a call answering rule for a user"
ms.author: tonysmit
author: tonysmit
manager: scotv
ms.date: 4/8/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 1da3c5bc-7227-4b37-96f6-67ceefc084d5
description: "You can use the Shell to remove one or more call answering rules for a user. You can also use the Remove-UMCallAnsweringRule cmdlet in an Exchange Management Shell script to remove one or more call answering rules for multiple users."
---

# Remove a call answering rule for a user

You can use the Shell to remove one or more call answering rules for a user. You can also use the **Remove-UMCallAnsweringRule** cmdlet in an Exchange Management Shell script to remove one or more call answering rules for multiple users. 
  
Call answering rules are applied to incoming calls similar to the way Inbox rules are applied to incoming email messages. By default, when a user is enabled for Unified Messaging (UM), no call answering rules are configured. Even so, incoming calls are answered by the mail system and callers are prompted to leave a voice message. 
  
> [!NOTE]
> Users that are UM-enabled can sign in to Outlook Web App to create, manage, and remove call answering rules. 
  
For additional management tasks related to Call Answering Rules, see [Forwarding calls procedures](forwarding-calls-procedures.md).
  
## What do you need to know before you begin?

- Estimated time to complete: Less than 1 minute.
    
- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "UM call answering rules" entry in the [Unified Messaging Permissions](http://technet.microsoft.com/library/d326c3bc-8f33-434a-bf02-a83cc26a5498.aspx) topic. 
    
- Before you perform this procedure, confirm that a UM dial plan has been created. For detailed steps, see [Create a UM dial plan](../../voice-mail-unified-messaging/connect-voice-mail-system/create-um-dial-plan.md).
    
- Before you perform this procedure, confirm that a UM mailbox policy has been created. For detailed steps, see [Create a UM mailbox policy](../../voice-mail-unified-messaging/set-up-voice-mail/create-um-mailbox-policy.md).
    
- Before you perform this procedure, confirm that the user's mailbox has been UM-enabled. For detailed steps, see [Enable a user for voice mail](../../voice-mail-unified-messaging/set-up-voice-mail/enable-a-user-for-voice-mail.md).
    
- You can only use the Shell to perform this procedure. To learn how to open the Exchange Management Shell in your on-premises Exchange organization, see **Open the Shell**. To learn how to use Windows PowerShell to connect to Exchange Online, see [Connect to Exchange Online PowerShell](https://go.microsoft.com/fwlink/p/?linkid=396554).
    
- For information about keyboard shortcuts that may apply to the procedures in this topic, see **Keyboard shortcuts in the Exchange admin center**.
    
> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612),[Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351).. 
  
## Use the Shell to remove a call answering rule

This example removes the call answering rule  `MyUMCallAnsweringRule` from a user's mailbox. The user's mailbox is the mailbox of the user running the cmdlet. 
  
```
Remove-UMCallAnsweringRule -Identity MyUMCallAnsweringRule
```

This example removes the call answering rule  `MyUMCallAnsweringRule` from the mailbox of Tony Smith. 
  
```
Remove-UMCallAnsweringRule -Identity MyUMCallAnsweringRule -Mailbox tonysmith
```


