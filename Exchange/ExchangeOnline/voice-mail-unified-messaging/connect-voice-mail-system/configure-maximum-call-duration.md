---
title: "Configure the maximum call duration"
ms.author: tonysmit
author: tonysmit
manager: scotv
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.service: exchange-online
localization_priority: Normal
ms.assetid: 01aa40d2-f918-472b-bace-158222143484
description: "You can specify the maximum number of minutes that an incoming call can be connected to the system without being transferred to a valid extension number before the call is ended. For most organizations, this value should be set to the default: 30 minutes. This setting applies to all calls, including incoming Outlook Voice Access calls, voice calls internal to your organization, voice calls into Unified Messaging (UM) auto attendants, and fax calls placed from outside your organization."
---

# Configure the maximum call duration

You can specify the maximum number of minutes that an incoming call can be connected to the system without being transferred to a valid extension number before the call is ended. For most organizations, this value should be set to the default: 30 minutes. This setting applies to all calls, including incoming Outlook Voice Access calls, voice calls internal to your organization, voice calls into Unified Messaging (UM) auto attendants, and fax calls placed from outside your organization.
  
This value can be set to a number from 10 through 120. Setting this value too low can cause incoming calls to be disconnected before they're completed. For example, if your organization receives many large fax messages, you may want to consider increasing this value from the default so that all the pages of fax messages are received. 
  
For additional tasks related to UM dial plans, see [UM Dial Plan Procedures](http://technet.microsoft.com/library/1bda77c8-c4e2-4ae0-a001-76ae029bf843.aspx).
  
## What do you need to know before you begin?

- Estimated time to complete: Less than 1 minute.
    
- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "UM dial plans" entry in the [Unified Messaging Permissions](http://technet.microsoft.com/library/d326c3bc-8f33-434a-bf02-a83cc26a5498.aspx) topic. 
    
- Before you perform these procedures, confirm that a UM dial plan has been created. For detailed steps, see [Create a UM dial plan](create-um-dial-plan.md).
    
- For information about keyboard shortcuts that may apply to the procedures in this topic, see **Keyboard shortcuts in the Exchange admin center**.
    
> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612),[Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351).. 
  
## What do you want to do?

### Use the EAC to configure the maximum call duration

1. In the EAC, navigate to **Unified Messaging** \> **UM dial plans**.
    
2. In the list view, select the UM dial plan you want to modify, and then click **Edit**![Edit icon](../../media/ITPro_EAC_EditIcon.gif).
    
3. On the **UM dial plan** page, click **Configure**.
    
4. In **Settings**, under **Maximum call duration (minutes)**, enter the number in minutes.
    
5. Click **Save**.
    
### Use the Shell to configure the maximum call duration

This example sets the maximum call duration to 10 minutes on a UM dial plan named  `MyUMDialPlan`.
  
```
Set-UMDialPlan -identity MyUMDialPlan -MaxCallDuration 10
```


