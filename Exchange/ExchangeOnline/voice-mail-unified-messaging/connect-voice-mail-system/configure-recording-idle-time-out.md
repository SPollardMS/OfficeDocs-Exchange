---
title: "Configure the recording idle time-out value"
ms.author: tonysmit
author: tonysmit
manager: scotv
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.service: exchange-online
localization_priority: Normal
ms.assetid: a7fb9a09-fde9-447d-ad2c-95598405e99b
description: "You can specify the number of seconds of silence that the system allows when a voice message is being recorded before the call is ended. For most organizations, this value should be set to the default of 5 seconds."
---

# Configure the recording idle time-out value

You can specify the number of seconds of silence that the system allows when a voice message is being recorded before the call is ended. For most organizations, this value should be set to the default of 5 seconds.
  
This value can be set from 2 through 10. Setting this value too low can cause the system to disconnect callers before they've finished leaving their voice messages. Setting this value too high allows lengthy silences in voice messages. 
  
For additional management tasks related to UM dial plans, see [UM Dial Plan Procedures](http://technet.microsoft.com/library/1bda77c8-c4e2-4ae0-a001-76ae029bf843.aspx).
  
## What do you need to know before you begin?

- Estimated time to complete: Less than 1 minute.
    
- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "UM dial plans" entry in the [Unified Messaging Permissions](http://technet.microsoft.com/library/d326c3bc-8f33-434a-bf02-a83cc26a5498.aspx) topic. 
    
- Before you perform these procedures, confirm that a UM dial plan has been created. For detailed steps, see [Create a UM dial plan](create-um-dial-plan.md).
    
- For information about keyboard shortcuts that may apply to the procedures in this topic, see **Keyboard shortcuts in the Exchange admin center**.
    
> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612),[Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351).. 
  
## What do you want to do?

### Use the EAC to configure the recording idle time-out value

1. In the EAC, navigate to **Unified Messaging** \> **UM dial plans**.
    
2. In the list view, select the UM dial plan you want to modify, and then click **Edit**![Edit icon](../../media/ITPro_EAC_EditIcon.gif).
    
3. On the **UM dial plan** page, click **Configure**.
    
4. In **Settings**, under **Recording idle time out (seconds)**, enter the number in seconds.
    
5. Click **Save**.
    
### Use the Shell to configure the recording idle time-out value

This example sets the recording idle time-out value to 10 for a UM dial plan named  `MyUMDialPlan`.
  
```
Set-UMDialPlan -identity MyUMDialPlan -RecordingIdleTimeout 10
```


