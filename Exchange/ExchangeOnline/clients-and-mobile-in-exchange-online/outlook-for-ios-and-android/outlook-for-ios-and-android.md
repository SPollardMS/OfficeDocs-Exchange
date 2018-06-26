---
title: "Outlook for iOS and Android in Exchange Online"
ms.author: dmaguire
author: msdmaguire
manager: laurawi
ms.date: 4/2/2018
ms.audience: ITPro
ms.topic: overview
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: b5cf21f4-57d2-4bfc-abc6-1f0689826af8
description: "Summary: This article contains architectural and security information for administrators about Outlook for iOS and Android."
---

# Outlook for iOS and Android in Exchange Online

 **Summary**: This article contains architectural and security information for administrators about Outlook for iOS and Android.
  
The Outlook app for iOS and Android is designed to bring together email, calendar, contacts, and other files, enabling users in your organization to do more from their mobile devices. This article provides an overview of the architecture and the storage design of the app, so that Office365 administrators can deploy and maintain Outlook for iOS and Android in their organizations.
  
> [!NOTE]
> The [Outlook for iOS and Android Help Center](https://support.office.com/en-us/article/Outlook-for-iOS-and-Android-Help-Center-cd84214e-a5ac-4e95-9ea3-e07f78d0cde6) is available for users, including help for using the app on specific devices and troubleshooting information. 
  
## Outlook for iOS and Android architecture

The Outlook app for iOS and Android is built to work natively with Exchange Server and Exchange Online. All data is protected by end-to-end, TLS-secured connections between the Outlook app and Office 365.
  
Previous versions of Outlook for iOS and Android were based on code that came from Microsoft's acquisition of Acompli. While these earlier versions leveraged cloud components that ran in Amazon Web Services (AWS), that architecture has been replaced. The new architecture supports Exchange Online mailboxes natively, which means there is no mailbox data that is cached outside of Office 365. Data simply stays in its current Exchange Online mailbox, and is protected by TLS-secured connections between Outlook for iOS and Android and the mailbox. The Outlook app is now fully integrated with Microsoft services, providing the security, privacy, and compliance that organizations need.
  
Outlook for iOS and Android also uses a stateless protocol translator component that is built to run in Azure. This component enables communication between the app and Exchange Online. It routes data and translate commands, but it does not cache any user data.
  
Outlook for iOS and Android is coded with the Outlook device API, a proprietary API that syncs commands and data between the app and Exchange. Exchange Online data is accessed via the publicly available REST APIs.
  

