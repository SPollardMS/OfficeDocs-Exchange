---
title: "Recipients Permissions"
ms.author: dmaguire
author: msdmaguire
manager: serdars
ms.date: 6/12/2018
ms.audience: ITPro
ms.topic: reference
ms.prod: exchange-server-itpro
localization_priority: Normal
ms.assetid: 5b690bcb-c6df-4511-90e1-08ca91f43b37
description: "Summary: Learn about permissions that are required to manage recipients in Exchange Server 2016."
---

# Recipients Permissions

 **Summary**: Learn about permissions that are required to manage recipients in Exchange Server 2016.
  
The permissions required to perform tasks to manage recipients vary depending on the procedure being performed or the cmdlet you want to run.
  
To find out what permissions you need to perform the procedure or run the cmdlet, do the following:
  
1. In the table below, find the feature that is most related to the procedure you want to perform or the cmdlet you want to run.
    
2. Next, look at the permissions required for the feature. You must be assigned one of those role groups, an equivalent custom role group, or an equivalent management role. You can also click on a role group to see its management roles. If a feature lists more than one role group, you only need to be assigned one of the role groups to use the feature. For more information about role groups and management roles, see **Understanding Role Based Access Control**.
    
3. Now, run the **Get-ManagementRoleAssignment** cmdlet to look at the role groups or management roles assigned to you to see if you have the permissions that are necessary to manage the feature.
    
    > [!NOTE]
    > You must be assigned the Role Management management role to run the **Get-ManagementRoleAssignment** cmdlet. If you don't have permissions to run the **Get-ManagementRoleAssignment** cmdlet, ask your Exchange administrator to retrieve the role groups or management roles assigned to you.
  
If you want to delegate the ability to manage a feature to another user, see **Delegate a Management Role**.
  
## Mailbox server permissions

Users who are assigned the View-Only Management role group can view the configuration of the features in the following table. For more information, see **View Only Organization Management**.
  
|**Feature**|**Permissions required**|
|:-----|:-----|
|Calendar repair, server configuration  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> [Server Management](http://technet.microsoft.com/library/30cbc4de-adb3-42e8-922f-7661095bdb8c.aspx) <br/> |
|Delegating Mailbox servers  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> |
|Email address policies  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> [Server Management](http://technet.microsoft.com/library/30cbc4de-adb3-42e8-922f-7661095bdb8c.aspx) <br/> |
|Exchange Search  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> [View-Only Organization Management](http://technet.microsoft.com/library/c514c6d0-0157-4c52-9ec6-441d9a30f3df.aspx) <br/> [Server Management](http://technet.microsoft.com/library/30cbc4de-adb3-42e8-922f-7661095bdb8c.aspx) <br/> |
|Exchange Search - diagnostics  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> [View-Only Organization Management](http://technet.microsoft.com/library/c514c6d0-0157-4c52-9ec6-441d9a30f3df.aspx) <br/> Support Diagnostics role  <br/> **Note:**: The Support Diagnostics role isn't assigned to a role group. For more information, see [Add a Role to a User or USG](http://technet.microsoft.com/library/ae5608de-a141-4714-8876-bce7d2a22cb5.aspx).  <br/> |
|Group metrics  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> [Server Management](http://technet.microsoft.com/library/30cbc4de-adb3-42e8-922f-7661095bdb8c.aspx) <br/> |
|Import Export  <br/> |Mailbox Import Export role  <br/> **Note:**: The Mailbox Import Export role isn't assigned to a role group. For more information, see [Mailbox Import Export Role](http://technet.microsoft.com/library/d7cdce7a-6c46-4750-b237-d1c1773e8d28.aspx).  <br/> |
|Mailbox Assistants  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> [Server Management](http://technet.microsoft.com/library/30cbc4de-adb3-42e8-922f-7661095bdb8c.aspx) <br/> |
|Mailbox moves  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> [Recipient Management](http://technet.microsoft.com/library/669d602e-68e3-41f9-a455-b942d212d130.aspx) <br/> |
|Mailbox recovery  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> |
|Mailbox repair request  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> [Server Management](http://technet.microsoft.com/library/30cbc4de-adb3-42e8-922f-7661095bdb8c.aspx) <br/> [Recipient Management](http://technet.microsoft.com/library/669d602e-68e3-41f9-a455-b942d212d130.aspx) <br/> |
|Mailbox restore request  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> |
|Mailbox server configuration  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> [Server Management](http://technet.microsoft.com/library/30cbc4de-adb3-42e8-922f-7661095bdb8c.aspx) <br/> |
|Manage Exchange Search Indexer service on a Mailbox server  <br/> |Local Administrator on the Mailbox server  <br/> |
|MAPI connectivity  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> [Server Management](http://technet.microsoft.com/library/30cbc4de-adb3-42e8-922f-7661095bdb8c.aspx) <br/> |
|OAB virtual directories  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> [Server Management](http://technet.microsoft.com/library/30cbc4de-adb3-42e8-922f-7661095bdb8c.aspx) <br/> |
|Remove store mailbox  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> [Server Management](http://technet.microsoft.com/library/30cbc4de-adb3-42e8-922f-7661095bdb8c.aspx) <br/> |
   
## Calendar and sharing permissions
<a name="calendar"> </a>

Users who are assigned the View-Only Management role group can view the configuration of the features in the following table. For more information, see **View Only Organization Management**.
  
|**Feature**|**Permissions required**|
|:-----|:-----|
|Calendar configuration  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> [Recipient Management](http://technet.microsoft.com/library/669d602e-68e3-41f9-a455-b942d212d130.aspx) <br/> [Help Desk](http://technet.microsoft.com/library/e7958752-22e4-4155-a2fc-948099dec6f7.aspx) <br/> |
|Calendar diagnostics  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> [Records Management](http://technet.microsoft.com/library/0e0c95ce-6109-4591-b86d-c6cfd44d21f5.aspx) <br/> [Hygiene Management](http://technet.microsoft.com/library/fc0a9ec2-9c3d-42f6-8442-8603fb29d464.aspx) <br/> [Compliance Management](http://technet.microsoft.com/library/b91b23a4-e9c7-4bd0-9ee3-ec5cb498da15.aspx) <br/> [Help Desk](http://technet.microsoft.com/library/e7958752-22e4-4155-a2fc-948099dec6f7.aspx) <br/> |
|Calendar processing  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> [Recipient Management](http://technet.microsoft.com/library/669d602e-68e3-41f9-a455-b942d212d130.aspx) <br/> [Help Desk](http://technet.microsoft.com/library/e7958752-22e4-4155-a2fc-948099dec6f7.aspx) <br/> |
|Notifications  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> [Recipient Management](http://technet.microsoft.com/library/669d602e-68e3-41f9-a455-b942d212d130.aspx) <br/> |
|Organization relationships  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> |
|Sharing policies  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> |
   
## Resource mailbox configuration permissions
<a name="calendar"> </a>

Users who are assigned the View-Only Management role group can view the configuration of the features in the following table. For more information, see **View Only Organization Management**.
  
|**Feature**|**Permissions required**|
|:-----|:-----|
|Booking policies  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> [Recipient Management](http://technet.microsoft.com/library/669d602e-68e3-41f9-a455-b942d212d130.aspx) <br/> [Help Desk](http://technet.microsoft.com/library/e7958752-22e4-4155-a2fc-948099dec6f7.aspx) <br/> |
|Delegation  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> [Recipient Management](http://technet.microsoft.com/library/669d602e-68e3-41f9-a455-b942d212d130.aspx) <br/> |
|Resource mailbox schema configuration  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> |
   
## Mailbox database permissions
<a name="calendar"> </a>

Users who are assigned the View-Only Management role group can view the configuration of the features in the following table. For more information, see **View Only Organization Management**.
  
|**Feature**|**Permissions required**|
|:-----|:-----|
|Mailbox databases  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> [Server Management](http://technet.microsoft.com/library/30cbc4de-adb3-42e8-922f-7661095bdb8c.aspx) <br/> |
   
## Recipient provisioning permissions
<a name="calendar"> </a>

This table contains the various permissions that are required to manage recipients.
  
Users who are assigned the View-Only Management role group can view the configuration of the features in the following table. For more information, see **View Only Organization Management**.
  
|**Feature**|**Permissions required**|
|:-----|:-----|
|Address list, GAL  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> |
|Antispam  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> [Recipient Management](http://technet.microsoft.com/library/669d602e-68e3-41f9-a455-b942d212d130.aspx) <br/> |
|Apps for Outlook  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> [View-Only Organization Management](http://technet.microsoft.com/library/c514c6d0-0157-4c52-9ec6-441d9a30f3df.aspx) <br/> [Help Desk](http://technet.microsoft.com/library/e7958752-22e4-4155-a2fc-948099dec6f7.aspx) <br/> |
|Applying sharing policies  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> [Recipient Management](http://technet.microsoft.com/library/669d602e-68e3-41f9-a455-b942d212d130.aspx) <br/> |
|Arbitration  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> |
|Archive connectivity  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> [View-Only Organization Management](http://technet.microsoft.com/library/c514c6d0-0157-4c52-9ec6-441d9a30f3df.aspx) <br/> [Server Management](http://technet.microsoft.com/library/30cbc4de-adb3-42e8-922f-7661095bdb8c.aspx) <br/> |
|Assigning offline address books  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> [Recipient Management](http://technet.microsoft.com/library/669d602e-68e3-41f9-a455-b942d212d130.aspx) <br/> |
|Automatic replies  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> [Recipient Management](http://technet.microsoft.com/library/669d602e-68e3-41f9-a455-b942d212d130.aspx) <br/> [Help Desk](http://technet.microsoft.com/library/e7958752-22e4-4155-a2fc-948099dec6f7.aspx) <br/> |
|Calendar configuration  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> [Recipient Management](http://technet.microsoft.com/library/669d602e-68e3-41f9-a455-b942d212d130.aspx) <br/> |
|Calendar repair  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> [Recipient Management](http://technet.microsoft.com/library/669d602e-68e3-41f9-a455-b942d212d130.aspx) <br/> |
|Contact aggregation settings  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> [Recipient Management](http://technet.microsoft.com/library/669d602e-68e3-41f9-a455-b942d212d130.aspx) <br/> [View-Only Organization Management](http://technet.microsoft.com/library/c514c6d0-0157-4c52-9ec6-441d9a30f3df.aspx) <br/> |
|Convert mailboxes  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> [Recipient Management](http://technet.microsoft.com/library/669d602e-68e3-41f9-a455-b942d212d130.aspx) <br/> |
|Disconnected mailboxes  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> [Recipient Management](http://technet.microsoft.com/library/669d602e-68e3-41f9-a455-b942d212d130.aspx) <br/> [Help Desk](http://technet.microsoft.com/library/e7958752-22e4-4155-a2fc-948099dec6f7.aspx) <br/> |
|Distribution groups  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> [Recipient Management](http://technet.microsoft.com/library/669d602e-68e3-41f9-a455-b942d212d130.aspx) <br/> |
|Dynamic distribution groups  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> [Recipient Management](http://technet.microsoft.com/library/669d602e-68e3-41f9-a455-b942d212d130.aspx) <br/> |
|Email addresses  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> [Recipient Management](http://technet.microsoft.com/library/669d602e-68e3-41f9-a455-b942d212d130.aspx) <br/> [UM Management](http://technet.microsoft.com/library/c91f0387-615c-4a1d-87d4-133ddac1e407.aspx) <br/> |
|Inbox rules  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> [Recipient Management](http://technet.microsoft.com/library/669d602e-68e3-41f9-a455-b942d212d130.aspx) <br/> [Help Desk](http://technet.microsoft.com/library/e7958752-22e4-4155-a2fc-948099dec6f7.aspx) <br/> |
|Mail contacts  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> [Recipient Management](http://technet.microsoft.com/library/669d602e-68e3-41f9-a455-b942d212d130.aspx) <br/> |
|Mail tips  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> [Recipient Management](http://technet.microsoft.com/library/669d602e-68e3-41f9-a455-b942d212d130.aspx) <br/> |
|Mail user  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> [Recipient Management](http://technet.microsoft.com/library/669d602e-68e3-41f9-a455-b942d212d130.aspx) <br/> |
|Mailbox folder permissions  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> [Recipient Management](http://technet.microsoft.com/library/669d602e-68e3-41f9-a455-b942d212d130.aspx) <br/> [Help Desk](http://technet.microsoft.com/library/e7958752-22e4-4155-a2fc-948099dec6f7.aspx) <br/> |
|Mailbox folders  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> [Recipient Management](http://technet.microsoft.com/library/669d602e-68e3-41f9-a455-b942d212d130.aspx) <br/> |
|MAPI connectivity  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> |
|Message configuration  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> [Recipient Management](http://technet.microsoft.com/library/669d602e-68e3-41f9-a455-b942d212d130.aspx) <br/> [Help Desk](http://technet.microsoft.com/library/e7958752-22e4-4155-a2fc-948099dec6f7.aspx) <br/> |
|Message quotas  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> [Recipient Management](http://technet.microsoft.com/library/669d602e-68e3-41f9-a455-b942d212d130.aspx) <br/> |
|Moderation  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> [Recipient Management](http://technet.microsoft.com/library/669d602e-68e3-41f9-a455-b942d212d130.aspx) <br/> |
|Permissions and delegation  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> |
|Archive mailboxes  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> [Recipient Management](http://technet.microsoft.com/library/669d602e-68e3-41f9-a455-b942d212d130.aspx) <br/> |
|Recipient data properties  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> [Recipient Management](http://technet.microsoft.com/library/669d602e-68e3-41f9-a455-b942d212d130.aspx) <br/> |
|Remote mailboxes  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> [Recipient Management](http://technet.microsoft.com/library/669d602e-68e3-41f9-a455-b942d212d130.aspx) <br/> |
|Retention and legal holds  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> [Recipient Management](http://technet.microsoft.com/library/669d602e-68e3-41f9-a455-b942d212d130.aspx) <br/> [Records Management](http://technet.microsoft.com/library/0e0c95ce-6109-4591-b86d-c6cfd44d21f5.aspx) <br/> |
|Send As  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> [Recipient Management](http://technet.microsoft.com/library/669d602e-68e3-41f9-a455-b942d212d130.aspx) <br/> |
|Spelling configuration  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> [Recipient Management](http://technet.microsoft.com/library/669d602e-68e3-41f9-a455-b942d212d130.aspx) <br/> [Help Desk](http://technet.microsoft.com/library/e7958752-22e4-4155-a2fc-948099dec6f7.aspx) <br/> |
|Unified Messaging  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> [UM Management](http://technet.microsoft.com/library/c91f0387-615c-4a1d-87d4-133ddac1e407.aspx) <br/> |
|User mailboxes  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> [Recipient Management](http://technet.microsoft.com/library/669d602e-68e3-41f9-a455-b942d212d130.aspx) <br/> |
|User photos  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> [Recipient Management](http://technet.microsoft.com/library/669d602e-68e3-41f9-a455-b942d212d130.aspx) <br/> [Help Desk](http://technet.microsoft.com/library/e7958752-22e4-4155-a2fc-948099dec6f7.aspx) <br/> |
   
## Mailbox move and migration permissions
<a name="calendar"> </a>

The table contains the permissions that are required to move on-premises mailboxes to different domains or forests and to migrate on-premises mailboxes to and from your cloud-based organization.
  
|**Feature**|**Permissions required**|
|:-----|:-----|
|Mailbox moves (local or cross-forest)  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> [Recipient Management](http://technet.microsoft.com/library/669d602e-68e3-41f9-a455-b942d212d130.aspx) <br/> |
|Mailbox moves (hybrid deployment)  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> [Recipient Management](http://technet.microsoft.com/library/669d602e-68e3-41f9-a455-b942d212d130.aspx) <br/> |
|Migration (on-boarding and off-boarding from the cloud)  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> [Recipient Management](http://technet.microsoft.com/library/669d602e-68e3-41f9-a455-b942d212d130.aspx) <br/> |
   

