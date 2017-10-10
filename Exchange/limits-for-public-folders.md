---
title: Limits for public folders
ms.prod: EXCHANGE
ms.assetid: 709b075e-9584-484b-bcaa-e781c26497b4
---


# Limits for public folders
Learn about supported limits for public folders in Exchange 2016.
In Exchange 2016, public folders are based on a mailbox architecture that allows public folders to benefit from things such as the resiliency of a Database Availability Group (DAG) and other mailbox enhancements. However, there are limits and performance considerations that should be taken into account.
  
    
    


## Limits

The following table lists the limits for public folders in on-premises Exchange 2016. Unless the limits are specifically stated as recommended, the values listed in this table are the supported limits for public folders. 
  
    
    

> [!IMPORTANT]
> Looking for Exchange Online limits for Office 365? See  [Exchange Online Limits](https://go.microsoft.com/fwlink/p/?LinkID=391188). 
  
    
    



|**Item**|**Limits**|**Notes**|
|:-----|:-----|:-----|
|Total number of public folder mailboxes  <br/> |1,000  <br/> |1,000 is the limit for Exchange Server 2016 CU2 or later. Although you can create more than 1,000 public folder mailboxes, it isn't supported.  [Create a public folder mailbox](create-a-public-folder-mailbox.md) <br/> |
|Total public folders in hierarchy  <br/> |1,000,000  <br/> |Although you can create more than 1,000,000 public folders, it isn't supported. For any deployment of 100,000 or more public folders, we recommend reading  [Considerations when deploying public folders](considerations-when-deploying-public-folders.md).  <br/> |
|Sub-folders under the parent folder  <br/> |10,000  <br/> |While you can create more than 1,000 sub-folders under a parent folder, we don't recommend that you do so.  <br/>  _FolderHierarchyChildrenCountReceiveQuota_ parameter on the [Set-Mailbox](http://technet.microsoft.com/library/a0d413b9-d949-4df6-ba96-ac0906dedae2.aspx) cmdlet. <br/> |
|Folder depth  <br/> |300  <br/> |The folder depth is the number levels of nested folders that can exist in one branch of a public folder tree.  _FolderHierarchyDepthRecieveQuota_ parameter on the [Set-Mailbox](http://technet.microsoft.com/library/a0d413b9-d949-4df6-ba96-ac0906dedae2.aspx) cmdlet. <br/> |
|Maximum messages per public folder  <br/> |1 million  <br/> | _MailboxMessagesPerFolderCountRecieveQuota_ parameter on the [Set-Mailbox](http://technet.microsoft.com/library/a0d413b9-d949-4df6-ba96-ac0906dedae2.aspx) cmdlet. <br/> |
|Maximum individual public folder size  <br/> |10 GB  <br/> |This limit doesn't include subfolders beneath a single folder.  <br/>  [Configure storage quotas for a mailbox](configure-storage-quotas-for-a-mailbox.md) <br/> |
|Public folder mailbox size  <br/> |100 GB  <br/> | [Configure storage quotas for a mailbox](configure-storage-quotas-for-a-mailbox.md) <br/> |
|Number of user logons per public folder mailbox  <br/> |2,000 concurrent user logons  <br/> |We recommend that you configure your hierarchy so that you have no more than 2,000 users per public folder mailbox. For example, if you have 20,000 users, you should have 10 public folder mailboxes.  <br/> |
|Moved item retention  <br/> |14 days recommended  <br/> |Use the  _DefaultPublicFolderMovedItemRetention_ parameter on the **Set-OrganizationConfig** cmdlet. <br/> |
|Age limit  <br/> |We recommend that you set this as the same default that you use for regular mailboxes.  <br/> | These settings can be set at the following levels: <br/> **Organizational level:** _DefaultPublicFolderAgeLimit_ parameter on the **Set-OrganizationConfig** cmdlet. <br/> **Mailbox level:** _AgeLimit_ parameter on the **Set-Mailbox** cmdlet. <br/> **Folder level:** _AgeLimit_ parameter on the **Set-PublicFolder** cmdlet. <br/> |
|Deleted item retention  <br/> |We recommend that you set this as the same default that you use for regular mailboxes.  <br/> | These settings can be set at the following levels: <br/> **Organizational level:** _DefaultPublicFolderMovedItemRetention_ parameter on the **Set-OrganizationConfig** cmdlet. <br/> **Mailbox level:** _RetainDeletedItemsFor_ on the **Set-Mailbox** cmdlet. <br/> **Folder level:** _RetainDeleteItemsFor_ parameter on the **Set-PublicFolder** cmdlet. <br/> |
|Maximum number of public folders that can be migrated to Exchange 2016  <br/> |500,000  <br/> |This is the maximum number of public folders you can move to Exchange 2016 from a legacy version of Exchange in a single migration. For details on migrating public folders, see  [Use batch migration to migrate public folders to Exchange 2016 from previous versions](use-batch-migration-to-migrate-public-folders-to-exchange-2016-from-previous-ver.md).  <br/> |
   

