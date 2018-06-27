---
title: "Configure global address list properties"
ms.author: kwekua
author: kwekua
manager: scotv
ms.date: 6/24/2018
ms.audience: ITPro
ms.topic: article
ms.service: exchange-online
localization_priority: Normal
ms.assetid: 5fd2c96f-fe93-4b5a-8495-70c450511a37
description: "This topic explains how to modify the settings of a global address list (GAL)."
---

# Configure global address list properties

This topic explains how to modify the settings of a global address list (GAL).
  
## What do you need to know before you begin?

- Estimated time to complete each procedure: 5 minutes.
    
- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Address lists" entry in the [Email Address and Address Book Permissions](http://technet.microsoft.com/library/1c1de09d-16ef-4424-9bfb-eb7edffbc8c2.aspx) topic. 
    
- By default in Exchange Online, the Address List role isn't assigned to any role groups. To use any cmdlets that require the Address List role, you need to add the role to a role group. For more information, see the "Add a role to a role group" section in the topic, **Manage role groups**.
    
- You can't edit the settings of the default GAL. 
    
- You can't use the Exchange Administration Center (EAC) to perform this procedure. You must use the Shell.
    
- For information about keyboard shortcuts that may apply to the procedures in this topic, see **Keyboard shortcuts in the Exchange admin center**.
    
> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612),[Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351). 
  
## Use the Shell to configure GAL properties

This example assigns a new name, FourthCoffee, to the GAL that has the GUID 96d0c505-eba8-4103-ad4f-577a1bf4ad7b.
  
```
Set-GlobalAddressList -Identity 96d0c505-eba8-4103-ad4f-577a1bf4ad7b -Name FourthCoffee
```

> [!NOTE]
> If you're using precanned conditional filter properties, the value for the  _IncludedRecipients_ parameter can't be blank. 
  
This example changes the recipients who will be included in the Fourth Coffee global GAL to those whose company is set to Fourth Coffee.
  
```
Set-GlobalAddressList -Identity Fourth Coffee -RecipientFilter {Company -eq "Fourth Coffee"}
```

For detailed syntax and parameter information, see [Set-GlobalAddressList](http://technet.microsoft.com/library/96bf236f-0fb8-44db-9b22-ddc0933db951.aspx).
  

