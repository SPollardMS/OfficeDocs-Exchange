---
title: Learn more about MRS Proxy
ms.prod: EXCHANGE
ms.assetid: 46372ada-07e4-4f81-b626-18a61fce03f8
---


# Learn more about MRS Proxy

When you use the move request cmdlets **New-MigrationBatch** and **New-MoveRequest** to move mailboxes, the move requests are processed by the following two services:
  
    
    


- **Microsoft Exchange Mailbox Replication service** MRS resides on an Exchange 2013 Client Access server and is the service that moves mailboxes from the source database to the target database.
    
  
- **Microsoft Exchange Mailbox Replication Proxy** Remote mailbox moves work over the Internet by way of the MRSProxy service.
    
  

You can start and stop the MRS services as you would any service. There's a sharing mechanism between all instances of MRS so that no two servers will attempt to perform the same move request.
  
    
    

For more information about moving mailboxes, see  [Manage on-premises mailbox moves in Exchange 2016](manage-on-premises-mailbox-moves-in-exchange-2016.md) and [Mailbox moves in Exchange 2016](mailbox-moves-in-exchange-2016.md).
