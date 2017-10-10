---
title: Learn more about selecting migration endpoints
ms.prod: EXCHANGE
ms.assetid: c6368d2d-8eec-4d01-b73d-2ef3bb4faad7
---


# Learn more about selecting migration endpoints

> [!IMPORTANT]
> This feature of Exchange 2016 isn't fully compatible with Office 365 operated by 21Vianet in China and some feature limitations may apply. For more information, see  [Learn about Office 365 operated by 21Vianet](https://go.microsoft.com/fwlink/?LinkId=313640). 
  
    
    

Microsoft Exchange Server 2016 introduces the concept of batch moves and migration endpoints. Migration endpoints are management objects that describe the remote server and the connections that can be associated with one or more batches. Migration endpoints capture the remote server information and then persist the required credentials for migrating the data and the source throttling settings. You can use migration endpoints to configure settings for remote and cross-forest moves.
The following list describes the types of moves that support migration endpoints:
  
    
    


- **Cross-forest move** This type moves mailboxes between two different on-premises Exchange forests. Cross-forest moves require the use of a **RemoteMove** endpoint. For more information, see [Prepare mailboxes for cross-forest move requests](prepare-mailboxes-for-cross-forest-move-requests.md) and [Manage on-premises mailbox moves in Exchange 2016](manage-on-premises-mailbox-moves-in-exchange-2016.md).
    
  
- **Remote moves** Like a cross-forest move, remote moves also require the use of a RemoteMove endpoint. Following are descriptions of various types of remote moves:
    
  - In a hybrid deployment, a remote move involves onboarding oroffboarding migrations. An onboarding migration moves mailboxes from an on-premises Exchange organization to Exchange Online in Office 365 and uses a RemoteMove endpoint as the source endpoint of the migration batch. An offboarding migration moves mailboxes from Exchange Online in Office 365 to an on-premises Exchange organization and uses a **RemoteMove** endpoint as the target endpoint of the migration batch. For more information, see [Prepare mailboxes for cross-forest move requests](prepare-mailboxes-for-cross-forest-move-requests.md).
    
  
  - In a staged Exchange migration, a remote move is typically used to migrate mailboxes to Exchange Online over a period of a few weeks or months. Staged migrations are used by organizations that plan to eventually move all mailboxes to Exchange Online and completely transition their on-premises Exchange organization to Exchange Online. For more information, see **Migrate Mailboxes to Exchange Online with a Staged Migration**.
    
  
  - In a cutover Exchange migration, all the mailboxes and corresponding mailbox data from your on-premises Exchange organization are migrated to Exchange Online in a single migration batch over the course of a few days. All on-premises mailboxes are migrated in preparation for moving your entire organization to Office 365 and Exchange Online. After mailboxes are migrated to Exchange Online, the corresponding user accounts are managed in Office 365. For more information, see **Migrate All Mailboxes to Exchange Online with a Cutover Migration**.
    
  
  - In an IMAP migration, you use Exchange management tools to migrate the contents of user mailboxes from an IMAP messaging system to Exchange Online mailboxes. Only mailbox items are migrated from the IMAP messaging system to Exchange Online. Exchange Online mailboxes must already exist to use an IMAP migration. For more information, see **Migrate Email from an IMAP Server to Exchange Online Mailboxes**.
    
  
For more information, see **Create Migration Endpoints**.
