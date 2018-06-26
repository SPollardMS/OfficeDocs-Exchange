---
title: "Create an address book policy"
ms.author: kwekua
author: kwekua
manager: scotv
ms.date: 6/24/2018
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 6359abaf-e6f6-4667-8c2b-3860728b39a9
description: "Address book policies (ABPs) allow you to segment users into specific groups to provide customized views of your organization's global address list (GAL). When creating an ABP, you assign a GAL, an offline address book (OAB), a room list, and one or more address lists to the policy. You can then assign the ABP to mailbox users, providing them with access to a customized GAL in Outlook and Outlook Web App. The goal is to provide a simpler mechanism to accomplish GAL segmentation for on-premises organizations that require multiple GALs. To learn more about ABPs, see Address book policies."
---

# Create an address book policy

Address book policies (ABPs) allow you to segment users into specific groups to provide customized views of your organization's global address list (GAL). When creating an ABP, you assign a GAL, an offline address book (OAB), a room list, and one or more address lists to the policy. You can then assign the ABP to mailbox users, providing them with access to a customized GAL in Outlook and Outlook Web App. The goal is to provide a simpler mechanism to accomplish GAL segmentation for on-premises organizations that require multiple GALs. To learn more about ABPs, see [Address book policies](address-book-policies.md).
  
Interested in scenarios that use this procedure? See [Scenario: Deploying Address Book Policies](http://technet.microsoft.com/library/6ac3c87d-161f-447b-afb2-149ae7e3f1dc.aspx). 
  
## What do you need to know before you begin?

- Estmated time to complete: Less than 5 minutes.
    
- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Address book policies" entry in the [Email Address and Address Book Permissions](http://technet.microsoft.com/library/1c1de09d-16ef-4424-9bfb-eb7edffbc8c2.aspx) topic. 
    
- By default in Exchange Online, the Address List role isn't assigned to any role groups. To use any cmdlets that require the Address List role, you need to add the role to a role group. For more information, see the "Add a role to a role group" section in the topic, **Manage role groups**.
    
- Creating an ABP for an organization is a multi-step process that requires planning. For more information, see [Scenario: Deploying Address Book Policies](http://technet.microsoft.com/library/6ac3c87d-161f-447b-afb2-149ae7e3f1dc.aspx).
    
- You can't use the Exchange Administration Center (EAC) to create ABPs. You must use the Shell.
    
- For information about keyboard shortcuts that may apply to the procedures in this topic, see **Keyboard shortcuts in the Exchange admin center**.
    
- Having problems? Ask for help in the Exchange forums. Visit the forums at [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612),[Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351).
    
## Use the Shell to create an ABP
<a name="UseShell"> </a>

This example creates an ABP with the following settings: 
  
- **Name**: All Fabrikam ABP
    
- **GAL**: All Fabrikam
    
- **OAB**: Fabrikam-All-OAB
    
- **Room list**: All Fabrikam Rooms
    
- **Address lists**: All Fabrikam, All Fabrikam Mailboxes, All Fabrikam DLs, and All Fabrikam Contacts
    
```
New-AddressBookPolicy -Name "All Fabrikam ABP" -AddressLists "\All Fabrikam","\All Fabrikam Mailboxes","\All Fabrikam DLs","\All Fabrikam Contacts" -OfflineAddressBook \Fabrikam-All-OAB -GlobalAddressList "\All Fabrikam" -RoomList "\All Fabrikam Rooms"
```

For detailed syntax and parameter information, see [New-AddressBookPolicy](http://technet.microsoft.com/library/07133bd2-ed6d-4a4b-8c3a-bd0c016f68eb.aspx).
  
## For more information
<a name="UseShell"> </a>

[Assign an address book policy to mail users](assign-an-address-book-policy-to-mail-users.md)
  

