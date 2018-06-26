---
title: "Create a public folder mailbox"
ms.author: dmaguire
author: msdmaguire
manager: serdars
ms.date: 4/19/2018
ms.audience: ITPro
ms.topic: article
ms.prod: exchange-server-itpro
localization_priority: Normal
ms.assetid: 64437ffd-231b-4c10-84df-232ccbe9538f
description: "Summary: Learn how to create a public folder mailbox in Exchange 2016."
---

# Create a public folder mailbox

 **Summary**: Learn how to create a public folder mailbox in Exchange 2016.
  
Before you can create a public folder in Exchange 2016, you must first create a public folder mailbox. Public folder mailboxes contain the hierarchy information as well as the content for public folders. The first public folder mailbox you create will be the primary hierarchy mailbox, which contains the only writable copy of the hierarchy. Any additional public folder mailboxes you create will be secondary mailboxes, which contain a read-only copy of the hierarchy.
  
> [!NOTE]
>  For more information about the storage quotas and limits for public folders, see the following topics: >  For public folders in Office 365, see [Exchange Online Limits](https://go.microsoft.com/fwlink/?LinkID=391188). >  For public folders in on-premises Exchange Server 2013, see [Limits for public folders](limits.md). 
  
For additional management tasks related to public folders in Exchange 2016, see [Public folder procedures](procedures.md).
  
## What do you need to know before you begin?

- Estimated time to complete: less than 5 minutes.
    
- Exchange 2016 public folders and public folders on legacy Exchange servers can't exist in the same organization. If you try to create a public folder mailbox when you still have legacy public folders, you'll receive the error **An existing Public Folder deployment has been detected. To migrate existing Public Folder data, create new Public Folder mailbox using -HoldForMigration switch.**
    
    Before you can create public folders in Exchange 2016, you need to migrate your legacy public folders to Exchange 2016. To do this, follow the steps in [Use batch migration to migrate public folders to Exchange 2016 from previous versions](batch-migration-from-previous-versions.md) if you currently have Exchange 2010 public folders, or [Migrate public folders from Exchange 2013 to Exchange 2016](migrate-from-exchange-2013.md) if you currently have Exchange 2013 public folders. 
    
- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Public folders" entry in the [Sharing and collaboration permissions](../../permissions/feature-permissions/sharing-and-collaboration-permissions.md) topic. 
    
- For information about keyboard shortcuts that may apply to the procedures in this topic, see [Keyboard shortcuts in the Exchange admin center](../../about-documentation/exchange-admin-center-keyboard-shortcuts.md).
    
## Use the EAC to create a public folder mailbox

In the Exchange admin center (EAC):
  
1. Navigate to **Public folders** \> **Public folder mailboxes**, and then click **Add**![Add icon](../../media/ITPro_EAC_AddIcon.png).
    
2. In **Public Folder Mailbox**, provide a name for the public folder mailbox.
    
3. Click **Save**.
    
## Use the Exchange Management Shell to create a public folder mailbox

This shows how to create the primary public folder mailbox.
  
```
New-Mailbox -PublicFolder -Name MasterHierarchy
```

This example shows how to create a secondary public folder mailbox, in this case, one names Istanbul.
  
```
New-Mailbox -PublicFolder -Name Istanbul 
```

The only difference between the primary hierarchy mailbox and a secondary hierarchy mailbox is that the primary mailbox is the first one created in the organization. You can create additional public folder mailboxes for load balancing.
  
For detailed syntax and parameter information, see [new-Mailbox](http://technet.microsoft.com/library/42dbb25a-0b23-4775-ae15-7af62c089565.aspx).
  
## How do you know this worked?

To verify that you have successfully created the primary public folder mailbox, run the following Exchange Management Shell command:
  
```
Get-OrganizationConfig | Format-List RootPublicFolderMailbox
```

For detailed syntax and parameter information, see [get-OrganizationConfig](http://technet.microsoft.com/library/3e07e5cc-5066-40e7-8642-845ad080f9a9.aspx).
  
Having problems? Ask for help in the Exchange forums. Visit the forums at: [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351).
  

