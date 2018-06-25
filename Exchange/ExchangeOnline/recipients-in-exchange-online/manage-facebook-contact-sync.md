---
title: "Manage Facebook contact sync in your organization"
ms.author: dmaguire
author: msdmaguire
manager: laurawi
ms.date: 12/9/2016
ms.audience: Developer
ms.topic: article
f1_keywords:
- 'ms.exch.eac.EditOwaMailboxPolicy_Facebook'
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 0f7e88eb-2b47-41ef-aedf-add22937c658
description: "Facebook contact synchronization lets people set up a connection between their Facebook account and their Office 365 account by using Outlook Web App. After they set up a Facebook connection, all their Facebook friends are listed as contacts in People in Office 365. They can then interact with their Facebook friends as they do with their other contacts. Facebook contact sync is turned on by default if the feature is available in your region."
---

# Manage Facebook contact sync in your organization

Facebook contact synchronization lets people set up a connection between their Facebook account and their Office 365 account by using Outlook Web App. After they set up a Facebook connection, all their Facebook friends are listed as contacts in People in Office 365. They can then interact with their Facebook friends as they do with their other contacts. Facebook contact sync is turned on by default if the feature is available in your region.
  
> [!TIP]
> As an administrator, you probably want to keep Facebook contact sync turned on if your organization uses Facebook for business purposes, such as networking and marketing. Turn it off if you don't want your users to download their Facebook friends as contacts in Outlook Web App. For information about how people set up Facebook contact sync, see [Add Facebook friends as contacts](https://go.microsoft.com/fwlink/?LinkId=280217). 
  
> [!NOTE]
> The features that are available to your Office 365 organization are determined by the service plan for your account. Some features aren't available to mailboxes or organizations in specific regions. 
  
## Turn Facebook contact sync on or off

You turn Facebook contact sync on or off for users in your organization by using Outlook Web App mailbox policy settings. Similar to other Outlook Web App mailbox policy settings, you can change the settings for Facebook contact sync by using the Exchange admin center (EAC) or the Exchange Management Shell (Shell). For detailed information about managing Outlook Web App mailbox policy settings, see [View or configure Outlook Web App mailbox policy properties](../clients-and-mobile-in-exchange-online/outlook-on-the-web/configure-outlook-web-app-mailbox-policy-properties.md). 
  
## For more information

The information for each Facebook friend is stored as a read-only contact record in the Facebook folder in People. The information that's synchronized between Facebook and Outlook Web App includes first name, last name, all phone numbers, all email addresses, and all street addresses. Facebook contacts are stored in the user's mailbox and are retained in accordance with the Office 365 service agreement.
  
During the Outlook Web App and Facebook connection setup, the contacts in the user's default contacts folder are uploaded to Facebook as part of a one-time synchronization with Facebook. Facebook uses this contact information as part of the "People you may know" friend suggestions on Facebook. The one-time upload of information also allows Facebook to include the information for your users' Outlook Web App contacts in Facebook applications that your users may choose to use, for example, mobile phone applications.
  
For information about how your users can set up a connection to Facebook using a desktop version of Outlook, see [Social Connector for Microsoft Outlook](https://go.microsoft.com/fwlink/?LinkId=280216).
  

