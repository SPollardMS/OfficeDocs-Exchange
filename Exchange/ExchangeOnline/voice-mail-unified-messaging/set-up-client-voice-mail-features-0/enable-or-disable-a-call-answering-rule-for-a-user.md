---
title: "Enable or disable a call answering rule for a user"
ms.author: tonysmit
author: tonysmit
manager: scotv
ms.date: 4/8/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: f9e40ac3-117f-44f6-9ab1-dc9f4c72e8ac
description: "You can use the Shell to enable or disable one or more call answering rules for a user. You can also use the Enable-UMCallAnsweringRule or Disable-UMCallAnsweringRule cmdlets in an Exchange Management Shell script to enable or disable one or more call answering rules for multiple users."
---

# Enable or disable a call answering rule for a user

You can use the Shell to enable or disable one or more call answering rules for a user. You can also use the **Enable-UMCallAnsweringRule** or **Disable-UMCallAnsweringRule** cmdlets in an Exchange Management Shell script to enable or disable one or more call answering rules for multiple users. 
  
Call answering rules are applied to incoming calls similar to the way Inbox rules are applied to incoming email messages. By default, when a user is enabled for Unified Messaging (UM), no call answering rules are configured. Even so, incoming calls are answered by the mail system and callers are prompted to leave a voice message. 
  
For additional management tasks related to call answering rules, see [Forwarding calls procedures](forwarding-calls-procedures.md).
  
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

### Use the Shell to enable a call answering rule

When a call answering rule is created, it's enabled. You can use the Shell to enable a call answering rule that was previously disabled. Enabling a call answering rule enables the **Enable-UMCallAnsweringRule** cmdlet to retrieve the call answering rule, including the conditions and actions for a specified call answering rule. 
  
This example enables the call answering rule  `MyUMCallAnsweringRule` in the mailbox for Tony Smith. 
  
```
Enable-UMCallAnsweringRule -Identity MyUMCallAnsweringRule -Mailbox tonysmith
```

The example uses the  _WhatIf_ switch to test whether the call answering rule  `MyUMCallAnsweringRule` in the mailbox for Tony Smith is ready to be enabled and if there are any errors within the command. 
  
```
Enable-UMCallAnsweringRule -Identity MyUMCallAnsweringRule -Mailbox tonysmith -WhatIf
```

This example enables the call answering rule  `MyUMCallAnsweringRule` in the mailbox for Tony Smith and prompts the signed-in user to confirm that the call answering rule is to be enabled. 
  
```
Enable-UMCallAnsweringRule -Identity MyUMCallAnsweringRule -Mailbox tonysmith -Confirm
```

### Use the Shell to disable a call answering rule

Disabling a call answering rule prevents it from being retrieved and processed when an incoming call is received. When you create a call answering rule, you should disable it while you're setting up conditions and actions. This prevents the call answering rule from being processed when an incoming call is received before you've correctly configured the call answering rule.
  
This example disables the call answering rule  `MyUMCallAnsweringRule` in the mailbox for Tony Smith. 
  
```
Disable -UMCallAnsweringRule -Identity MyUMCallAnsweringRule -Mailbox tonysmith
```

This example uses the  _WhatIf_ switch to test whether the call answering rule  `MyUMCallAnsweringRule` in the mailbox for Tony Smith is ready to be disabled and if there are any errors within the command. 
  
```
Disable -UMCallAnsweringRule -Identity MyUMCallAnsweringRule -Mailbox tonysmith -WhatIf
```

This example disables the call answering rule  `MyUMCallAnsweringRule` in the mailbox for Tony Smith and prompts the signed-in user to confirm that they're disabling the call answering rule. 
  
```
Disable-UMCallAnsweringRule -Identity MyUMCallAnsweringRule -Mailbox tonysmith -Confirm
```


