---
title: "Collaboration in Exchange Online"
ms.author: dmaguire
author: msdmaguire
manager: laurawi
ms.date: 6/24/2018
ms.audience: ITPro
ms.topic: article
ms.service: exchange-online
localization_priority: Normal
ms.assetid: 7d433daa-c68f-4441-b2f5-1280991185c2
description: "Office 365 and Exchange Online provides several features that can help your end users easily collaborate in email."
---

# Collaboration in Exchange Online

Office 365 and Exchange Online provides several features that can help your end users easily collaborate in email.
  
Each of these features, described in the following sections, has a different user experience and feature set and should be used based on what your users need to accomplish and what your organization can provide. For example, site mailboxes provide great documentation collaboration features. However, site mailboxes rely on SharePoint, so if you aren't planning on subscribing to SharePoint, you can use public folders to share documents. 
  
This topic compares these collaboration features to help you decide which features to offer your users.
  
## Site mailboxes
<a name="SiteMbx"> </a>

A site mailbox is functionally comprised of a SharePoint site membership (owners and members), shared storage through an Exchange mailbox for email messages, and a SharePoint site to store and share. Essentially, site mailboxes bring Exchange email and SharePoint documents together. For users, a site mailbox serves as a central filing cabinet for the project, providing a place to file project email and documents that can be accessed and edited only by site members. In addition, site mailboxes have a specified lifecycle and are optimized to be used for projects that have set start and end dates. To fully implement site mailboxes, end users must use Outlook 2013.
  
To learn more, see [Prepare for using Site Mailboxes in Office 365](https://go.microsoft.com/fwlink/?LinkId=286170).
  
## Public folders
<a name="PFs"> </a>

Public folders are designed for shared access and provide an easy and effective way to collect, organize, and share information with other people in your workgroup or organization. 
  
Public folders organize content in a deep hierarchy that's easy to browse. Users discover interesting and relevant content by browsing through branches of the hierarchy that are relevant to them. Users always see the full hierarchy in their Outlook folder view. Public folders are a great technology for distribution group archiving. A public folder can be mail-enabled and added as a member of the distribution group. Email sent to the distribution group is automatically added to the public folder for later reference. Public folders also provide simple document sharing and don't require SharePoint to be installed in your organization. Finally, end users can use public folders with the following supported Outlook clients: Outlook 2007, Outlook 2010, Outlook 2013, and Outlook Web App, but with some limitations.
  
To learn more, see [Public folders in Office 365 and Exchange Online](public-folders/public-folders.md).
  
## Shared mailboxes
<a name="Shared"> </a>

A shared mailbox is a mailbox that multiple designated users can access to read and send email messages and to share a common calendar. Shared mailboxes can provide a generic email address (such as info@contoso.com or sales@contoso.com) that customers can use to inquire about your company. If the shared mailbox has the Send As permission assigned when a delegated user responds to the email message, it can appear as though the mailbox (for example, sales@contoso.com) is responding, not the actual user. 
  
To learn more, see [Shared Mailboxes](http://technet.microsoft.com/library/1d71c01b-e261-408e-a633-1d1c9d00032a.aspx).
  
## Groups
<a name="Groups"> </a>

Groups (also called distribution groups) are a collection of two or more recipients that appears in the shared address book. When an email message is sent to a group, it's received by all members of the group. Distribution groups can be organized by a particular discussion subject (such as "Dog Lovers") or by users who share a common work structure that requires them to communicate frequently.
  
To learn more, see [Recipients in Exchange Online](../recipients-in-exchange-online/recipients-in-exchange-online.md).
  
## Which one to use?
<a name="Groups"> </a>

The following table gives you a quick glance at each of the collaboration features to help you decide which one to use.
  
||**Site mailboxes**|**Public folders**|**Shared mailboxes**|**Groups**|
|:-----|:-----|:-----|:-----|:-----|
|**Type of group** <br/> |Users who work together as a team on a specific project with definitive start and end dates.  <br/> |With the proper permissions, everyone in your organization can access and search public folders. Public folders are ideal for maintaining history or distribution group conversations.  <br/> |Delegates working on behalf of a virtual identity, and they can respond to email as that shared mailbox identity. Example: support@tailspintoys.com  <br/> |Users who need to send email to a group of recipients with a common interest or characteristic.  <br/> |
|**Ideal group size** <br/> |Small  <br/> |Large  <br/> |Small  <br/> |Large  <br/> |
|**Access** <br/> |Site mailbox owners and members.  <br/> |Accessible by anyone in your organization.  <br/> |Users can be granted Full Access and/or Send As permissions. If granted Full Access permissions, users must also add the shared mailbox to their Outlook profile to access the shared mailbox.  <br/> |For distribution groups, members must be manually added. For dynamic distribution groups, members are added based on filtering criteria.  <br/> |
|**Shared calendar?** <br/> |No  <br/> |Yes  <br/> |Yes  <br/> |No  <br/> |
|**Email arrives in user's personal Inbox?** <br/> |No. Email arrives in the site mailbox.  <br/> |No. Email arrives in the public folder.  <br/> |No. Email arrives in the Inbox of the shared mailbox.  <br/> |Yes. Email arrives in the Inbox of a distribution group member.  <br/> |
|**Supported clients** <br/> | Outlook 2013  <br/>  SharePoint Online  <br/> | Outlook 2013  <br/>  Outlook Web App  <br/>  Outlook 2010  <br/>  Outlook 2007  <br/> | Outlook 2013  <br/>  Outlook Web App  <br/>  Outlook 2010  <br/>  Outlook 2007  <br/> | Outlook 2013  <br/>  Outlook Web App  <br/>  Outlook 2010  <br/>  Outlook 2007  <br/> |
   

