---
title: "Account setup with modern authentication in Exchange Online"
ms.author: dmaguire
author: msdmaguire
manager: serdars
ms.date: 1/29/2018
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 1efe7737-b573-4f36-a0f2-27714d2ebdb0
description: "Summary: How users with modern authentication-enabled accounts can quickly set up their Outlook for iOS and Android accounts in Exchange Online."
---

# Account setup with modern authentication in Exchange Online

 **Summary**: How users with modern authentication-enabled accounts can quickly set up their Outlook for iOS and Android accounts in Exchange Online.
  
There are two ways that users in your Exchange Online organization can set up their own Outlook for iOS and Android accounts: AutoDetect and single sign-on. Both methods leverage modern authentication.
  
## AutoDetect

Outlook for iOS and Android offers a solution called AutoDetect that helps end-users quickly setup their accounts. AutoDetect will first determine which type of account a user has, based on the SMTP domain. Account types that are covered by this service include Office 365, Outlook.com, Google, Yahoo, and iCloud. Next, AutoDetect will make the appropriate configurations to the app on the user's device based on that account type. This saves time for users and eliminates the need for manual input of configuration settings like hostname and port number.
  
For modern authentication, which is used by all Office 365 accounts and [on-premises accounts that are part of a hybrid configuration](https://blogs.technet.microsoft.com/exchange/2017/09/27/tap-outlook-mobile-support-for-exchange-on-premises-with-microsoft-enterprise-mobility-security/), AutoDetect queries Exchange Online for a user's account information and then configures Outlook for iOS and Android on the user's device so that the app can connect to Exchange Online. During this process, the only information required from the user is their SMTP address and credentials.
  
The following images show an example of account configuration via AutoDetect:
  
![Outlook for iOS and Android onboarding](../../media/67c22e0d-ba01-4923-bdb9-375f26ec90fb.png)
  
In the event that AutoDetect fails for a user, the following images show an alternative account configuration path using manual configuration:
  
![Manaul account setup for Outlook for iOS and Android](../../media/fdb9b8e8-499d-4702-b362-4fe9a2e9c978.png)
  
## Single sign-on

For devices enrolled in Intune Company Portal, Outlook for iOS and Android supports single sign-on via authentication token re-use. If a user is already signed in to another Office 365 app on their device, like Word or Company Portal, Outlook for iOS for Android will detect that token and use it for its own authentication. When such a token is detected, users already enrolled in Outlook for iOS and Android will see their account available as "Found" under **Accounts** on the **Settings** menu. New users will see their account in the initial account setup screen. 
  
The following images show an example of account configuration via single sign-on for a first-time user:
  
![Single sign-on in Outlook for iOS and Android](../../media/d11691ca-49e9-4282-80f0-c73547ccc98e.png)
  
If a user already has Outlook for iOS and Android, such as for a personal account, but an Office 365 account is detected because they recently enrolled, the single-sign on path will look as follows:
  
![Alternative single-sign on path for Outlook for iOS and Android](../../media/e24efc89-10e1-4a11-b80c-bbfc08033334.png)
  

