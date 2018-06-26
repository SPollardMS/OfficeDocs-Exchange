---
title: "Delete a UM mailbox policy"
ms.author: tonysmit
author: tonysmit
manager: scotv
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: c8758464-3c52-4dd3-b2a6-142a99bb0628
description: "When you delete a Unified Messaging (UM) mailbox policy, the UM mailbox policy will no longer be available to be associated with recipients who are being enabled for UM. You can't delete a UM mailbox policy if it's referenced by any UM-enabled mailboxes, and you can't delete a UM dial plan if a UM mailbox policy is associated with it."
---

# Delete a UM mailbox policy

When you delete a Unified Messaging (UM) mailbox policy, the UM mailbox policy will no longer be available to be associated with recipients who are being enabled for UM. You can't delete a UM mailbox policy if it's referenced by any UM-enabled mailboxes, and you can't delete a UM dial plan if a UM mailbox policy is associated with it.
  
For additional management tasks related to UM mailbox policies, see [UM mailbox policy procedures](um-mailbox-policy-procedures.md).
  
## What do you need to know before you begin?

- Estimated time to complete: Less than 1 minute.
    
- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "UM mailbox policies" entry in the [Unified Messaging Permissions](http://technet.microsoft.com/library/d326c3bc-8f33-434a-bf02-a83cc26a5498.aspx) topic. 
    
- Before you perform these procedures, confirm that a UM mailbox policy has been created. For detailed steps, see [Create a UM mailbox policy](create-um-mailbox-policy.md).
    
- For information about keyboard shortcuts that may apply to the procedures in this topic, see **Keyboard shortcuts in the Exchange admin center**.
    
> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612),[Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351).. 
  
## What do you want to do?

### Use the EAC to delete a UM mailbox policy

1. In the EAC, navigate to **Unified Messaging** \> **UM dial plans**. In the list view, select the UM dial plan you want to modify, and then click **Edit**![Edit icon](../../media/ITPro_EAC_EditIcon.gif).
    
2. On the **UM dial plan** page, under **UM Mailbox Policies**, on the toolbar, click **Delete**![Delete icon](../../media/ITPro_EAC_DeleteIcon.gif).
    
### Use the Shell to delete a UM mailbox policy

This example deletes a UM mailbox policy named  `MyUMMailboxPolicy`.
  
```
Remove-UMMailboxPolicy -Identity MyUMMailboxPolicy
```


