---
title: "Assign an address book policy to mail users"
ms.author: kwekua
author: kwekua
manager: scotv
ms.date: 6/24/2018
ms.audience: ITPro
ms.topic: article
ms.service: exchange-online
localization_priority: Normal
ms.assetid: bdfe6575-24c0-47d0-9cfb-ece910db248b
description: "After you create an address book policy (ABP), you must assign it to mailbox users. Users aren't assigned a default ABP when their user account is created. If you don't assign an ABP to a user, the global address list (GAL) for your entire organization will be accessible to the user through Outlook and Outlook Web App. To learn more, see Address book policies."
---

# Assign an address book policy to mail users

After you create an address book policy (ABP), you must assign it to mailbox users. Users aren't assigned a default ABP when their user account is created. If you don't assign an ABP to a user, the global address list (GAL) for your entire organization will be accessible to the user through Outlook and Outlook Web App. To learn more, see [Address book policies](address-book-policies.md).
  
Interested in scenarios that use this procedure? See [Scenario: Deploying Address Book Policies](http://technet.microsoft.com/library/6ac3c87d-161f-447b-afb2-149ae7e3f1dc.aspx).
  
## What do you need to know before you begin?

- Estmated time to complete: Less than 5 minutes.
    
- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Address book policies" entry in the [Email Address and Address Book Permissions](http://technet.microsoft.com/library/1c1de09d-16ef-4424-9bfb-eb7edffbc8c2.aspx) topic. 
    
- For information about keyboard shortcuts that may apply to the procedures in this topic, see **Keyboard shortcuts in the Exchange admin center**.
    
> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612),[Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351). 
  
## What do you want to do?

### Use the EAC to assign an ABP to a mailbox user
<a name="UseEMC"> </a>

1. Navigate to **Recipients** \> **Mailboxes**.
    
2. In the list view, select the user that you want to assign the policy to, and then click **Edit**![Edit icon](../../media/ITPro_EAC_EditIcon.gif).
    
3. Click **Mailbox features**.
    
4. In the **Address book policy** list, select the ABP that you want to apply to this user. 
    
5. Click **Save**.
    
### Use the EAC to assign an ABP to multiple mailbox users
<a name="Bulk"> </a>

1. Navigate to **Recipients** \> **Mailboxes**.
    
2. In the list view use the Ctrl key to select multiple users.
    
3. In the details pane, click **More options**.
    
4. Under **Address Book Policy**, click **Update**.
    
5. In the **Select Address Book Policy** list, select the ABP that you want to apply to these users. 
    
6. Click **Save**.
    
### Use the Shell to assign an ABP to mailbox users
<a name="UseShell"> </a>

This example assigns the ABP All Fabrikam to the existing mailbox user joe@fabrikam.com.
  
```
Set-Mailbox -Identity joe@fabrikam.com -AddressBookPolicy "All Fabrikam"
```

This example assigns the ABP ABP_EngineeringDepartment to all mailbox users whose  `CustomAttribute11` value contains "Engineering Department". 
  
```
Get-Mailbox -Filter {(CustomAttribute11 -like "Engineering Department")} | Set-Mailbox -AddressBookPolicy ABP_EngineeringDepartment
```

For detailed syntax and parameter information, see [Set-Mailbox](http://technet.microsoft.com/library/a0d413b9-d949-4df6-ba96-ac0906dedae2.aspx) and [Get-Mailbox](http://technet.microsoft.com/library/8a5a6eb9-4a75-47f9-ae3b-a3ba251cf9a8.aspx).
  

