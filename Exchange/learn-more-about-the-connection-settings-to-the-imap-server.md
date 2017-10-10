---
title: Learn more about the connection settings to the IMAP server
ms.prod: EXCHANGE
ms.assetid: 46768c73-8a01-435b-a65d-a068f082c59d
---


# Learn more about the connection settings to the IMAP server

An IMAP migration endpoint is used to migrate email items from mailboxes on an IMAP server to mailboxes in Exchange Online. It contains the connection settings for the source IMAP server that hosts the mailboxes that you want to migrate to Exchange Online. The migration endpoint also defines the number of mailboxes to migrate simultaneously during initial synchronization and the number of mailboxes to synchronize simultaneously duringincremental synchronization, which occurs once every 24 hours for selected migration types. During incremental synchronization, on-premises and Exchange Online mailboxes are synchronized so that new email sent to mailboxes on the IMAP server is copied to the corresponding Exchange Online mailbox.
  
    
    


Depending on whether any IMAP migration endpoints have been created in your Exchange Online organization, you have to do one of the following on the **IMAP migration configuration** page:
  
    
    


- **No migration endpoints have been created:** Configure the following settings:
    
  - *** IMAP server** Type the FQDN (also called the full computer name) of the IMAP server for the IMAP messaging system. This is required.
    
  
  - **Authentication** Select the authentication method used by the IMAP server. Options are `Basic` (the default), or `NTLM`. Use  `NTLM` if it's required by your IMAP server.
    
  
  - **Encryption** Select the encryption method used by the IMAP server. Options are `None`,  `SSL` (the default), or `TLS`.
    
  
  - *** Port** Type the TCP port number used to connect to the IMAP server. Use port 143 for unencrypted connections, port 143 for TLS connections, or port 993 (the default), for SSL connections. This is required.
    
  

    After you click **Next**, Exchange Online will use the settings to test the connection to the IMAP server. You have to successfully connect to the IMAP server to continue. If the connection is successful, Exchange Online creates a new migration endpoint using these connection settings. By default, this migration endpoint is configured to support 100 maximum concurrent migrations and 20 maximum incremental synchronizations.
    
    > [!TIP]
      > Although you can create the first IMAP migration endpoint when you create the first IMAP migration batch, it's a good idea to create migration endpoints before you create a migration batch. When you create a migration endpoint, Exchange Online tests the connection to the IMAP server. The migration endpoint isn't created unless Exchange Online can successfully connect to the IMAP server. This lets you troubleshoot and resolve connectivity issues before you create a migration batch. Otherwise, you have to cancel the migration batch and resolve any connectivity issues before you can create a migration batch. 
- **One migration endpoint has been created:** The connection settings from the IMAP migration endpoint are displayed in read-only boxes. Verify the connection settings, and then click **Next**.
    
  

## For more information

 [Create Migration Endpoints](http://technet.microsoft.com/library/11351cb5-b529-4b4d-a5de-45a494565a16.aspx)
  
    
    
 [Migrate Email from an IMAP Server to Exchange Online Mailboxes](http://technet.microsoft.com/library/16090006-7298-4400-a892-655353db1c63.aspx)
  
    
    

