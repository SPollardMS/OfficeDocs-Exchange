---
title: "Add-ins for Outlook"
ms.author: dmaguire
author: msdmaguire
manager: laurawi
ms.date: 3/13/2017
ms.audience: ITPro
ms.topic: overview
ms.service: exchange-online
localization_priority: Normal
ms.assetid: 28b6f2a1-a235-4023-b561-6fd304962775
description: "Summary: An overview of add-ins for Outlook, which work with Outlook on Windows and MacIntosh computers, on mobile devices, and in Outlook Web App and Outlook on the web."
---

# Add-ins for Outlook

 **Summary**: An overview of add-ins for Outlook, which work with Outlook on Windows and MacIntosh computers, on mobile devices, and in Outlook Web App and Outlook on the web.
  
Add-ins for Outlook are applications that extend the usefulness of Outlook clients by adding information or tools that your users can use without having to leave Outlook. Add-ins are built by third-party developers and can be installed either from a file or URL or from the Office Store. By default, all users can install add-ins. Exchange administrators can use Roles to control users' ability to install add-ins.
  
> [!TIP]
> For information about add-ins for Outlook from an end-user perspective, check out the Help topic [Installed add-ins](https://go.microsoft.com/fwlink/p/?LinkId=282387) at Office.com. That topic provides an overview of the add-ins and also shows you some of the add-ins for Outlook that may be installed by default. 
  
## Office Store add-ins and custom add-ins

Outlook clients supports a variety of add-ins that are available through the Office Store. Outlook also supports custom add-ins that you can create and distribute to users in your organization. 
  
> [!NOTE]
> Access to the Office Store isn't supported for mailboxes or organizations in specific regions. If you don't see **Add from the Office Store** as an option in the **Exchange admin center** under **Organization** \> **Add-ins** \> ![Add Icon](../../media/ITPro_EAC_AddIcon.gif), you may be able to install an add-in for Outlook from a URL or file location. For more information, contact your service provider. 
  
> [!NOTE]
> Some add-ins for Outlook are installed by default. Default add-ins for Outlook only activate on English language content. For example, German postal addresses in the message body won't activate the Bing Maps add-in. 
  
## Add-in access and installation

By default, all users can install and remove add-ins. Exchange administrators have a number of controls available for managing add-ins and users' access to them. Administrators can disable users from installing add-ins that are not downloaded from the Office Store (instead they are "side loaded" from a file or URL). Administrators can also disable users from installing Office Store add-ins, and from installing add-ins on behalf of other users. It is also possible to assign users to a role that allows them to install add-ins for your organization or for a subset of users in your organization.
  
To prevent users from installing an add-in that isn't from the Office Store, remove the **My Custom Apps** role from them. To disable users from installing add-ins from the Office Store, remove the **My Marketplace Apps** role from them. For more details, see [Specify the administrators and users who can install and manage add-ins for Outlook](specify-who-can-install-and-manage-add-ins.md).
  
To install add-ins for some or all users in your organization, see [Install or remove add-ins for Outlook for your organization](install-or-remove-outlook-add-ins.md).
  
If required, you can limit availability of an add-in to specific users in your organization. For more information, see [Manage user access to add-ins for Outlook](manage-user-access-to-add-ins.md). 
  
### Common administrative tasks with add-ins for Outlook

There are a couple of common scenarios that Exchange administrators manage in their organizations.
  
 **If you want to prevent end users from installing add-ins for Outlook on all Outlook clients, make the following changes to roles in the Exchange admin center**:
  
- To prevent users from installing Office Store add-ins, remove the **My Marketplace** role from them. 
    
- To prevent users from loading add-ins from sources other than the Office Store, remove the **My Custom Apps** role from them. 
    
- To prevent users from installing all add-ins, remove both of the above roles from them.
    
See [Specify the administrators and users who can install and manage add-ins for Outlook](specify-who-can-install-and-manage-add-ins.md) for more information. 
  
 **If your end users are currently able to access add-ins and you want to remove that access, use the  `Get-App` cmdlet to see which add-ins each user has installed. **
  
Next, use the  `Remove-App` cmdlet to remove any add-ins from one or more users. 
  
For more information, see [Get-App](http://technet.microsoft.com/library/85dfb69d-d637-410e-931c-36685dda84c7.aspx) and [Remove-App](http://technet.microsoft.com/library/cfd1245f-dcd2-48c1-b753-a7ebedd2803f.aspx) for Exchange 2013. For Exchange Online or Exchange 2016, go [here](https://go.microsoft.com/fwlink/p/?linkid=844721). 
  
## Allow administrators and users to install add-ins

You can specify which administrators in your organization have permission to install and manage add-ins for Outlook. You can also specify which users in your organization have permission to install and manage add-ins for their own use. For more information, see [Specify the administrators and users who can install and manage add-ins for Outlook](specify-who-can-install-and-manage-add-ins.md).
  

