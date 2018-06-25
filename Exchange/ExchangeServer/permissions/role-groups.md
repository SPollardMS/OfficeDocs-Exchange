---
title: "Manage role groups"
ms.author: dstrome
author: dstrome
manager: serdars
ms.date: 6/7/2018
ms.audience: ITPro
ms.topic: article
ms.prod: exchange-server-itpro
localization_priority: Normal
ms.assetid: ab9b7a3b-bf67-4ba1-bde5-8e6ac174b82c
description: "Summary: Learn how to add, remove, copy, and view management role groups in Microsoft Exchange Server 2016."
---

# Manage role groups

 **Summary**: Learn how to add, remove, copy, and view management role groups in Microsoft Exchange Server 2016.
  
A management role group is a universal security group (USG) used in the Role Based Access Control (RBAC) permissions model in Exchange 2016. A management role group simplifies the assignment of management roles to a group of users. All members of a role group are assigned the same set of roles. For more information about role groups in Exchange 2016, see [Understanding Management Role Groups](http://technet.microsoft.com/library/2a92e06c-523e-4fd4-a937-152562b7741d.aspx).
  
For additional management tasks related to role groups, see [Permissions](permissions.md).
  
## What do you need to know before you begin?

- Estimated time to complete each procedure: 5 to 10 minutes
    
- To open the EAC, see [Exchange admin center in Exchange 2016](../architecture/client-access/exchange-admin-center.md). To open the Exchange Management Shell, see [Open the Exchange Management Shell](http://technet.microsoft.com/library/63976059-25f8-4b4f-b597-633e78b803c0.aspx).
    
- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Role groups" entry in the [Role management permissions](feature-permissions/rbac-permissions.md) topic. 
    
- For information about keyboard shortcuts that may apply to the procedures in this topic, see [Keyboard shortcuts in the Exchange admin center](../about-documentation/exchange-admin-center-keyboard-shortcuts.md).
    
> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at: [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351). 
  
## Create a role group
<a name="CreateRG"> </a>

If you want to customize the permissions that you can assign to a group of users, create a new custom management role group.
  
### Use the EAC to create a role group

1. In the Exchange Administration Center (EAC), navigate to **Permissions** \> **Admin Roles** and then click **Add**![Add icon](../media/ITPro_EAC_AddIcon.png).
    
2. In the **New role group** window, provide a name for the new role group. 
    
3. You can either select the roles that you want to be assigned to the role group and the members you want to be added to the role group now, or you can do this at another time.
    
4. Select the write scope that you want to apply to the new role group.
    
5. Click **Save** to create the role group. 
    
### Use the Exchange Management Shell to create a role group

To create a role group, see the [Examples](http://technet.microsoft.com/library/c59f596d-cbdd-459e-b31f-99d03e684299.aspx#Examples) section in [New-RoleGroup](http://technet.microsoft.com/library/c59f596d-cbdd-459e-b31f-99d03e684299.aspx).
  
### How do you know this worked?

To verify that you have successfully created a role group, do the following:
  
1. In the EAC, navigate to **Permissions** \> **Admin Roles**.
    
2. Verify that the new role group appears in the role group list and then select it.
    
3. Verify that members, assigned roles, and scope that you specified on the new role group are listed in the role group details pane.
    
## Copy a role group
<a name="CopyRG"> </a>

### Use the EAC to copy a role group

If you have a role group that contains the permissions you want to grant to users, but you want to apply a different management scope, or remove or add one or two management roles without having to add all the other roles manually, you can copy the existing role group.
  
> [!IMPORTANT]
> You can't use the EAC to copy a role group if you've used the Exchange Management Shell to configure multiple management role scopes or exclusive scopes on the role group. If you've configured multiple scopes or exclusive scopes on the role group, you must use the Exchange Management Shell procedures later in this topic to copy the role group. For more information about management role scopes, see [Understanding Management Role Scopes](http://technet.microsoft.com/library/24ed4a38-438a-4223-9f9c-5d4dea4b046b.aspx). 
  
1. In the EAC, navigate to **Permissions** \> **Admin Roles**.
    
2. Select the role group you want to copy and then click **Copy**![Copy icon](../media/ITPro_EAC_CopyIcon.png).
    
3. In the **New role group** window, provide a name for the new role group. 
    
4. Review the roles that have been copied to the new role group. Add or remove roles as necessary.
    
5. Review the write scope, and change it as necessary.
    
6. Review the members that have been copied to the new role group. Add or remove members as necessary.
    
7. Click **Save** to create the role group. 
    
### Use the Exchange Management Shell to copy a role group with no scope
<a name="NoScope"> </a>

1. Store the role group that you want to copy in a variable using the following syntax.
    
  ```
  $RoleGroup = Get-RoleGroup <name of role group to copy>
  ```

2. Create the new role group, and also add members to the role group and specify who can delegate the new role group to other users, using the following syntax.
    
  ```
  New-RoleGroup <name of new role group> -Roles $RoleGroup.Roles -Members <member1, member2, member3...> -ManagedBy <user1, user2, user3...>
  ```

For example, the following commands copy the Organization Management role group, and name the new role group "Limited Organization Management". It adds the members Isabelle, Carter, and Lukas and can be delegated by Jenny and Katie.
  
```
$RoleGroup = Get-RoleGroup "Organization Management"
New-RoleGroup "Limited Organization Management" -Roles $RoleGroup.Roles -Members Isabelle, Carter, Lukas -ManagedBy Jenny, Katie
```

After the new role group is created, you can add or remove roles, change the scope of role assignments on the role, and more.
  
For detailed syntax and parameter information, see [Get-RoleGroup](http://technet.microsoft.com/library/369800ff-fced-4d1c-adb0-1ddbe798670d.aspx) and [New-RoleGroup](http://technet.microsoft.com/library/c59f596d-cbdd-459e-b31f-99d03e684299.aspx).
  
### Use the Exchange Management Shell to copy a role group with a custom scope
<a name="NoScope"> </a>

1. Store the role group that you want to copy in a variable using the following syntax.
    
  ```
  $RoleGroup = Get-RoleGroup <name of role group to copy>
  ```

2. Create the new role group with a custom scope using the following syntax.
    
  ```
  New-RoleGroup <name of new role group> -Roles $RoleGroup.Roles -CustomRecipientWriteScope <recipient scope name> -CustomConfigWriteScope <configuraiton scope name>
  ```

For example, the following commands copy the Organization Management role group and create a new role group called Vancouver Organization Management with the Vancouver Users recipient scope and Vancouver Servers configuration scope.
  
```
$RoleGroup = Get-RoleGroup "Organization Management"
New-RoleGroup "Vancouver Organization Management" -Roles $RoleGroup.Roles -CustomRecipientWriteScope "Vancouver Users" -CustomConfigWriteScope "Vancouver Servers"
```

You can also add members to the role group when you create it by using the _Members_ parameter as shown in [Use the Exchange Management Shell to copy a role group with no scope](#NoScope.md) earlier in this topic. For more information about management scopes, see [Understanding Management Scopes](http://technet.microsoft.com/library/24ed4a38-438a-4223-9f9c-5d4dea4b046b.aspx).
  
After the new role group is created, you can add or remove roles, change the scope of role assignments on the role, and perform other tasks.
  
For detailed syntax and parameter information, see [Get-RoleGroup](http://technet.microsoft.com/library/369800ff-fced-4d1c-adb0-1ddbe798670d.aspx) and [New-RoleGroup](http://technet.microsoft.com/library/c59f596d-cbdd-459e-b31f-99d03e684299.aspx).
  
### Use the Exchange Management Shell to copy a role group with an OU scope
<a name="NoScope"> </a>

1. Store the role group that you want to copy in a variable using the following syntax.
    
  ```
  $RoleGroup = Get-RoleGroup <name of role group to copy>
  ```

2. Create the new role group with a custom scope using the following syntax.
    
  ```
  New-RoleGroup <name of new role group> -Roles $RoleGroup.Roles -RecipientOrganizationalUnitScope <OU name>
  ```

For example, the following commands copy the Recipient Management role group and create a new role group called Toronto Recipient Management that allows management of only users in the Toronto Users OU.
  
```
$RoleGroup = Get-RoleGroup "Recipient Management"
New-RoleGroup "Toronto Recipient Management" -Roles $RoleGroup.Roles -RecipientOrganizationalUnitScope "contoso.com/Toronto Users"
```

You can also add members to the role group when you create it by using the _Members_ parameter as shown in [Use the Exchange Management Shell to copy a role group with no scope](#NoScope.md) earlier in this topic. For more information about management scopes, see [Understanding Management Scopes](http://technet.microsoft.com/library/24ed4a38-438a-4223-9f9c-5d4dea4b046b.aspx).
  
After the new role group is created, you can add or remove roles, change the scope of role assignments on the role, and more.
  
For detailed syntax and parameter information, see [Get-RoleGroup](http://technet.microsoft.com/library/369800ff-fced-4d1c-adb0-1ddbe798670d.aspx) and [New-RoleGroup](http://technet.microsoft.com/library/c59f596d-cbdd-459e-b31f-99d03e684299.aspx).
  
### How do you know this worked?
<a name="NoScope"> </a>

To verify that you have successfully copied a role group, do the following:
  
1. In the EAC, navigate to **Permissions** \> **Admin Roles**.
    
2. Verify that the copied role group appears in the role group list, and then select it.
    
3. Verify that members, assigned roles, and scope that you specified on the copied role group are listed in the role group details pane.
    
## Remove a role group
<a name="RemoveRG"> </a>

If you no longer need a role group you created, you can remove it. When you remove a role group, the management role assignments between the role group and the management roles are deleted. The management roles aren't deleted. If a user depended on the role group for access to a feature, the user will no longer have access to the feature. You can't remove built-in role groups.
  
### Use the EAC to remove a role group

1. In the EAC, navigate to **Permissions** \> **Admin Roles**.
    
2. Select the role group you want to remove and then click **Delete**![Delete icon](../media/ITPro_EAC_DeleteIcon.png).
    
3. Verify that you want to remove the selected role group, and if so, respond **Yes** to the warning. 
    
### Use the Exchange Management Shell to remove a role group

To remove a role group, see the [Examples](http://technet.microsoft.com/library/6fe6975b-bc0f-4920-b0b0-6da245429f64.aspx#Examples) section in [Remove-RoleGroup](http://technet.microsoft.com/library/6fe6975b-bc0f-4920-b0b0-6da245429f64.aspx).
  
## View role groups
<a name="ViewRG"> </a>

You can view either a list of role groups or the detailed information about a specific role group that exists in your organization.
  
### Use the EAC to view a list of role groups and role group details

1. In the EAC, navigate to **Permissions** \> **Admin Roles**. All of the role groups in your organization are listed here.
    
2. Select a role group to view the members, assigned roles, and scope that are configured on the role group.
    
### Use the Exchange Management Shell to view a list of role groups and role group details

To view a list of role groups, see the [Examples](http://technet.microsoft.com/library/369800ff-fced-4d1c-adb0-1ddbe798670d.aspx#Examples) section in [Get-RoleGroup](http://technet.microsoft.com/library/369800ff-fced-4d1c-adb0-1ddbe798670d.aspx).
  
## Add a role to a role group
<a name="AddRemoveRGRole"> </a>

Adding a management role to a role group is the best and simplest way to grant permissions to a group of administrators or specialist users. If you want to give users that are members of a role group the ability to manage a feature, you add the management role that manages the feature to the role group. After the role is added, the members of the role group are granted the permissions provided by the role.
  
### Use the EAC to add a management role to a role group

> [!IMPORTANT]
> You can't use the EAC to add roles to a role group if you've used the Exchange Management Shell to configure multiple management role scopes or exclusive scopes on the role group. If you've configured multiple scopes or exclusive scopes on the role group, you must use the Exchange Management Shell procedures later in this topic to add roles to the role group. For more information about management role scopes, see [Understanding Management Role Scopes](http://technet.microsoft.com/library/24ed4a38-438a-4223-9f9c-5d4dea4b046b.aspx). 
  
1. In the EAC, navigate to **Permissions** \> **Admin Roles**.
    
2. Select the role group you want to add a role to, and then click **Edit**![Edit icon](../media/ITPro_EAC_EditIcon.png).
    
3. In the **Roles** section, select the roles you want to add to the role group. 
    
4. When you've finished adding roles to the role group, click **Save**.
    
### Use the Exchange Management Shell to create a role assignment with no scope

You can create a role assignment with no scope between a role and a role group. When you do this, the implicit read and implicit write scopes of the role apply.
  
Use the following syntax to assign a role without any scope to a role group. A role assignment name is created automatically if you don't specify one.
  
```
New-ManagementRoleAssignment -SecurityGroup <role group name> -Role <role name>
```

This example assigns the Transport Rules management role to the Seattle Compliance role group.
  
```
New-ManagementRoleAssignment -SecurityGroup "Seattle Compliance" -Role "Transport Rules"
```

For detailed syntax and parameter information, see [New-ManagementRoleAssignment](http://technet.microsoft.com/library/34d4f2e3-f2c5-49e1-a6a9-1366da65a78c.aspx).
  
### Use the Exchange Management Shell to create a role assignment with a predefined scope

If a predefined scope meets your business requirements, you can apply that scope to the role assignment rather than create a new one. For a list of predefined scopes and their descriptions, see [Understanding Management Role Scopes](http://technet.microsoft.com/library/24ed4a38-438a-4223-9f9c-5d4dea4b046b.aspx).
  
For more information about role assignments, see [Understanding Management Role Assignments](http://technet.microsoft.com/library/1dc33dd6-52fb-4852-a5ce-027bc73e1d8f.aspx).
  
Use the following syntax to assign a role to a role group with a predefined scope. A role assignment name is created automatically if you don't specify one.
  
```
New-ManagementRoleAssignment -SecurityGroup <role group name> -Role <role name> -RecipientRelativeWriteScope < MyGAL | MyDistributionGroups | Organization | Self >
```

This example assigns the Message Tracking role to the Enterprise Support role group and applies the Organization predefined scope.
  
```
New-ManagementRoleAssignment -SecurityGroup "Enterprise Support" -Role "Message Tracking" -RecipientRelativeWriteScope Organization
```

For detailed syntax and parameter information, see [New-ManagementRoleAssignment](http://technet.microsoft.com/library/34d4f2e3-f2c5-49e1-a6a9-1366da65a78c.aspx).
  
### Use the Exchange Management Shell to create a role assignment with a recipient filter-based scope

If you created a recipient filter-based scope, you need to include the scope in the command used to assign the role to a role group by using the _CustomRecipientWriteScope_ parameter. 
  
You can also include a configuration write scope when you create a role assignment that has a recipient write scope.
  
For more information about role assignments and scopes, see the following topics:
  
- [Understanding Management Role Assignments](http://technet.microsoft.com/library/1dc33dd6-52fb-4852-a5ce-027bc73e1d8f.aspx)
    
- [Understanding Management Role Scopes](http://technet.microsoft.com/library/24ed4a38-438a-4223-9f9c-5d4dea4b046b.aspx)
    
Use the following syntax to assign a role to a role group with a recipient filter-based scope. A role assignment name is created automatically if you don't specify one.
  
```
New-ManagementRoleAssignment -SecurityGroup <role group name> -Role <role name> -CustomRecipientWriteScope <role scope name>
```

This example assigns the Message Tracking role to the Seattle Recipient Admins role group and applies the Seattle Recipients scope.
  
```
New-ManagementRoleAssignment -SecurityGroup "Seattle Recipient Admins" -Role "Message Tracking" -CustomRecipientWriteScope "Seattle Recipients"
```

For detailed syntax and parameter information, see [New-ManagementRoleAssignment](http://technet.microsoft.com/library/34d4f2e3-f2c5-49e1-a6a9-1366da65a78c.aspx).
  
### Use the Exchange Management Shell to create a role assignment with a configuration scope

If you created a server or database configuration filter or list-based scope, you need to include the scope in the command used to assign the role to a role group by using the _CustomConfigWriteScope_ parameter. 
  
You can also include a recipient write scope when you create a role assignment that has a configuration write scope.
  
For more information about role assignments and management scopes, see the following topics:
  
- [Understanding Management Role Assignments](http://technet.microsoft.com/library/1dc33dd6-52fb-4852-a5ce-027bc73e1d8f.aspx)
    
- [Understanding Management Role Scopes](http://technet.microsoft.com/library/24ed4a38-438a-4223-9f9c-5d4dea4b046b.aspx)
    
Use the following syntax to assign a role to a role group with a configuration scope. A role assignment name is created automatically if you don't specify one.
  
```
New-ManagementRoleAssignment -SecurityGroup <role group name> -Role <role name> -CustomConfigWriteScope <role scope name>
```

This example assigns the Databases role to the Seattle Server Admins role group and applies the Seattle Servers scope.
  
```
New-ManagementRoleAssignment -SecurityGroup "Seattle Server Admins" -Role "Databases" -CustomConfigWriteScope "Seattle Servers"
```

For detailed syntax and parameter information, see [New-ManagementRoleAssignment](http://technet.microsoft.com/library/34d4f2e3-f2c5-49e1-a6a9-1366da65a78c.aspx).
  
### Use the Exchange Management Shell to create a role assignment with an OU scope

If you want to scope a role's write scope to an OU, you can specify the OU in the _RecipientOrganizationalUnitScope_ parameter directly. 
  
For more information about role assignments and management scopes, see the following topics:
  
- [Understanding Management Role Assignments](http://technet.microsoft.com/library/1dc33dd6-52fb-4852-a5ce-027bc73e1d8f.aspx)
    
- [Understanding Management Role Scopes](http://technet.microsoft.com/library/24ed4a38-438a-4223-9f9c-5d4dea4b046b.aspx)
    
Use the following command to assign a role to a role group and restrict the write scope of a role to a specific OU. A role assignment name is created automatically if you don't specify one.
  
```
New-ManagementRoleAssignment -SecurityGroup <role group name> -Role <role name> -RecipientOrganizationalUnitScope <OU>
```

This example assigns the Mail Recipients role to the Seattle Recipient Admins role group and scopes the assignment to the Sales\Users OU in the Contoso.com domain.
  
```
New-ManagementRoleAssignment -SecurityGroup "Seattle Recipient Admins" -Role "Mail Recipients" -RecipientOrganizationalUnitScope contoso.com/sales/users
```

For detailed syntax and parameter information, see [New-ManagementRoleAssignment](http://technet.microsoft.com/library/34d4f2e3-f2c5-49e1-a6a9-1366da65a78c.aspx).
  
### How do you know this worked?

To verify that you have successfully added roles to a role group, do the following:
  
1. In the EAC, navigate to **Permissions** \> **Admin Roles**.
    
2. Select the role group you added roles to. In the role group details pane, verify that the roles that you added are listed.
    
## Remove a role from a role group
<a name="AddRemoveRGRole"> </a>

Removing a role from a management role group is the best and simplest way to revoke permissions granted to a group of administrators or specialist users. If you don't want administrators or specialist users to have permissions to manage a feature, you remove the management role from the management role group that manages the permissions. After the role is removed, the members of the role group will no longer have permissions to manage the feature.
  
> [!NOTE]
> Some role groups, such as the Organization Management role group, restrict what roles can be removed from a role group. For more information, see [Understanding Management Role Groups](http://technet.microsoft.com/library/2a92e06c-523e-4fd4-a937-152562b7741d.aspx). > If an administrator is a member of another role group that contains management roles that grants permissions to manage the feature, you need to either remove the administrator from the other role groups, or remove the role that grants permissions to manage the feature from the other role groups. 
  
### Use the EAC to remove a management role from a role group

> [!IMPORTANT]
> You can't use the EAC to remove roles from a role group if you've used the Exchange Management Shell to configure multiple scopes or exclusive scopes on the role group. If you've configured multiple scopes or exclusive scopes on the role group, you must use the Exchange Management Shell procedures later in this topic to remove roles from the role group. For more information about management role scopes, see [Understanding Management Role Scopes](http://technet.microsoft.com/library/24ed4a38-438a-4223-9f9c-5d4dea4b046b.aspx). 
  
1. In the EAC, navigate to **Permissions** \> **Admin Roles**.
    
2. Select the role group you want to remove a role from, and then click **Edit**![Edit icon](../media/ITPro_EAC_EditIcon.png).
    
3. In the **Roles** section, select the roles you want to remove from the role group. 
    
4. When you've finished removing roles from the role group, click **Save**.
    
### Use the Exchange Management Shell to remove a role from a role group

You can remove roles from role groups by retrieving the associated management role assignment using the **Get-ManagementRoleAssignment** cmdlet and then piping the role assignment returned to the **Remove-ManagementRoleAssignment** cmdlet. Unless you want to remove both delegating and regular role assignments at the same time, specify the _Delegating_ parameter to specify whether you want to remove regular or delegating role assignments. 
  
For more information about regular and delegating role assignments, see [Understanding Management Role Assignments](http://technet.microsoft.com/library/1dc33dd6-52fb-4852-a5ce-027bc73e1d8f.aspx).
  
This procedure uses pipelining. For more information about pipelining, see [Pipelining](http://technet.microsoft.com/library/59411ed3-926b-4eec-a462-84e6b26056c9.aspx).
  
To remove a role from a role group, use the following syntax.
  
```
Get-ManagementRoleAssignment -RoleAssignee <role group name> -Role <role name> -Delegating <$true | $false> | Remove-ManagementRoleAssignment
```

This example removes the Distribution Groups role, which enables administrators to manage distribution groups, from the Seattle Recipient Administrators role group. Because we want to remove the role assignment that provides permissions to manage distribution groups, the _Delegating_ parameter is set to `$False`, which returns only regular role assignments.
  
```
Get-ManagementRoleAssignment -RoleAssignee "Seattle Recipient Administrators" -Role "Distribution Groups" -Delegating $false | Remove-ManagementRoleAssignment
```

For detailed syntax and parameter information, see [Remove-ManagementRoleAssignment](http://technet.microsoft.com/library/e2fd10e1-c0ae-48a6-992d-5b34bc73880b.aspx).
  
### How do you know this worked?

To verify that you have successfully removed roles from a role group, do the following:
  
1. In the EAC, navigate to **Permissions** \> **Admin Roles**.
    
2. Select the role group you removed roles from. In the role group details pane, verify that the roles that you removed are no longer listed.
    
## Change a role group's scope
<a name="ChangeRGScope"> </a>

The management role assignments between a role group and a role contain management scopes, which determine what objects are made available to members of that role group. By changing the write scope on a role group, you can change what objects are made available to role group members to create, change, or remove. You can't change the read scope on a role group.
  
Exchange 2016 includes scopes that are applied by default to role assignments when no custom scopes are created. If you want to use a custom scope with a role assignment on a role group, you must create one first. For more information about creating custom scopes, which is an advanced task, see [Create a Regular or Exclusive Scope](http://technet.microsoft.com/library/b97a5be3-15cc-4954-ba30-a824a95e21be.aspx).
  
For more information about management role scopes and assignments in Exchange 2016, see the following topics:
  
- [Understanding Management Role Scopes](http://technet.microsoft.com/library/24ed4a38-438a-4223-9f9c-5d4dea4b046b.aspx)
    
- [Understanding Management Role Assignments](http://technet.microsoft.com/library/1dc33dd6-52fb-4852-a5ce-027bc73e1d8f.aspx)
    
### Use the EAC to change the scope on a role group

When you use the EAC to change the scope on a role group, you're actually changing the scope on all the role assignments between the role group and each of the management roles assigned to the role group. If you want to change the scope on specific role assignments, you must use the Exchange Management Shell procedures later in this topic.
  
> [!IMPORTANT]
> You can't use the EAC to manage scopes on role assignments between roles and a role group if you've used the Exchange Management Shell to configure multiple scopes or exclusive scopes on those role assignments. If you've configured multiple scopes or exclusive scopes on those role assignments, you must use the Exchange Management Shell procedures later in this topic to manage scopes. For more information about management role scopes, see [Understanding Management Role Scopes](http://technet.microsoft.com/library/24ed4a38-438a-4223-9f9c-5d4dea4b046b.aspx). 
  
1. In the EAC, navigate to **Permissions** \> **Admin Roles**.
    
2. Select the role group you want to change the scope on, and then click **Edit**![Edit icon](../media/ITPro_EAC_EditIcon.png).
    
3. Select one of the two following **Write scope** options: 
    
  - A write scope from the drop-down box, where you can select either the default write scope or a custom write scope.
    
  - **Organizational unit**: Select this option and provide an organizational unit (OU) if you want to scope this role group to an OU.
    
4. Click **Save** to save the changes to the role group. 
    
### Use the Exchange Management Shell to change the scope of all role assignments on a role group at the same time

Role assignments between the role group and the roles assigned to it can use the implicit scope obtained from the roles themselves, the same custom scope, or different custom scopes. For more information about role assignments, see [Understanding Management Role Assignments](http://technet.microsoft.com/library/1dc33dd6-52fb-4852-a5ce-027bc73e1d8f.aspx).
  
The scopes on the role assignments are managed using the **Set-ManagementRoleAssignment** cmdlet. You can't manage scopes using the **Set-RoleGroup** cmdlet. 
  
To change the scope of all the role assignments between a role group and a set of management roles at the same time, you need to first retrieve the role assignments on the role group, and then set the new scope on each of the assignments. You can do this by using the **Get-ManagementRoleAssignment** cmdlet to retrieve the role assignments, and then pipe them to the **Set-ManagementRoleAssignment** cmdlet. 
  
This procedure uses the concepts of pipelining and the _WhatIf_ switch. For more information, see the following topics: 
  
- [Pipelining](http://technet.microsoft.com/library/59411ed3-926b-4eec-a462-84e6b26056c9.aspx)
    
- [WhatIf, Confirm, and ValidateOnly Switches](http://technet.microsoft.com/library/a850eea7-431e-49c5-b877-1ebde2a2b48f.aspx)
    
To set the scope on all of the role assignments on a role group at the same time, use the following syntax.
  
```
Get-ManagementRoleAssignment -RoleAssignee <name of role group> | Set-ManagementRoleAssignment -CustomRecipientWriteScope <recipient scope name> -CustomConfigWriteScope <configuration scope name> -RecipientRelativeScopeWriteScope < MyDistributionGroups | Organization | Self> -ExclusiveRecipientWriteScope <exclusive recipient scope name> -ExclusiveConfigWriteScope <exclusive configuration scope name> -RecipientOrganizationalUnitScope <organizational unit>
```

You use only the parameters you need to configure the scope you want to use. For example, if you want to change the recipient scope for all role assignments on the Sales Recipient Management role group to Direct Sales Employees, use the following command.
  
```
Get-ManagementRoleAssignment -RoleAssignee "Sales Recipient Management" | Set-ManagementRoleAssignment -CustomRecipientWriteScope "Direct Sales Employees"
```

> [!NOTE]
> You can use the _WhatIf_ switch to verify that only the role assignments you want to change are changed. Run the preceding command with the _WhatIf_ switch to verify the results, and then remove the _WhatIf_ switch to apply the changes. 
  
For more information about changing management role assignments, see [Change a Role Assignment](http://technet.microsoft.com/library/0fa77efc-e393-461f-b3c0-232cc56cee85.aspx).
  
For detailed syntax and parameter information, see [Get-ManagementRoleAssignment](http://technet.microsoft.com/library/a3a6ee46-061b-444a-8639-43a416309445.aspx).
  
### Use the Exchange Management Shell to change the scope of individual role assignments on a role group

Role assignments between the role group and the roles assigned to it can use the implicit scope obtained from the roles themselves, the same custom scope, or different custom scopes. For more information about role assignments, see [Understanding Management Role Assignments](http://technet.microsoft.com/library/1dc33dd6-52fb-4852-a5ce-027bc73e1d8f.aspx).
  
The scopes on the role assignments are managed using the **Set-ManagementRoleAssignment** cmdlet. You can't manage scopes using the **Set-RoleGroup** cmdlet. 
  
This procedure uses the concepts of pipelining and the **Format-List** cmdlet. For more information, see the following topics: 
  
- [Pipelining](http://technet.microsoft.com/library/59411ed3-926b-4eec-a462-84e6b26056c9.aspx)
    
- [Working with Command Output](http://technet.microsoft.com/library/8320e1a5-d3f5-4615-878d-b23e2aaa6b1e.aspx)
    
To change the scope on a role assignment between a role group and a management role, you first find the name of the role assignment, and then set the scope on the role assignment.
  
1. To find the names of all the role assignments on a role group, use the following command. By piping the management role assignments to the **Format-List** cmdlet, you can view the full name of the assignment. 
    
  ```
  Get-ManagementRoleAssignment -RoleAssignee <role group name> | Format-List Name
  ```

2. Find the name of the role assignment you want to change. Use the name of the role assignment in the next step.
    
3. To set the scope on an individual assignment, use the following syntax.
    
  ```
  Set-ManagementRoleAssignment <role assignment name> -CustomRecipientWriteScope <recipient scope name> -CustomConfigWriteScope <configuration scope name> -RecipientRelativeScopeWriteScope < MyDistributionGroups | Organization | Self> -ExclusiveRecipientWriteScope <exclusive recipient scope name> -ExclusiveConfigWriteScope <exclusive configuration scope name> -RecipientOrganizationalUnitScope <organizational unit>
  ```

You use only the parameters you need to configure the scope you want to use. For example, if you want to change the recipient scope for the Mail Recipients_Sales Recipient Management role assignment to All Sales Employees, use the following command.
  
```
Set-ManagementRoleAssignment "Mail Recipients_Sales Recipient Management" -CustomRecipientWriteScope "All Sales Employees"
```

For more information about changing management role assignments, see [Change a Role Assignment](http://technet.microsoft.com/library/0fa77efc-e393-461f-b3c0-232cc56cee85.aspx).
  
For detailed syntax and parameter information, see [Set-ManagementRoleAssignment](http://technet.microsoft.com/library/2e0659f9-dfb6-4d91-93fb-35a6a7f8a449.aspx).
  
### How do you know this worked?

To verify that you have successfully changed the scope of a role assignment on a role group, do the following:
  
- If you used the EAC to configure the scope on the role group, do the following:
    
1. In the EAC, navigate to **Permissions**\> **Admin Roles**. All the role groups in your organization are listed here.
    
2. Select a role group to view the scope that's configured on the role group.
    
- If you used the Exchange Management Shell to configure the scope on the role group, do the following:
    
1. Run the following command in the Exchange Management Shell.
    
  ```
  Get-ManagementRoleAssignment -RoleAssignee <role group name> | Format-Table *WriteScope
  ```

2. Verify that the write scope on the role assignments has been changed to the scope you specified.
    
## Add or remove a role group delegate
<a name="AddRemoveRGDelegate"> </a>

Role group delegates are users or universal security groups (USGs) that can add or remove members from a role group or change the properties of a role group. By adding or removing role group delegates, you can control who is allowed to manage a role group.
  
> [!IMPORTANT]
> After you add a delegate to a role group, the role group can only be managed by the delegates on the role group, or by users who are assigned, either directly or indirectly, the Role Management management role. > If a user is assigned, either directly or indirectly, the Role Management role and isn't added as a delegate of the role group, the user must use the _BypassSecurityGroupManagerCheck_ switch on the **Add-RoleGroupMember**, **Remove-RoleGroupMember**, **Update-RoleGroupMember**, and **Set-RoleGroup** cmdlets to manage a role group. 
  
> [!NOTE]
> You can't use the EAC to add a delegate to a role group. 
  
### Use the Exchange Management Shell to add a delegate to a role group

To change the list of delegates on a role group, you use the _ManagedBy_ parameter on the **Set-RoleGroup** cmdlet. The _ManagedBy_ parameter overwrites the entire delegate list on the role group. If you want to add delegates to the role group rather than replace the entire list of delegates, use the following steps: 
  
1. Store the role group in a variable using the following command.
    
  ```
  $RoleGroup = Get-RoleGroup <role group name>
  ```

2. Add the delegate to the role group stored in the variable using the following command.
    
  ```
  $RoleGroup.ManagedBy += (Get-User <user to add>).Identity
  ```

    > [!NOTE]
    > Use the **Get-Group** cmdlet if you want to add a USG. 
  
3. Repeat Step 2 for each delegate you want to add.
    
4. Apply the new list of delegates to the actual role group using the following command.
    
  ```
  Set-RoleGroup <role group name> -ManagedBy $RoleGroup.ManagedBy
  ```

This example adds the user David Strome as a delegate on the Organization Management role group.
  
```
$RoleGroup = Get-RoleGroup "Organization Management"
$RoleGroup.ManagedBy += (Get-User "David Strome").Identity
Set-RoleGroup "Organization Management" -ManagedBy $RoleGroup.ManagedBy
```

For detailed syntax and parameter information, see [Set-RoleGroup](http://technet.microsoft.com/library/c66ee1a2-cec7-4b76-a592-a5e626f4f9d3.aspx).
  
### Use the Exchange Management Shell to remove a delegate from a role group

To change the list of delegates on a role group, you use the _ManagedBy_ parameter on the **Set-RoleGroup** cmdlet. The _ManagedBy_ parameter overwrites the entire delegate list on the role group. If you want to remove delegates from the role group rather than replace the entire list of delegates, use the following steps: 
  
1. Store the role group in a variable using the following command.
    
  ```
  $RoleGroup = Get-RoleGroup <role group name>
  ```

2. Remove the delegate from the role group stored in the variable using the following command.
    
  ```
  $RoleGroup.ManagedBy -= (Get-User <user to remove>).Identity
  ```

    > [!NOTE]
    > Use the **Get-Group** cmdlet if you want to remove a USG. 
  
3. Repeat Step 2 for each delegate you want to remove.
    
4. Apply the new list of delegates to the actual role group using the following command.
    
  ```
  Set-RoleGroup <role group name> -ManagedBy $RoleGroup.ManagedBy
  ```

This example removes the user David Strome as a delegate on the Organization Management role group.
  
```
$RoleGroup = Get-RoleGroup "Organization Management"
$RoleGroup.ManagedBy -= (Get-User "David Strome").Identity
Set-RoleGroup "Organization Management" -ManagedBy $RoleGroup.ManagedBy
```

For detailed syntax and parameter information, see [Set-RoleGroup](http://technet.microsoft.com/library/c66ee1a2-cec7-4b76-a592-a5e626f4f9d3.aspx).
  
### How do you know this worked?

To verify that you have successfully changed the delegate list on a role group, do the following:
  
1. In the Exchange Management Shell, run the following command.
    
  ```
  Get-RoleGroup <role group name> | Format-List ManagedBy
  ```

2. Verify that the delegates listed on the _ManagedBy_ property include only the delegates that should be able to manage the role group. 
    

