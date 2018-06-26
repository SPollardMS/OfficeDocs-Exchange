---
title: "Assign eDiscovery permissions in Exchange"
ms.author: markjjo
author: markjjo
manager: scotv
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.service: exchange-online
localization_priority: Normal
ms.assetid: 729e09d8-614b-431f-ae04-ae41fb4c628e
description: "If you want users to be able to use Microsoft Exchange Server 2013 In-Place eDiscovery, you must first authorize them by adding them to the Discovery Management role group. Members of the Discovery Management role group have Full Access mailbox permissions for the Discovery mailbox that's created by Exchange Setup."
---

# Assign eDiscovery permissions in Exchange

If you want users to be able to use Microsoft Exchange Server 2013 In-Place eDiscovery, you must first authorize them by adding them to the Discovery Management role group. Members of the Discovery Management role group have Full Access mailbox permissions for the Discovery mailbox that's created by Exchange Setup.
  
> [!CAUTION]
> Members of the Discovery Management role group can access sensitive message content. Specifically, these members can use [In-Place eDiscovery](in-place-ediscovery.md) to search all mailboxes in your Exchange organization, preview messages (and other mailbox items), copy them to a Discovery mailbox and export the copied messages to a .pst file. In most organizations, this permission is granted to legal, compliance, or Human Resources personnel. > 
  
To learn more about the Discovery Management role group, see [Discovery Management](http://technet.microsoft.com/library/b8bc5922-a8c9-4707-906d-fa38bb87da8f.aspx). To learn more about Role Based Access Control (RBAC), see [Understanding Role Based Access Control](http://technet.microsoft.com/library/fd268867-2ae5-441b-8103-7a7583eb2bbe.aspx).
  
Interested in scenarios where this procedure is used? See the following topics:
  
- [Create an In-Place eDiscovery search](create-in-place-ediscovery-search.md)
    
- [Create or remove an In-Place Hold](../../security-and-compliance/create-or-remove-in-place-holds.md)
    
## What do you need to know before you begin?

- Estimated time to complete: 1 minute.
    
- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Role groups" entry in the [Role Management Permissions](http://technet.microsoft.com/library/cb9591c4-fbb3-4199-8007-6bbfdfd5a2e9.aspx) topic. 
    
- By default, the Discovery Management role group doesn't contain any members. Administrators with the Organization Management role are also unable to create or manage discovery searches without being added to the Discovery Management role group. 
    
- In Exchange 2013, members of the Organization Management role group can create an [In-Place Hold and Litigation Hold](../../security-and-compliance/in-place-and-litigation-holds.md) to place all mailbox content on hold. However, to create a query-based In-Place Hold, the user must be a member of the Discovery Management role group or have the Mailbox Search role assigned. 
    
- For information about keyboard shortcuts that may apply to the procedures in this topic, see **Keyboard shortcuts in the Exchange admin center**.
    
## Use the EAC to add a user to the Discovery Management role group

1. Go to **Permissions** \> **Admin roles**.
    
2. In the list view, select **Discovery Management** and then click **Edit**![Edit icon](../../media/ITPro_EAC_EditIcon.gif)
  
3. In **Role Group**, under **Members**, click **Add**![Add Icon](../../media/ITPro_EAC_AddIcon.gif).
    
4. In **Select Members**, select one or more users, click **Add**, and then click **OK**.
    
5. In **Role Group**, click **Save**.
    
## Use the Shell to add a user to the Discovery Management role group

This example adds the user Bsuneja to the Discovery Management role group.
  
```
Add-RoleGroupMember -Identity "Discovery Management" -Member Bsuneja
```

For detailed syntax and parameter information, see [Add-RoleGroupMember](http://technet.microsoft.com/library/ed53e269-a855-4066-88a7-1ba36086bd72.aspx).
  
## How do you know this worked?

To verify that you've added the user to the Discovery Management role group, do the following: 
  
1. In the EAC, go to **Permissions** \> **Admin roles**.
    
2. In the list view, select **Discovery Management**.
    
3. In the details pane, verify that the user is listed under **Members**.
    
You can also run this command to list the members of the Discovery Management role group.
  
```
Get-RoleGroupMember -Identity "Discovery Management"
```

> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612),[Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351). 
  

