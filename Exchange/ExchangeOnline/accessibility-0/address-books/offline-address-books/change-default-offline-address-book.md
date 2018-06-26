---
title: "Change the default offline address book"
ms.author: kwekua
author: kwekua
manager: scotv
ms.date: 12/16/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 61abf78e-2543-4431-acc8-839e3c7a4548
description: "By default, when you install the Mailbox server role, a Web-based default offline address book (OAB) named Default Offline Address Book is created. You can set any OAB in your Exchange organization as the default OAB. This new default OAB is associated with all newly created mailbox databases. You can have only one default OAB in your organization. If you delete the default OAB, Microsoft Exchange doesn't automatically assign another OAB as the default. You must manually designate another OAB as the default."
---

# Change the default offline address book

By default, when you install the Mailbox server role, a Web-based default offline address book (OAB) named Default Offline Address Book is created. You can set any OAB in your Exchange organization as the default OAB. This new default OAB is associated with all newly created mailbox databases. You can have only one default OAB in your organization. If you delete the default OAB, Microsoft Exchange doesn't automatically assign another OAB as the default. You must manually designate another OAB as the default. 
  
For additional management tasks related to OABs, see [Offline address book procedures](offline-address-book-procedures.md).
  
## What do you need to know before you begin?

- Estimated time to complete each procedure: 5 minutes.
    
- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Offline address books" entry in the [Mailbox Permissions](http://technet.microsoft.com/library/5b690bcb-c6df-4511-90e1-08ca91f43b37.aspx) topic. 
    
- By default in Exchange Online, the Address List role isn't assigned to any role groups. To use any cmdlets that require the Address List role, you need to add the role to a role group. For more information, see the "Add a role to a role group" section in the topic, **Manage role groups**.
    
- You can't use the Exchange Administration Center (EAC) to perform this procedure. You must use the Shell.
    
- For information about keyboard shortcuts that may apply to the procedures in this topic, see **Keyboard shortcuts in the Exchange admin center**.
    
> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612),[Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351). 
  
## Use the Shell to change the default OAB

This example sets the OAB named My OAB as the default OAB.
  
```
Set-OfflineAddressBook -Identity "My OAB" -IsDefault $true
```

For detailed syntax and parameter information, see [Set-OfflineAddressBook](http://technet.microsoft.com/library/1221dda7-1923-4fec-a756-7540e18ae9f9.aspx).
  

