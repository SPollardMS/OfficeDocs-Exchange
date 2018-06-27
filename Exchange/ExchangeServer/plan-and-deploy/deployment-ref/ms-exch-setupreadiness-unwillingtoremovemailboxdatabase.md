---
title: "Cannot remove mailbox database [UnwillingToRemoveMailboxDatabase]"
ms.author: dstrome
author: dstrome
manager: serdars
ms.date: 7/22/2015
ms.audience: ITPro
ms.topic: reference
f1_keywords:
- 'ms.exch.setupreadiness.UnwillingToRemoveMailboxDatabase'
ms.prod: exchange-server-itpro
localization_priority: Normal
ms.assetid: 5881e4c0-c2e2-48db-84b4-7f9ce3cf46a7
description: "Microsoft Exchange Server 2016 Setup can't continue because it can't remove a user mailbox database from the local server without incurring potential data loss."
---

# Cannot remove mailbox database [UnwillingToRemoveMailboxDatabase]

Microsoft Exchange Server 2016 Setup can't continue because it can't remove a user mailbox database from the local server without incurring potential data loss.
  
 Exchange 2016 Setup determines whether all mailbox databases have been removed from the server before the Mailbox server role is removed. However, user mailboxes might still remain on the server.
  
To resolve this issue, move any mailboxes on the server to another Exchange server or, if the mailboxes and the data contained within them are no longer required, disable the mailboxes. Then run Exchange 2016 Setup again.
  
- For more information about how to identify a mailbox in the database, see [Get-Mailbox](http://technet.microsoft.com/library/8a5a6eb9-4a75-47f9-ae3b-a3ba251cf9a8.aspx).
    
- For more information about how to move a mailbox, see [Mailbox moves in Exchange 2016](../../recipients/mailbox-moves.md).
    
- For more information about how to disable a mailbox, see [Disable-Mailbox](http://technet.microsoft.com/library/33be55a3-1880-437d-a631-c1cca1736421.aspx).
    
- For more information about how to remove a mailbox database, see [Manage mailbox databases in Exchange 2016](../../architecture/mailbox-servers/manage-databases.md).
    
Having problems? Ask for help in the Exchange forums. Visit the forums at: [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351).
  
Did you find what you're looking for? Please take a minute to [send us feedback](mailto:ExchangeHelpFeedback@microsoft.com&subject=Exchange%202016%20help%20feedback&Body=Thanks%20for%20taking%20the%20time%20to%20send%20us%20feedback!%20We%20strive%20to%20respond%20to%20every%20message%20we%20receive,%20even%20though%20it%20might%20take%20us%20a%20while.%20Let%20us%20know%20what%20you%20think%20about%20Exchange%20content:%20What%20are%20we%20doing%20right%3F%20How%20can%20we%20make%20help%20better%3F%0APlease%20note%20that%20we're%20unable%20to%20respond%20to%20requests%20for%20support%20submitted%20via%20this%20email%20address.%20If%20you%20need%20help,%20please%20contact%20Exchange%20Server%20support%20at%20http://go.microsoft.com/fwlink/p/%3FLinkId=402506.%0AThanks!%0AThe%20Exchange%20Server%20Content%20Publishing%20team) about the information you were hoping to find.
  

