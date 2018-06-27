---
title: "Install or remove add-ins for Outlook for your organization"
ms.author: dmaguire
author: msdmaguire
manager: laurawi
ms.date: 2/3/2017
ms.audience: End User
ms.topic: article
ms.service: exchange-online
localization_priority: Normal
ms.assetid: 112f3ef7-9943-4a1e-8a42-e08e8e9f67f4
description: "You can install or remove add-ins for Outlook for your organization by using the EAC or the Shell."
---

# Install or remove add-ins for Outlook for your organization

You can install or remove add-ins for Outlook for your organization by using the EAC or the Shell. 
  
> [!NOTE]
> By default, after you install an add-in for your organization, the add-in is available for all users in your organization. After installation, you can use the EAC or the Shell to make the add-in optional or required for your users, and to specify whether you want the add-in to be enabled or disabled. For information about how to change the default settings for an add-in, see [Manage user access to add-ins for Outlook](manage-user-access-to-add-ins.md). To limit availability of add-ins to specific users in your organization, you must use the Shell. For more information, see [Manage user access to add-ins for Outlook](manage-user-access-to-add-ins.md). 
  
For additional management tasks, see [Add-ins for Outlook](add-ins-for-outlook.md).
  
## What do you need to know before you begin?

- Estimated time to complete: 5 minutes.
    
- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Apps for Outlook" entry in the [Recipients permissions](http://technet.microsoft.com/library/5b690bcb-c6df-4511-90e1-08ca91f43b37.aspx) topic. 
    
- You can assign administrators permission to install and manage add-ins for your organization. You can also assign users permission to install and manage add-ins for their own use. For more information, see [Specify the administrators and users who can install and manage add-ins for Outlook](specify-who-can-install-and-manage-add-ins.md). 
    
- Access to the Office Store isn't supported for mailboxes or organizations in specific regions. If you don't see **Add from the Office Store** as an option in the **Exchange admin center** under **Organization** \> **Add-ins** \> ![Add Icon](../../media/ITPro_EAC_AddIcon.gif), you may be able to install an add-in for Outlook from a URL or file location. For more information, contact your service provider.
    
- For information about keyboard shortcuts that may apply to the procedures in this topic, see **Keyboard shortcuts in the Exchange admin center**.
    
> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612),[Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351).. 
  
## What do you want to do?

### Install an add-in for Outlook

#### Use the EAC to add an add-in
<a name="BKMK_EAC"> </a>

1. In the EAC, navigate to **Organization** \> **Add-ins**.
    
2. Click **New**![Add Icon](../../media/ITPro_EAC_AddIcon.gif), and then choose the location that you want to install the add-in from.
    
  - **Add from the Office Store**. At the Office Store, select the app you want to install, and then click **Add**. Apps that work with Outlook Web App are listed under **Add-ins for Office and SharePoint** \> **Outlook**.
    
    > [!NOTE]
    > Access to the Office Store isn't supported for mailboxes or organizations in specific regions. If you don't see **Add from the Office Store** as an option in the **Exchange admin center** under **Organization** \> **Add-ins** \> ![Add Icon](../../media/ITPro_EAC_AddIcon.gif), you may be able to install an add-in for Outlook from a URL or file location. For more information, contact your service provider. 
  
  - **Add from URL**. In **URL**, enter the full URL for the add-in manifest file that you want to install.
    
  - **Add from file**. Select **Browse**, and then navigate to the location of the add-in manifest file that you want to install.
    
3. Click **Save**.
    
#### Use the Shell to add an add-in
<a name="BKMK_Shell"> </a>

This example shows you how to add an add-in from a URL.
  
```
New-App -OrganizationApp -Url <URL location for add-in manifest file>
```

This example shows you how to add an add-in from a file.
  
```
New-App -OrganizationApp -FileData <File location for add-in manifest file>
```

> [!TIP]
> When you use the Shell to install an add-in for your organization, you can install the add-in and configure settings for it at the same time. 
  
For syntax and parameters, see [New-App](http://technet.microsoft.com/library/f05951d8-1e49-42b6-a341-66eb67b2870f.aspx).
  
### Remove an add-in for Outlook

#### Use the EAC to remove an add-in

1. In the EAC, navigate to **Organization** \> **Add-ins**.
    
2. In the list view, select the app that you want to remove, and then click **Delete**![Delete icon](../../media/ITPro_EAC_DeleteIcon.gif). 
    
#### Use the Shell to remove an add-in

You can use the Shell to remove an add-in from your organization.
  
> [!NOTE]
> Run the following command to look up the display names and application IDs for all the add-ins for Outlook installed for your organization. 
  
```
Get-App -OrganizationApp |FL DisplayName,AppID
```

Run the following command to remove the custom add-in Finance Test Add-in from the organization.
  
```
Remove-App -OrganizationApp -Identity <GUID for Finance Test Add-in>
```

For syntax and parameters, see [Remove-App](http://technet.microsoft.com/library/cfd1245f-dcd2-48c1-b753-a7ebedd2803f.aspx). 
  
## How do you know this worked?

To view the add-ins that are installed in your organization, do one the following:
  
- In the EAC, navigate to **Organization** \> **Add-ins**, and then review the list of installed add-ins.
    
- From the Shell, run  `Get-App`, and then review the list of installed add-ins.
    

