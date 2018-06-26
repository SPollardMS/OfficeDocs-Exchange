---
title: "Remove an offline address book"
ms.author: kwekua
author: kwekua
manager: scotv
ms.date: 12/16/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: d69f1e8a-b3cb-4739-90cd-85ea450d06f3
description: "This topic explains how to remove an offline address book (OAB)."
---

# Remove an offline address book

This topic explains how to remove an offline address book (OAB).
  
For additional management tasks related to OABs, see [Offline address book procedures](offline-address-book-procedures.md).
  
## What do you need to know before you begin?

- Estimated time to complete each procedure: 5 minutes.
    
- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Offline address books" entry in the [Email Address and Address Book Permissions](http://technet.microsoft.com/library/1c1de09d-16ef-4424-9bfb-eb7edffbc8c2.aspx) topic. 
    
- By default in Exchange Online, the Address List role isn't assigned to any role groups. To use any cmdlets that require the Address List role, you need to add the role to a role group. For more information, see the "Add a role to a role group" section in the topic, **Manage role groups**.
    
- After you remove an OAB that's linked to a user or to a mailbox database, the recipient will download the default OAB until you assign a new OAB for that user. If you remove the default OAB, you must assign a different OAB as the default OAB. For instructions about how to change the default OAB, see [Change the default offline address book](change-default-offline-address-book.md).
    
- You can't use the Exchange Administration Center (EAC) to perform this procedure. You must use the Shell.
    
- For information about keyboard shortcuts that may apply to the procedures in this topic, see **Keyboard shortcuts in the Exchange admin center**.
    
> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612),[Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351). 
  
## Use the Shell to remove an OAB

This example removes an OAB named My OAB.
  
```
Remove-OfflineAddressBook -Identity "My OAB"
```

Type Y to confirm that you want to remove the OAB, and then press ENTER. 
  
For detailed syntax and parameter information, see [Remove-OfflineAddressBook](http://technet.microsoft.com/library/88a8f173-34b9-4e75-8f1a-26ad6f972e98.aspx).
  

