---
title: "Configure the limit on personal greetings for Outlook Voice Access users"
ms.author: tonysmit
author: tonysmit
manager: scotv
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: d400f250-0f55-45f5-9918-5f1d7819fbdf
description: "The Limit on personal greetings (minutes) setting enables you to enter the maximum number of minutes that users associated with the Unified Messaging (UM) mailbox policy can use to record their voice mail greetings. This setting applies to both their standard voice mail and their Out of Office voice mail greetings. By default, the maximum greeting duration is set to 5 minutes. However, you can configure the maximum greeting duration to any setting between 1 and 10 minutes."
---

# Configure the limit on personal greetings for Outlook Voice Access users

The **Limit on personal greetings (minutes)** setting enables you to enter the maximum number of minutes that users associated with the Unified Messaging (UM) mailbox policy can use to record their voice mail greetings. This setting applies to both their standard voice mail and their Out of Office voice mail greetings. By default, the maximum greeting duration is set to 5 minutes. However, you can configure the maximum greeting duration to any setting between 1 and 10 minutes. 
  
For additional management tasks related to UM mailbox policies, see [UM mailbox policy procedures](../../voice-mail-unified-messaging/set-up-voice-mail/um-mailbox-policy-procedures.md).
  
## What do you need to know before you begin?

- Estimated time to complete: Less than 1 minute.
    
- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "UM mailbox policies" entry in the [Unified Messaging Permissions](http://technet.microsoft.com/library/d326c3bc-8f33-434a-bf02-a83cc26a5498.aspx) topic. 
    
- Before you perform these procedures, confirm that a UM dial plan has been created. For detailed steps, see [Create a UM dial plan](../../voice-mail-unified-messaging/connect-voice-mail-system/create-um-dial-plan.md).
    
- Before you perform these procedures, confirm that a UM mailbox policy has been created. For detailed steps, see [Create a UM mailbox policy](../../voice-mail-unified-messaging/set-up-voice-mail/create-um-mailbox-policy.md).
    
- For information about keyboard shortcuts that may apply to the procedures in this topic, see **Keyboard shortcuts in the Exchange admin center**.
    
> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612),[Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351).. 
  
## What do you want to do?

### Use the EAC to change the maximum greeting duration

1. In the EAC, navigate to **Unified Messaging** \> **UM dial plans**. In the list view, select the UM dial plan you want to modify, and then on the toolbar, click **Edit**![Edit icon](../../media/ITPro_EAC_EditIcon.gif).
    
2. On the **UM Dial Plan** page, under **UM Mailbox Policies**, select the UM mailbox policy you want to manage, and then on the toolbar, click **Edit**![Edit icon](../../media/ITPro_EAC_EditIcon.gif).
    
3. On the **UM mailbox policy** page \> **General**, under **Limit on personal greetings (minutes)**, enter the length of time, in minutes, allowed for personal greetings for voice mail users.
    
4. Click **Save**.
    
### Use the Shell to change the maximum greeting duration

This example configures the maximum greeting duration on the UM mailbox policy  `MyUMMailboxPolicy` to 3 minutes. 
  
```
Set-UMMailboxPolicy -identity MyUMMailboxPolicy MaxGreetingDuration 3
```


