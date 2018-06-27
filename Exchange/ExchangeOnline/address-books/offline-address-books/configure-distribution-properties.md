---
title: "Configure offline address book distribution properties"
ms.author: dstrome
author: dstrome
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
f1_keywords:
- 'Microsoft.Exchange.Management.SnapIn.Esm.Servers.ClientAccess.OabDistributionGeneralPage'
ms.service: exchange-online
localization_priority: Normal
ms.assetid: 8df985e9-75ba-47ea-9cc3-aa98a5d8acf4
description: "For each offline address book (OAB) distribution point in Exchange, you can configure two URLs—an internal URL that can be accessed only from your internal corporate network and an external URL that can be accessed from the Internet."
---

# Configure offline address book distribution properties

For each offline address book (OAB) distribution point in Exchange, you can configure two URLs—an internal URL that can be accessed only from your internal corporate network and an external URL that can be accessed from the Internet. 
  
For additional management tasks related to OABs, see [Offline address book procedures](offline-address-book-procedures.md).
  
## What do you need to know before you begin?

- Estimated time to complete each procedure: 5 minutes.
    
- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Offline address books" entry in the [Email Address and Address Book Permissions](http://technet.microsoft.com/library/1c1de09d-16ef-4424-9bfb-eb7edffbc8c2.aspx) topic. 
    
- You can't use the Exchange Administration Center (EAC) to perform this procedure. You must use the Shell.
    
- For information about keyboard shortcuts that may apply to the procedures in this topic, see **Keyboard shortcuts in the Exchange admin center**.
    
> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612),[Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351). 
  
## Use the Shell to configure OAB distribution properties
<a name="UseShell"> </a>

This example sets the polling interval for OAB distribution on the OAB virtual directory OAB (Default Web Site) to six hours.
  
```
Set-OABVirtualDirectory "OAB (Default Web Site)" -PollInterval 360
```

This example sets the external distribution point to https://contoso.com/OAB for the default OAB virtual directory OAB (Default Web Site).
  
```
Set-OABVirtualDirectory "OAB (Default Web Site)" -ExternalUrl https://contoso.com/OAB
```

For detailed syntax and parameter information, see [set-OabVirtualDirectory](http://technet.microsoft.com/library/d1184716-920c-47cf-9e03-638434c16462.aspx).
  
## For More Information
<a name="UseShell"> </a>

[Understanding Offline Address Books](http://technet.microsoft.com/library/a6bcb072-4ab9-400e-a5d0-c05264629097.aspx)
  

