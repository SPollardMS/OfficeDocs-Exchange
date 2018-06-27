---
title: "Configure Voice Mail Preview partner services for users"
ms.author: tonysmit
author: tonysmit
manager: scotv
ms.date: 12/9/2016
ms.audience: ITPro
ms.topic: article
ms.service: exchange-online
localization_priority: Normal
ms.assetid: 7bb914ca-5502-4e64-bae5-555034138d8a
description: "You can configure a Voice Mail Preview partner on a Unified Messaging (UM) mailbox policy. After you've configured Voice Mail Preview partner settings, such as the Voice Mail Preview partner ID and Voice Mail Preview partner address, on a UM mailbox policy, the settings you configure will apply to all UM-enabled users who are linked with that mailbox policy."
---

# Configure Voice Mail Preview partner services for users

You can configure a Voice Mail Preview partner on a Unified Messaging (UM) mailbox policy. After you've configured Voice Mail Preview partner settings, such as the Voice Mail Preview partner ID and Voice Mail Preview partner address, on a UM mailbox policy, the settings you configure will apply to all UM-enabled users who are linked with that mailbox policy.
  
> [!NOTE]
> You must use the Shell to configure a Voice Mail Preview partner. 
  
For additional management tasks related to UM mailbox policies, see [UM mailbox policy procedures](../../voice-mail-unified-messaging/set-up-voice-mail/um-mailbox-policy-procedures.md).
  
## What do you need to know before you begin?

- Estimated time to complete: 5 minutes.
    
- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "UM mailbox policies" entry in the [Unified Messaging Permissions](http://technet.microsoft.com/library/d326c3bc-8f33-434a-bf02-a83cc26a5498.aspx) topic. 
    
- Before you perform these procedures, confirm that a UM dial plan has been created. For detailed steps, see [Create a UM dial plan](../../voice-mail-unified-messaging/connect-voice-mail-system/create-um-dial-plan.md).
    
- Before you perform these procedures, confirm that a UM mailbox policy has been created. For detailed steps, see [Create a UM mailbox policy](../../voice-mail-unified-messaging/set-up-voice-mail/create-um-mailbox-policy.md).
    
- For information about keyboard shortcuts that may apply to the procedures in this topic, see **Keyboard shortcuts in the Exchange admin center**.
    
> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612),[Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351).. 
  
## How do you do this?

### Step 1: Sign up with a partner service

To find the list of certified partners and detailed instructions for how to sign up, see [Voice Mail Preview advisor](voice-mail-preview-advisor.md) or see the [Microsoft PinPoint](https://go.microsoft.com/fwlink/p/?LinkId=281966) website. After you've signed up, the Voice Mail Preview partner will provide you a partner ID and the SMTP address to use to forward the voice messages. 
  
In Step 2, you'll apply the Partner ID and SMTP address you acquired in Step 1 to the required UM mailbox policies.
  
### Step 2: Set the Voice Mail Preview partner address and ID

This example sets the Voice Mail Preview partner address to exumvmp@fabrikam.com and the Voice Mail Preview partner ID to CON123-2010 on a UM mailbox policy named  _MyUMMailboxPolicy_.
  
```
Set-UMMailboxPolicy -identity MyUMMailboxPolicy -VoiceMailPreviewPartnerAddress exumvmp@fabrikam.com
-VoiceMailPreviewPartnerAssignedID CON123-2010
```

### Step 3: Configure advanced Voice Mail Preview partner settings

If the partner requires custom settings, you may want to set two additional parameters for a Voice Mail Preview partner as follows:
  
-  _VoiceMailPreviewPartnerMaxMessageDuration_
    
-  _VoiceMailPreviewPartnerMaxDeliveryDelay_
    
This example sets the maximum message duration to 300 seconds (5 minutes) and the maximum delivery delay to 600 seconds (10 minutes) on a UM mailbox policy named  _MyUMMailboxPolicy_.
  
```
Set-UMMailboxPolicy -identity MyUMMailboxPolicy -VoiceMailPreviewPartnerMaxMessageDuration 300 -VoiceMailPreviewPartnerMaxDeliveryDelay 600
```

### Step 4: Assign a UM-enabled user to the UM mailbox policy for a Voice Mail Preview partner

If you want to configure the Voice Mail Preview partner service for some, but not all, UM-enabled users in a UM dial plan, you must create a new UM mailbox policy and configure the partner settings. When you've finished, you can apply the new policy to selected UM-enabled users. For more information about how to assign a UM-enabled user to a UM mailbox policy, see the following topics:
  
- [Assign a UM mailbox policy](../../voice-mail-unified-messaging/set-up-voice-mail/assign-um-mailbox-policy.md)
    
- [Set-UMMailbox](http://technet.microsoft.com/library/dd7b429d-53a8-46dd-b16b-3a8ca8424bbc.aspx)
    
For more information about the Voice Mail Preview partner program, see [Voice Mail Preview advisor](voice-mail-preview-advisor.md).
  

