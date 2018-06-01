---
title: "Remove a database availability group"
ms.author: dmaguire
author: msdmaguire
manager: serdars
ms.date: 4/19/2018
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 071296e9-31b0-40f4-9a02-177d97486ebd
description: "Summary: How to remove a database availability group (DAG) in Exchange 2016."
---

# Remove a database availability group

 **Summary**: How to remove a database availability group (DAG) in Exchange 2016.
  
Removing a DAG is a quick and easy task. You can use the EAC or the Exchange Management Shell to remove a DAG.
  
Looking for other management tasks related to DAGs? Check out [Managing database availability groups](http://technet.microsoft.com/library/4abde67b-4995-4a57-894f-ba76aa72341c.aspx).
  
## What do you need to know before you begin?

- Estimated time to complete: 1 minute
    
- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Database availability groups" entry in the [High availability and site resilience permissions](../../permissions/feature-permissions/ha-perms.md) topic. 
    
- Before you can remove a DAG, the DAG must be empty. If the DAG you want to remove contains any Mailbox servers, you must first remove the servers from the DAG. For detailed steps about how to remove a Mailbox server from a DAG, see [Manage database availability group membership](dag-memberships.md).
    
- For information about keyboard shortcuts that may apply to the procedures in this topic, see [Keyboard shortcuts in the Exchange admin center](../../about-documentation/eac-keyboard-shortcuts.md).
    
> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at: [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351).. 
  
## Use the EAC to remove a database availability group

1. Navigate to **Servers** > **Database availability groups**.
    
2. Select the DAG you want to remove and click **Delete**![Delete icon](../../media/ITPro_EAC_DeleteIcon.png).
    
3. Click **Yes** to confirm the warning and remove the DAG. 
    
## Use the Exchange Management Shell to remove a database availability group

This example removes the DAG DAG1.
  
```
Remove-DatabaseAvailabilityGroup -Identity DAG1
```

## How do you know this worked?

To verify that you've successfully removed the DAG, do one of the following:
  
- In the EAC, go to **Servers** > **Database Availability Groups**, and see if the DAG is still displayed.
    
- In the Exchange Management Shell, run the following command to see if the DAG still exists:
    
  ```
  Get-DatabaseAvailabilityGroup <DAGName>
  ```

    If the DAG was successfully deleted, the preceding command will produce an error message indicating the object could not be found.
    

