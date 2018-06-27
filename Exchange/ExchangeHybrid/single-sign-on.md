---
title: "Single sign-on with hybrid deployments"
ms.author: dstrome
author: dstrome
manager: laurawi
ms.date: 6/25/2018
ms.audience: ITPro
ms.topic: article
ms.prod: exchange-server-itpro
localization_priority: Normal
ms.collection:
- Hybrid
- Ent_O365_Hybrid
ms.assetid: 050606f9-718d-4a1f-b7a6-50b08c6e9e07
description: "Single sign-on enables users to access both the on-premises and Office 365 organizations with a single user name and password. It provides users with a familiar sign-on experience and can allow administrators to easily control account policies for Exchange Online organization mailboxes by using on-premises Active Directory management tools. While you don't have to configure a hybrid deployment with single sign-on enabled, we strongly recommend that you do. Without single sign-on, users will need to remember two different sets of credentials, one for your on-premises organization, and one for Office 365. Here are a few other advantages to single sign-on:"
---

# Single sign-on with hybrid deployments

 Single sign-on enables users to access both the on-premises and Office 365 organizations with a single user name and password. It provides users with a familiar sign-on experience and can allow administrators to easily control account policies for Exchange Online organization mailboxes by using on-premises Active Directory management tools. While you don't have to configure a hybrid deployment with single sign-on enabled, we strongly recommend that you do. Without single sign-on, users will need to remember two different sets of credentials, one for your on-premises organization, and one for Office 365. Here are a few other advantages to single sign-on: 
  
- **Exchange Online Archiving** When single sign-on is deployed, on-premises Outlook users are prompted for their credentials when accessing archived content in the Exchange Online organization for the first time. However, users can then temporarily avoid future credential prompting by choosing "save password" and then will only be prompted for credentials again when their on-premises account password is changed. If single sign-on isn't deployed in Exchange organizations and Exchange Online Archiving is enabled, the on-premises user principal name (UPN) must match their Exchange Online account and users will always be prompted for their on-premises credentials when accessing their archive. 
    
- **Policy control** You can control account policies through Active Directory, which gives you the ability to manage password policies, workstation restrictions, lock-out controls, and more, without having to perform additional tasks in your Office 365 organization. 
    
- **Reduced support calls** Forgotten passwords are a common source of support calls in all companies. If users have fewer passwords to remember, they are less likely to forget them. 
    
You have a couple of options when deploying single sign-on: password synchronization and Active Directory Federation Services (AD FS). Both options are provided by Azure Active Directory Connect. We strongly recommend using the password synchronization method unless you have a specific need that requires AD FS. Password synchronization provides many of the same benefits of AD FS without the complexity of its deployment. The following table provides some common advantages and disadvantages for each option.
  
> [!NOTE]
> By default, if you deploy AD FS and your on-premises AD FS servers aren't reachable from the Internet for any reason, Office 365 will fall back to password synchronization to authenticate users. This allows users with Office 365 mailboxes to continue working uninterrupted even if your on-premises servers aren't available. 
  
To learn more about each option, see [Azure AD Connect User Sign-on options](http://go.microsoft.com/fwlink/p/?LinkId=723514).
  
|
|
|**Single sign-on method**|**Advantages**|**Disadvantages**|
|:-----|:-----|:-----|
|Password synchronization (recommended)  <br/> | Significantly less complex than AD FS  <br/>  Users can log in to Office 365 even if your on-premises Active Directory is unavailable.  <br/>  Fewer additional servers are required to deploy password synchronization.  <br/>  No third-party certificates are required.  <br/>  Doesn't require external access to your on-premises Active Directory via AD FS.  <br/>  Deployment can often be completed in just a few hours.  <br/> | Disabling a user account in your on-premises Active Directory doesn't disable it in Office 365. You need to manually disable the account in the Office 365 Admin portal.  <br/>  Requires on-premises Active Directory. Other directory services aren't supported.  <br/> |
|AD FS  <br/> | Password changes are immediate.  <br/>  Disabling a user in your on-premises Active Directory disables both their on-premises network access and their Office 365 account.  <br/>  Supports directory services other than Active Directory.  <br/>  Supports very large and diverse deployments.  <br/>  Support for two-factor authentication.  <br/> | Requires more servers, at least one of which needs to reside in your perimeter network.  <br/>  Requires a public IP address and TCP port 443 to be opened on your firewall.  <br/>  Connectivity with your on-premises Active Directory is required to detect changes to account passwords and with an account has recently been enabled or disabled.  <br/> |
   

