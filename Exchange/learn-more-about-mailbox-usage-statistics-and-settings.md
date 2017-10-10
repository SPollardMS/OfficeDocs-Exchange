---
title: Learn more about mailbox usage statistics and settings
ms.prod: EXCHANGE
ms.assetid: 191eb983-7abf-40a3-8c68-d42abbe6bc57
---


# Learn more about mailbox usage statistics and settings

You can use the **Mailbox Usage** page to view or change the mailbox storage quota and deleted item retention settings for the mailbox. These settings are configured by default when the mailbox is created. They use the values that are configured for the mailbox database and apply to all mailboxes in that database. You can customize these settings for each mailbox instead of using the mailbox database defaults.
  
    
    


> [!NOTE]
> The following settings are available only for Exchange on-premises mailboxes. They aren't available in Exchange Online. Check out  [Message and Recipient Limits in Exchange Online](http://technet.microsoft.com/library/0932b938-43c8-40b8-a037-4780a3349e82.aspx) for mailbox and message limits in Exchange Online.
  
    
    


> [!TIP]
> To view or change the mailbox storage quota or deleted item retention settings for a mailbox database, navigate to **Servers** > **Databases**. Select a database, click **Edit**
  
    
    
![Edit icon](images/ITPro_EAC_EditIcon.png)
  
    
    
, and then click **Limits**. For more information, see  [Manage mailbox databases in Exchange 2016](manage-mailbox-databases-in-exchange-2016.md). 
  
    
    

The following list describes the information and settings on the **Mailbox Usage** page.
- **Last logon** This read-only box displays the last time that the user signed in to their mailbox.
    
  
- **Mailbox usage** This area shows the total size of the mailbox and the percentage of the total mailbox quota that has been used.
    
  

> [!NOTE]
> To obtain the information that's displayed in the previous two boxes, the EAC queries the mailbox database that hosts the mailbox. If the EAC isn't able to communicate with the Exchange store that contains the mailbox database, these boxes will be blank. A warning message will be displayed if the user hasn't signed in to the mailbox for the first time. 
  
    
    

Click **More options** to view or change the mailbox storage quota and the deleted item retention settings for the mailbox.
- **Storage quota settings** You can customize the following settings for the mailbox instead of using the mailbox database defaults by clicking **Customize the settings for this mailbox**, and then providing a new value. 
    
  - **Issue a warning at (GB)** This box displays the maximum storage limit before a warning is issued to the user. If the mailbox size reaches or exceeds the value specified, Exchange sends a warning message to the user.
    
  
  - **Prohibit send at (GB)** This box displays theprohibit send limit for the mailbox. If the mailbox size reaches or exceeds the specified limit, Exchange prevents the user from sending new messages and displays a descriptive error message.
    
  
  - **Prohibit send and receive at (GB)** This box displays theprohibit send and receive limit for the mailbox. If the mailbox size reaches or exceeds the specified limit, Exchange prevents the mailbox user from sending new messages and won't deliver any new messages to the mailbox. Any messages sent to the mailbox are returned to the sender with a descriptive error message.
    
  

    > [!NOTE]
      > The value for any of the previous storage quota settings can range from 0 through 2047 gigabytes (GB). 
- **Deleted item retention settings** You can also customize these settings for the mailbox instead of using the mailbox database defaults.
    
  - **Keep deleted items for (days)** This box displays the length of time that deleted items are retained before they're permanently deleted and can't be recovered by the user. When the mailbox is created, this value is based on the deleted item retention settings configured for the mailbox database. By default, a mailbox database is configured to retain deleted items for 14 days. The value for this property can range from 0 through 24855 days.
    
  
  - **Don't permanently delete items until the database is backed up** Select this check box to prevent mailboxes and email messages from being deleted until after the mailbox database on which the mailbox is located has been backed up.
    
  

## For more information

 [Manage User Mailboxes](http://technet.microsoft.com/library/957ca61c-1fa1-42ab-a0e6-8488e4782566.aspx)
  
    
    
 [Message and Recipient Limits in Exchange Online](http://technet.microsoft.com/library/0932b938-43c8-40b8-a037-4780a3349e82.aspx)
  
    
    

