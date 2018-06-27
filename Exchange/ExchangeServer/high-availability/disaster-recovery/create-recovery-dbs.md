---
title: "Create a recovery database"
ms.author: dmaguire
author: msdmaguire
manager: serdars
ms.date: 6/8/2018
ms.audience: ITPro
ms.topic: article
ms.prod: exchange-server-itpro
localization_priority: Normal
ms.collection: Strat_EX_Admin
ms.assetid: 34d87491-b7b7-44a9-8d69-e1a9c1fe5852
description: "Summary: Step-by-step guidance for creating a recovery database in Exchange 2016."
---

# Create a recovery database

 **Summary**: Step-by-step guidance for creating a recovery database in Exchange 2016.
  
You can use the Exchange Management Shell to create a recovery database, a special kind of mailbox database that's used to mount and extract data from the restored database as part of a recovery operation. After you create a recovery database, you can move a recovered or restored mailbox database into the recovery database, and then use the [New-MailboxRestoreRequest](http://technet.microsoft.com/library/0b67defd-3c6c-4470-acfa-7f22a6c1d2bd.aspx) cmdlet to extract data from the recovered database. After extraction, the data can then be exported to a folder or merged into an existing mailbox. Using recovery databases, you can recover data from a backup or copy of a database without disrupting user access to current data.
  
Looking for other management tasks related to recovery databases? Check out [Recovery databases](recovery-databases.md).
  
## What do you need to know before you begin?

- Estimated time to complete this task: 1 minute
    
- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Mailbox recovery" entry in the [Recipients Permissions](../../permissions/feature-permissions/recipient-permissions.md)topic.
    
- For information about keyboard shortcuts that may apply to the procedures in this topic, see [Keyboard shortcuts in the Exchange admin center](../../about-documentation/exchange-admin-center-keyboard-shortcuts.md).
    
> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at: [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351)..
  
## Use the Exchange Management Shell to create a recovery database

This example creates the recovery database RDB1 on the Mailbox server MBX2.
  
```
New-MailboxDatabase -Recovery -Name RDB1 -Server MBX2
```

This example creates the recovery database RDB2 on the Mailbox server MBX1 using a custom path for the database file and log folder.
  
```
New-MailboxDatabase -Recovery -Name RDB2 -Server MBX1 -EdbFilePath "C:\Recovery\RDB2\RDB2.EDB" -LogFolderPath "C:\Recovery\RDB2"
```

For detailed syntax and parameter information, see [New-MailboxDatabase](http://technet.microsoft.com/library/5008090b-e776-4ff6-807c-208e00f4daab.aspx).
  
## How do you know this worked?

To verify that you've successfully created a recovery database, do the following:
  
- In the Exchange Management Shell, run the following command to display configuration information for the recovery database.
    
  ```
  Get-MailboxDatabase <RecoveryDatabaseName> | Format-List
  ```

## Other Tasks

After you create a recovery database, you may also want to restore data using a recovery database. For detailed steps, see [Restore data using a recovery database](restore-data-using-recovery-dbs.md).
  

