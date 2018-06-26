---
title: "Create an offline address book"
ms.author: kwekua
author: kwekua
manager: scotv
ms.date: 4/24/2015
ms.audience: ITPro
ms.topic: article
f1_keywords:
- 'Microsoft.Exchange.Management.SnapIn.Esm.OrganizationConfiguration.Mailbox.NewOabWizardForm.OabIntroductionWizardPage'
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: b57bb4ce-5b6e-4702-a2f8-04bf3898a861
description: "An offline address book (OAB) in Exchange Server 2013 is a downloaded copy of an address book that allows an Outlook user to access the information while disconnected from the server. Exchange administrators can decide which address books are made available to users who work offline, and they can also configure the method by which the address books are distributed (web-based distribution or public folder distribution)."
---

# Create an offline address book

An offline address book (OAB) in Exchange Server 2013 is a downloaded copy of an address book that allows an Outlook user to access the information while disconnected from the server. Exchange administrators can decide which address books are made available to users who work offline, and they can also configure the method by which the address books are distributed (web-based distribution or public folder distribution).
  
For additional management tasks related to OABs, see [Offline address book procedures](offline-address-book-procedures.md).
  
## What do you need to know before you begin?

- Estimated time to complete each procedure: 5 minutes.
    
- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Offline address books" entry in the [Email Address and Address Book Permissions](http://technet.microsoft.com/library/1c1de09d-16ef-4424-9bfb-eb7edffbc8c2.aspx) topic. 
    
- By default in Exchange Online, the Address List role isn't assigned to any role groups. To use any cmdlets that require the Address List role, you need to add the role to a role group. For more information, see the "Add a role to a role group" section in the topic, **Manage role groups**.
    
- You can't use the Exchange Administration Center (EAC) to perform this procedure. You must use the Shell.
    
- For information about keyboard shortcuts that may apply to the procedures in this topic, see **Keyboard shortcuts in the Exchange admin center**.
    
> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612),[Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351). 
  
## Use the Shell to create an OAB with web-based distribution
<a name="UseShellWeb"> </a>

This example creates an OAB named OAB_Contoso that uses web-based distribution for Outlook 2007 or later clients by using the default virtual directory.
  
```
New-OfflineAddressBook -Name "OAB_Contoso" -AddressLists "\Default Global Address List" -VirtualDirectories $Null -GlobalWebDistributionEnabled $True
```

For detailed syntax and parameter information, see [New-OfflineAddressBook](http://technet.microsoft.com/library/8b9a3931-90c3-4b36-9dcb-5e2e65cd7e5e.aspx).
  

