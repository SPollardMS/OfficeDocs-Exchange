---
title: Learn more about setting up a forest trust to support linked mailboxes
ms.prod: EXCHANGE
ms.assetid: f6f49363-697c-470f-befb-fedb9c9da70d
---


# Learn more about setting up a forest trust to support linked mailboxes

Linked mailboxes are mailboxes located in an Exchange forest (called a resource forest) that are accessed by users in a separate, trusted forest (called an account forest). This two-forest scenario allows organizations to centralize Exchange in a single resource forest, while allowing access to the Exchange organization by users with accounts in one or more account forests. So before you can create linked mailboxes, you must set up a trust between the Exchange forest and at least one account forest. Specifically, you have to create a one-way, outgoing trust so that the Exchange forest trusts the account forest.
  
    
    

The following figure illustrates the Exchange resource forest topology and the trust relationship between the two forests.
 **Resource forest topology and trust relationship**
  
    
    


  
    
    
![Complex Exchange organization with resource forest](images/ExPlanningArchitect_ComplexOrg_01.gif)
  
    
    

    
> [!NOTE]
> If you create a one-way outgoing trust where the Exchange forest trusts the account forest, you will be prompted for administrator credentials in the account forest whenever you create a linked mailbox. To create a linked mailbox without being prompted for administrator credentials in the account forest, you have to create a two-way trust, or create another one-way outgoing trust where the account forest also trusts the Exchange forest. This step requires administrator credentials in the account forest. 
  
    
    


## For more information

 [Windows Server 2003: Create a one-way, outgoing, forest trust for one side of the trust](https://go.microsoft.com/fwlink/?LinkId=264233)
  
    
    
 [Windows Server 2003: Create a one-way, outgoing, forest trust for both sides of the trust](https://go.microsoft.com/fwlink/p/?linkId=69130)
  
    
    
 [Windows Server 2008: Create a One-Way, Outgoing, Forest Trust for One Side of the Trust](https://go.microsoft.com/fwlink/?LinkId=264235)
  
    
    
 [Windows Server 2008: Create a One-Way, Outgoing, Forest Trust for Both Sides of the Trust](https://go.microsoft.com/fwlink/?LinkId=264236)
  
    
    
 [Windows Server 2012: Create a Forest Trust](https://go.microsoft.com/fwlink/?LinkId=264237)
  
    
    
 [Manage linked mailboxes](manage-linked-mailboxes.md)
  
    
    

