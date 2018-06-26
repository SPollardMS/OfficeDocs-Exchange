---
title: "Recover deleted messages in a user's mailbox"
ms.author: markjjo
author: markjjo
manager: scotv
ms.date: 12/9/2016
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 9e0e34ce-efc5-454e-8d15-57b4da867f12
description: "(This topic is intended for Exchange administrators.)"
---

# Recover deleted messages in a user's mailbox

(This topic is intended for Exchange administrators.)
  
Administrators can search for and recover deleted email messages in a user's mailbox. This includes items that are permanently deleted (purged) by a person (by using the Recover Deleted Items feature in Outlook or Outlook Web App), or items deleted by an automated process, such as the retention policy assigned to user mailboxes. In these situations, the purged items can't be recovered by a user. But administrators can recover purged messages if the deleted item retention period for the item hasn't expired. 
  
> [!NOTE]
> In addition to using this procedure to search for and recover deleted items (which are moved to the Recoverable Items\Purges folder if either single item recovery or litigation hold is enabled), you can also use this procedure to search for items residing in other folders in the mailbox and to delete items from the source mailbox (also known as search and destroy). 
  
## What you need to know before you begin?

- Estimated time to complete: 15-30 minutes.
    
- Procedures in this topic require specific permissions. See each procedure for its permissions information.
    
- Single item recovery must be enabled for a mailbox before the item you want to recover is deleted. In Exchange Online, single item recovery is enabled by default when a new mailbox is created. In Exchange 2013, single item recovery is disabled when a mailbox is created. For more information, see [Enable or disable single item recovery for a mailbox](enable-or-disable-single-item-recovery.md).
    
- To search for and recover items, you must have the following information:
    
  - **Source mailbox** This is the mailbox being searched. 
    
  - **Target mailbox** This is the discovery mailbox in which messages will be recovered. Exchange Setup creates a default discovery mailbox. In Exchange Online, a discovery mailbox is also created by default. If required, you can create additional discovery mailboxes. For details, see [Create a discovery mailbox](../../security-and-compliance/in-place-ediscovery/create-a-discovery-mailbox.md).
    
    > [!NOTE]
    > When using the **Search-Mailbox** cmdlet, you can also specify a target mailbox that isn't a discovery mailbox. However, you can't specify the same mailbox as the source and target mailbox. 
  
  - **Search criteria** Criteria include sender or recipient, or keywords (words or phrases) in the message. 
    
- This topic focuses on using PowerShell to recover deleted items in a user's mailbox. You can also use the GUI-based In-Place eDiscovery tool to find and export deleted items to a PST file. The user will use this PST file to restore the deleted messages to their mailbox. For detailed instructions, see [Recover deleted items in a user's mailbox - Admin Help](https://go.microsoft.com/fwlink/p/?LinkId=722928).
    
## (Optional) Step 1: Connect to Exchange Online using remote PowerShell

You only need to perform this step if you have an Exchange Online or Office 365 organization. If you have an Exchange 2013 organization, go to the next step and run the command in the Exchange Management Shell.
  
1. On your local computer, open Windows PowerShell and run the following command.
    
  ```
  $UserCredential = Get-Credential
  ```

    In the **Windows PowerShell Credential Request** dialog box, type user name and password for an Office 365 global admin account, and then click **OK**.
    
2. Run the following command.
    
  ```
  $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell-liveid/ -Credential $UserCredential -Authentication Basic -AllowRedirection
  ```

3. Run the following command.
    
  ```
  Import-PSSession $Session
  ```

4. To verify that you're connected to your Exchange Online organization, run the following command to get a list of all the mailboxes in your organization.
    
  ```
  Get-Mailbox
  ```

For more information or if you have problems connecting to your Exchange Online organization, see [Connect to Exchange Online using remote PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=517283).
  
## Step 2: Search for and recover missing items

You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "In-Place eDiscovery" entry in the [Messaging Policy and Compliance Permissions](http://technet.microsoft.com/library/ec4d3b9f-b85a-4cb9-95f5-6fc149c3899b.aspx) topic. 
  
> [!NOTE]
> You can use In-Place eDiscovery in the Exchange admin center (EAC) to search for missing items. However, when using the EAC, you can't restrict the search to the Recoverable Items folder. Messages matching your search parameters will be returned even if they're not deleted. After they're recovered to the specified discovery mailbox, you may need to review the search results and remove unnecessary messages before recovering the remaining messages to the user's mailbox or exporting them to a .pst file. > For details about how to use the EAC to perform an In-Place eDiscovery search, see [Create an In-Place eDiscovery search](../../security-and-compliance/in-place-ediscovery/create-in-place-ediscovery-search.md). 
  
The first step in the recovery process is to search for messages in the source mailbox. Use one of the following methods to search a user mailbox and copy messages to a discovery mailbox.
  
This example searches for messages in April Stewart's mailbox that meet the following criteria:
  
- Sender: Ken Kwok
    
- Keyword: Seattle
    
```
Search-Mailbox "April Stewart" -SearchQuery "from:'Ken Kwok' AND seattle" -TargetMailbox "Discovery Search Mailbox" -TargetFolder "April Stewart Recovery" -LogLevel Full
```

> [!NOTE]
> When using the **Search-Mailbox** cmdlet, you can scope the search by using the  _SearchQuery_ parameter to specify a query formatted using Keyword Query Language (KQL). You can also use the  _SearchDumpsterOnly_ switch to search only items in the Recoverable Items folder. 
  
For detailed syntax and parameter information, see [Search-Mailbox](http://technet.microsoft.com/library/9ee3b02c-d343-4816-a583-a90b1fad4b26.aspx).
  
 **How do you know this worked?**
  
To verify that you have successfully searched the messages you want to recover, log on to the discovery mailbox you selected as the target mailbox and review the search results.
  
## Step 3: Restore recovered items

You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "In-Place eDiscovery" entry in the [Messaging Policy and Compliance Permissions](http://technet.microsoft.com/library/ec4d3b9f-b85a-4cb9-95f5-6fc149c3899b.aspx) topic. 
  
> [!NOTE]
> You can't use the EAC to restore recovered items. 
  
After messages have been recovered to a discovery mailbox, you can restore them to the user's mailbox by using the **Search-Mailbox** cmdlet. In Exchange 2013, you can also use the **New-MailboxExportRequest** and **New-MailboxImportRequest** cmdlets to export the messages to or import the messages from a .pst file. 
  
### Use the Shell to restore messages

This example restores messages to April Stewart's mailbox and deletes them from the Discovery Search Mailbox.
  
```
Search-Mailbox "Discovery Search Mailbox" -SearchQuery "from:'Ken Kwok' AND seattle" -TargetMailbox "April Stewart" -TargetFolder "Recovered Messages" -LogLevel Full -DeleteContent
```

For detailed syntax and parameter information, see [Search-Mailbox](http://technet.microsoft.com/library/9ee3b02c-d343-4816-a583-a90b1fad4b26.aspx).
  
 **How do you know this worked?**
  
To verify that you have successfully recovered messages to the user's mailbox, have the user review messages in the target folder you specified in the above command. 
  
### (Exchange 2013) Use the Shell to export and import messages from a .pst file

In Exchange 2013, you can export contents from a mailbox to a .pst file and import the contents of a .pst file to a mailbox. To learn more about mailbox import and export, see [Understanding Mailbox Import and Export Requests](http://technet.microsoft.com/library/157a7d88-d3aa-4056-9a50-df67451b14be.aspx). You can't perform this task in Exchange Online.
  
This example uses the following settings to export messages from the folder April Stewart Recovery in the Discovery Search Mailbox to a .pst file:
  
- **Mailbox** Discovery Search Mailbox 
    
- **Source folder** April Stewart Recovery 
    
- **ContentFilter** April travel plans 
    
- **PST file path** \\MYSERVER\HelpDeskPst\AprilStewartRecovery.pst 
    
```
New-MailboxExportRequest -Mailbox "Discovery Search Mailbox" -SourceRootFolder "April Stewart Recovery" -ContentFilter {Subject -eq "April travel plans"} -FilePath \\MYSERVER\HelpDeskPst\AprilStewartRecovery.pst
```

For detailed syntax and parameter information, see [New-MailboxExportRequest](http://technet.microsoft.com/library/1625c25a-7cc9-459c-97ea-281ac421bbce.aspx).
  
This example uses the following settings to import messages from a .pst file to the folder Recovered By Helpdesk in April Stewart's mailbox:
  
- **Mailbox** April Stewart 
    
- **Target folder** Recovered By Helpdesk 
    
- **PST file path** \\MYSERVER\HelpDeskPst\AprilStewartRecovery.pst 
    
```
New-MailboxImportRequest -Mailbox "April Stewart" -TargetRootFolder "Recovered By Helpdesk" -FilePath \\MYSERVER\HelpDeskPst\AprilStewartRecovery.pst 
```

For detailed syntax and parameter information, see [New-MailboxImportRequest](http://technet.microsoft.com/library/4ca9af1a-33fa-4d53-a765-f46a1b7f2d3a.aspx).
  
 **How do you know this worked?**
  
To verify that you have successfully exported messages to a .pst file, use Outlook to open the .pst file and inspect its contents. To verify that you have successfully imported messages from the .pst file, have the user inspect the contents of the target folder you specified in the above command. 
  
## More information

- The ability to recover deleted items is enabled by single item recovery, which lets an administrator recover a message that's been purged by a user or by retention policy as long as the deleted item retention period hasn't expired for that item. To learn more about single item recovery, see [Recoverable Items Folder](http://technet.microsoft.com/library/efc48fb4-2ed8-4d05-93af-f3505fbc389d.aspx).
    
- An Exchange Online mailbox is configured to retain deleted items for 14 days, by default. You can change this setting to a maximum of 30 days. In Exchange 2013, a mailbox database is configured to retain deleted items for 14 days, by default. You can configure deleted item retention settings for a mailbox or mailbox database. For more information, see:
    
  - [Change how long permanently deleted items are kept for an Exchange Online mailbox](change-deleted-item-retention.md)
    
  - [Configure Deleted Item Retention and Recoverable Items Quotas](http://technet.microsoft.com/library/de7d667a-1c93-4364-a4f9-2aa5e3678b12.aspx)
    
- As previously explained, you can also use the In-Place eDiscovery tool to find and export deleted items to a PST file. The user will use this PST file to restore the deleted messages to their mailbox. For detailed instructions, see [Recover deleted items in a user's mailbox - Admin Help](https://go.microsoft.com/fwlink/p/?LinkId=722928).
    
- Users can recover a deleted item if it hasn't been purged and if the deleted item retention period for that item hasn't expired. If users need to recover deleted items from the Recoverable Items folder, point them to the following topics:
    
  - [Recover deleted items in Outlook 2010](https://go.microsoft.com/fwlink/p/?LinkId=524923)
    
  - [Recover deleted items in Outlook 2013](https://go.microsoft.com/fwlink/p/?LinkId=624829)
    
  - [Recover deleted items or email in Outlook Web App](https://go.microsoft.com/fwlink/p/?LinkId=524924)
    
- This topic shows you how to use the **Search-Mailbox** cmdlet to search for and recover missing items. If you use this cmdlet, you can search only one mailbox at a time. If you want to search multiple mailboxes at the same time, you can use [In-Place eDiscovery](../../security-and-compliance/in-place-ediscovery/in-place-ediscovery.md) in the Exchange admin center (EAC) or the [New-MailboxSearch](http://technet.microsoft.com/library/74303b47-bb49-407c-a43b-590356eae35c.aspx) cmdlet in Windows PowerShell. 
    
- In addition to using this procedure to search for and recover deleted items, you can also use a similar procedure to search for items in user mailboxes and then delete those items from the source mailbox. For more information, see [Search and delete messages](http://technet.microsoft.com/library/8c36bb03-e716-4fdd-9958-4aa7a2a1db42.aspx).
    

