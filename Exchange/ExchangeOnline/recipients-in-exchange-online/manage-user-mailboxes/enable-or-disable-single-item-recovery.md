---
title: "Enable or disable single item recovery for a mailbox"
ms.author: markjjo
author: markjjo
manager: scotv
ms.date: 6/24/2018
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 2e7f1bcd-8395-45ad-86ce-22868bd46af0
description: "You can use the Shell to enable or disable single item recovery on a mailbox. In Exchange Online, single item recovery is enabled by default when a new mailbox is created. In Exchange Server, single item recovery is disabled when a mailbox is created. If single item recovery is enabled, messages that are permanently deleted (purged) by the user are retained in the Recoverable Items folder of the mailbox until the deleted item retention period expires. This lets an administrator recover messages purged by the user before the deleted item retention period expires. Also, if a message is changed by a user or a process, copies of the original item are also retained when single item recovery is enabled."
---

# Enable or disable single item recovery for a mailbox

You can use the Shell to enable or disable single item recovery on a mailbox. In Exchange Online, single item recovery is enabled by default when a new mailbox is created. In Exchange Server, single item recovery is disabled when a mailbox is created. If single item recovery is enabled, messages that are permanently deleted (purged) by the user are retained in the Recoverable Items folder of the mailbox until the deleted item retention period expires. This lets an administrator recover messages purged by the user before the deleted item retention period expires. Also, if a message is changed by a user or a process, copies of the original item are also retained when single item recovery is enabled. 
  
## What do you need to know before you begin?

- Estimated time to complete: 2 minutes.
    
- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Retention and legal holds" entry in the [Mailbox Permissions](http://technet.microsoft.com/library/5b690bcb-c6df-4511-90e1-08ca91f43b37.aspx) topic. 
    
- You can't use the Exchange admin center (EAC) to enable or disable single item recovery.
    
- In Exchange Online, the deleted item retention period is set to 14 days, by default. You can change this setting to a maximum of 30 days. For details, see [Change how long permanently deleted items are kept for an Exchange Online mailbox](change-deleted-item-retention.md).
    
-  In Exchange Server, the mailbox uses the deleted item retention settings of the mailbox database, by default. The deleted item retention period for a mailbox database is set to 14 days, but you can override the default by configuring this setting on a per-mailbox basis. For details, see [Configure deleted item retention and recoverable items quotas](http://technet.microsoft.com/library/de7d667a-1c93-4364-a4f9-2aa5e3678b12.aspx).
    
- For information about keyboard shortcuts that may apply to the procedures in this topic, see **Keyboard shortcuts in the Exchange admin center**.
    
Having problems? Ask for help in the Exchange forums. Visit the forums at [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612),[Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351).
  
## Use the Shell to enable single item recovery

This example enables single item recovery for the mailbox of April Summers. 
  
```
Set-Mailbox -Identity "April Summers" -SingleItemRecoveryEnabled $true
```

This example enables single item recovery for the mailbox of Pilar Pinilla and sets the number of days that deleted items are retained to 30 days. 
  
```
Set-Mailbox -Identity "Pilar Pinilla" -SingleItemRecoveryEnabled $true -RetainDeletedItemsFor 30
```

This example enables single item recovery for all user mailboxes in the organization.
  
```
Get-Mailbox -ResultSize unlimited -Filter {(RecipientTypeDetails -eq 'UserMailbox')} | Set-Mailbox -SingleItemRecoveryEnabled $true
```

This example enables single item recovery for all user mailboxes in the organization and sets the number of days that deleted items are retained to 30 days
  
```
Get-Mailbox -ResultSize unlimited -Filter {(RecipientTypeDetails -eq 'UserMailbox')} | Set-Mailbox -SingleItemRecoveryEnabled $true -RetainDeletedItemsFor 30
```

For detailed syntax and parameter information, see [Set-Mailbox](http://technet.microsoft.com/library/a0d413b9-d949-4df6-ba96-ac0906dedae2.aspx). 
  
## Use the Shell to disable single item recovery

You might need to disable single item recovery for a user's mailbox. For example, before you can use **Search-Mailbox -DeleteContent** to permanently delete content from a mailbox, you have to disable single item recovery. For more information, see [Search and Delete Messages](http://technet.microsoft.com/library/8c36bb03-e716-4fdd-9958-4aa7a2a1db42.aspx).
  
This example disables single item recovery for the mailbox of Ayla Kol.
  
```
Set-Mailbox -Identity "Ayla Kol" -SingleItemRecoveryEnabled $false
```

## How do you know this worked?

To verify that you've enabled single item recovery for a mailbox and display the value for how long deleted items will be retained (in days), run the following command. 
  
```
Get-Mailbox <Name> | FL SingleItemRecoveryEnabled,RetainDeletedItemsFor
```

You can use this same command to verify that single item recovery is disabled for a mailbox.
  
## More information

- To learn more about single item recovery, see [Recoverable Items folder](http://technet.microsoft.com/library/efc48fb4-2ed8-4d05-93af-f3505fbc389d.aspx). To recover messages purged by the user before the deleted item retention period expires, see [Recover deleted messages in a user's mailbox](recover-deleted-messages.md).
    
- If a mailbox is placed on In-Place Hold or Litigation Hold, messages in the Recoverable Items folder are retained until the hold duration expires. If the hold duration is unlimited, then items are retained until the hold is removed or the hold duration is changed.
    

