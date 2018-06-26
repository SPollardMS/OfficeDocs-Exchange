---
title: "Run a non-owner mailbox access report"
ms.author: markjjo
author: markjjo
manager: scotv
ms.date: 6/23/2018
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: dbbef170-e726-4735-abf1-2857db9bb52d
description: "The Non-Owner Mailbox Access Report in the Exchange Administration Center (EAC) lists the mailboxes that have been accessed by someone other than the person who owns the mailbox. When a mailbox is accessed by a non-owner, Microsoft Exchange logs information about this action in a mailbox audit log that's stored as an email message in a hidden folder in the mailbox being audited. Entries from this log are displayed as search results and include a list of mailboxes accessed by a non-owner, who accessed the mailbox and when, the actions performed by the non-owner, and whether the action was successful. By default, entries in the mailbox audit log are retained for 90 days."
---

# Run a non-owner mailbox access report

The Non-Owner Mailbox Access Report in the Exchange Administration Center (EAC) lists the mailboxes that have been accessed by someone other than the person who owns the mailbox. When a mailbox is accessed by a non-owner, Microsoft Exchange logs information about this action in a mailbox audit log that's stored as an email message in a hidden folder in the mailbox being audited. Entries from this log are displayed as search results and include a list of mailboxes accessed by a non-owner, who accessed the mailbox and when, the actions performed by the non-owner, and whether the action was successful. By default, entries in the mailbox audit log are retained for 90 days. 
  
When you enable mailbox audit logging for a mailbox, Microsoft Exchange logs specific actions by non-owners, including both administrators and users, called delegated users, who have been assigned permissions to a mailbox. You can also narrow the search to users inside or outside your organization.
  
## What do you need to know before you begin?
<a name="beforeyoubegin"> </a>

- Estimated time to complete: 5 minutes.
    
- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Mailbox audit logging" entry in the [Messaging policy and compliance permissions](http://technet.microsoft.com/library/ec4d3b9f-b85a-4cb9-95f5-6fc149c3899b.aspx) topic. 
    
- For information about keyboard shortcuts that may apply to the procedures in this topic, see **Keyboard shortcuts in the Exchange admin center**.
    
> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612),[Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351).. 
  
## Enable mailbox audit logging
<a name="beforeyoubegin"> </a>

You have to enable mailbox audit logging for each mailbox that you want to run a non-owner mailbox access report for. If mailbox audit logging isn't enabled, you won't get any results when you run a report. 
  
To enable mailbox audit logging for a single mailbox, run the following Shell command.
  
```
Set-Mailbox <Identity> -AuditEnabled $true
```

For example, to enable mailbox auditing for a user named Florence Flipo, run the following command.
  
```
Set-Mailbox "Florence Flipo" -AuditEnabled $true
```

To enable mailbox auditing for all user mailboxes in your organization, run the following commands.
  
```
$UserMailboxes = Get-mailbox -Filter {(RecipientTypeDetails -eq 'UserMailbox')}
```

```
$UserMailboxes | ForEach {Set-Mailbox $_.Identity -AuditEnabled $true}
```

### How do you know this worked?

Run the following command to verify that you've successfully configured mailbox audit logging.
  
```
Get-Mailbox | FL Name,AuditEnabled
```

A value of  `True` for the  _AuditEnabled_ property verifies that audit logging is enabled. 
  
## Run a non-owner mailbox access report
<a name="runreport"> </a>

1. In the EAC, navigate to **Compliance Management** \> **Auditing**.
    
2. Click **Run a non-owner mailbox access report**.
    
    By default, Microsoft Exchange runs the report for non-owner access to any mailboxes in the organization over the past two weeks. The mailboxes listed in the search results have been enabled for mailbox audit logging.
    
3. To view non-owner access for a specific mailbox, select the mailbox from the list of mailboxes. View the search results in the details pane.
    
> [!TIP]
> Want to narrow the search results? Select the start date, end date, or both, and select specific mailboxes to search. Click **Search** to re-run the report. 
  
### Search for specific types of non-owner access

You can also specify the type of non-owner access, also called the logon type, to search for. Here are your options:
  
- **All non-owners** Search for access by administrators and delegated users inside your organization. Also includes access user outside of your organization. 
    
- **External users** Search for access by users outside of your organization. 
    
- **Administrators and delegated users** Search for access by administrators and delegated users inside your organization. 
    
- **Administrators** Search for access by administrators in your organization. 
    
### How do you know this worked?

To verify that you've successfully run a non-owner mailbox access report, check the search results pane. Mailboxes that you ran the report for are displayed in this pane. If there are no results for a specific mailbox, it's possible there hasn't been access by a non-owner or that non-owner access hasn't taken place within the specified date range. As previously described, be sure to verify that audit logging has been enabled for the mailboxes you want to search for access by non-owners.
  
## What gets logged in the mailbox audit log?
<a name="whatislogged"> </a>

When you run a non-owner mailbox access report, entries from the mailbox audit log are displayed in the search results in the EAC. Each report entry contains this information:
  
- Who accessed the mailbox and when
    
- The actions performed by the non-owner
    
- The affected message and its folder location
    
- Whether the action was successful
    
The following table lists the actions performed by non-owners that can be logged by mailbox audit logging. In the table, a **Yes** indicates that the action can be logged for that logon type, and a **No** indicates that an action can't be logged. An asterisk ( **\*** ) indicates that the action is logged by default when mailbox audit logging is enabled for the mailbox. If you want to track actions that aren't logged by default, you have to use PowerShell to enable logging of those actions. 
  
> [!NOTE]
> An administrator who has been assigned the Full Access permission to a user's mailbox is considered a delegated user. 
  
|**Action**|**Description**|**Administrator**|**Delegated user**|
|:-----|:-----|:-----|:-----|
|**Copy** <br/> |A message was copied to another folder.  <br/> |Yes  <br/> |No  <br/> |
|**Create** <br/> |An item is created in the Calendar, Contacts, Notes, or Tasks folder in the mailbox; for example, a new meeting request is created. Note that message or folder creation isn't audited.  <br/> |Yes\*  <br/> |Yes\*  <br/> |
|**FolderBind** <br/> |A mailbox folder was accessed.  <br/> |Yes\*  <br/> |Yes  <br/> |
|**Hard-delete** <br/> |A message was purged from the Recoverable Items folder.  <br/> |Yes\*  <br/> |Yes\*  <br/> |
|**MessageBind** <br/> |A message was viewed in the preview pane or opened.  <br/> |Yes  <br/> |No  <br/> |
|**Move** <br/> |A message was moved to another folder.  <br/> |Yes\*  <br/> |Yes  <br/> |
|**Move To Deleted Items** <br/> |A message was moved to the Deleted Items folder.  <br/> |Yes\*  <br/> |Yes  <br/> |
|**Send as** <br/> |A message was sent using SendAs permission. This means another user sent the message as though it came from the mailbox owner.  <br/> |Yes\*  <br/> |Yes\*  <br/> |
|**Send on behalf of** <br/> |A message was sent using SendOnBehalf permission. This means another user sent the message on behalf of the mailbox owner. The message will indicate to the recipient who the message was sent on behalf of and who actually sent the message.  <br/> |Yes\*  <br/> |Yes  <br/> |
|**Soft-delete** <br/> |A message was deleted from the Deleted Items folder.  <br/> |Yes\*  <br/> |Yes\*  <br/> |
|**Update** <br/> |A message was changed.  <br/> |Yes\*  <br/> |Yes\*  <br/> |
   
> [!NOTE]
> <sup>\*</sup> Audited by default if auditing is enabled for a mailbox. 
  

