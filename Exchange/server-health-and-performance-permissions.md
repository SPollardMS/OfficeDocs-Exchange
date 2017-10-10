---
title: Server health and performance permissions
ms.prod: EXCHANGE
ms.assetid: 00b23fd3-6679-4b06-a3d4-51df3112b9cd
---


# Server health and performance permissions
Learn about permissions that are required to manage workloads and event logs in Exchange Server 2016.
The permissions required to perform tasks to configure various components of Microsoft Exchange Server 2016 depend on the procedure being performed or the cmdlet you want to run. See each of the sections in this topic for more information about their respective features. 
  
    
    

To find out what permissions you need to perform the procedure or run the cmdlet, do the following:
1. In the table below, find the feature that is most related to the procedure you want to perform or the cmdlet you want to run.
    
  
2. Next, look at the permissions required for the feature. You must be assigned one of those role groups, an equivalent custom role group, or an equivalent management role. You can also click on a role group to see its management roles. If a feature lists more than one role group, you only need to be assigned one of the role groups to use the feature. For more information about role groups and management roles, see **Understanding Role Based Access Control**.
    
  
3. Now, run the **Get-ManagementRoleAssignment** cmdlet to look at the role groups or management roles assigned to you to see if you have the permissions that are necessary to manage the feature.
    
    > [!NOTE]
      > You must be assigned the Role Management management role to run the **Get-ManagementRoleAssignment** cmdlet. If you don't have permissions to run the **Get-ManagementRoleAssignment** cmdlet, ask your Exchange administrator to retrieve the role groups or management roles assigned to you.
If you want to delegate the ability to manage a feature to another user, see **Delegate a Management Role**.
> [!NOTE]
> Some features may require that you have local administrator permissions on the server you want to manage. To manage these features, you must be a member of the Local Administrators group on that server. 
  
    
    


## Exchange workload management permissions

The following table lists the permissions required to perform tasks that manage the health and performance of your Exchange 2016 organization. For more information, see  [Exchange Workload Management](http://technet.microsoft.com/library/276740c4-bdb7-49f1-9470-ae6f2bfd65aa.aspx).
  
    
    
Users who are assigned the View-Only Management role group can view the configuration of the features in the following table. For more information, see **View Only Organization Management**.
  
    
    


|**Feature**|**Permissions required**|
|:-----|:-----|
|User throttling  <br/> | [Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/>  [Recipient Management](http://technet.microsoft.com/library/669d602e-68e3-41f9-a455-b942d212d130.aspx) <br/>  [View-Only Organization Management](http://technet.microsoft.com/library/c514c6d0-0157-4c52-9ec6-441d9a30f3df.aspx) <br/> |
|Exchange workload throttling  <br/> | [Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/>  [View-Only Organization Management](http://technet.microsoft.com/library/c514c6d0-0157-4c52-9ec6-441d9a30f3df.aspx) <br/> |
   

## Exchange event log permissions

The following table lists the permissions required to perform tasks that manage Exchange event log settings. 
  
    
    
Users who are assigned the View-Only Management role group can view the configuration of the features in the following table. For more information, see **View Only Organization Management**.
  
    
    


|**Feature**|**Permissions required**|
|:-----|:-----|
|Exchange event log management  <br/> | [Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/>  [Server Management](http://technet.microsoft.com/library/30cbc4de-adb3-42e8-922f-7661095bdb8c.aspx) <br/>  [View-Only Organization Management](http://technet.microsoft.com/library/c514c6d0-0157-4c52-9ec6-441d9a30f3df.aspx) <br/>  [UM Management](http://technet.microsoft.com/library/c91f0387-615c-4a1d-87d4-133ddac1e407.aspx) <br/> |
   

