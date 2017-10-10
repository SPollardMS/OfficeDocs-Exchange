---
title: Learn more about configuring mailbox features
ms.prod: EXCHANGE
ms.assetid: 6b1a0fe4-5af1-4f32-9c30-d3e350cc3896
---


# Learn more about configuring mailbox features

> [!IMPORTANT]
> This feature of Exchange 2016 isn't fully compatible with Office 365 operated by 21Vianet in China and some feature limitations may apply. For more information, see  [Learn about Office 365 operated by 21Vianet](https://go.microsoft.com/fwlink/?LinkId=313640). 
  
    
    

When you edit a user mailbox, a linked mailbox, or a shared mailbox, you can view or edit the following features on the **Mailbox features** page. For more information, see [Manage User Mailboxes](http://technet.microsoft.com/library/957ca61c-1fa1-42ab-a0e6-8488e4782566.aspx).
- **Sharing policy** A sharing policy controls how users in your organization can share calendar and contact information with users outside your Exchange organization. The Default Sharing Policy is assigned to mailboxes when they're created. You can change the sharing policy that's assigned to the user by selecting a different one from the drop-down list.
    
  
- **Role assignment policy** The role assignment policy specifies the role-based access control (RBAC) roles that are assigned to the user and control which mailbox and distribution group configuration settings users can modify. You can change the role assignment policy that's assigned to the user by selecting a different one from the drop-down list. For more information, see:
    
  -  [Understanding Management Role Assignment Policies](http://technet.microsoft.com/library/25913e43-326a-4371-90b5-021a35f100fe.aspx)
    
  
  -  [Manage role assignment policies](manage-role-assignment-policies.md)
    
  
- **Retention policy** A retention policy is a group of retention tags that are applied to the user's mailbox. They allow you to control how long to keep items in users' mailboxes and define what action to take on items that have reached a certain age. A retention policy isn't assigned to a mailbox when it's created. You can assign a retention policy to the user by selecting one from the drop-down list. For more information, see [Messaging records management in Exchange 2016](messaging-records-management-in-exchange-2016.md)
    
  
- **Address book policy** This box shows the address book policy applied to the mailbox. An address book policy allows you to segment users into specific groups to provide customized views of the address book. You can apply or change the address book policy applied to the mailbox by selecting one from the drop-down list. For more information, see [Address book policies in Exchange 2016](address-book-policies-in-exchange-2016.md).
    
  
- **Unified Messaging** By default, this feature is disabled. When you enable Unified Messaging (UM) for a user, the user will be able to use your organization's UM features and a default set of UM properties are applied to the user. For information about how to enable UM for a user, see [Enable a User for Unified Messaging](http://technet.microsoft.com/library/ad027767-5e14-4cb1-9f8a-0791d9188db5.aspx).
    
    > [!NOTE]
      > A UM dial plan and a UM mailbox policy must exist before you can enable UM for a user. 
- **Mobile Devices** Use this section to view and change the settings for Exchange ActiveSync, which is enabled by default. Exchange ActiveSync enables access to an Exchange mailbox from a mobile device. You can disable this feature by clicking **Disable Exchange ActiveSync**.
    
  
- **Outlook Web App** This feature is enabled by default. Outlook Web App enables access to an Exchange mailbox from a web browser. You can disable Outlook Web App for the mailbox, and add or change an Outlook Web App mailbox policy for the mailbox.
    
  
- **IMAP** This feature is enabled by default. Click **Disable** to disable IMAP for the mailbox.
    
  
- **POP3** This feature is enabled by default. Click **Disable** to disable POP3 for the mailbox.
    
  
- **MAPI** This feature is enabled by default. MAPI enables access to an Exchange mailbox from a MAPI client such as Outlook.
    
  
- **Litigation hold** This feature is disabled by default. Litigation hold preserves deleted mailbox items and records changes made to mailbox items. Deleted items and all instances of changed items are returned in a discovery search. You can place a mailbox on litigation hold by clicking **Enable**. If the mailbox is on litigation hold, you can remove the litigation hold by clicking **Disable**.
    
  
- **Archiving** If an archive mailbox doesn't exist for the user, this feature is disabled. To enable an archive mailbox, click **Enable**. If the user has an archive mailbox, the size of the archive mailbox and usage statistics are displayed. For more information about archive mailboxes, see  [In-Place Archiving in Exchange 2016](in-place-archiving-in-exchange-2016.md).
    
  
- **Delivery Options** Use these settings to forward email messages sent to the user to another recipient and to set the maximum number of recipients that the user can send a message to. Click **View details** to view and change these settings.
    
  
- **Message Size Restrictions** These settings control the size of messages that the user can send and receive. Click **View details** to view and change maximum size for sent and received messages.
    
  
- **Message Delivery Restrictions** These settings control who can send email messages to this user. Click **View details** to view and change these restrictions.
    
  

