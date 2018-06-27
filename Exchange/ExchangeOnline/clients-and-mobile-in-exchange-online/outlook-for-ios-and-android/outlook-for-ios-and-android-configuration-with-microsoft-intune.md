---
title: "Manage Outlook for iOS and Android configuration with Microsoft Intune"
ms.author: dmaguire
author: msdmaguire
manager: serdars
ms.date: 6/1/2018
ms.audience: ITPro
ms.topic: article
ms.service: exchange-online
localization_priority: Normal
ms.assetid: e8a034f6-39b8-4dea-a3bc-9421aaa75d1d
description: "Summary: How to use Microsoft Intune to customize the behavior of Outlook for iOS and Android in your Exchange organization."
---

# Manage Outlook for iOS and Android configuration with Microsoft Intune

 **Summary**: How to use Microsoft Intune to customize the behavior of Outlook for iOS and Android in your Exchange organization.
  
Outlook for iOS and Android supports app settings that allow Office 365 and Intune administrators to customize the behavior of the app with Microsoft Intune. This article describes how to create the Outlook for iOS and Android app configuration settings and how to deploy them.
  
## Create an app configuration policy for Outlook for iOS and Android

The following steps will create your app configuration policy. After the configuration is created, you can assign its settings to groups of users. 
  
1. Sign in to the Azure portal.
    
2. Select **More Services** \> **Monitoring + Management** \> **Intune**.
    
3. On the **Mobile apps** blade of the Manage list, select **App configuration policies**.
    
4. On the **App Configuration policies** blade, choose **Add**. 
    
5. On the **Add app configuration** blade, enter a **Name**, and optional **Description** for the app configuration settings. 
    
6. For **Device enrollment** type, choose **Managed apps**.
    
7. For **Associated app**, choose **Select the required apps**, and then, on the **Targeted apps** blade, choose **Outlook** for both the iOS and Android platforms. 
    
    > [!NOTE]
    > If Outlook is not listed as an available app, then you must add it by following the instructions in [Add Android store apps to Microsoft Intune](https://docs.microsoft.com/intune/store-apps-android) and [Add iOS store apps to Microsoft Intune](https://docs.microsoft.com/intune/store-apps-ios). 
  
8. Click **OK** to return to the **Add app configuration** blade. 
    
9. Choose **Configuration Settings**. On the **Configuration** blade, define the key and value pairs that will supply configurations for Outlook for iOS and Android. The key and value pairs you can define are described in the following sections. 
    
10. When you are done, choose **OK**.
    
11. On the **Add app configuration** blade, choose **Create**.
    
The newly created configuration will be displayed on the **App configuration** blade. 
  
## Assign the configuration settings that you created

You assign the settings to groups of users in Azure Active Directory. When a user has the Microsoft Outlook app installed, the app will be managed by the settings you have specified. To do this:
  
1. From the **Intune** blade, on the **Mobile apps** blade of the Manage list, select **App configuration policies**.
    
2. From the list of app configuration policies, select the one you want to assign.
    
3. On the next blade, choose **Assignments**.
    
4. On the **Assignments** blade, select the Azure AD group to which you want to assign the app configuration, and then choose **OK**.
    
> [!NOTE]
> The policy can take up to 24 hours to be applied on Android devices. 
  
## How to configure Wearables for Outlook for iOS and Android

By default, Outlook for iOS and Android supports wearable technology, allowing the user to receive message notifications and event reminders, and the ability to interact with messages and view daily calendars. Organizations that want to disable the ability to access corporate data on wearables can deploy the following key via App configuration policies.
  
|**Key**|**Value**|
|:-----|:-----|
|com.microsoft.intune.mam.areWearablesAllowed  <br/> |This value specifies if Outlook data can be synchronized to a wearable device. Setting the value to False disables wearable synchronization.  <br/> **Accepted values**: True, False  <br/> **Default if not specified**: True  <br/> **Example**: False  <br/> |
   
## How to configure the Contact Field Sync to native Contacts for Outlook for iOS and Android
<a name="contacts"> </a>

The settings in the following table allow you to control the contact fields that will sync between Outlook on iOS and Android and the native Contacts applications.
  
> [!NOTE]
> Outlook for Android supports bi-directional contact synchronization. If a user edits a field in the native contacts app that is restricted (such as the **Notes** field), then that data will not synchronize back into Outlook for Android. 
  
|**Key**|**Values**|
|:-----|:-----|
|com.microsoft.outlook.ContactSync.AddressAllowed  <br/> |This value specifies if the contact's address should be synchronized to native contacts.  <br/> **Accepted values**: True, False  <br/> **Default if not specified**: True  <br/> **Example**: True  <br/> |
|com.microsoft.outlook.ContactSync.BirthdayAllowed  <br/> |This value specifies if the contact's birthday should be synchronized to native contacts.  <br/> **Accepted values**: True, False  <br/> **Default if not specified**: True  <br/> **Example**: True  <br/> |
|com.microsoft.outlook.ContactSync.CompanyAllowed  <br/> |This value specifies if the contact's company name should be synchronized to native contacts.  <br/> **Accepted values**: True, False  <br/> **Default if not specified**: True  <br/> **Example**: True  <br/> |
|com.microsoft.outlook.ContactSync.DepartmentAllowed  <br/> |This value specifies if the contact's department should be synchronized to native contacts.  <br/> **Accepted values**: True, False  <br/> **Default if not specified**: True  <br/> **Example**: True  <br/> |
|com.microsoft.outlook.ContactSync.EmailAllowed  <br/> |This value specifies if the contact's email address should be synchronized to native contacts.  <br/> **Accepted values**: True, False  <br/> **Default if not specified**: True  <br/> **Example**: True  <br/> |
|com.microsoft.outlook.ContactSync.InstantMessageAllowed  <br/> |This value specifies if the contact's instant messaging address should be synchronized to native contacts.  <br/> **Accepted values**: True, False  <br/> **Default if not specified**: True  <br/> **Example**: True  <br/> |
|com.microsoft.outlook.ContactSync.JobTitleAllowed  <br/> |This value specifies if the contact's job title should be synchronized to native contacts.  <br/> **Accepted values**: True, False  <br/> **Default if not specified**: True  <br/> **Example**: True  <br/> |
|com.microsoft.outlook.ContactSync.NicknameAllowed  <br/> |This value specifies if the contact's nickname should be synchronized to native contacts.  <br/> **Accepted values**: True, False  <br/> **Default if not specified**: True  <br/> **Example**: True  <br/> |
|com.microsoft.outlook.ContactSync.NotesAllowed  <br/> |This value specifies if the contact's notes should be synchronized to native contacts.  <br/> **Accepted values**: True, False  <br/> **Default if not specified**: True  <br/> **Example**: True  <br/> |
|com.microsoft.outlook.ContactSync.PhoneHomeAllowed  <br/> |This value specifies if the contact's home phone number should be synchronized to native contacts.  <br/> **Accepted values**: True, False  <br/> **Default if not specified**: True  <br/> **Example**: True  <br/> |
|com.microsoft.outlook.ContactSync.PhoneHomeFaxAllowe  <br/> |This value specifies if the contact's home fax number should be synchronized to native contacts.  <br/> **Accepted values**: True, False  <br/> **Default if not specified**: True  <br/> **Example**: True  <br/> |
|com.microsoft.outlook.ContactSync.PhoneMobileAllowed  <br/> |This value specifies if the contact's mobile phone number should be synchronized to native contacts.  <br/> **Accepted values**: True, False  <br/> **Default if not specified**: True  <br/> **Example**: True  <br/> |
|com.microsoft.outlook.ContactSync.PhoneOtherAllowed  <br/> |This value specifies if the contact's other phone number should be synchronized to native contacts.  <br/> **Accepted values**: True, False  <br/> **Default if not specified**: True  <br/> **Example**: True  <br/> |
|com.microsoft.outlook.ContactSync.PhonePagerAllowed  <br/> |This value specifies if the contact's pager phone number should be synchronized to native contacts.  <br/> **Accepted values**: True, False  <br/> **Default if not specified**: True  <br/> **Example**: True  <br/> |
|com.microsoft.outlook.ContactSync.PhoneWorkAllowed  <br/> |This value specifies if the work phone number should be synchronized to native contacts.  <br/> **Accepted values**: True, False  <br/> **Default if not specified**: True  <br/> **Example**: True  <br/> |
|com.microsoft.outlook.ContactSync.PhoneWorkFaxAllowed  <br/> |This value specifies if the contact's work fax number should be synchronized to native contacts.  <br/> **Accepted values**: True, False  <br/> **Default if not specified**: True  <br/> **Example**: True  <br/> |
|com.microsoft.outlook.ContactSync.PrefixAllowed  <br/> |This value specifies if the contact's name prefix should be synchronized to native contacts.  <br/> **Accepted values**: True, False  <br/> **Default if not specified**: True  <br/> **Example**: True  <br/> |
|com.microsoft.outlook.ContactSync.SuffixAllowed  <br/> |This value specifies if the contact's name suffix should be synchronized to native contacts.  <br/> **Accepted values**: True, False  <br/> **Default if not specified**: True  <br/> **Example**: True  <br/> |
   

