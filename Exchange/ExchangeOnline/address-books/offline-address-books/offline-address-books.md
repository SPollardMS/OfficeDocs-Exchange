---
title: "Offline address books in Exchange Online"
ms.author: kwekua
author: kwekua
manager: scotv
ms.date: 6/19/2017
ms.audience: ITPro
ms.topic: overview
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 3f4b2c64-6cbc-445f-bf65-05b8fdfe9a0b
description: "Learn about offline address books in Exchange Online (Office 365 for Business)."
---

# Offline address books in Exchange Online

Learn about offline address books in Exchange Online (Office 365 for Business).
  
An offline address book (OAB) is a copy of an address list collection that's been downloaded so an Office 365 user can access the address book while disconnected from the on-premises server. Exchange generates the new OAB files and then compresses the files and places them on a local share. You can decide which address lists are made available to users who work offline, and you can also configure the method by which the address books are distributed.
  
To learn more about address lists, see [Address lists](../../address-books/address-lists/address-lists.md).
  
Looking for the Exchange 2016 version of this topic? See [Offline Address Books in Exchange 2016](http://technet.microsoft.com/library/a6bcb072-4ab9-400e-a5d0-c05264629097.aspx). 
  
Looking for the Exchange Server 2013 topic? See [Offline Address Books in Exchange Server 2013](http://technet.microsoft.com/library/a6bcb072-4ab9-400e-a5d0-c05264629097.aspx)
  
> [!NOTE]
>  The Update-AddressList and Update-GlobalAddressList cmdlets aren't available in Exchange Online. 
  
## Download an offline address book

You can use Outlook Web App to download the GAL. 
  
1. Open Outlook Web App in Internet Explorer.
    
2. Click **Tools**, and then click **Send/Receive**.
    
3. Click **Download Address Book**. The offline address book dialog box is displayed.
    
4. Check the **Download changes since last send/receive** option. 
    
5. Select **Full details** to download all notes and details with each contact in hour address book or click **No details** to download only the contact and their contact information. 
    
6. Click **Choose Address Book** and then click **Global Address List**.
    
7. Click **OK**. The global address list is downloaded and saved to your computer.
    
### Conditions that cause a full download of the OAB

There are circumstances in which Outlook Web App will perform a full OAB download. These include:
  
- There is no OAB on the client computer. This condition may occur if Outlook has not performed an initial complete synchronization.
    
- There is a differential file missing on the server. Outlook cannot update to the current version without it. This behavior may occur if one of the following conditions is true:
    
  - You did not start Outlook (to log on to your Exchange mailbox) for more than 30 days. The server policy permits only 30 days of differential files.
    
  - There was an error on the server, and it did not generate the differential file for a day.
    
- The version on the server and the version on the client do not match. There is a more recent version of the OAB present on the server. For example, Version 4 (Unicode OAB) is now available, and you previously downloaded a Version 3a OAB.
    
- Applying changes to the OAB failed. For example, differential files are corrupted on the server. Corruption may occur if the server goes down during differential file generation.
    
- One or more OAB files are not present on the client computer. For example, a user accidentally deletes one of the OAB files on the user's computer.
    
- A previous full download failed, and Outlook has to start from the beginning.
    
- You manually download the full OAB.
    
- The public folder store containing the only copy of the OAB is lost, and replaced with a new database and new OAB. To prevent this from occurring, it is recommended that you replicate the OAB folders to at least two public folder servers (the original server and one replica).
    
- When Outlook is initially deployed in Cached Exchange Mode, it will download a full OAB. If you are initially deploying a large number of Outlook clients using Cached Exchange Mode, this will cause a large download of the full OAB as a new OAB is downloaded by each new install of Outlook.
    
- The public folder that Outlook uses for the OAB is based on the **msExchUseOAB** attribute of the private information store. If a mailbox is moved to a different server with a different OAB, Outlook will download a new OAB. If a large number of mailboxes are moved between mailbox stores and the target store is configured to use a different offline address list, this will cause a full OAB download for these mailboxes. 
    
- When a mailbox is moved between versions of Exchange, the server will direct Outlook to the latest Unicode version of the OAB and download a new version of the OAB. If a large number of mailboxes are moved, this will trigger a large number of full OAB downloads for these mailboxes.
    
- When a user has multiple MAPI profiles on the same Outlook client computer and they switch between the two profiles that both use Cached Exchange Mode, multiple full OAB downloads of the same OAB files will occur. Outlook supports only one OAB per user account on a computer. If you have multiple profiles, only one profile can download the OAB. If you have to use two or more profiles that use Cached Exchange Mode, make sure that one of the profiles is configured to not download the OAB.
    

