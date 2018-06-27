---
title: "Remove a global address list"
ms.author: kwekua
author: kwekua
manager: scotv
ms.date: 12/16/2014
ms.audience: ITPro
ms.topic: article
ms.service: exchange-online
localization_priority: Normal
ms.assetid: 65d75b69-641b-4a37-a63c-47cf018f5f22
description: "The global address list (GAL) is a directory that contains entries for every group, user, and contact within an Exchange organization."
---

# Remove a global address list

The global address list (GAL) is a directory that contains entries for every group, user, and contact within an Exchange organization.
  
For additional management tasks related to address lists, see [Managing Address Lists](http://technet.microsoft.com/library/44c87349-964b-4700-9ce9-87bd4cb2249e.aspx).
  
## What do you need to know before you begin?

- Estimated time to complete each procedure: 5 minutes.
    
- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Address lists" entry in the [Email Address and Address Book Permissions](http://technet.microsoft.com/library/1c1de09d-16ef-4424-9bfb-eb7edffbc8c2.aspx) topic. 
    
- By default in Exchange Online, the Address List role isn't assigned to any role groups. To use any cmdlets that require the Address List role, you need to add the role to a role group. For more information, see the "Add a role to a role group" section in the topic, **Manage role groups**.
    
- You can't remove the default GAL.
    
- You can't use the Exchange Administration Center (EAC) to perform this procedure. You must use the Shell.
    
- For information about keyboard shortcuts that may apply to the procedures in this topic, see **Keyboard shortcuts in the Exchange admin center**.
    
> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612),[Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351). 
  
## Use the Shell to remove a GAL

This example removes the GAL Fourth Coffee from the domain controller ad-server.fourthcoffee.com.
  
```
Remove-GlobalAddressList -Identity "Fourth Coffee" -DomainController ad-server.fourthcoffee.com
```

To confirm that you want to remove the GAL, type Y, and then press ENTER.
  
For detailed syntax and parameter information, see [Remove-GlobalAddressList](http://technet.microsoft.com/library/b9d537c9-6a50-4f61-9cb7-bdedc7e7e0c8.aspx).
  

