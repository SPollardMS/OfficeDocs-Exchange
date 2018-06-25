---
title: "Specify the administrators and users who can install and manage add-ins for Outlook"
ms.author: dmaguire
author: msdmaguire
manager: laurawi
ms.date: 2/8/2017
ms.audience: End User
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 7ee4302d-b8bb-40a0-9810-10d3a0271bcb
description: "You can specify which administrators in your organization have permissions to install and manage add-ins for Outlook. You can also specify which users in your organization have permission to install and manage add-ins for their own use."
---

# Specify the administrators and users who can install and manage add-ins for Outlook

You can specify which administrators in your organization have permissions to install and manage add-ins for Outlook. You can also specify which users in your organization have permission to install and manage add-ins for their own use. 
  
This is done by assigning or removing management roles specific to add-ins. There are five built-in roles you can use.
  
Administrative roles
  
- **Org Marketplace Apps** Enables an administrator to install and manage add-ins that are available from the Office Store for their organization. 
    
- **Org Custom Apps** Enables an administrator to install and manage custom add-ins for their organization. 
    
User roles
  
- **My Marketplace Apps** Enables a user to install and manage Office Store add-ins for their own use. 
    
- **My Custom Apps** Enables a user to install and manage custom add-ins for their own use. 
    
- **My ReadWriteMailbox Apps** Enables a user to install and manage add-ins that request the ReadWriteMailbox permission level in their manifest. 
    
By default, all administrators who have the **Organization Management** role group have both of the above administrative roles enabled. Also by default, end users have the above user roles enabled. 
  
For information about each of these roles, see [Org Marketplace Apps role](http://technet.microsoft.com/library/137ee328-0bad-4911-a7bf-82da7678f246.aspx), [Org Custom Apps role](http://technet.microsoft.com/library/ab2aac13-f783-43e6-a369-75cce1d4943f.aspx), [My Marketplace Apps role](http://technet.microsoft.com/library/5c208d2d-8f76-46a7-9d2e-7c616f21ee67.aspx), [My Custom Apps role](http://technet.microsoft.com/library/aa0321b3-2ec0-4694-875b-7a93d3d99089.aspx), and [My ReadWriteMailbox Apps role](http://technet.microsoft.com/library/febb73fb-3a0b-4c67-b53b-9566d7c32cd2.aspx).
  
For information about add-ins, see [Add-ins for Outlook](add-ins-for-outlook.md).
  
## What do you need to know before you begin?

- Estimated time to complete: 5 minutes.
    
- You need to be assigned permissions before you can run this cmdlet. Although all parameters for this cmdlet are listed in this topic, you may not have access to some parameters if they're not included in the permissions assigned to you. To see what permissions you need, see the "Role assignments" entry in the [Role management permissions](http://technet.microsoft.com/library/cb9591c4-fbb3-4199-8007-6bbfdfd5a2e9.aspx) topic. 
    
- Access to the Office Store isn't supported for mailboxes or organizations in specific regions. If you don't see **Add from the Office Store** as an option in the **Exchange admin center** under **Organization** \> **Add-ins** \> ![Add Icon](../../media/ITPro_EAC_AddIcon.gif), you may be able to install an add-in for Outlook from a URL or file location. For more information, contact your service provider.
    
- For information about keyboard shortcuts that may apply to the procedures in this topic, see **Keyboard shortcuts in the Exchange admin center**.
    
> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612),[Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351).. 
  
## What do you want to do?

### Assign administrators the permissions required to install and manage add-ins for your organization

#### Use the EAC to assign permissions to administrators

You can use the EAC to assign administrators the permissions required to install and manage add-ins that available from the Office Store for your organization. For detailed information about how to do this, see [Manage role groups](http://technet.microsoft.com/library/ab9b7a3b-bf67-4ba1-bde5-8e6ac174b82c.aspx).
  
### Assign users the permissions required to install and manage add-ins for their own use

#### Use the EAC to assign permissions to users

You can use the EAC to assign users the permissions required to view and modify custom add-ins for their own use. For detailed information about how to do this, see [Manage role groups](http://technet.microsoft.com/library/ab9b7a3b-bf67-4ba1-bde5-8e6ac174b82c.aspx). 
  
## How do you know this worked?

To verify that you've successfully assigned permissions for a user, run a Shell command using the format  `Get-ManagementRoleAssignment -Role <Role Name> -GetEffectiveUsers`, where  `Role Name` is the role for which you want to verify assigned permissions. 
  
This example shows you how to verify whom you've assigned permissions to install add-ins from the Office Store for the organization.
  
1. Run  `Get-ManagementRoleAssignment -Role "Org Marketplace Apps" -GetEffectiveUsers`.
    
2. In the results, review the entries in the **Effective Users** column. 
    
For more information about syntax and parameters, see [Get-ManagementRoleAssignment](http://technet.microsoft.com/library/a3a6ee46-061b-444a-8639-43a416309445.aspx).
  

