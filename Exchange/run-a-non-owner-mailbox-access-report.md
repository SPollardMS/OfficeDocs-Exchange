---
title: Run a non-owner mailbox access report
ms.prod: EXCHANGE
ms.assetid: dbbef170-e726-4735-abf1-2857db9bb52d
---


# Run a non-owner mailbox access report
 **Summary**: Learn how to enable mailbox audit logging in Exchange so that you run reports on non-owner mailbox access.
The Non-Owner Mailbox Access Report in the Exchange admin center (EAC) lists the mailboxes that have been accessed by someone other than the person who owns the mailbox. When a non-owner accesses a mailbox, Exchange logs information about this action. Exchange stores this mailbox audit log as an email message in a hidden folder in the audited mailbox. The report displays entries from this log as search results and includes any mailboxes accessed by a non-owner, who accessed each mailbox and when, the actions performed by non-owners, and whether or not the actions were successful.
  
    
    

Exchange logs specific actions by non-owners, which includes administrators and users who have been assigned permissions to a mailbox (who are called delegated users). You can also narrow the search to users inside or outside your organization. By default, Exchange retains entries in the mailbox audit log for 90 days.
You enable mailbox audit logging in the Exchange Management Shell. 
  
    
    


## What do you need to know before you begin?


- Estimated time to complete: 5 minutes.
    
  
- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Mailbox audit logging" entry in the  [Messaging policy and compliance permissions in Exchange 2016](messaging-policy-and-compliance-permissions-in-exchange-2016.md) topic.
    
  
- For information about keyboard shortcuts that may apply to the procedures in this topic, see  [Keyboard shortcuts in the Exchange admin center](keyboard-shortcuts-in-the-exchange-admin-center.md).
    
  

> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at:  [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612),  [Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or  [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351). 
  
    
    


## What do you want to do?


### Enable mailbox audit logging

You have to enable mailbox audit logging for each mailbox that you want to include in a non-owner mailbox access report. If you don't enable mailbox audit logging, you won't get any results when you run a report.
  
    
    
To enable mailbox audit logging for a single mailbox, run the following command in the Exchange Management Shell.
  
    
    



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


#### How do you know this worked?

Run the following command to verify that you've successfully configured mailbox audit logging.
  
    
    

```
Get-Mailbox | FL Name,AuditEnabled
```

A value of  `True` for the _AuditEnabled_ property verifies that audit logging is enabled.
  
    
    

### Run a non-owner mailbox access report
<a name="runreport"> </a>


1. In the EAC, navigate to **Compliance Management** > **Auditing**.
    
  
2. Click **Run a non-owner mailbox access report**.
    
    By default, Exchange runs the report for non-owner access to any mailboxes in the organization over the past two weeks. Audit logging was enabled for the mailboxes listed in the search results.
    
  
3. To view non-owner access for a specific mailbox, select the mailbox from the list of mailboxes. View the search results in the details pane.
    
  

> [!TIP]
> Want to narrow the search results? Select the start date, end date, or both, and select specific mailboxes to search. Click **Search** to re-run the report.
  
    
    


#### Search for specific types of non-owner access

You can also specify that you want to search for the non-owner access type, also called the logon type. Here are your options:
  
    
    

- **All non-owners** Search for access by administrators and delegated users inside your organization. Also includes access user outside of your organization.
    
  
- **External users** Search for access by users outside of your organization.
    
  
- **Administrators and delegated users** Search for access by administrators and delegated users inside your organization.
    
  
- **Administrators** Search for access by administrators in your organization.
    
  

#### What gets logged in the mailbox audit log?
<a name="whatislogged"> </a>

When you run a non-owner mailbox access report, the EAC search results displays entries from the mailbox audit log. Each report entry contains this information:
  
    
    

- Who accessed the mailbox and when.
    
  
- The actions performed by the non-owner.
    
  
- The affected message and its folder location.
    
  
- Whether the action was successful.
    
  
The following table describes the types of actions logged, and whether these actions are logged by default for access by administrators and for access by delegated users. If you want to track actions that aren't logged by default, you have to use the Exchange Management Shell to enable logging of those actions.
  
    
    


|**Action**|**Description**|**Administrators**|**Delegated users**|
|:-----|:-----|:-----|:-----|
|**Update** <br/> |A message was changed.  <br/> |Yes  <br/> |Yes  <br/> |
|**Copy** <br/> |A message was copied to another folder.  <br/> |No  <br/> |No  <br/> |
|**Move** <br/> |A message was moved to another folder.  <br/> |Yes  <br/> |No  <br/> |
|**Move To Deleted Items** <br/> |A message was moved to the Deleted Items folder.  <br/> |Yes  <br/> |No  <br/> |
|**Soft-delete** <br/> |A message was deleted from the Deleted Items folder.  <br/> |Yes  <br/> |Yes  <br/> |
|**Hard-delete** <br/> |A message was purged from the Recoverable Items folder.  <br/> |Yes  <br/> |Yes  <br/> |
|**FolderBind** <br/> |A mailbox folder was accessed.  <br/> |Yes  <br/> |No  <br/> |
|**Send as** <br/> |A message was sent using SendAs permission. This means another user sent the message as though it came from the mailbox owner.  <br/> |Yes  <br/> |Yes  <br/> |
|**Send on behalf of** <br/> |A message was sent using SendOnBehalf permission. This means another user sent the message on behalf of the mailbox owner. The message will indicate to the recipient who the message was sent on behalf of and who actually sent the message.  <br/> |Yes  <br/> |No  <br/> |
|**MessageBind** <br/> |A message was viewed in the preview pane or opened.  <br/> |No  <br/> |No  <br/> |
   

## How do you know this worked?

To verify that you've successfully run a non-owner mailbox access report, check the search results pane. The results pane displays the mailboxes that you ran the report for, whether an individual user or a group of mailboxes. If there are no results for a specific mailbox, it's possible there was no non-owner access or there was no non-owner access in the specified date range. As we previously recommended, be sure to verify that you enabled audit logging for the mailboxes you want to search for access by non-owners.
  
    
    

