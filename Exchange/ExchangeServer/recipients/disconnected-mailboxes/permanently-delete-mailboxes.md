---
title: "Permanently delete a mailbox"
ms.author: serdars
author: SerdarSoysal
manager: serdars
ms.date: 6/12/2018
ms.audience: ITPro
ms.topic: article
ms.prod: exchange-server-itpro
localization_priority: Normal
ms.assetid: df35765a-0bef-4561-9846-d91d69c0269c
description: "Summary: Learn how to permanently delete a mailbox in Exchange 2016."
---

# Permanently delete a mailbox

 **Summary**: Learn how to permanently delete a mailbox in Exchange 2016.
  
When you permanently delete active mailboxes and disconnected mailboxes, all mailbox contents are purged from the Exchange mailbox database, and the data loss is permanent. When you permanently delete an active mailbox, the associated Active Directory user account is also deleted.
  
An alternative to permanently deleting a mailbox is to disconnect it. After you disconnect a mailbox, by default, Exchange retains the data in the mailbox database for 30 days. This gives you the opportunity to reconnect or restore a mailbox before it's purged from the database.
  
To learn more about disconnected mailboxes and perform other related management tasks in Exchange, see the following topics:
  
- [Disconnected mailboxes](disconnected-mailboxes.md)
    
- [Disable or delete a mailbox in Exchange 2016](disable-or-delete-mailboxes.md)
    
- [Connect a disabled mailbox](connect-disabled-mailboxes.md)
    
- [Connect or restore a deleted mailbox](restore-deleted-mailboxes.md)
    
> [!NOTE]
> You can't use the Exchange admin center (EAC) to permanently delete an active mailbox or a disconnected mailbox.
  
## What do you need to know before you begin?

- Estimated time to complete: 2 minutes.
    
- The procedures in this topic require the Exchange Management Shell. For more information, see [Open the Exchange Management Shell](http://technet.microsoft.com/library/63976059-25f8-4b4f-b597-633e78b803c0.aspx).
    
- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Recipient Provisioning Permissions" section in the [Recipients Permissions](../../permissions/feature-permissions/recipient-permissions.md) topic.
    
- For information about keyboard shortcuts that may apply to the procedures in this topic, see [Keyboard shortcuts in the Exchange admin center](../../about-documentation/exchange-admin-center-keyboard-shortcuts.md).
    
> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at: [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351)..
  
## Use the Exchange Management Shell to permanently delete an active mailbox

If you don't include the _Permanent_ parameter when you delete a mailbox, the deleted mailbox is retained in the mailbox database for 30 days (by default) before it's permanently deleted.
  
Run the following command to permanently delete an active mailbox and the associated Active Directory user account:
  
```
Remove-Mailbox -Identity <Identity> -Permanent $true
```

For detailed syntax and parameter information, see [Remove-Mailbox](http://technet.microsoft.com/library/0477708c-768c-4040-bad2-8f980606fcf4.aspx).
  
### How do you know this worked?

To verify that you've permanently deleted an active mailbox, do the following:
  
1. Verify that the mailbox is no longer listed in the Exchange admin center (EAC).
    
2. Verify that the associated user account is no longer listed in Active Directory Users and Computers.
    
3. Run the following command in the Exchange Management Shell to verify that the mailbox was successfully purged from the Exchange mailbox database:
    
  ```
  Get-MailboxDatabase | Get-MailboxStatistics | where {$_.DisplayName -eq "<display name>"}
  ```

    If you successfully purged the mailbox, the command won't return any results. If the mailbox wasn't purged, the command will return information about the mailbox.
    
## Use the Exchange Management Shell to find the disconnected mailbox type

A disconnected mailbox can be either disabled or soft-deleted. You need to specify the correct type to permanently delete a disconnected mailbox. If you don't, the command will fail.
  
Run the following command to determine whether a disconnected mailbox is disabled or soft-deleted:
  
```
Get-MailboxDatabase | Get-MailboxStatistics | where { $_.DisplayName -eq "<display name>" } | Format-List DisplayName,MailboxGuid,Database,DisconnectReason
```

The value for the _DisconnectReason_ property will be either `Disabled` or `SoftDeleted`.
  
You can run the following command to display the type for all disconnected mailboxes in your organization:
  
```
Get-MailboxDatabase | Get-MailboxStatistics | where { $_.DisconnectReason -ne $null } | Format-List DisplayName,MailboxGuid,Database,DisconnectReason
```

## Use the Exchange Management Shell to permanently delete a disconnected mailbox

> [!CAUTION]
> When you use the **Remove-StoreMailbox** cmdlet to permanently delete a disconnected mailbox, all its contents are purged from the mailbox database and the data loss is permanent.
  
This example permanently deletes the disabled mailbox with the GUID 2ab32ce3-fae1-4402-9489-c67e3ae173d3 from mailbox database named MBD01.
  
```
Remove-StoreMailbox -Database MBD01 -Identity "2ab32ce3-fae1-4402-9489-c67e3ae173d3" -MailboxState Disabled
```

This example permanently deletes the soft-deleted mailbox for Dan Jump from mailbox database named MBD01.
  
```
Remove-StoreMailbox -Database MBD01 -Identity "Dan Jump" -MailboxState SoftDeleted
```

This example permanently deletes all soft-deleted mailboxes from mailbox database named MBD01.
  
```
Get-MailboxStatistics -Database MBD01 | where {$_.DisconnectReason -eq "SoftDeleted"} | ForEach {Remove-StoreMailbox -Database $_.Database -Identity $_.MailboxGuid -MailboxState SoftDeleted}
```

For detailed syntax and parameter information, see [Remove-StoreMailbox](http://technet.microsoft.com/library/d5cb00f2-f475-45cf-b72e-0962e5eed070.aspx) and [Get-MailboxStatistics](http://technet.microsoft.com/library/cec76f70-941f-4bc9-b949-35dcc7671146.aspx).
  
### How do you know this worked?

To verify that you've permanently deleted a disconnected mailbox and that it was successfully purged from the mailbox database, run the following command.
  
```
Get-MailboxDatabase | Get-MailboxStatistics | where {$_.DisplayName -eq "<display name>"}
```

If you successfully purged the mailbox, the command won't return any results. If the mailbox wasn't purged, the command will return information about the mailbox.
  

