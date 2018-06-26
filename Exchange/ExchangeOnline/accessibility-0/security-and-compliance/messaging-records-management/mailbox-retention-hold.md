---
title: "Place a mailbox on retention hold"
ms.author: markjjo
author: markjjo
manager: scotv
ms.date: 11/17/2014
ms.audience: End User
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 2baac4a7-3402-4142-bfb3-1649a950e677
description: "Placing a mailbox on retention hold suspends the processing of a retention policy or managed folder mailbox policy for that mailbox. Retention hold is designed for situations such as a user being on vacation or away temporarily."
---

# Place a mailbox on retention hold

Placing a mailbox on retention hold suspends the processing of a retention policy or managed folder mailbox policy for that mailbox. Retention hold is designed for situations such as a user being on vacation or away temporarily. 
  
During retention hold, users can log on to their mailbox and change or delete items. When you perform a mailbox search, deleted items that are past the deleted item retention period aren't returned in search results. To make sure items changed or deleted by users are preserved in legal hold scenarios, you must place a mailbox on legal hold. For more information, see [Create or remove an In-Place Hold](../../security-and-compliance/create-or-remove-in-place-holds.md).
  
You can also include retention comments for mailboxes you place on retention hold. The comments are displayed in supported versions of Microsoft Outlook.
  
For additional management tasks related to messaging records management (MRM), see [Messaging Records Management Procedures](http://technet.microsoft.com/library/bc2ff408-4a2b-4202-9515-e3e922a6320d.aspx).
  
## What do you need to know before you begin?

- Estimated time to complete: 1 minute.
    
- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Messaging records management" entry in the [Messaging Policy and Compliance Permissions](http://technet.microsoft.com/library/ec4d3b9f-b85a-4cb9-95f5-6fc149c3899b.aspx) topic. 
    
- You can't use the Exchange Administration Center (EAC) to place a mailbox on retention hold. You must use the Shell.
    
- For information about keyboard shortcuts that may apply to the procedures in this topic, see **Keyboard shortcuts in the Exchange admin center**.
    
> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612),[Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351). 
  
## What do you want to do?

### Use the Shell to place a mailbox on retention hold

This example places Michael Allen's mailbox on retention hold.
  
```
Set-Mailbox "Michael Allen" -RetentionHoldEnabled $true
```

For detailed syntax and parameter information, see [Set-Mailbox](http://technet.microsoft.com/library/a0d413b9-d949-4df6-ba96-ac0906dedae2.aspx).
  
### Use the Shell to remove retention hold for a mailbox

This example removes the retention hold from Michael Allen's mailbox.
  
```
Set-Mailbox "Michael Allen" -RetentionHoldEnabled $false
```

For detailed syntax and parameter information, see [Set-Mailbox](http://technet.microsoft.com/library/a0d413b9-d949-4df6-ba96-ac0906dedae2.aspx).
  
## How do you know this worked?

To verify that you have successfully placed a mailbox on retention hold, use the [Get-Mailbox](http://technet.microsoft.com/library/8a5a6eb9-4a75-47f9-ae3b-a3ba251cf9a8.aspx) cmdlet to retrieve the  _RetentionHoldEnabled_ property of the mailbox. 
  
This command retrieves the  _RetentionHoldEnabled_ property for Michael Allen's mailbox. 
  
```
Get-Mailbox "Michael Allen" | Select RetentionHoldEnabled
```

This command retrieves all mailboxes in the Exchange organization, filters the mailboxes that are placed on retention hold, and lists them along with the retention policy applied to each.
  
> [!IMPORTANT]
> Because  _RetentionHoldEnabled_ isn't a filterable property in Exchange 2013, you can't use the  _Filter_ parameter with the **Get-Mailbox** cmdlet to filter mailboxes that are placed on retention hold on the server-side. This command retrieves a list of all mailboxes and filters on the client running the Shell session. In large environments with thousands of mailboxes, this command may take a long time to complete. 
  
```
Get-Mailbox -ResultSize unlimited | Where-Object {$_.RetentionHoldEnabled -eq $true} | Format-Table Name,RetentionPolicy,RetentionHoldEnabled -Auto
```


