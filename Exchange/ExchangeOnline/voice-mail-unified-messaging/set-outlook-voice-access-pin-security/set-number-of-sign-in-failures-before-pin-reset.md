---
title: "Set the number of sign-in failures before a voice mail PIN is reset"
ms.author: tonysmit
author: tonysmit
manager: scotv
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.service: exchange-online
localization_priority: Normal
ms.assetid: 4de38499-0a6f-4f00-8697-eeff805d7266
description: "You can configure the number of sign-in failures allowed before the PIN is reset for an Outlook Voice Access user to a value from 1 through 998. The default is 5. The number of sign-in failures allowed before a PIN is reset is configured on a Unified Messaging (UM) mailbox policy and applies to all Outlook Voice Access users associated with the UM mailbox policy."
---

# Set the number of sign-in failures before a voice mail PIN is reset

You can configure the number of sign-in failures allowed before the PIN is reset for an Outlook Voice Access user to a value from 1 through 998. The default is 5. The number of sign-in failures allowed before a PIN is reset is configured on a Unified Messaging (UM) mailbox policy and applies to all Outlook Voice Access users associated with the UM mailbox policy.
  
> [!NOTE]
> You can increase security by configuring the **Number of sign-in failures before PIN reset** setting to a number less than 5. You decrease security if you configure it to a number more than 5. 
  
For additional tasks related to Outlook Voice Access PIN security, see [PIN security procedures](pin-security-procedures.md).
  
## What do you need to know before you begin?

- Estimated time to complete: 3 minutes.
    
- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "UM mailbox policies" entry in the [Unified Messaging Permissions](http://technet.microsoft.com/library/d326c3bc-8f33-434a-bf02-a83cc26a5498.aspx) topic. 
    
- Before you perform these procedures, confirm that a UM dial plan has been created. For detailed steps, see [Create a UM dial plan](../../voice-mail-unified-messaging/connect-voice-mail-system/create-um-dial-plan.md).
    
- Before you perform these procedures, confirm that a UM mailbox policy has been created. For detailed steps, see [Create a UM mailbox policy](../../voice-mail-unified-messaging/set-up-voice-mail/create-um-mailbox-policy.md).
    
- For information about keyboard shortcuts that may apply to the procedures in this topic, see **Keyboard shortcuts in the Exchange admin center**.
    
> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612),[Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351).. 
  
## What do you want to do?

### Use the EAC to configure the number of sign-in failures before a PIN is reset

1. In the EAC, navigate to **Unified Messaging** \> **UM dial plans**.
    
2. In the list view, select the UM dial plan you want to change, and then click **Edit**![Edit icon](../../media/ITPro_EAC_EditIcon.gif).
    
3. On the **UM dial plan** page, under **UM Mailbox Policies**, select the UM mailbox policy you want to change, and then click **Edit**![Edit icon](../../media/ITPro_EAC_EditIcon.gif).
    
4. Click **PIN policies**, and next to **Number of sign-in failures before PIN reset**, enter a value between 0 and 999. 
    
5. Click **Save**.
    
### Use the Shell to configure the number of sign-in failures before a PIN is reset

This example sets the number of sign-in failures before the user's PIN is reset to 3 for UM-enabled users who are associated with a UM mailbox policy named  `MyUMMailboxPolicy`.
  
```
Set-UMMailboxPolicy -Identity MyUMMailboxPolicy -LogonFailuresBeforePINReset 3
```

This example sets the number of sign-in failures before the user's PIN is reset to 3, the maximum number of sign-in attempts to 5, and the minimum PIN length to 9 for UM-enabled users who are associated with a UM mailbox policy named  `MyUMMailboxPolicy`.
  
```
Set-UMMailboxPolicy -Identity MyUMMailboxPolicy -LogonFailuresBeforePINReset 3 -MaxLogonAttempts 5 -MinPINLength 9
```


