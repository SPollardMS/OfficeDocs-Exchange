---
title: "Update offline address book"
ms.author: dstrome
author: dstrome
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.service: exchange-online
localization_priority: Normal
ms.assetid: 448a207e-41b4-4cef-9fe9-a68b81e2ec4e
description: "After you create an OAB or modify OAB settings, the changes aren't available to users until the OAB generation (OABGen) process has completed."
---

# Update offline address book

After you create an OAB or modify OAB settings, the changes aren't available to users until the OAB generation (OABGen) process has completed. 
  
For additional management tasks related to OABs, see [Offline address book procedures](offline-address-book-procedures.md). 
  
## What do you need to know before you begin?

- Estimated time to complete each procedure: 5 minutes.
    
- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Offline address books" entry in the [Email Address and Address Book Permissions](http://technet.microsoft.com/library/1c1de09d-16ef-4424-9bfb-eb7edffbc8c2.aspx) topic. 
    
- You can't use the Exchange Administration Center (EAC) to perform this procedure. You must use the Shell.
    
- For information about keyboard shortcuts that may apply to the procedures in this topic, see **Keyboard shortcuts in the Exchange admin center**.
    
> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612),[Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351). 
  
## Use the Shell to update an OAB

This example updates the OAB named My OAB.
  
```
Update-OfflineAddressBook -Identity "My OAB"
```

For detailed syntax and parameter information, see [Update-OfflineAddressBook](http://technet.microsoft.com/library/08ee5bd7-1c23-492e-8952-d37b2a61c022.aspx).
  

