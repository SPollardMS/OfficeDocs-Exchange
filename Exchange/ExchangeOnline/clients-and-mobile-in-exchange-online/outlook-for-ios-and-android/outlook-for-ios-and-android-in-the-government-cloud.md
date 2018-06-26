---
title: "Using Outlook for iOS and Android in the Government Community Cloud"
ms.author: dmaguire
author: msdmaguire
manager: serdars
ms.date: 4/2/2018
ms.audience: ITPro
ms.topic: article
ms.service: exchange-online
localization_priority: Normal
ms.assetid: 73b693d9-39bb-4689-a1ff-4be505a5945b
description: "Summary: How organizations in the Office 365 U.S. Government Community Cloud (GCC) can enable Outlook for iOS and Android for their users."
---

# Using Outlook for iOS and Android in the Government Community Cloud

 **Summary**: How organizations in the Office 365 U.S. Government Community Cloud (GCC) can enable Outlook for iOS and Android for their users.
  
Outlook for iOS and Android is fully architected in the Microsoft Cloud and now includes a solution that routes data through Azure Government Community data centers (the Azure Government Community Cloud). This solution is FedRAMP-compliant and approved, which means the Outlook for iOS and Android architecture and underlying translation protocol service now meet the data-handling requirements for GCC tenants (these requirements are defined by NIST Special Publication 800-145). For more information, please see the Office 365 FedRAMP System Security plan located in the FedRAMP Audit Reports section of the [Microsoft Service Trust Portal](https://servicetrust.microsoft.com/). 
  
This article covers how to:
  
- Enable Outlook for iOS and Android for new Office 365 GCC customers.
    
- Unblock Outlook for iOS and Android for existing Office 365 GCC customers who were blocked from the Microsoft Azure public cloud.
    
- Migrate Office 365 GCC mobile users from the Azure public cloud to the O365 GCC compliant solution. This applies to tenants who had been previously unblocked from the Azure public cloud through signing a waiver with Microsoft Support.
    
> [!NOTE]
> Outlook for iOS and Android works with Office 365 GCC, but does not currently work in Office 365 GCC High or Office 365 DoD tenants. 
  
## Enabling Outlook for iOS and Android for Office 365 GCC customers

The instructions to enable Outlook for iOS and Android for Office 365 GCC customers depends on your existing deployment. There are:
  
1. Organizations who are currently not using Outlook for iOS and Android at all.
    
2. Organizations who are currently using Outlook for iOS and Android with the Azure public cloud, after they signed a waiver with Microsoft Support (the "Government Community Cloud Bypass Waiver").
    
### For organizations currently not using Outlook for iOS and Android

For Office 365 GCC customers who are not currently using Outlook for iOS and Android, enabling the app requires unblocking Outlook for iOS and Android in the organization, downloading the app on users' devices, and having end-users enable GCC mode on their devices.
  
 **1. Unblock Outlook for iOS and Android**
  
Remove any restrictions placed within your Exchange environment that may be blocking Outlook for iOS and Android. This means you'll need to update your Exchange Web Services application policies, your Exchange mobile device access rules, or any relevant Azure Active Directory Conditional Access policies so that the app is no longer blocked. See [Securing Outlook for iOS and Android in Exchange Online](secure-outlook-for-ios-and-android.md) for information about enabling Outlook as the only mobile messaging client in an organization. 
  
 **2. Download and install Outlook for iOS and Android**
  
End users need to install the app on their devices. How the installation happens depends on whether or not the devices are enrolled in a mobile device management (MDM) solution, such as Microsoft Intune. Users with enrolled devices can install the app through their MDM solution, like the Intune Company Portal. Users with devices that are not enrolled in an MDM solution can search for "Microsoft Outlook" in the Apple App Store or Google Play Store and download it from one of those locations.
  
> [!NOTE]
> To leverage app-based conditional access policies, the Microsoft Authenticator app must be installed on iOS devices. For Android devices, the Intune Company Portal app is leveraged. For more information, see [App-based conditional access with Intune](https://docs.microsoft.com/en-us/intune/app-based-conditional-access-intune). 
  
 **3. Have end users enable GCC mode on their devices**
  
Share the following instructions with your end-users so that they can enable GCC mode on their devices. The instructions depend on the operating system of each device.
  
For iOS devices:
  
1. Open Settings in iOS, scroll to find Outlook, and then tap to select it.
    
2. In Outlook settings, slide the toggle beside **Restrict app to GCC accounts** so that the feature is enabled. If you're asked to remove existing accounts, say Yes. Then, exit Settings. 
    
3. Open Outlook, and then add your Office 365 GCC account by following the on-screen instructions, using your Office 365 GCC email account and credentials.
    
For Android devices that have a new installation of Outlook for Android (i.e. no existing email accounts):
  
1. Open Outlook on the Android device.
    
2. On the initial screen, tap to select **Restrict app to GCC mode**.
    
3. Add your Office 365 GCC account by following the on-screen instructions, using your Office 365 GCC email account and credentials.
    
For Android devices that already have Outlook for Android installed:
  
1. Open Outlook, and then go to Settings.
    
2. Slide the toggle beside **GCC mode** so that the feature is enabled. You will get a pop-up message informing you that your accounts and settings will be removed and that you'll only be able to add GCC accounts. Tap **Apply**.
    
3. The app should automatically re-start. If it doesn't, manually close and re-start the app.
    
4. Follow the on-screen instructions to add your Office 365 GCC account, making sure GCC mode is on.
    
### For organizations currently using Outlook for iOS and Android after signing the Government Community Cloud Bypass Waiver

Prior to Outlook for iOS and Android obtaining FedRAMP approval and certification, Office 365 GCC customers may have opted to use Outlook for iOS and Android through the Government Community Cloud Bypass Waiver process, which used the public Azure cloud architecture. For organizations that did this, you must use the following steps to leverage the new, end-to-end Office 365 GCC offering for Outlook for iOS and Android that uses the Azure Government Community Cloud.
  
1. File a request with Microsoft Support to remove your tenant from the exception whitelist. Your tenant will then be blocked from the public Azure data centers.
    
    > [!NOTE]
    > Once this occurs, users will be blocked from connecting to their email using Outlook for iOS and Android, so be sure to notify your users in advance. 
  
2. Direct your end-users to follow the relevant steps in the preceding section in order to resume using Outlook for iOS and Android.
    
## Known limitations of GCC mode

Features of Outlook for iOS and Android that are not supported in GCC mode.
  
- **In-app support**: users will not be able to submit support tickets from within the app. They should contact their internal help desk. If necessary, the organization's IT department can then contact Microsoft Support directly.
    
- **Full-text notifications**: Notifications are obfuscated, which means instead of seeing the subject and first line of text in a new message, the notification will simply say "New messages."
    
- **Multiple accounts**: Only one Office 365 GCC account and one OneDrive for Business account can be added to a single device. Personal accounts cannot be added. Customers can use another device for personal accounts, or an ActiveSync client from another provider.
    

