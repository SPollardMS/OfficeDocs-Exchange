---
title: "Exchange admin center in Exchange Online"
ms.author: kwekua
author: kwekua
manager: scotv
ms.date: 6/23/2018
ms.audience: ITPro
ms.topic: overview
ms.service: exchange-online
localization_priority: Normal
ms.assetid: ace44f6b-4084-4f9c-89b3-e0317962472b

description: "You use the Exchange admin center to manage email settings for your organization."
---

# Exchange admin center in Exchange Online

You use the Exchange admin center to manage email settings for your organization.
  
## Get to the Exchange admin center

You must have [Office 365 admin permissions](https://go.microsoft.com/fwlink/p/?LinkID=255444) to access the Exchange admin center. 
  
1. [Sign in](https://go.microsoft.com/fwlink/p/?LinkID=529144) to Office 365 using your work or school account, and then choose the **Admin** tile. 
    
2. In the Office 365 admin center, choose **Admin centers** \> **Exchange**.
    
    ![Get to the Exchange admin center](media/ae439954-b836-47fa-9d02-3709b93cdb10.jpg)
  
## Exchange admin center features

Here's what the Exchange admin center looks like.
  
![Common User Interface Elements of the EAC](media/ITPro_EXO_EAC_EACwCallouts.png)
  
### Feature pane

Here are the features you'll find in the left-hand navigation.
  
|**Area**|**What you do here**|
|:-----|:-----|
|**Dashboard** <br/> |An overview of the admin center.  <br/> |
|**Recipients** <br/> |View and manage your mailboxes, groups, resource mailboxes, contacts, shared mailboxes, and mailbox migrations.  <br/> |
|**Permissions** <br/> |Manage administrator roles, user roles, and Outlook Web App policies.  <br/> |
|**Compliance management** <br/> |Manage In-Place eDiscovery &amp; Hold, auditing, data loss prevention (DLP), retention policies, retention tags, and journal rules.  <br/> |
|**Organization** <br/> |Manage organization sharing and apps for Outlook  <br/> |
|**Protection** <br/> |Manage malware filters, connection filters, content filters, outbound spam, and quarantine for your organization.  <br/> |
|**Mail flow** <br/> |Manage rules, message tracing, accepted domains, remote domains, and connectors.  <br/> |
|**Mobile** <br/> |Manage the mobile devices that you allow to connect to your organization. You can manage mobile device access and mobile device mailbox policies.  <br/> |
|**Public folders** <br/> |Manage public folders and public folder mailboxes.  <br/> |
|**Unified messaging** <br/> |Manage Unified Messaging (UM) dial plans and UM IP gateways.  <br/> |
   
### Tabs

The tabs are your second level of navigation. Each of the feature areas contains various tabs, each representing a complete feature.
  
### Toolbar

When you click most tabs, you'll see a toolbar. The toolbar has icons that perform a specific action. The following table describes the most common icons and their actions. To display the action associated with an icon, simply hover over the icon.
  
|**Icon**|**Name**|**Action**|
|:-----|:-----|:-----|
|![Add Icon](media/ITPro_EAC_AddIcon.gif)           <br/> |Add, New  <br/> |Create a new object. Some of these icons have an associated down arrow you can click to show additional objects you can create.  <br/> For example, in **Recipients** \> **Groups**, clicking the down arrow displays **Distribution group**, **Security group**, and **Dynamic distribution group** as additional options.  <br/> |
|![Edit icon](media/ITPro_EAC_EditIcon.gif)           <br/> |Edit  <br/> |Edit an object.  <br/> |
|![Delete icon](media/ITPro_EAC_DeleteIcon.gif)           <br/> |Delete  <br/> |Delete an object. Some delete icons have a down arrow you can click to show additional options.  <br/> |
|![Search icon](media/ITPro_EAC_.gif)           <br/> |Search  <br/> |Open a search box in which you can type the search phrase for an object you want to find.  <br/> |
|![Icon: Upgrade distribution group to Office 365 group](media/f48d2ecd-36e1-4ec1-a4eb-7c97a23d81dc.gif)           <br/> ||Upgrade a distribution group to an Office 365 group. This icon can be used only for a distribution group.  <br/> |
|![Refresh Icon](media/ITPro_EAC_RefreshIcon.gif)           <br/> |Refresh  <br/> |Refresh the list view.  <br/> |
|![More Options Icon](media/ITPro_EAC_MoreOptionsIcon.gif)           <br/> |More options  <br/> |View more actions you can perform for that tab's objects.  <br/> For example, in **Recipients** \> **Mailboxes** clicking this icon shows the following options: **Add/Remove columns**, **Deleted mailboxes**, **Export data to a CSV file**, and **Advanced search**.  <br/> |
|![Up Arrow Icon](media/ITPro_EAC_UpArrowIcon.gif)![Down Arrow Icon](media/ITPro_EAC_DownArrowIcon.gif)           <br/> |Up arrow and down arrow  <br/> |Move an object's priority up or down.  <br/>  For example, in **Mail flow** \> **Rules** click the up arrow to raise the priority of a rule. You can also use these arrows to navigate the public folder hierarchy.  <br/> |
|![Copy Icon](media/ITPro_EAC_CopyIcon.gif)           <br/> |Copy  <br/> |Copy an object so you can make changes to it without changing the original object.  <br/> For example, in **Permissions** \> **Admin roles**, select a role from the list view, and then click this icon to create a new role group based on an existing one.  <br/> |
|![Remove icon](media/ITPro_EAC_RemoveIcon.gif)           <br/> |Remove  <br/> |Remove an item from a list.  <br/> For example, in the **Public Folder Permissions** dialog box, you can remove users from the list of users allowed to access the public folder by selecting the user and clicking this icon.  <br/> |
   
### List view

When you select a tab, in most cases you'll see a list view. The list view in Exchange admin center is designed to remove limitations that existed in Exchange Control Panel.
  
In Exchange Online, the viewable limit from within the Exchange admin center list view is approximately 10,000 objects. In addition, paging is included so you can page to the results. In the **Recipients** list view, you can also configure page size and export the data to a CSV file. 
  
### Details pane

When you select an item from the list view, information about that object is displayed in the details pane.
  
 **To bulk edit several items**: press the CTRL key, select the objects you want to bulk edit, and use the options in the details pane. 
  
### Centers, Me tile, and Help

The Centers tile allows you to change from one admin center to another. The Me tile allows you to sign out of the EAC and sign in as a different user. From the Help ![Help Icon](media/ITPro_EAC_HelpIcon.gif) drop-down menu, you can perform the following actions: 
  
- **Help** Click ![Help Icon](media/ITPro_EAC_HelpIcon.gif) to view the online help content. 
    
- **Disable Help bubble** The Help bubble displays contextual help for fields when you create or edit and object. You can turn off the Help bubble help or turn it on if it has been disabled. 
    
## Supported browsers
<a name="SB"> </a>

See the following articles:
  
- [Office 365 System Requirements](https://go.microsoft.com/fwlink/p/?LinkID=402699): lists supported browsers for Office 365 and the Exchange admin center.
    
- [Supported Browsers for Outlook Web App](https://go.microsoft.com/fwlink/p/?LinkId=402700).
    
## Related articles
<a name="SB"> </a>

Are you using Exchange Server 2013? See [Exchange admin center in Exchange 2013](http://technet.microsoft.com/library/a9aea11a-6ba3-4f4a-a76e-79072e7cfc7d.aspx).
  
Are you using Exchange Online Protection? See [Exchange admin center in Exchange Online Protection](http://technet.microsoft.com/library/97921f0e-832f-40c7-b56d-414faede5191.aspx).
  

