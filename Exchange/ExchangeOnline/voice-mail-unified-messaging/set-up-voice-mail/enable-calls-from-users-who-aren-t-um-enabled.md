---
title: "Enable calls from users who aren't UM-enabled"
ms.author: tonysmit
author: tonysmit
manager: scotv
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.service: exchange-online
localization_priority: Normal
ms.assetid: 3c39c6df-6d7a-469f-b92b-85b3f14bad31
description: "You can enable or disable calls from users who aren't enabled for Unified Messaging (UM). By default, Unified Messaging allows incoming calls from unauthenticated callers through an auto attendant to be transferred to UM-enabled users. With this option enabled, users from outside an organization can transfer calls to UM-enabled users."
---

# Enable calls from users who aren't UM-enabled

You can enable or disable calls from users who aren't enabled for Unified Messaging (UM). By default, Unified Messaging allows incoming calls from unauthenticated callers through an auto attendant to be transferred to UM-enabled users. With this option enabled, users from outside an organization can transfer calls to UM-enabled users. 
  
If this setting has been disabled for a UM-enabled user, the user's mailbox can still be located using a directory search. However, if an external caller tries to transfer to the user, the system says, "I'm sorry, I am unable to transfer the call to this user." The caller is then transferred to the operator, if an operator has been configured on the auto attendant. If no operator has been configured on the auto attendant, the call is transferred to a dial plan operator, if one has been configured. If no operator extension has been configured on the speech-enabled auto attendant, the dual tone multi-frequency (DTMF) fallback auto attendant, or the dial plan, the system responds by saying, "Sorry. Neither the operator or the touchtone service are available." 
  
For additional management tasks related to users who are enabled for voice mail, see [Voice mail-enabled user procedures](voice-mail-enabled-user-procedures.md).
  
## What do you need to know before you begin?

- Estimated time to complete: Less than 1 minute.
    
- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "UM mailboxes" entry in the [Unified Messaging Permissions](http://technet.microsoft.com/library/d326c3bc-8f33-434a-bf02-a83cc26a5498.aspx) topic. 
    
- Before you perform this procedure, confirm that a UM dial plan has been created. For detailed steps, see [Create a UM dial plan](../../voice-mail-unified-messaging/connect-voice-mail-system/create-um-dial-plan.md).
    
- Before you perform this procedure, confirm that a UM mailbox policy has been created. For detailed steps, see [Create a UM mailbox policy](create-um-mailbox-policy.md).
    
- Before you perform this procedure, confirm that the user's mailbox has been UM-enabled. For detailed steps, see [Enable a user for voice mail](enable-a-user-for-voice-mail.md).
    
- For information about keyboard shortcuts that may apply to the procedures in this topic, see **Keyboard shortcuts in the Exchange admin center**.
    
> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612),[Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351).. 
  
## Use the Shell to enable calls from users who aren't UM-enabled

This example allows Tony Smith to receive voice calls from callers who aren't UM-enabled.
  
```
Set UMMailbox -Identity tony@contoso.com -AllowUMCallsFromNonUsers SearchEnabled
```


