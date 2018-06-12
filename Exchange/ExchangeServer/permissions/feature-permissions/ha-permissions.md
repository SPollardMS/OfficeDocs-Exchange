---
title: "High availability and site resilience permissions"
ms.author: serdars
author: SerdarSoysal
manager: serdars
ms.date: 6/7/2018
ms.audience: ITPro
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 66085107-4d4d-41c3-a425-82314acd9eee
description: "Summary: Learn about permissions that are required to manage high availability in Exchange Server 2016."
---

# High availability and site resilience permissions

 **Summary**: Learn about permissions that are required to manage high availability in Exchange Server 2016.
  
The permissions required to configure high availability vary depending on the procedure being performed or the cmdlet you want to run. For more information about high availability, see [High Availability and Site Resilience](http://technet.microsoft.com/library/6628285e-d07c-443d-866b-be784ad1ed1e.aspx).
  
To find out what permissions you need to perform the procedure or run the cmdlet, do the following:
  
1. In the table below, find the feature that is most related to the procedure you want to perform or the cmdlet you want to run.
    
2. Next, look at the permissions required for the feature. You must be assigned one of those role groups, an equivalent custom role group, or an equivalent management role. You can also click on a role group to see its management roles. If a feature lists more than one role group, you only need to be assigned one of the role groups to use the feature. For more information about role groups and management roles, see **Understanding Role Based Access Control**.
    
3. Now, run the **Get-ManagementRoleAssignment** cmdlet to look at the role groups or management roles assigned to you to see if you have the permissions that are necessary to manage the feature. 
    
    > [!NOTE]
    > You must be assigned the Role Management management role to run the **Get-ManagementRoleAssignment** cmdlet. If you don't have permissions to run the **Get-ManagementRoleAssignment** cmdlet, ask your Exchange administrator to retrieve the role groups or management roles assigned to you. 
  
If you want to delegate the ability to manage a feature to another user, see **Delegate a Management Role**.
  
## Database availability group permissions

You can use the features in the following table to add, remove, and configure settings for database availability groups (DAGs).
  
Users who are assigned the View-Only Management role group can view the configuration of the features in the following table. For more information, see **View Only Organization Management**.
  
|**Feature**|**Permissions required**|
|:-----|:-----|
|Database availability group membership  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> [Database Availability Groups](http://technet.microsoft.com/library/0b3e0f7a-21e5-4209-8d5b-b63c6b9de3cc.aspx) <br/> |
|Database availability group properties  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> [Database Availability Groups](http://technet.microsoft.com/library/0b3e0f7a-21e5-4209-8d5b-b63c6b9de3cc.aspx) <br/> |
|Database availability groups  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> [Database Availability Groups](http://technet.microsoft.com/library/0b3e0f7a-21e5-4209-8d5b-b63c6b9de3cc.aspx) <br/> |
|Database availability networks  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> [Database Availability Groups](http://technet.microsoft.com/library/0b3e0f7a-21e5-4209-8d5b-b63c6b9de3cc.aspx) <br/> |
   
## Mailbox database copy permissions

You can use the features in the following table to add, remove, update, and activate mailbox database copies.
  
|**Feature**|**Permissions required**|
|:-----|:-----|
|Database switchover  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> [Database Copies](http://technet.microsoft.com/library/71a95f5b-1f75-4ae9-9ee9-515c3a19d394.aspx) <br/> |
|Mailbox database copies  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> [Database Copies](http://technet.microsoft.com/library/71a95f5b-1f75-4ae9-9ee9-515c3a19d394.aspx) <br/> |
|Server switchover  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> [Database Copies](http://technet.microsoft.com/library/71a95f5b-1f75-4ae9-9ee9-515c3a19d394.aspx) <br/> |
|Update a mailbox database copy  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> [Database Copies](http://technet.microsoft.com/library/71a95f5b-1f75-4ae9-9ee9-515c3a19d394.aspx) <br/> |
   

