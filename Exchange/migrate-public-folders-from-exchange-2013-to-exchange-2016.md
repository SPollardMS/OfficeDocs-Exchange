---
title: Migrate public folders from Exchange 2013 to Exchange 2016
ms.prod: EXCHANGE
ms.assetid: 0f98801d-ad5c-4109-a021-63645e9c9ca2
---


# Migrate public folders from Exchange 2013 to Exchange 2016
 **Summary:** Learn how to migrate on-premises public folders from Exchange 2013 to Exchange 2016.
In order to migrate your Exchange 2013 public folders to Exchange 2016, you need to move all of your Exchange 2013 public folder mailboxes to an Exchange 2016 server.
  
    
    

Before you move your public folder mailboxes, here are some things you should consider:
- **Exchange 2016 capacity** The size of your public folder mailboxes might vary significantly depending on how many public folders and public folder mailboxes you have. Make sure the Exchange 2016 servers where you'll move your public folder mailboxes have enough storage capacity.
    
  
- **Time to move** It might take a while for your public folder mailboxes to be moved to Exchange 2016. Things that could impact how long it'll take include public folder mailbox size, the number of public folder mailboxes, available network capacity, and other factors. The good news is that your public folders will remain available during the public folder mailbox move. There will only be a brief window as the move completes where public folders may not be available.
    
  

## How do I do this?

Perform the following steps to move your public folder mailboxes from Exchange 2013 to Exchange 2016.
  
    
    

1. Open the Exchange 2013 on your Exchange 2016 Mailbox server.
    
  
2. Run the following command to get a list of Exchange 2016 mailbox databases that you can move your public folder mailboxes to. You can use this information to check how much drive space is available for each Exchange 2016 mailbox database.
    
  ```
  
Get-ExchangeServer | Where {($_.AdminDisplayVersion -Like "Version 15.1*") -And ($_.ServerRole -Like "*Mailbox*")} | Get-MailboxDatabase | Format-Table Name, EdbFilePath, Server
  ```

3. Run the following command to get a list of Exchange 2013 public folder mailboxes. The list that this command creates includes the public folder mailbox name, its size, and what Exchange 2013 server it's on.
    
  ```
  Get-ExchangeServer | Where {($_.AdminDisplayVersion -Like "Version 15.0*") -And ($_.ServerRole -Like "*Mailbox*")} | Get-Mailbox -PublicFolder | Get-MailboxStatistics | Format-Table DisplayName, TotalItemSize, ServerName
  ```

4. You can use the information from the previous command to decide which Exchange 2016 server (if you have more than one) to move some or all of your public folder mailboxes to. For example, you might not want to move three large public folder mailboxes to a server with low available drive space. You can also decide whether you want to move all public folder mailboxes at once, all public folder mailboxes on a specific server, or a specific public folder mailbox. Choose the command that fits the kind of move you want to do. Replace the Exchange server, database, and public folder mailbox names with your own.
    
  - Move all Exchange 2013 public folder mailboxes at once.
    
  ```
   Get-ExchangeServer | Where {($_.AdminDisplayVersion -Like "Version 15.0*") -And ($_.ServerRole -Like "*Mailbox*")} | Get-Mailbox -PublicFolder | New-MoveRequest -TargetDatabase Ex2016MbxDatabase
  ```

  - Move all public folder mailboxes on a specific Exchange 2013 server at once.
    
  ```
  Get-Mailbox -PublicFolder -Server Ex2013Mbx | New-MoveRequest -TargetDatabase Ex2016MbxDatabase
  ```

  - Move a specific Exchange 2013 public folder mailbox.
    
  ```
  New-MoveRequest "Sales Public Folder Mailbox" -TargetDatabase Ex2016MbxDatabase
  ```

5. Use the following command to see the status of the move requests you created. Depending on the size of the public folder mailboxes you're moving and your available network capacity, it could take several hours or days for the moves to complete. For a list of possible status values that can be returned, see the "How do I know this worked?" section.
    
  ```
  Get-MoveRequest
  ```


## How do I know this worked?

To verify that you've successfully migrated all of your public folders to Exchange 2016, you can check the status of the move requests you created, and also check the location of the public folder mailboxes.
  
    
    
Do the following to check the status of your move requests:
  
    
    

1. Open the Exchange Management Shell on your Exchange 2016 Mailbox server.
    
  
2. Run the following command to see the status of the move requests you created. 
    
  ```
  Get-MoveRequest
  ```

The command above will return each move request you created along with one of the following statuses:
  
    
    

- **Completed** The public folder mailbox was successfully moved to the target Exchange 2016 mailbox database.
    
  
- **CompletedWithWarning** The public folder mailbox was moved to the target Exchange 2016 mailbox database, but one or more issues were encountered during the move. You can find more information by viewing the move report that was delivered to the Administrator mailbox.
    
  
- **CompletionInProgress** The public folder mailbox's move to the target Exchange 2016 mailbox database is in its final stages. Public folders hosted in this mailbox may be unavailable for a brief period of time while the move is finalized.
    
  
- **InProgress** The public folder mailbox's move to the target Exchange 2016 mailbox database is underway. Public folders hosted in this mailbox are available during this portion of the move.
    
  
- **Failed** The public folder mailbox's move failed for one or more reasons. You can find more information by viewing the move report that was delivered to the Administrator mailbox.
    
  
- **Queued** The public folder mailbox's move has been submitted but the move hasn't started yet.
    
  
- **AutoSuspended** The public folder mailbox's move is ready to enter its final stages but won't proceed further until you manually resume the move. This can be helpful if you want to choose the time a move will complete. Moves can be automatically suspended when they're created by using the _SuspendWhenReadyToComplete_ switch on the **New-MoveRequest** cmdlet. To resume the move when you're ready, use the **Resume-MoveRequest** cmdlet.
    
  
- **Suspended** The public folder mailbox's move has been suspended by **Suspend-MoveRequest** cmdlet and won't proceed further until you manually resume the move. To resume the move when you're ready, use the **Resume-MoveRequest** cmdlet.
    
  
Do the following to view the location of your public folder mailboxes after their move request has completed:
  
    
    

1. Open the Exchange Management Shell on your Exchange 2016 Mailbox server.
    
  
2. Run the following command to see the location of your public folder mailboxes. 
    
  ```
  Get-Mailbox -PublicFolder | Get-MailboxStatistics | Format-Table DisplayName, TotalItemSize, ServerName
  ```

In the list public folder mailboxes that are returned, verify that they've each been moved to an Exchange 2016 Mailbox server.
  
    
    
Having problems? Ask for help in the Exchange forums. Visit the forums at:  [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612),  [Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or  [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351).
  
    
    

