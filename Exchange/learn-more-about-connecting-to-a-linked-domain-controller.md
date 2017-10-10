---
title: Learn more about connecting to a linked domain controller
ms.prod: EXCHANGE
ms.assetid: cb979095-1810-457e-be19-9943ba1013f7
---


# Learn more about connecting to a linked domain controller

When you create a new linked mailbox for a user in a trusted forest, Exchange has to connect to a domain controller in that forest. It connects to retrieve a list of user accounts from which you can select the master account for the linked mailbox. In other words, the linked master account is the user account in the trusted account forest that's associated with the linked mailbox in your Exchange organization.
  
    
    

If you or your organization has configured a one-way outgoing trust, where the Exchange forest trusts the account forest, you'll be prompted for administrator credentials in the account forest so that you can gain access to a domain controller to select a master account for the linked mailbox. However, if you've created a two-way trust or have created another one-way outgoing trust where the account forest trusts the Exchange forest, you won't be prompted for administrator credentials in the account forest.
## For more information

 [Manage linked mailboxes](manage-linked-mailboxes.md)
  
    
    
 [Windows Server 2003: Create a one-way, outgoing, forest trust for one side of the trust](https://go.microsoft.com/fwlink/?LinkId=264233)
  
    
    
 [Windows Server 2003: Create a one-way, outgoing, forest trust for both sides of the trust](https://go.microsoft.com/fwlink/p/?linkId=69130)
  
    
    
 [Windows Server 2008: Create a One-Way, Outgoing, Forest Trust for One Side of the Trust](https://go.microsoft.com/fwlink/?LinkId=264235)
  
    
    
 [Windows Server 2008: Create a One-Way, Outgoing, Forest Trust for Both Sides of the Trust](https://go.microsoft.com/fwlink/?LinkId=264236)
  
    
    
 [Windows Server 2012: Create a Forest Trust](https://go.microsoft.com/fwlink/?LinkId=264237)
  
    
    

