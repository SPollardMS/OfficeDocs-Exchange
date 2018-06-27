---
title: "Call answering rules"
ms.author: tonysmit
author: tonysmit
manager: scotv
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.service: exchange-online
localization_priority: Normal
ms.assetid: 81863440-8b21-4523-bdab-6a2311889a0d
description: "You can specify whether you want individual users to be able to create and manage their own call answering rules by configuring their mailbox properties. By default, they can create call answering rules."
---

# Call answering rules

You can specify whether you want individual users to be able to create and manage their own call answering rules by configuring their mailbox properties. By default, they can create call answering rules.
  
You can enable or disable Call Answering Rules for multiple users that are enabled for Unified Messaging (UM) by configuring Call Answering Rules on a UM dial plan or UM mailbox policy. 
  
> [!NOTE]
> You can't use the EAC to configure this feature. You must use the Shell to enable or disable Call Answering Rules for a voice mail user. 
  
For additional management tasks related to allowing users to forward calls, see [Forwarding calls procedures](forwarding-calls-procedures.md).
  
## What do you need to know before you begin?

- Estimated time to complete: Less than 1 minute.
    
- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "UM mailboxes" entry in the [Unified Messaging Permissions](http://technet.microsoft.com/library/d326c3bc-8f33-434a-bf02-a83cc26a5498.aspx) topic. 
    
- Before you perform this procedure, confirm that a UM dial plan has been created. For detailed steps, see [Create a UM dial plan](../../voice-mail-unified-messaging/connect-voice-mail-system/create-um-dial-plan.md).
    
- Before you perform this procedure, confirm that a UM mailbox policy has been created. For detailed steps, see [Create a UM mailbox policy](../../voice-mail-unified-messaging/set-up-voice-mail/create-um-mailbox-policy.md).
    
- Before you perform this procedure, confirm that the user's mailbox has been UM-enabled. For detailed steps, see [Enable a user for voice mail](../../voice-mail-unified-messaging/set-up-voice-mail/enable-a-user-for-voice-mail.md).
    
- For information about keyboard shortcuts that may apply to the procedures in this topic, see **Keyboard shortcuts in the Exchange admin center**.
    
> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612),[Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351).. 
  
## Use the Shell to enable or disable call answering rules for a UM-enabled user

This example enables Call Answering Rules for the user tony@contoso.com. 
  
```
Set-UMMailbox -Identity tony@contoso.com -CallAnsweringRulesEnabled $true
```

This example disables Call Answering Rules for the user tony@contoso.com. 
  
```
Set-UMMailbox -Identity tony@contoso.com -CallAnsweringRulesEnabled $false
```


