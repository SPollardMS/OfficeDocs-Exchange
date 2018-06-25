---
title: "Sharing and collaboration permissions"
ms.author: dmaguire
author: msdmaguire
manager: scotv
ms.date: 6/7/2018
ms.audience: ITPro
ms.topic: reference
ms.prod: exchange-server-itpro
localization_priority: Normal
ms.assetid: b7fa4b7c-1266-45bd-a14b-f66be0459cc5
description: "Summary: Learn about permissions that are required to manage sharing and collaboration features in Exchange Server 2016."
---

# Sharing and collaboration permissions

 **Summary**: Learn about permissions that are required to manage sharing and collaboration features in Exchange Server 2016.
  
The permissions required to configure sharing and collaboration features vary depending on the procedure being performed or the cmdlet you want to run. For more information about sharing and collaboration, see [Collaboration](http://technet.microsoft.com/library/f45c1be1-2a66-4610-a28d-4adc6d212769.aspx) and [Sharing](http://technet.microsoft.com/library/09e6732a-4e99-44d0-801d-9463fdc57a9b.aspx).
  
To find out what permissions you need to perform the procedure or run the cmdlet, do the following:
  
1. In the table below, find the feature that is most related to the procedure you want to perform or the cmdlet you want to run.
    
2. Next, look at the permissions required for the feature. You must be assigned one of those role groups, an equivalent custom role group, or an equivalent management role. You can also click on a role group to see its management roles. If a feature lists more than one role group, you only need to be assigned one of the role groups to use the feature. For more information about role groups and management roles, see **Understanding Role Based Access Control**.
    
3. Now, run the **Get-ManagementRoleAssignment** cmdlet to look at the role groups or management roles assigned to you to see if you have the permissions that are necessary to manage the feature. 
    
    > [!NOTE]
    > You must be assigned the Role Management management role to run the **Get-ManagementRoleAssignment** cmdlet. If you don't have permissions to run the **Get-ManagementRoleAssignment** cmdlet, ask your Exchange administrator to retrieve the role groups or management roles assigned to you. 
  
If you want to delegate the ability to manage a feature to another user, see **Delegate a Management Role**.
  
## Sharing and collaboration feature permissions

You can use the features in the following table to configure sharing and collaboration features. The role groups that are required to configure each feature are listed.
  
Users who are assigned the View-Only Management role group can view the configuration of the features in the following table. For more information, see **View Only Organization Management**.
  
|**Feature**|**Permissions required**|
|:-----|:-----|
|Partner applications - configure  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> |
|Public folders, mail-enabled  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> [Recipient Management](http://technet.microsoft.com/library/669d602e-68e3-41f9-a455-b942d212d130.aspx) <br/> |
|Public folders  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> [Public Folder Management](http://technet.microsoft.com/library/e167d95e-bb39-43fd-b960-204ab0de27da.aspx) <br/> |
|Site mailboxes  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> [Recipient Management](http://technet.microsoft.com/library/669d602e-68e3-41f9-a455-b942d212d130.aspx) <br/> |
|Site mailbox provisioning policy  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> [Recipient Management](http://technet.microsoft.com/library/669d602e-68e3-41f9-a455-b942d212d130.aspx) <br/> |
   

