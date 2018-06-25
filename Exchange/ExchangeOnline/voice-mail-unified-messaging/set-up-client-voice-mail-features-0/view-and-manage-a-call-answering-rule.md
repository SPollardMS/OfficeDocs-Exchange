---
title: "View and manage a call answering rule"
ms.author: tonysmit
author: tonysmit
manager: scotv
ms.date: 4/8/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: de6d9fa1-7878-49a9-bddb-e3317d94f4d8
description: "You can use the Shell to view or configure one or more call answering rules for a user. You can also use the Get-UMCallAnsweringRule or Set-UMCallAnsweringRule cmdlets in an Exchange Management Shell script to view or manage call answering rules for multiple users."
---

# View and manage a call answering rule

You can use the Shell to view or configure one or more call answering rules for a user. You can also use the **Get-UMCallAnsweringRule** or **Set-UMCallAnsweringRule** cmdlets in an Exchange Management Shell script to view or manage call answering rules for multiple users. 
  
Call answering rules are applied to incoming calls similar to the way Inbox rules are applied to incoming email messages. By default, when a user is enabled for Unified Messaging (UM), no call answering rules are configured. Even so, incoming calls are answered by the mail system and callers are prompted to leave a voice message.
  
> [!IMPORTANT]
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
  
## What do you want to do?

### Use the Shell to view a call answering rule

You can retrieve the properties for a single call answering rule or a list of call answering rules in a UM-enabled user's mailbox.
  
This example returns a formatted list of call answering rules in a user's UM-enabled mailbox.
  
```
Get-UMCallAnsweringRule-Mailbox tonysmith | Format-List
```

This example displays the properties of the call answering rule  `MyUMCallAnsweringRule`.
  
```
Get-UMCallAnsweringRule -Identity MyUMCallAnsweringRule
```

### Use the Shell to configure a call answering rule

You can configure or change a call answering rule that's stored in a user's mailbox. You can specify the following conditions:
  
- Who the incoming call is from
    
- Time of day
    
- Calendar free/busy status
    
- Whether automatic replies are turned on for email
    
You can also specify the following actions:
  
- Find me
    
- Transfer the caller to someone else
    
- Leave a voice message
    
This example sets the priority to 2 on the call answering rule  `MyCallAnsweringRule` that exists in the mailbox for Tony Smith. 
  
```
Set-UMCallAnsweringRule -Mailbox tonysmith -Name MyCallAnsweringRule -Priority 2

```

This example performs the following actions on the call answering rule  `MyCallAnsweringRule` in the mailbox for Tony Smith: 
  
- Sets the call answering rule to two caller IDs.
    
- Sets the priority of the call answering rule to 2.
    
- Sets the call answering rule to allow callers to interrupt the greeting.
    
```
Set-UMCallAnsweringRule -Name MyCallAnsweringRule -CallerIds "1,4255550100,,","1,4255550123,," -Priority 2 -CallersCanInterruptGreeting $true -Mailbox tonysmith
```

This example changes the free/busy status to Away on the call answering rule  `MyCallAnsweringRule` in the mailbox for Tony Smith and sets the priority to 2. 
  
```
Set-UMCallAnsweringRule -Name MyCallAnsweringRule -Priority 2 -Mailbox tonysmith@contoso.com -ScheduleStatus 0x8
```


