---
title: Learn more about providing credentials for an administrator account
ms.prod: EXCHANGE
ms.assetid: 1a8f56de-d718-47f6-9233-243b299123ff
---


# Learn more about providing credentials for an administrator account

> [!IMPORTANT]
> This feature of Exchange 2016 isn't fully compatible with Office 365 operated by 21Vianet in China and some feature limitations may apply. For more information, see  [Learn about Office 365 operated by 21Vianet](https://go.microsoft.com/fwlink/?LinkId=313640). 
  
    
    

When you create a migration endpoint or migrate mailboxes before a migration endpoint has been created, you have to provide credentials (user name and password) for an administrator account. For some types of migrations, you also have to provide an email address for a mailbox that you want to migrate. Exchange Online uses the credentials of this account and the Autodiscover service to detect the connection settings for the migration endpoint, which is typically a server in the Exchange organization that hosts the mailboxes you're migrating. Exchange Online also tests the connectivity to the mailbox that you provided the email address for to verify that the migration administrator account has the necessary permissions to access that mailbox. 
The following list identifies the administrator account for which you have to provide credentials for different migration types:
  
    
    


- **Cross-forest enterprise move:** An administrator account in the forest that hosts the mailboxes that you're migrating.
    
  
- **Remote move migration:** In a hybrid deployment, you can either migrate on-premises mailboxes to Office 365 (calledonboarding) or migrate Office 365 mailboxes to your on-premises organization (called offboarding). For both of these types of migration, you have to provide credentials for an administrator account in your on-premises Exchange organization.
    
  
- **Cutover Exchange migration:** An administrator account in the on-premises Exchange organization that hosts the mailboxes that you're migrating to Exchange Online.
    
  
- **Staged Exchange migration:** An administrator account in the on-premises Exchange organization that hosts the mailboxes that you're migrating to Exchange Online.
    
  

## For more information

 [Assign Permissions to Migrate Mailboxes to Exchange Online](http://technet.microsoft.com/library/3dcf0e78-e894-4e34-9955-1509d14707a0.aspx)
  
    
    
 [Create Migration Endpoints](http://technet.microsoft.com/library/11351cb5-b529-4b4d-a5de-45a494565a16.aspx)
  
    
    
 [Manage on-premises mailbox moves in Exchange 2016](manage-on-premises-mailbox-moves-in-exchange-2016.md)
  
    
    
 [Moving Mailboxes Between On-premises and Exchange Online Organizations in 2013 Hybrid Deployments](http://technet.microsoft.com/library/d6289f7b-f67e-48db-9570-9fd3c9547548.aspx)
  
    
    
 [Migrate Mailboxes to Exchange Online with a Staged Migration](http://technet.microsoft.com/library/9ecb3e28-c5fd-4e16-8d97-3496ebba0777.aspx)
  
    
    
 [Migrate All Mailboxes to Exchange Online with a Cutover Migration](http://technet.microsoft.com/library/582ae252-fb25-4321-9f93-4e34c8db0b50.aspx)
  
    
    

