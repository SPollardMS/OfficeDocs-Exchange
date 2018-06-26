---
title: "Add an address list to or remove an address list from an offline address book"
ms.author: kwekua
author: kwekua
manager: scotv
ms.date: 12/16/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 86bd5651-ad41-4516-bf23-6579f4e4da03
description: "You can use the Shell to add or remove an address list from an offline address book (OAB). By default, there is an OAB named the Default Offline Address Book that contains the global address list (GAL). OABs are generated based on the address lists that they contain. To create custom OABs that users can download, you can add or remove address lists from OABs."
---

# Add an address list to or remove an address list from an offline address book

You can use the Shell to add or remove an address list from an offline address book (OAB). By default, there is an OAB named the Default Offline Address Book that contains the global address list (GAL). OABs are generated based on the address lists that they contain. To create custom OABs that users can download, you can add or remove address lists from OABs. 
  
For additional management tasks related to OABs, see [Offline address book procedures](offline-address-book-procedures.md).
  
## What do you need to know before you begin?

- Estimated time to complete each procedure: 5 minutes
    
- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Offline address books" entry in the [Mailbox Permissions](http://technet.microsoft.com/library/5b690bcb-c6df-4511-90e1-08ca91f43b37.aspx) topic. 
    
- By default in Exchange Online, the Address List role isn't assigned to any role groups. To use any cmdlets that require the Address List role, you need to add the role to a role group. For more information, see the "Add a role to a role group" section in the topic, **Manage role groups**.
    
- Changes to the address list aren't available for client download until after the OAB in which the address list resides has been generated. For more information, see [Update offline address book](update-offline-address-book.md).
    
- You can't use the Exchange Administration Center (EAC) to perform this procedure. You must use the Shell.
    
- For information about keyboard shortcuts that may apply to the procedures in this topic, see **Keyboard shortcuts in the Exchange admin center**.
    
> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612),[Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351). 
  
## What do you want to do?

### Use the Shell to add an address list to an OAB

When using the  _AddressLists_ parameter, any address lists that currently exist will be overwritten. You must include existing address lists when you use the  _AddressLists_ parameter to continue to generate those address lists in your OAB. This example, in which you have AddressList1 and AddressList2, adds AddressList3. 
  
```
Set-OfflineAddressBook -Identity "My OAB" -AddressLists AddressList1,AddressList2,AddressList3
```

For detailed syntax and parameter information, see [Set-OfflineAddressBook](http://technet.microsoft.com/library/1221dda7-1923-4fec-a756-7540e18ae9f9.aspx).
  
### Use the Shell to remove an address list from an OAB

To remove an address list from an OAB, simply omit that address list from the list of address lists. This example, in which you have AddressList1, AddressList2, and AddressList3, removes AddressList3.
  
```
Set-OfflineAddressBook -Identity "My OAB" -AddressLists AddressList1,AddressList2
```

For detailed syntax and parameter information, see [Set-OfflineAddressBook](http://technet.microsoft.com/library/1221dda7-1923-4fec-a756-7540e18ae9f9.aspx).
  

