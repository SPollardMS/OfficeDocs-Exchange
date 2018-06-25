---
title: "Securing Outlook for iOS and Android in Exchange Online"
ms.author: dmaguire
author: msdmaguire
manager: laurawi
ms.date: 4/19/2018
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: dd886cdc-bfc1-42a4-8e67-66ae1d08af0f
description: "Summary: How to enable Outlook for iOS and Android in your Exchange Online environment in a secure manner."
---

# Securing Outlook for iOS and Android in Exchange Online

 **Summary**: How to enable Outlook for iOS and Android in your Exchange Online environment in a secure manner.
  
Outlook for iOS and Android provides users the fast, intuitive email and calendar experience that users expect from a modern mobile app, while being the only app to provide support for the best features of Office 365.
  
Protecting company or organizational data on users' mobile devices is extremely important. Begin by reviewing [Setting up Outlook for iOS and Android](secure-outlook-for-ios-and-android.md#settingup), to ensure your users have all the required apps installed. After that, choose one of the following options to secure your devices and your organization's data:
  
1. **Recommended**: If your organization has an Enterprise Mobility + Security subscription, or has separately obtained licensing for Microsoft Intune and Azure Active Directory Premium, follow the steps in [Leveraging Enterprise Mobility + Security suite to protect corporate data with Outlook for iOS and Android](secure-outlook-for-ios-and-android.md#leverageenterprise) to protect corporate data with Outlook for iOS and Android. 
    
2. If your organization doesn't have an Enterprise Mobility + Security subscription or licensing for Microsoft Intune and Azure Active Directory Premium, follow the steps in [Leveraging Mobile Device Management for Office 365](secure-outlook-for-ios-and-android.md#leveragemdm), and use the Mobile Device Management (MDM) for Office 365 capabilities that are included in your Office 365 subscription.
    
3. Follow the steps in [Leveraging Exchange Online mobile device policies](secure-outlook-for-ios-and-android.md#leverageexo) to implement basic Exchange mobile device mailbox and device access policies. 
    
If, on the other hand, you don't want to use Outlook for iOS and Android in your organization, see [Blocking Outlook for iOS and Android](secure-outlook-for-ios-and-android.md#blocking).
  
> [!NOTE]
> See [Exchange Web Services (EWS) application policies](secure-outlook-for-ios-and-android.md#additionalmethods) later in this article if you'd rather implement an EWS application policy to manage mobile device access in your organization. 
  
## Setting up Outlook for iOS and Android
<a name="settingup"> </a>

For devices enrolled in a mobile device management (MDM) solution, users will utilize the MDM solution, like the Intune Company Portal, to install the required apps: Outlook for iOS and Android and Microsoft Authenticator.
  
For devices that are not enrolled in an MDM solution, users need to install:
  
- Outlook for iOS and Android via the Apple App Store or Google Play Store
    
- Microsoft Authenticator app via the Apple App Store or Google Play Store
    
- Intune Company Portal app via Apple App Store or Google Play Store
    
Once the app is installed, users can follow these steps to add their corporate email account and configure basic app settings:
  
- [Set up email account in Outlook for iOS mobile app](https://support.office.com/article/set-up-email-in-outlook-for-ios-mobile-app-b2de2161-cc1d-49ef-9ef9-81acd1c8e234)
    
- [Set up email in the Outlook for Android app](https://support.office.com/article/set-up-email-in-the-outlook-for-android-app-886db551-8dfa-4fd5-b835-f8e532091872)
    
- [Optimizing the Outlook mobile app for your iOS or Android phone](https://support.office.com/article/optimize-the-outlook-mobile-app-for-your-ios-or-android-phone-de075b19-b73c-4d8a-841b-459982c7e890)
    
> [!IMPORTANT]
> To leverage app-based conditional access policies, the Microsoft Authenticator app must be installed on iOS devices. For Android devices, the Intune Company Portal app is leveraged. For more information, see [App-based Conditional Access with Intune](https://docs.microsoft.com/intune/app-based-conditional-access-intune). 
  
## Leveraging Enterprise Mobility + Security suite to protect corporate data with Outlook for iOS and Android
<a name="leverageenterprise"> </a>

The richest and broadest protection capabilities for Office 365 data are available when you subscribe to the Enterprise Mobility + Security suite, which includes Microsoft Intune and Azure Active Directory Premium features, such as conditional access. At a minimum, you will want to deploy a conditional access policy that only allows connectivity to Outlook for iOS and Android from mobile devices and an Intune app protection policy that ensures the corporate data is protected.
  
> [!NOTE]
> While the Enterprise Mobility + Security suite subscription includes both Microsoft Intune and Azure Active Directory Premium, customers can purchase Microsoft Intune licenses and Azure Active Directory Premium licenses separately. All users must be licensed in order to leverage the conditional access and Intune app protection policies that are discussed in this article. 
  
### Block all email apps except Outlook for iOS and Android using conditional access
<a name="blockallemail"> </a>

When an organization decides to standardize how users access Exchange data, using Outlook for iOS and Android as the only email app for end users, they can configure a conditional access policy that blocks other mobile access methods. To do this, you will need two conditional access policies, with each policy targeting all potential users. Details on creating these polices can be found in [Azure Active Directory app-based conditional access](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-mam#exchange-online-policy).
  
1. The first policy allows Outlook for iOS and Android, and it blocks OAuth capable Exchange ActiveSync clients from connecting to Exchange Online. See "Step 1 - Configure an Azure AD conditional access policy for Exchange Online."
    
2. The second policy prevents Exchange ActiveSync clients leveraging basic authentication from connecting to Exchange Online. See "Step 2 - Configure an Azure AD conditional access policy for Exchange Online with Active Sync (EAS)."
    
The policies leverage the grant control [Require approved client app](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-technical-reference), which ensures only Microsoft apps that have integrated the Intune SDK are granted access.
  
> [!NOTE]
> After the conditional access policies are enabled, it may take up to 6 hours for any previously connected mobile device to become blocked. > Mobile device access rules (allow, block, or quarantine) in Exchange Online are skipped when access is managed by a conditional access policy that includes either [Require device to be marked as compliant](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-policy-connected-applications) or [Require approved client app](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-technical-reference). > To leverage app-based conditional access policies, the Microsoft Authenticator app must be installed on iOS devices. For Android devices, the Intune Company Portal app is leveraged. For more information, see [App-based Conditional Access with Intune](https://docs.microsoft.com/intune/app-based-conditional-access-intune). 
  
### Protect corporate data in Outlook for iOS and Android using Intune app protection policies
<a name="blockallemail"> </a>

Regardless of whether the device is enrolled in an MDM solution, an Intune app protection policy needs to be created for both iOS and Android apps, using the steps in [How to create and assign app protection policies](https://docs.microsoft.com/intune/app-protection-policies). These policies, at a minimum, must meet the following conditions:
  
1. They include all Microsoft mobile applications, such as Word, Excel, or PowerPoint, as this will ensure that users can access and manipulate corporate data within any Microsoft app in a secure fashion.
    
2. They mimic the security features that Exchange provides for mobile devices, including:
    
  - Requiring a PIN for access (which includes Select Type, PIN length, Allow Simple PIN, Allow fingerprint)
    
  - Encrypting app data
    
  - Blocking managed apps from running on "jailbroken" and rooted devices
    
3. They are assigned to all users. This ensures that all users are protected, regardless of whether they use Outlook for iOS and Android.
    
In addition to the above minimum policy requirements, you should consider deploying advanced protection policy settings like **Restrict cut, copy and paste with other apps** to further prevent corporate data leakage. For more information on the available settings, see [Android app protection policy settings in Microsoft Intune](https://docs.microsoft.com/intune/app-protection-policy-settings-android) and [iOS app protection policy settings](https://docs.microsoft.com/intune/app-protection-policy-settings-ios).
  
> [!IMPORTANT]
> To apply Intune app protection policies against apps on Android devices that are not enrolled in Intune, the user must also install the Intune Company Portal. For more information, see [What to expect when your Android app is managed by app protection policies](https://docs.microsoft.com/en-us/intune/app-protection-enabled-apps-android). 
  
## Leveraging Mobile Device Management for Office 365
<a name="leveragemdm"> </a>

If you don't plan to leverage the Enterprise Mobility + Security suite, you can use Mobile Device Management (MDM) for Office 365. This solution requires that mobile devices be enrolled. When a user attempts to access Exchange Online with a device that is not enrolled, the user is blocked from accessing the resource until they enroll the device.
  
Because this is a device management solution, there is no native capability to control which apps can be used even after a device is enrolled. If you want to limit access to Outlook for iOS and Android, you will need to obtain Azure Active Directory Premium licenses and leverage the conditional access policies discussed in [Block all email apps except Outlook for iOS and Android using conditional access](secure-outlook-for-ios-and-android.md#blockallemail).
  
An Office 365 global admin must complete the following steps to activate and set up MDM for Office 365. See [Set up Mobile Device Management (MDM) in Office 365](https://support.office.com/article/Set-up-Mobile-Device-Management-MDM-in-Office-365-dd892318-bc44-4eb1-af00-9db5430be3cd) for complete steps. In summary, these steps include: 
  
1. Activating MDM for Office 365 by following steps in the Security &amp; Compliance Center.
    
2. Setting up MDM for Office 365 by, for example, creating an APNs certificate to manage iOS devices, and by adding a Domain Name System (DNS) record for your domain to support Windows phones.
    
3. Creating device policies and apply them to groups of users. When you do this, your users will get an enrollment message on their device. And when they've completed enrollment, their devices will be restricted by the policies you've set up for them.
    
> [!NOTE]
> Policies and access rules created in MDM for Office 365 will override both Exchange mobile device mailbox policies and device access rules created in the Exchange admin center. After a device is enrolled in MDM for Office 365, any Exchange mobile device mailbox policy or device access rule that is applied to that device will be ignored. 
  
## Leveraging Exchange Online mobile device policies
<a name="leverageexo"> </a>

If you don't plan on leveraging either the Enterprise Mobility + Security suite or the MDM for Office 365 functionality, you can implement Exchange mobile device mailbox policy to secure the device, and device access rules to limit device connectivity.
  
### Mobile device mailbox policy

Outlook for iOS and Android supports the following mobile device mailbox policy settings in Exchange Online:
  
- Device encryption enabled
    
- Min password length
    
- Password enabled
    
For information on how to create or modify an existing mobile device mailbox policy, see [Mobile device mailbox policies in Exchange Online](../../clients-and-mobile-in-exchange-online/exchange-activesync/mobile-device-mailbox-policies.md).
  
In addition, Outlook for iOS and Android supports Exchange Online's device-wipe capability. When executed, only the app is wiped, because Exchange Online considers the Outlook for iOS and Android app as the mobile device. For more information on how to perform a remote wipe, see [Wipe a mobile device in Office 365](https://support.office.com/article/Wipe-a-mobile-device-in-Office-365-9d727c7d-8b47-4499-bf24-d046b449214c).
  
> [!NOTE]
> Outlook for iOS and Android only supports the "Wipe Data" remote wipe command and does not support "Account Only Remote Wipe Device." 
  
### Device access policy

Outlook for iOS and Android should be enabled by default, but in some existing Exchange Online environments the app may be blocked for a variety of reasons. Once an organization decides to standardize how users access Exchange data and use Outlook for iOS and Android as the only email app for end users, you can configure blocks for other email apps running on users' iOS and Android devices. You have two options for instituting these blocks within Exchange Online: the first option blocks all devices and only allows usage of Outlook for iOS and Android; the second option allows you to block individual devices from using the native Exchange ActiveSync apps. 
  
 **Option 1: Block all email apps except Outlook for iOS and Android**
  
You can define a default block rule and then configure an allow rule for Outlook for iOS and Android, and for Windows devices, using the following Exchange Management Shell commands. This configuration will prevent any Exchange ActiveSync native app from connecting, and will only allow Outlook for iOS and Android.
  
1. Create the default block rule:
    
  ```
  Set-ActiveSyncOrganizationSettings -DefaultAccessLevel Block
  ```

2. Create an allow rule for Outlook for iOS and Android
    
  ```
  New-ActiveSyncDeviceAccessRule -Characteristic DeviceModel -QueryString "Outlook for iOS and Android" -AccessLevel Allow
  ```

3. **Optional**: Create rules that allow Outlook on Windows devices for Exchange ActiveSync connectivity (WP refers to Windows Phone, WP8 refers to Windows Phone 8 and later, and WindowsMail refers to the Mail app included in Windows 10):
    
  ```
  New-ActiveSyncDeviceAccessRule -Characteristic DeviceType -QueryString "WP" -AccessLevel Allow
  New-ActiveSyncDeviceAccessRule -Characteristic DeviceType -QueryString "WP8" -AccessLevel Allow
  New-ActiveSyncDeviceAccessRule -Characteristic DeviceType -QueryString "WindowsMail" -AccessLevel Allow
  
  ```

 **Option 2: Block native Exchange ActiveSync apps on Android and iOS devices**
  
Alternatively, you can block native Exchange ActiveSync apps on specific Android and iOS devices or other types of devices.
  
1. Confirm that there are no Exchange ActiveSync device access rules in place that block Outlook for iOS and Android:
    
  ```
  Get-ActiveSyncDeviceAccessRule | where {$_.AccessLevel -eq "Block" -and $_.QueryString -like "Outlook*"} | ft Name,AccessLevel,QueryString -auto
  ```

    If any device access rules that block Outlook for iOS and Android are found, type the following to remove them:
    
  ```
  Get-ActiveSyncDeviceAccessRule | where {$_.AccessLevel -eq "Block" -and $_.QueryString -like "Outlook*"} | Remove-ActiveSyncDeviceAccessRule
  ```

2. You can block most Android and iOS devices with the following commands:
    
  ```
  New-ActiveSyncDeviceAccessRule -Characteristic DeviceType -QueryString "Android" -AccessLevel Block
  New-ActiveSyncDeviceAccessRule -Characteristic DeviceType -QueryString "iPad" -AccessLevel Block
  New-ActiveSyncDeviceAccessRule -Characteristic DeviceType -QueryString "iPhone" -AccessLevel Block
  New-ActiveSyncDeviceAccessRule -Characteristic DeviceType -QueryString "iPod" -AccessLevel Block
  
  ```

3. Not all Android device manufacturers specify "Android" as the DeviceType. Manufacturers may specify a unique value with each release. In order to find other Android devices that are accessing your environment, execute the following command to generate a report of all devices that have an active Exchange ActiveSync partnership:
    
  ```
  Get-MobileDevice | Select-Object DeviceOS,DeviceModel,DeviceType | Export-CSV c:\temp\easdevices.csv
  ```

4. Create additional block rules, depending on your results from Step 3. For example, if you find your environment has a high usage of HTCOne Android devices, you can create an Exchange ActiveSync device access rule that blocks that particular device, forcing the users to use Outlook for iOS and Android. In this example, you would type:
    
  ```
  New-ActiveSyncDeviceAccessRule -Characteristic DeviceType -QueryString "HTCOne" -AccessLevel Block
  ```

    > [!NOTE]
    > The QueryString parameter does not accept wildcards or partial matches. 
  
    **Additional resources**:
    
  - [New-ActiveSyncDeviceAccessRule](http://technet.microsoft.com/library/a33c69d8-4d19-4e9d-b5cf-27727b7c4a8f.aspx)
    
  - [Get-MobileDevice](http://technet.microsoft.com/library/ce8a4142-23c1-47d5-89c5-961bd6e9d162.aspx)
    
  - [Set-ActiveSyncOrganizationSettings](http://technet.microsoft.com/library/a447bf51-fcdc-4f8d-8d06-533d299c11fe.aspx)
    
## Blocking Outlook for iOS and Android
<a name="blocking"> </a>

If you don't want users in your organization to access Exchange data with Outlook for iOS and Android, the approach you take depends on whether you are using Azure Active Directory conditional access policies or Exchange Online's device access policies.
  
### Option 1: Block mobile device access using a conditional access policy

Azure Active Directory conditional access does not provide a mechanism whereby you can specifically block Outlook for iOS and Android while allowing other Exchange ActiveSync clients. With that said, conditional access policies can be used to block mobile device access in two ways:
  
- Option A: Block mobile device access on both the iOS and Android platforms
    
- Option B: Block mobile device access on a specific mobile device platform
    
 **Option A: Block mobile device access on both the iOS and Android platforms**
  
If you want to prevent mobile device access for all users, or a subset of users, using conditional access, follow these steps.
  
Create conditional access policies, with each policy either targeting all users or a subset of users via a security group. Details are in [Azure Active Directory app-based conditional access](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-mam#exchange-online-policy).
  
1. The first policy blocks Outlook for iOS and Android and other OAuth capable Exchange ActiveSync clients from connecting to Exchange Online. See "Step 1 - Configure an Azure AD conditional access policy for Exchange Online," but for the fifth step, choose **Block access**.
    
2. The second policy prevents Exchange ActiveSync clients leveraging basic authentication from connecting to Exchange Online. See "Step 2 - Configure an Azure AD conditional access policy for Exchange Online with Active Sync (EAS)."
    
 **Option B: Block mobile device access on a specific mobile device platform**
  
If you want to prevent a specific mobile device platform from connecting to Exchange Online, while allowing Outlook for iOS and Android to connect using that platform, create the following conditional access policies, with each policy targeting all users. Details are in [Azure Active Directory app-based conditional access](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-mam#exchange-online-policy).
  
1. The first policy allows Outlook for iOS and Android on the specific mobile device platform and blocks other OAuth capable Exchange ActiveSync clients from connecting to Exchange Online. See "Step 1 - Configure an Azure AD conditional access policy for Exchange Online," but for step 4a, select only the desired mobile device platform (such as iOS) to which you want to allow access.
    
2. The second policy blocks the app on the specific mobile device platform and other OAuth capable Exchange ActiveSync clients from connecting to Exchange Online. See "Step 1 - Configure an Azure AD conditional access policy for Exchange Online," but for step 4a, select only the desired mobile device platform (such as Android) to which you want to block access, and for step 5, choose **Block access**.
    
3. The third policy prevents Exchange ActiveSync clients leveraging basic authentication from connecting to Exchange Online. See "Step 2 - Configure an Azure AD conditional access policy for Exchange Online with Active Sync (EAS)."
    
### Option 2: Block Outlook for iOS and Android using Exchange mobile device access rules

If you are managing your mobile device access via Exchange Online's device access rules, you have two options:
  
- Option A: Block Outlook for iOS and Android on both the iOS and Android platforms
    
- Option B: Block Outlook for iOS and Android on a specific mobile device platform
    
Every Exchange organization has different policies regarding security and device management. If an organization decides that Outlook for iOS and Android doesn't meet their needs or is not the best solution for them, administrators have the ability to block the app. Once the app is blocked, mobile Exchange users in your organization can continue accessing their mailboxes by using the built-in mail applications on iOS and Android.
  
The  `New-ActiveSyncDeviceAccessRule` cmdlet has a  `Characteristic` parameter, and there are three  `Characteristic` options that administrators can use to block the Outlook for iOS and Android app. The options are UserAgent, DeviceModel, and DeviceType. In the two blocking options described in the following sections, you will use one or more of these characteristic values to restrict the access that Outlook for iOS and Android has to the mailboxes in your organization.
  
The values for each characteristic are displayed in the following table:
  
|**Characteristic**|**String for iOS**|**String for Android**|
|:-----|:-----|:-----|
|DeviceModel  <br/> |Outlook for iOS and Android  <br/> |Outlook for iOS and Android  <br/> |
|DeviceType  <br/> |Outlook  <br/> |Outlook  <br/> |
|UserAgent  <br/> |Outlook-iOS/2.0  <br/> |Outlook-Android/2.0  <br/> |
   
 **Option A: Block Outlook for iOS and Android on both the iOS and Android platforms**
  
With the  `New-ActiveSyncDeviceAccessRule` cmdlet, you can define a device access rule, using either the  `DeviceModel` or  `DeviceType` characteristic. In both cases, the access rule blocks Outlook for iOS and Android across all platforms, and will prevent any device, on both the iOS platform and Android platform, from accessing an Exchange mailbox via the app. 
  
The following are two examples of a device access rule. The first example uses the  `DeviceModel` characteristic; the second example uses the  `DeviceType` characteristic. 
  
```
New-ActiveSyncDeviceAccessRule -Characteristic DeviceType -QueryString "Outlook" -AccessLevel Block
```

```
New-ActiveSyncDeviceAccessRule -Characteristic DeviceModel -QueryString "Outlook for iOS and Android" -AccessLevel Block
```

 **Option B: Block Outlook for iOS and Android on a specific mobile device platform**
  
With the  `UserAgent` characteristic, you can define a device access rule that blocks Outlook for iOS and Android across a specific platform. This rule will prevent a device from using Outlook for iOS and Android to connect on the platform you specify. The following examples show how to use the device-specific value for the  `UserAgent` characteristic. 
  
To block Android and allow iOS:
  
```
New-ActiveSyncDeviceAccessRule -Characteristic UserAgent -QueryString "Outlook-Android/2.0" -AccessLevel Block
New-ActiveSyncDeviceAccessRule -Characteristic UserAgent -QueryString "Outlook-iOS/2.0" -AccessLevel Allow

```

To block iOS and allow Android:
  
```
New-ActiveSyncDeviceAccessRule -Characteristic UserAgent -QueryString "Outlook-Android/2.0" -AccessLevel Allow
New-ActiveSyncDeviceAccessRule -Characteristic UserAgent -QueryString "Outlook-iOS/2.0" -AccessLevel Block

```

## Exchange Web Services (EWS) application policies
<a name="additionalmethods"> </a>

Beyond Microsoft Intune, MDM for Office 365, and Exchange mobile device policies, you can also manage the access that mobile devices have to information in your organization through EWS application policies. An EWS application policy can control whether or not applications are allowed to leverage the REST API. Note that when you configure an EWS application policy that only allows specific applications access to your messaging environment, you must add the user-agent string for Outlook for iOS and Android to the EWS allow list. 
  
The following example shows how to add the user-agent strings to the EWS allow list:
  
```
Set-OrganizationConfig -EwsAllowList @{Add="Outlook-iOS/*","Outlook-Android/*"}
```


