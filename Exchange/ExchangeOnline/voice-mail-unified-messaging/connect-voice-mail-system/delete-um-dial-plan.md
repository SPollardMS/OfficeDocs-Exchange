---
title: "Delete a UM dial plan"
ms.author: tonysmit
author: tonysmit
manager: scotv
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.service: exchange-online
localization_priority: Normal
ms.assetid: c9b32ef6-432c-45ca-b94c-31bbcc973128
description: "You can delete an existing Unified Messaging (UM) dial plan. When you delete the UM dial plan, it will no longer be available for UM IP gateways, UM mailbox policies, and UM hunt groups. You can't delete a UM dial plan if it's referenced by or associated with UM mailbox policies, UM auto attendants, UM IP gateways, or UM hunt groups."
---

# Delete a UM dial plan

You can delete an existing Unified Messaging (UM) dial plan. When you delete the UM dial plan, it will no longer be available for UM IP gateways, UM mailbox policies, and UM hunt groups. You can't delete a UM dial plan if it's referenced by or associated with UM mailbox policies, UM auto attendants, UM IP gateways, or UM hunt groups. 
  
For additional management tasks related to UM dial plans, see [UM Dial Plan Procedures](http://technet.microsoft.com/library/1bda77c8-c4e2-4ae0-a001-76ae029bf843.aspx).
  
## What do you need to know before you begin?

- Estimated time to complete: Less than 1 minute.
    
- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "UM dial plans" entry in the [Unified Messaging Permissions](http://technet.microsoft.com/library/d326c3bc-8f33-434a-bf02-a83cc26a5498.aspx) topic. 
    
- Before you perform these procedures, confirm that a UM dial plan has been created. For detailed steps, see [Create a UM dial plan](create-um-dial-plan.md).
    
- For information about keyboard shortcuts that may apply to the procedures in this topic, see **Keyboard shortcuts in the Exchange admin center**.
    
> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612),[Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351).. 
  
## What do you want to do?

### Use the EAC to delete an existing dial plan

1. In the EAC, navigate to **Unified Messaging** \> **UM dial plans**.
    
2. In the list view, select the UM dial plan you want to delete, and then click **Delete**![Delete icon](../../media/ITPro_EAC_DeleteIcon.gif).
    
3. On the warning page, click **Yes**.
    
### Use the Shell to delete an existing dial plan

This example deletes a UM dial plan named  `MyUMDialPlan`.
  
```
RemoveUMDialplan -identity MyUMDialPlan
```


