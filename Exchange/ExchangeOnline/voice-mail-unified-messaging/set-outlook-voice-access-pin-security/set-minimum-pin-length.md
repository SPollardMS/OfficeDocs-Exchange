---
title: "Set the minimum PIN length for voice mail"
ms.author: tonysmit
author: tonysmit
manager: scotv
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.service: exchange-online
localization_priority: Normal
ms.assetid: b2ecab54-42e6-45af-8322-615cc1f68dd9
description: "You can configure the minimum PIN length for your Outlook Voice Access users who are enabled for Unified Messaging (UM). The PIN settings that you configure on a UM mailbox policy will apply to all UM-enabled users associated with the UM mailbox policy."
---

# Set the minimum PIN length for voice mail

You can configure the minimum PIN length for your Outlook Voice Access users who are enabled for Unified Messaging (UM). The PIN settings that you configure on a UM mailbox policy will apply to all UM-enabled users associated with the UM mailbox policy.
  
Outlook Voice Access is used by UM-enabled users to access their voice mail, email, calendar, and personal contact information located in their mailbox. However, before they can access their mailbox, they must enter a PIN so they can be authenticated by the voice mail system. 
  
> [!NOTE]
> If you change the minimum PIN length value, existing Outlook Voice Access users will be prompted to enter a new PIN that contains the new minimum number of digits before they can continue. The default is 6. 
  
For additional tasks related to Outlook Voice Access PIN security, see [PIN security procedures](pin-security-procedures.md).
  
## What do you need to know before you begin?

- Estimated time to complete: Less than 1 minute.
    
- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "UM mailbox policies" entry in the [Unified Messaging Permissions](http://technet.microsoft.com/library/d326c3bc-8f33-434a-bf02-a83cc26a5498.aspx) topic. 
    
- Before you perform these procedures, confirm that a UM dial plan has been created. For detailed steps, see [Create a UM dial plan](../../voice-mail-unified-messaging/connect-voice-mail-system/create-um-dial-plan.md).
    
- Before you perform these procedures, confirm that a UM mailbox policy has been created. For detailed steps, see [Create a UM mailbox policy](../../voice-mail-unified-messaging/set-up-voice-mail/create-um-mailbox-policy.md).
    
- For information about keyboard shortcuts that may apply to the procedures in this topic, see **Keyboard shortcuts in the Exchange admin center**.
    
> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612),[Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351).. 
  
## What do you want to do?

### Use the EAC to configure the minimum PIN length for Outlook Voice Access

1. In the EAC, navigate to **Unified Messaging** \> **UM dial plans**.
    
2. In the list view, select the dial plan you want to change, and then click **Edit**![Edit icon](../../media/ITPro_EAC_EditIcon.gif).
    
3. On the **UM dial plan** page, under **UM Mailbox Policies**, select the UM mailbox policy you want to change, and then click **Edit**![Edit icon](../../media/ITPro_EAC_EditIcon.gif).
    
4. Click **PIN policies**, and next to **Minimum PIN length**, enter a value between 4 and 24. 
    
5. Click **Save**.
    
### Use the Shell to configure the minimum PIN length for Outlook Voice Access

This example sets the minimum PIN length to 8 digits for Outlook Voice Access users who are associated with the UM mailbox policy named  `MyUMMailboxPolicy`.
  
```
Set-UMMailboxPolicy -Identity MyUMMailboxPolicy -MinPINLength 8
```

This example sets the minimum PIN length to 8 digits and sets the number of times a sign-in can fail before the user's PIN is reset to 3. This applies to UM-enabled users who are associated with the UM mailbox policy named  `MyUMMailboxPolicy`.
  
```
Set-UMMailboxPolicy -Identity MyUMMailboxPolicy -LogonFailuresBeforePINReset 3 -MinPINLength 8
```


