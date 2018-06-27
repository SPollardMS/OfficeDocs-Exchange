---
title: "Call answering rules in the same mailbox policy"
ms.author: tonysmit
author: tonysmit
manager: scotv
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.service: exchange-online
localization_priority: Normal
ms.assetid: e44acaa6-d5a8-41e8-94aa-100be0bd6391
description: "You can allow users who are associated with a Unified Messaging (UM) mailbox policy to configure call answering rules, or prevent them from doing so. If the option to configure call answering rules is disabled on a UM dial plan, the Call Answering Rules feature won't be available to UM-enabled users associated with the UM mailbox policy. The default setting is enabled."
---

# Call answering rules in the same mailbox policy

You can allow users who are associated with a Unified Messaging (UM) mailbox policy to configure call answering rules, or prevent them from doing so. If the option to configure call answering rules is disabled on a UM dial plan, the Call Answering Rules feature won't be available to UM-enabled users associated with the UM mailbox policy. The default setting is enabled.
  
For additional management tasks related to allowing users to forward calls, see [Forwarding calls procedures](forwarding-calls-procedures.md).
  
## What do you need to know before you begin?

- Estimated time to complete: 2 minutes.
    
- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "UM mailbox policies" entry in the [Unified Messaging Permissions](http://technet.microsoft.com/library/d326c3bc-8f33-434a-bf02-a83cc26a5498.aspx) topic. 
    
- Before you perform these procedures, confirm that a UM dial plan has been created. For detailed steps, see [Create a UM dial plan](../../voice-mail-unified-messaging/connect-voice-mail-system/create-um-dial-plan.md).
    
- Before you perform these procedures, confirm that a UM mailbox policy has been created. For detailed steps, see [Create a UM mailbox policy](../../voice-mail-unified-messaging/set-up-voice-mail/create-um-mailbox-policy.md).
    
- For information about keyboard shortcuts that may apply to the procedures in this topic, see **Keyboard shortcuts in the Exchange admin center**.
    
> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612),[Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351).. 
  
## What do you want to do?

### Use the EAC to enable or disable call answering rules on a UM mailbox policy

1. In the EAC, navigate to **Unified Messaging** \> **UM dial plans**. In the list view, select the UM dial plan you want to change, and then click **Edit**![Edit icon](../../media/ITPro_EAC_EditIcon.gif).
    
2. Under **UM Mailbox Policies**, select the UM mailbox policy you want to manage, and then click **Edit**![Edit icon](../../media/ITPro_EAC_EditIcon.gif). 
    
3. On the **UM Mailbox Policy** page, select or clear the check box next to **Allow users to configure call answering rules**.
    
4. Click **Save**.
    
### Use the Shell to enable or disable call answering rules on a UM mailbox policy

This example allows users who are associated with the UM mailbox policy  `MyUMMailboxPolicy` to create call answering rules. 
  
```
Set-UMMailboxPolicy -identity MyUMMailboxPolicy -AllowCallAnsweringRules $true
```

This example prevents users who are associated with the UM mailbox policy  `MyUMMailboxPolicy` from creating call answering rules. 
  
```
Set-UMMailboxPolicy -identity MyUMMailboxPolicy -AllowCallAnsweringRules $false
```


