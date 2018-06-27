---
title: "Authorize calls for a group of users"
ms.author: tonysmit
author: tonysmit
manager: scotv
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.service: exchange-online
localization_priority: Normal
ms.assetid: 7fc36757-868c-4bde-b793-6ae630da155c
description: ""
---

# Authorize calls for a group of users

You can enable dialing authorizations on a Unified Messaging (UM) mailbox policy. You can use dialing authorizations on a mailbox policy to prohibit authenticated Outlook Voice Access users that are linked to the UM mailbox policy from making in-country/region or international telephone calls, or outdialing. Outdialing happens when Unified Messaging places an outgoing call for a user after they've called in to an Outlook Voice Access phone number that is configured on a UM dial plan. When you configure a setting on a UM mailbox policy, that setting applies to all UM-enabled users linked with the UM mailbox policy.
  
For additional management tasks related to outdialing, see [Allowing users to make calls procedures](allow-users-to-make-calls-procedures.md).
  
## What do you need to know before you begin?

- Estimated time to complete: Less than 1 minute.
    
- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "UM mailbox policies" entry in the [Unified Messaging Permissions](http://technet.microsoft.com/library/d326c3bc-8f33-434a-bf02-a83cc26a5498.aspx) topic. 
    
- Before you perform these procedures, confirm that a UM mailbox policy has been created. For detailed steps, see [Create a UM mailbox policy](../../voice-mail-unified-messaging/set-up-voice-mail/create-um-mailbox-policy.md).
    
- Before you perform these procedures, confirm that in-country/region and international dialing rules have been created on a UM dial plan. For detailed steps, see [Create dialing rules for users](create-dialing-rules.md).
    
- For information about keyboard shortcuts that may apply to the procedures in this topic, see **Keyboard shortcuts in the Exchange admin center**.
    
> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612),[Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351).. 
  
## What do you want to do?

### Use the EAC to enable dialing authorizations on a UM mailbox policy for in-country/region dialing rule groups

1. In the EAC, navigate to **Unified Messaging** \> **UM dial plans**. In the list view, select the UM dial plan you want to change, and then click **Edit**![Edit icon](../../media/ITPro_EAC_EditIcon.gif).
    
2. On the **UM Dial Plan** page, under **UM Mailbox Policies**, select the UM mailbox policy for which you want to create a dialing authorization, and then click **Edit**![Edit icon](../../media/ITPro_EAC_EditIcon.gif).
    
3. On the **UM Mailbox Policy** page \> **Dialing authorization**, click **Add**![Add Icon](../../media/ITPro_EAC_AddIcon.gif) under **Authorized in-country/region dialing rule groups**.
    
4. On the **Select Dialing Rule Groups to Allow** page, select the dialing rule group, click **OK**, and then click **Save**.
    
### Use the EAC to enable dialing authorizations on a UM mailbox policy for international dialing rule groups

1. In the EAC, navigate to **Unified Messaging** \> **UM dial plans**. In the list view, select the UM dial plan you want to change, and then click **Edit**![Edit icon](../../media/ITPro_EAC_EditIcon.gif).
    
2. On the **UM Dial Plan** page, under **UM Mailbox Policies**, select the UM mailbox policy for which you want to create a dialing authorization, and then click **Edit**![Edit icon](../../media/ITPro_EAC_EditIcon.gif).
    
3. On the **UM Mailbox Policy** page \> **Dialing authorization**, click **Add**![Add Icon](../../media/ITPro_EAC_AddIcon.gif) under **Authorized international dialing rule groups**.
    
4. On the **Select Dialing Rule Groups to Allow** page, select the dialing rule group, click **OK**, and then click **Save**.
    
### Use the Shell to enable in-country/region and international dialing authorizations on a UM mailbox policy

This example enables the InCountry/RegionGroup1, InCountry/RegionGroup2, InternationalGroup1, and InternationalGroup2 dialing authorizations on a UM mailbox policy named  `MyUMMailboxPolicy`.
  
```
Set-UMMailboxPolicy -Identity MyUMMailboxPolicy -AllowedInCountryOrRegionGroups InCountry/RegionGroup1,InCountry/RegionGroup2 -AllowedInternationalGroups InternationalGroup1,InternationalGroup2
```


