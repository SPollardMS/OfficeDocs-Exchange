---
title: "Create an offline address book virtual directory"
ms.author: dstrome
author: dstrome
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.service: exchange-online
localization_priority: Normal
ms.assetid: 2c70e21f-2b12-414a-9e8c-65634a767c72
description: "The OAB virtual directory is the distribution for the OAB. By default, when Microsoft Exchange Server 2013 is installed, a new virtual directory named OAB is created in the default internal website in Internet Information Services (IIS). If you have client-side users that connect to Microsoft Outlook from outside your organization's firewall, you can add an external website. Alternatively, when you run the New-OABVirtualDirectory cmdlet in the Shell, a new virtual directory named OAB is created in the default IIS website on the local Exchange server."
---

# Create an offline address book virtual directory

The OAB virtual directory is the distribution for the OAB. By default, when Microsoft Exchange Server 2013 is installed, a new virtual directory named OAB is created in the default internal website in Internet Information Services (IIS). If you have client-side users that connect to Microsoft Outlook from outside your organization's firewall, you can add an external website. Alternatively, when you run the **New-OABVirtualDirectory** cmdlet in the Shell, a new virtual directory named OAB is created in the default IIS website on the local Exchange server. 
  
Creating an OAB virtual directory isn't a common task. Exchange allows for one OAB virtual directory named OAB, and you should create an OAB virtual directory only if there is a problem with the existing OAB virtual directory, and the previous OAB virtual directory was removed. 
  
For additional management tasks related to OABs, see [Offline address book procedures](offline-address-book-procedures.md).
  
> [!IMPORTANT]
> Before you create an OAB virtual directory, make sure that your users are aware of the changes you are making. This procedure may interrupt the OAB downloading process for your users. 
  
## What do you need to know before you begin?

- Estimated time to complete each procedure: 5 minutes.
    
- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Offline address books" entry in the [Email Address and Address Book Permissions](http://technet.microsoft.com/library/1c1de09d-16ef-4424-9bfb-eb7edffbc8c2.aspx) topic. 
    
- The local Exchange server must have the Client Access server role installed.
    
- A default IIS website must exist (for example, /w3svc/1/root).
    
- A virtual directory named OAB doesn't already exist.
    
- Although Web-based distribution is enabled by default and doesn't require further configuration, we recommend that you enable Secure Sockets Layer (SSL) for the OAB distribution point.
    
- You can't use the Exchange Administration Center (EAC) to perform this procedure. You must use the Shell.
    
- For information about keyboard shortcuts that may apply to the procedures in this topic, see **Keyboard shortcuts in the Exchange admin center**.
    
> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612),[Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351). 
  
## Use the Shell to create an OAB virtual directory

To create an OAB virtual directory with all of the default settings, you can run the **New-OABVirtualDirectory** cmdlet without any parameters. Use the following procedure to create an OAB virtual directory with custom settings. 
  
> [!NOTE]
> When creating an OAB virtual directory, we recommend that you have SSL enabled. 
  
This example creates an OAB virtual directory on the Client Access server named CASServer01 that has SSL enabled and an external URL.
  
```
New-OABVirtualDirectory -Server CASServer01 -RequireSSL $true -ExternalURL "https://www.contoso.com/OAB"
```

After you create a new OAB virtual directory, you must edit the settings on each OAB that uses Web-based distribution to reconnect to the OAB virtual directory. For more information, see [Change the offline address book generation schedule](change-address-book-generation-schedule.md).
  
For detailed syntax and parameter information, see [New-OABVirtualDirectory](http://technet.microsoft.com/library/8f976c83-fd98-43c9-9d50-b252bdaae0fc.aspx).
  

