---
title: Learn more about migration endpoints the first time you create a migration batch
ms.prod: EXCHANGE
ms.assetid: 492e2340-aaea-45e3-ad83-c16a8c4c38c9
---


# Learn more about migration endpoints the first time you create a migration batch

If no migration endpoints have been created in your Exchange Online organization when you create a migration batch (or in your on-premises Exchange organization when you run a cross-forest enterprise move), you have to provide credentials of a user account that has administrative privileges in the organization that hosts the mailboxes you're migrating. This account is typically called the migration administrator. 
  
    
    

Exchange Online uses the migration administrator account and the Autodiscover service to detect the connection settings to the server that hosts the mailboxes you're migrating. It also tests the connectivity to a mailbox in the host organization to verify that the migration administrator account has the necessary permissions to access that mailbox. If the connection settings are successfully discovered, Exchange Online uses those settings to create a new migration endpoint after the migration batch is created.
> [!TIP]
> It's a good idea to create migration endpoints before you create a migration batch. When you create a migration endpoint, Exchange Online tests the connection to the source server. The migration endpoint isn't created unless Exchange Online can successfully connect to the server. This lets you troubleshoot and resolve connectivity issues before you create a migration batch. Otherwise, you have to cancel the migration batch and resolve any connectivity issues before you can create a migration batch. 
  
    
    


## For more information

 [Assign Permissions to Migrate Mailboxes to Exchange Online](http://technet.microsoft.com/library/3dcf0e78-e894-4e34-9955-1509d14707a0.aspx)
  
    
    
 [Create Migration Endpoints](http://technet.microsoft.com/library/11351cb5-b529-4b4d-a5de-45a494565a16.aspx)
  
    
    

