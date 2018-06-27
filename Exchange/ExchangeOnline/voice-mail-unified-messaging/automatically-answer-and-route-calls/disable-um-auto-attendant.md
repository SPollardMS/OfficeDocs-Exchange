---
title: "Disable a UM auto attendant"
ms.author: tonysmit
author: tonysmit
manager: scotv
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.service: exchange-online
localization_priority: Normal
ms.assetid: ad79f374-f68f-430b-8b9c-2c841e1c55ae
description: "By default, when a Unified Messaging (UM) auto attendant is created, its status is set to disabled. After you create the UM auto attendant, you can change its status to control whether it can answer incoming calls. For example, you might want to disable the UM auto attendant when you're recording or re-recording customized prompts and messages."
---

# Disable a UM auto attendant

By default, when a Unified Messaging (UM) auto attendant is created, its status is set to disabled. After you create the UM auto attendant, you can change its status to control whether it can answer incoming calls. For example, you might want to disable the UM auto attendant when you're recording or re-recording customized prompts and messages. 
  
For additional management tasks related to UM auto attendants, see [UM auto attendant procedures](um-auto-attendant-procedures.md).
  
## What do you need to know before you begin?

- Estimated time to complete: Less than 1 minute.
    
- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "UM auto attendants" entry in the [Unified Messaging Permissions](http://technet.microsoft.com/library/d326c3bc-8f33-434a-bf02-a83cc26a5498.aspx) topic. 
    
- Before you perform these procedures, confirm that a UM dial plan has been created. For detailed steps, see [Create a UM dial plan](../../voice-mail-unified-messaging/connect-voice-mail-system/create-um-dial-plan.md).
    
- Before you perform these procedures, confirm that a UM auto attendant has been created. For detailed steps, see [Create a UM auto attendant](create-a-um-auto-attendant.md). Also confirm that the status of the UM auto attendant is set to enabled.
    
- For information about keyboard shortcuts that may apply to the procedures in this topic, see **Keyboard shortcuts in the Exchange admin center**.
    
> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612),[Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351).. 
  
## What do you want to do?

### Use the EAC to disable a UM auto attendant

1. In the EAC, navigate to **Unified Messaging** \> **UM dial plans**. In the list view, select the dial plan you want to change, and on the toolbar, click **Edit**![Edit icon](../../media/ITPro_EAC_EditIcon.gif).
    
2. On the **UM Dial Plan** page, under **UM Auto Attendants**, select the UM auto attendant you want to disable. On the toolbar, click **Down arrow**![Down Arrow Icon](../../media/ITPro_EAC_DownArrowIcon.gif)
  
3. On the **Warning** page, click **Yes**. 
    
### Use the Shell to disable a UM auto attendant

This example disables a UM auto attendant named  `MyUMAutoAttendant`.
  
```
Disable-UMAutoAttendant -Identity MyUMAutoAttendant
```


