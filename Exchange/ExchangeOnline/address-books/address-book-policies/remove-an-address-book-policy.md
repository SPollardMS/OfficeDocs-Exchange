---
title: "Remove an address book policy"
ms.author: kwekua
author: kwekua
manager: scotv
ms.date: 6/24/2018
ms.audience: ITPro
ms.topic: article
ms.service: exchange-online
localization_priority: Normal
ms.assetid: c20c6f82-2f75-4116-9be1-c5af10113f71
description: "Use this procedure to remove an address book policy (ABP)."
---

# Remove an address book policy

Use this procedure to remove an address book policy (ABP).
  
## What do you need to know before you begin?

- Estimated time to complete: Less than 5 minutes.
    
- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Address book policies" entry in the [Email Address and Address Book Permissions](http://technet.microsoft.com/library/1c1de09d-16ef-4424-9bfb-eb7edffbc8c2.aspx) topic. 
    
- You can't remove an ABP if it's assigned to a user's mailbox or to a soft-deleted mailbox. To determine if an ABP is assigned to a user, run the following Shell command:
    
     `Get-Mailbox | Where $._AddressBookPolicy -eq <AddressBookPolicyName>`
    
    To determine if an ABP is assigned to a soft-deleted mailbox, run the following command: 
    
     `Get-Mailbox -SoftDeletedMailbox | Where $._AddressBookPolicy -eq <AddressBookPolicyName>`
    
- To remove an ABP from a user's mailbox, you can use the **Mailbox features** page of the mailbox's properties or the **Set-Mailbox** cmdlet. 
    
- You can't use the Exchange Administration Center (EAC) to remove an ABP. You must use the Shell.
    
- For information about keyboard shortcuts that may apply to the procedures in this topic, see **Keyboard shortcuts in the Exchange admin center**.
    
> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612),[Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351). 
  
## Use the Shell to remove an ABP

This example removes the ABP ABP_TailspinToys.
  
```
Remove-AddressBookPolicy -Identity "ABP_TailspinToys"
```

For detailed syntax and parameter information, see [Remove-AddressBookPolicy](http://technet.microsoft.com/library/57ff215a-cba5-46d1-a7f7-ab2512ce4b6f.aspx).
  

