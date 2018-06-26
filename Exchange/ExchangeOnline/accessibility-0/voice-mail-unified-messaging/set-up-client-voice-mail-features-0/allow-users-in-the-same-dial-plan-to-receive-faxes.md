---
title: "Allow users in the same dial plan to receive faxes"
ms.author: tonysmit
author: tonysmit
manager: scotv
ms.date: 12/9/2016
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: cb245028-0b86-4171-879e-934dd35fa626
description: "You can enable all users who are linked with a Unified Messaging (UM) dial plan to receive fax messages in their mailboxes. By default, users who are enabled for Unified Messaging and are linked with a UM dial plan can receive fax messages. To allow UM-enabled users to receive fax messages in their mailboxes, the dial plan must be configured to accept incoming fax calls. You must also enable faxing on the UM mailbox policy and for the user. By default, faxing is enabled on dial plans, UM mailbox policies, and for users. However, there may be times when these default settings have changed and UM-enabled users can't receive fax messages."
---

# Allow users in the same dial plan to receive faxes

You can enable all users who are linked with a Unified Messaging (UM) dial plan to receive fax messages in their mailboxes. By default, users who are enabled for Unified Messaging and are linked with a UM dial plan can receive fax messages. To allow UM-enabled users to receive fax messages in their mailboxes, the dial plan must be configured to accept incoming fax calls. You must also enable faxing on the UM mailbox policy and for the user. By default, faxing is enabled on dial plans, UM mailbox policies, and for users. However, there may be times when these default settings have changed and UM-enabled users can't receive fax messages. 
  
If you prevent fax messages from being received on a dial plan, all users who are associated with the dial plan won't be able to receive fax messages, even if you configure an individual user's properties to allow them to receive fax messages. Enabling or disabling faxing on a UM dial plan takes precedence over the settings for faxing on a UM mailbox policy or an individual UM-enabled user.
  
> [!NOTE]
> You can use the EAC to configure fax settings on a UM mailbox policy. However, you must use the Shell to configure fax settings on dial plans or for individual users. 
  
For more information about fax partners, see [Microsoft PinPoint for Fax Partners](https://go.microsoft.com/fwlink/?LinkId=190238).
  
For additional management tasks related to faxing, see [Faxing procedures](faxing-procedures.md).
  
## What do you need to know before you begin?

- Estimated time to complete: Less than 1 minute.
    
- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "UM dial plans" entry in the [Unified Messaging Permissions](http://technet.microsoft.com/library/d326c3bc-8f33-434a-bf02-a83cc26a5498.aspx) topic. 
    
- Before you perform these procedures, confirm that a UM dial plan has been created. For detailed steps, see [Create a UM dial plan](../../voice-mail-unified-messaging/connect-voice-mail-system/create-um-dial-plan.md).
    
- For information about keyboard shortcuts that may apply to the procedures in this topic, see **Keyboard shortcuts in the Exchange admin center**.
    
> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612),[Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351).. 
  
## Use the Shell to allow users who are linked to a dial plan to receive faxes

This example enables UM-enabled users who are linked with the UM dial plan named  `MyUMDialPlan` to receive incoming faxes. 
  
```
Set-UMDialPlan -Identity MyUMDialPlan -FaxEnabled $true
```


