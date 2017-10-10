---
title: Learn more about administrator credentials for migration
ms.prod: EXCHANGE
ms.assetid: a8202849-e7a9-49b1-80e1-ea6d7fc4f12a
---


# Learn more about administrator credentials for migration

To migrate mailboxes to Exchange Online using a staged Exchange migration, you need to specify the credentials for a user account in your on-premises Exchange organization that has been assigned the necessary permissions to access and modify the on-premises mailboxes that you want to migrate. This account is typically called the migration administrator. It's easiest to use the credentials for a migration administrator account that is a member of the Domain Admins group in the on-premises organization, although this might not be possible in large organizations or if you're migrating mailboxes from a hosted service provider. If this is the case, you can assign specific mailbox permissions to the migration administrator account.
  
    
    

Exchange Online uses the migration administrator account and the Autodiscover service to detect the connection settings to an on-premises server that hosts the mailboxes you're migrating. It also tests the connectivity to a mailbox in the CSV file that you submitted on the previous page to verify that the migration administrator account has the necessary permissions to access the mailbox.
> [!TIP]
> The reason you're being prompted for the credentials of the migration administrator is because no Outlook Anywhere migration endpoints have been created in your Exchange Online organization. It's a good idea to create a migration endpoint before you create a migration batch. When you create a migration endpoint, Exchange Online tests the connection to the on-premises Exchange server. The migration endpoint isn't created unless Exchange Online can successfully connect to the on-premises server. This lets you troubleshoot and resolve connectivity issues before you create a migration batch. Otherwise, you have to cancel the migration batch and resolve any connectivity issues before you can create a migration batch. 
  
    
    


## For more information

 [Assign Permissions to Migrate Mailboxes to Exchange Online](http://technet.microsoft.com/library/3dcf0e78-e894-4e34-9955-1509d14707a0.aspx)
  
    
    
 [Create Migration Endpoints](http://technet.microsoft.com/library/11351cb5-b529-4b4d-a5de-45a494565a16.aspx)
  
    
    

