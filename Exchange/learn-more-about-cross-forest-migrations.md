---
title: Learn more about cross-forest migrations
ms.prod: EXCHANGE
ms.assetid: d10e8624-bcb9-40fc-9c98-d8563f3835d2
---


# Learn more about cross-forest migrations

> [!IMPORTANT]
> This feature of Exchange 2016 isn't fully compatible with Office 365 operated by 21Vianet in China and some feature limitations may apply. For more information, see  [Learn about Office 365 operated by 21Vianet](https://go.microsoft.com/fwlink/?LinkId=313640). 
  
    
    

Exchange 2013 supports remote and cross-forest mailbox moves and migrations. You can move a mailbox from a source Exchange 2013 forest to a target Exchange 2013 forest. You can move your mailboxes via the Exchange 2013 Administration Center or the **New-MigrationBatch** and **New-MoveRequest** cmdlets. To move a mailbox from an Exchange 2013 to another Exchange 2013 forest, the Exchange 2013 target forest must contain a valid mail-enabled user with a specified set of Active Directory attributes. If there is at least one Exchange 2013 Client Access server deployed in the forest, the forest is considered an Exchange 2010 forest.
You can generate a .csv file containing a list of mailbox identities from the source forest. Then, you can pipe the content of this file into the script to bulk create the target mail-enabled users.
  
    
    

For more information about cross-forest moves, see  [Mailbox moves in Exchange 2016](mailbox-moves-in-exchange-2016.md) and [Manage on-premises mailbox moves in Exchange 2016](manage-on-premises-mailbox-moves-in-exchange-2016.md).
