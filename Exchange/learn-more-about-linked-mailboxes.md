---
title: Learn more about linked mailboxes
ms.prod: EXCHANGE
ms.assetid: 5ea5af67-5952-45b3-a558-2dca88c30ad8
---


# Learn more about linked mailboxes

Linked mailboxes are mailboxes that are accessed by users in a separate, trusted forest. Linked mailboxes may be necessary for organizations that deploy Exchange in a resource forest. The resource forest scenario allows an organization to centralize Exchange in a single forest, while allowing access to the Exchange organization with user accounts in one or more trusted forests. The user account that accesses the linked mailbox doesn't exist in the forest where Exchange is deployed. When you create a linked mailbox, a disabled user account is created in the same forest as Exchange and is associated with the linked mailbox.
  
    
    

The following figure illustrates the relationship between the linked user account used to access the linked mailbox and the disabled user account in the Exchange resource forest associated with the linked mailbox.
  
    
    
![Complex Exchange organization with resource forest](images/ExPlanningArchitect_ComplexOrg_01.gif)
  
    
    

  
    
    

  
    
    

## For more information

 [Manage linked mailboxes](manage-linked-mailboxes.md)
  
    
    
 [Learn more about setting up a forest trust to support linked mailboxes](learn-more-about-setting-up-a-forest-trust-to-support-linked-mailboxes.md)
  
    
    

