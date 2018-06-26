---
title: "Delete or restore user mailboxes in Exchange Online"
ms.author: kwekua
author: kwekua
manager: scotv
ms.date: 6/24/2018
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: be7f59a5-bbc9-4b7a-a28b-f47b26dd33a7
description: "There are several things you should consider before you decide to delete a user mailbox. There's different kinds of deletions that you can do on a user mailbox and some of them won't allow you to restore or recover the mailbox. This article walks you through the deleted mailbox scenarios, as well as how to delete, recover or permanently remove a mailbox from Exchange Online."
---

# Delete or restore user mailboxes in Exchange Online

There are several things you should consider before you decide to delete a user mailbox. There's different kinds of deletions that you can do on a user mailbox and some of them won't allow you to restore or recover the mailbox. This article walks you through the deleted mailbox scenarios, as well as how to delete, recover or permanently remove a mailbox from Exchange Online.
  
## Soft-deleted user mailboxes
<a name="BKMK_softdeleted"> </a>

A soft-deleted user mailbox is a mailbox that has been deleted using the Office 365 admin center or the **Remove-Mailbox** cmdlet in the Exchange Management Shell, and has still been in the Azure active directory (Azure AD) recycle bin for less than 30 days. 
  
A soft-deleted user mailbox is a mailbox that has been deleted in the following cases:
  
- The user mailbox's associated Azure active directory user account is soft deleted (the Azure active directory user object is out of scope or in the recycle bin container).
    
- The user mailbox's associated Azure active directory user account has been hard deleted but the Exchange Online mailbox is in a litigation hold or eDiscovery hold.
    
- The user mailbox's associated Azure active directory user account has been purged within the last 30 days; which is the retention length Exchange Online will keep the mailbox in a soft deleted state before it is permanently purged and unrecoverable.
    
> [!NOTE]
> If you run the Azure cmdlet  `Remove-MsolUser` with the  `-RemoveFromRecycleBin` parameter in order to remove a user from the Azure AD recycle bin, it will always put an existing Exchange Online mailbox associated with the Azure AD user in a soft-deleted state, as long as the user's license was not removed. However, if you remove the user's license prior to removing the user from the recycle bin, the user will not go into a soft-deleted user mailbox state. 
  
If in the 30 day time period a new Azure Active Directory user is synchronized from the original on-premises recipient account with the same ExchangeGuid or ArchiveGuid, this will result in an ExchangeGuid validation conflict error.
  
Check out [Manage inactive mailboxes in Office 365](http://technet.microsoft.com/library/c60e9ae7-dd02-4c5f-9f5d-7626a9101094.aspx) for more info on putting a mailbox in a litigation hold. 
  
## Hard-deleted user mailboxes
<a name="BKMK_harddeleted"> </a>

A hard-deleted user mailbox is a mailbox that has been deleted in the following cases:
  
- The user mailbox has been soft-deleted for more than 30 days, and the associated Azure active directory user has been hard-deleted. Check out the **Remove-MsolUser** cmdlet. All mailbox content such as emails, contacts and files will be permanently deleted. 
    
- The user mailbox's associated Azure active directory user account has been hard-deleted in the Azure active directory. The user mailbox is now soft-deleted in Exchange Online and stays in the soft deleted state for 30 days. If in the 30 days time period a new Azure active directory user is synchronized from the original on-premises recipient account with the same ExchangeGuid or ArchiveGuid, and that new account is licensed for Exchange Online, this will result in a hard deletion of the original user mailbox. All mailbox content such as emails, contacts and files will be permanently deleted.
    
- The soft deleted mailbox has been deleted using the **Remove-Mailbox -PermanentlyDelete** cmdlet and parameter in Exchange Management Shell. 
    
The above scenarios assume that the user mailbox isn't in any of the hold states, like Litigation hold or eDiscovery hold. If there is any type of hold on the user mailbox the mailbox can't be removed from Exchange Online. For all mail user recipient types, Litigation hold or eDiscovery hold are ignored and have no impact on the mail users hard-deleted or soft-delete behavior. The mail user object can't be deleted if there is a journal mailbox associated You can disable journaling on the mail user by using the **Disable-JournalArchiving** cmdlet. 
  
## Delete a user mailbox
<a name="BKMK_harddeleted"> </a>

### Use the Office 365 admin center to delete a user account

When you delete an Office 365 user account, the corresponding Exchange Online mailbox is deleted and removed from the list of mailboxes in the EAC. After the user account is deleted, it's listed on the **Deleted Users** page in the Office 365 admin center. It can be recovered within 30 days after being deleted. After 30 days, the user account and mailbox are permanently deleted and not recoverable. 
  
To delete an Office 365 work or school account, see [Delete or restore users](https://go.microsoft.com/fwlink/p/?LinkId=279162).
  
### Use the Exchange Management Shell to delete a mailbox

- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the"Recipient Provisioning Permissions" section in the [Recipients permissions](http://technet.microsoft.com/library/5b690bcb-c6df-4511-90e1-08ca91f43b37.aspx) topic. 
    
- To learn how to use Windows PowerShell to connect to Exchange Online, see [Connect to Exchange Online PowerShell](https://go.microsoft.com/fwlink/p/?linkid=396554).
    
When you delete an Exchange Online mailbox using the Exchange Management Shell, the corresponding Office 365 user is deleted and removed from the list of users in the Office 365 admin center. The user will still be recoverable for 30 days. After the 30 days time limit, the user is permanently deleted.
  
This example deletes an Exchange Online mailbox and the corresponding Office 365 user account for Walter Harp.
  
```
Remove-Mailbox -Identity "Walter Harp"
```

### Use Windows Powershell to permanently delete a user mailbox

This example deletes the user account for Walter Harp from the Azure active directory.
  
```
Remove-MsolUser -UserPrincipalName <Walter Harp> -RemoveFromRecycleBin true
```

For more details, check out, [Remove-MsolUser](https://go.microsoft.com/fwlink/?LinkID=809043).
  
### How do you know this worked?

To verify that you've successfully deleted an Exchange Online mailbox, do one of following:
  
- In the EAC, navigate to **Recipients** \> **Mailboxes**. The deleted mailbox is removed from the mailbox list.
    
    Click **Refresh**![Refresh Icon](../media/ITPro_EAC_RefreshIcon.gif) if the deleted mailbox is still displayed. 
    
- If you deleted the Office 365 user account, verify that the user account isn't listed on the **Active users** page in the Office 365 admin center, and that it's listed on the **Deleted Users** page. 
    
- In the Exchange Management Shell, use the following syntax to verify that the mailbox has been deleted.
    
  ```
  Get-Mailbox <identity>
  ```

    The command will return an error stating that the mailbox couldn't be found, which verifies that the mailbox was deleted.
    
- If you permanently deleted the user mailbox, verify that the user mailbox isn't still showing up in the Azure active directory recycle bin.
    
## Restore a user mailbox
<a name="BKMK_harddeleted"> </a>

When you delete a mailbox, Exchange Online retains the mailbox and all its contents until the deleted mailbox retention period expires, which is 30 days. After 30 days, the mailbox is permanently deleted and can't be recovered. The method for restoring a mailbox depends on whether the mailbox was deleted by deleting the Office 365 user account or removing the Exchange Online license.
  
### Use the Office 365 admin center to restore a user account

If the mailbox was deleted by deleting the corresponding Office 365 user account, you can restore the mailbox by restoring the user account in the Office 365 admin center.
  
To restore an Office 365 user account, see [Delete or restore users](https://go.microsoft.com/fwlink/p/?LinkId=279162).
  
### Use Exchange PowerShell to restore a user account

You can recover soft-deleted mailboxes using the PowerShell cmdlet below. The cmdlet example below restores the mailbox for Allie Bellew.
  
1. [Connect to Exchange PowerShell](https://go.microsoft.com/fwlink/?LinkID=785881)
    
2. Run the **Undo- SoftDeletedMailbox** cmdlet. 
    
  ```
  Undo- SoftDeletedMailbox allieb@contoso.com -WindowsLiveID allieb@contoso.com -Password (ConvertTo-SecureString -String 'Pa$$word1' -AsPlainText -Force) 
  
  ```

### How do you know this worked?

To verify that you've successfully restored a mailbox, do one of the following:
  
- In the EAC, navigate to **Recipients** \> **Mailboxes**. The restored mailbox is displayed in the mailbox list.
    
    Click **Refresh**![Refresh Icon](../media/ITPro_EAC_RefreshIcon.gif) if the mailbox isn't displayed at first. 
    
- In the Exchange Management Shell, use the following syntax to verify that the mailbox was restored.
    
  ```
  Get-Mailbox <identity>
  ```

## Restoring a user in a hybrid scenario
<a name="BKMK_harddeleted"> </a>

For user mailboxes in a hybrid scenario, if the mailbox has been soft-deleted and the Azure active directory user that was associated with the mailbox has been hard-deleted from Azure Active Directory, you can use **New-MailboxRestoreRequest** to recover the mailbox. Read [Configure Office 365 Groups with on-premises Exchange hybrid](https://go.microsoft.com/fwlink/?LinkID=809310) for more info. The cmdlet example below restores the mailbox for a soft-deleted user. 
  
1. [Connect to Exchange PowerShell](https://go.microsoft.com/fwlink/?LinkID=785881)
    
2. Run the following cmdlet and retrieve the GUID for the soft-deleted mailbox that you want to restore.
    
  ```
  Get-Mailbox -SoftDeletedMailbox
  ```

    This cmdlet will return a GUID of soft-deleted mailboxes.
    
3. Run the following cmdlet to restore the mailbox.
    
  ```
  New-MailboxRestoreRequest -SourceMailbox <GUID from above step> -TargetMailbox <GUID from new target mailbox you've created>
  ```

## License removal
<a name="BKMK_harddeleted"> </a>

For info on removing a license from a user in Office 365 and Exchange Online, check out [Change in behavior for delicensed Exchange Online users](https://go.microsoft.com/fwlink/p/?LinkId=834307).
  
## Additional information
<a name="BKMK_harddeleted"> </a>

- For information about keyboard shortcuts that may apply to the procedures in this topic, see **Keyboard shortcuts in the Exchange admin center**.
    
> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612),[Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351). 
  

