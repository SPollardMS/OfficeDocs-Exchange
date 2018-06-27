---
title: "Address books in Exchange Online"
ms.author: kwekua
author: kwekua
manager: scotv
ms.date: 12/9/2016
ms.audience: ITPro
ms.topic: article
ms.service: exchange-online
localization_priority: Normal
ms.assetid: 7c90d413-f978-4af5-8bc5-6b86d897edc3
description: "Exchange Online can deliver or route messages to any recipient that has an email address. People, resources (such as a business device or a conference room), and groups can all have email addresses. Address books help you find the email address that you need and can be organized in multiple ways to suit your business. This topic helps Office 365 administrators who manage email address books for an organization. See Key terminology for descriptions of address book features."
---

# Address books in Exchange Online

Exchange Online can deliver or route messages to any recipient that has an email address. People, resources (such as a business device or a conference room), and groups can all have email addresses. Address books help you find the email address that you need and can be organized in multiple ways to suit your business. This topic helps Office 365 administrators who manage email address books for an organization. See [Key terminology](address-books.md#terms) for descriptions of address book features. 
  
For help with everyday email tasks, such as organizing your contacts in Outlook, check the [Office 365 Learning Center](https://go.microsoft.com/fwlink/?LinkId=615390). You can find help including:
  
- [Add an email contact](https://go.microsoft.com/fwlink/?LinkId=615396)
    
- [Import your contacts](https://go.microsoft.com/fwlink/?LinkId=615393)
    
- [Create a contact group](https://go.microsoft.com/fwlink/?LinkId=615370)
    
- [Send an email message to a contact group](https://go.microsoft.com/fwlink/?LinkId=615391)
    
## Key terminology
<a name="terms"> </a>

The following terms define the core components associated with email addresses and address books in Exchange Online.
  
 **address book policies**
  
> Address book policies (ABPs) allow you to segment users into specific groups to provide customized views of your organization's global address list (GAL). When creating an ABP, you assign a GAL, an offline address book (OAB), a room list, and one or more address lists to the policy. You can then assign the ABP to mailbox users, providing them with access to a customized GAL in Outlook and Outlook Web App. The goal is to provide a simpler mechanism to accomplish GAL segmentation for on-premises organizations that require multiple GALs.
    
 **address lists**
  
> An address list is a subset of a GAL. Each address list is a collection of one or more types of mail-enabled recipients (for example, users, contacts, groups, public folders, conferencing, and other resources). You can use address lists to organize recipients and resources, making it easier for users to find the recipients and resources they need. Address lists are updated dynamically. Therefore, when new recipients are added to your organization, they're automatically added to the appropriate address lists.
    
 **offline address books**
  
> An offline address book (OAB) is a copy of a collection of address lists that has been downloaded so that a Microsoft Outlook user can access the information it contains while disconnected from the server.
    
 **hierarchical address books**
  
> The hierarchical address book (HAB) enables end users to look for recipients in their address book using an organizational hierarchy, such as seniority or management structure. Normally, users are limited to the default GAL and its associated recipient properties and the structure of the GAL often doesn't accurately reflect the management or seniority relationships for recipients in your organization. Being able to customize an HAB that maps to your organization's unique business structure provides your users with an efficient method for locating internal recipients.
    

