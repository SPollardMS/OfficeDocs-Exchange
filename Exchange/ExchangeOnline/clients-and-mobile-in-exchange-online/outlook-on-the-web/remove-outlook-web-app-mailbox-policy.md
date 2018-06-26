---
title: "Remove an Outlook Web App mailbox policy from Exchange"
ms.author: dmaguire
author: msdmaguire
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: edab7bac-b62c-4b82-8f21-dcac77cf0e8f
description: "You can remove a Microsoft Outlook Web App mailbox policy from an Exchange organization by using either the EAC or the Shell."
---

# Remove an Outlook Web App mailbox policy from Exchange

You can remove a Microsoft Outlook Web App mailbox policy from an Exchange organization by using either the EAC or the Shell.
  
For additional management tasks related to Outlook Web App mailbox policies, see [Outlook Web App mailbox policies](outlook-web-app-mailbox-policies.md).
  
## What do you need to know before you begin?

- Estimated time to complete each procedure: 3 minutes.
    
- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Outlook Web App mailbox policies" entry in the [Client Access Permissions](http://technet.microsoft.com/library/57eca42a-5a7f-4c65-89f0-7a84f2dbea19.aspx) topic. 
    
- For information about keyboard shortcuts that may apply to the procedures in this topic, see **Keyboard shortcuts in the Exchange admin center**.
    
> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612),[Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351).. 
  
## What do you want to do?

### Use the EAC to remove an Outlook Web App mailbox policy

1. In the EAC, click **Permissions** \> **Outlook Web App policies**.
    
2. In the result pane, click to select the mailbox policy you want to remove.
    
3. Click the **Delete** button. 
    
4. In the confirmation window, click **Yes** to remove the mailbox policy, or click **No** to cancel. 
    
### Use the Shell to remove an Outlook Web App mailbox policy

This example removes an Outlook Web App mailbox policy named  `Policy1`.
  
```
Remove-OwaMailboxPolicy -Name Policy1 
```

For more information about syntax and parameters, see [Remove-OwaMailboxPolicy](http://technet.microsoft.com/library/834bee7a-1044-4628-9d0d-1601e88a73f8.aspx).
  
## How do you know this worked?

To verify that you've successfully removed an Outlook Web App mailbox policy: 
  
- In the EAC, click **Permissions** \> **Outlook Web App policies**. The policy you removed should no longer appear in the list.
    

