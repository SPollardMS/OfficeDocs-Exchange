---
title: Managing devices for Outlook for iOS and Android for Exchange Server
ms.prod: EXCHANGE
ms.assetid: 8c566e98-72d8-4174-87fb-d0771c14f0dd
---


# Managing devices for Outlook for iOS and Android for Exchange Server
 **Summary**: This article describes how to manage mobile devices with Outlook for iOS and Android in your Exchange on-premises organization.
Microsoft recommends Exchange ActiveSync for managing the mobile devices that are used to access Exchange mailboxes in your on-premises environment. Exchange ActiveSync is a Microsoft Exchange synchronization protocol that lets mobile phones access an organization's information on a server that's running Microsoft Exchange.
  
    
    

This article focuses on specific Exchange ActiveSync features and scenarios for mobile devices running Outlook for Android and iOS. Complete information about the Microsoft Exchange synchronization protocol is available in  [Exchange ActiveSync](exchange-activesync.md). In addition, there is information on  [the Office Blog](https://go.microsoft.com/fwlink/p/?LinkId=623922) detailing password enforcement and other benefits of using Exchange ActiveSync with devices running Outlook for iOS and Android.
## PIN lock and device encryption

If your organization's Exchange ActiveSync policy requires a password on mobile devices in order for users to synchronize email, Outlook will enforce this policy at the device level. This works differently between iOS devices and Android devices, based on the available controls provided by Apple and Google.
  
    
    
On iOS devices, Outlook checks to make sure a passcode or PIN is properly set. In the event a passcode is not set, Outlook prompts users to create a passcode in iOS settings. Until the passcode is setup, the user will be unable to access Outlook for iOS.
  
    
    
Outlook for iOS only runs on iOS 8.0 or later. These devices are shipped with built-in encryption, which Outlook uses once the passcode is enabled to encrypt all the data Outlook stores locally on the iOS device. Therefore, iOS devices with a PIN will be encrypted whether or not this is required by an ActiveSync policy.
  
    
    
On Android devices, Outlook will enforce screen lock rules. In addition, Google provides controls that allow Outlook for Android to comply with Exchange policies regarding password length and complexity, and the number of allowable screen-unlock attempts before wiping the phone. Outlook for Android will also encourage storage encryption if it is not enabled, guiding users through this process with a step-by-step walkthrough.
  
    
    
iOS and Android devices that do not support these password security settings will not be able to connect to an Exchange mailbox.
  
    
    

## Remote wipe with Exchange ActiveSync

Exchange ActiveSync enables administrators to remotely wipe devices, such as if they become compromised. With Outlook for iOS and Android, a remote wipe is done on the Outlook app itself, and not a full device wipe.
  
    
    
After the remote wipe command is requested by the administrator, the wipe happens within seconds of the Outlook app's next connection to Exchange. The Outlook app will reset and all Outlook email, calendar, contacts, and files data will be removed from the device, as well as from the Outlook service. The wipe will not affect any of the user's personal apps and information outside of Outlook. 
  
    
    
Since Outlook for iOS and Android appears as a single mobile device association under a user's mobile devices in Exchange, a remote wipe command will remove data and delete sync relationships from all devices running Outlook (iPhone, iPad, Android) associated with that user.
  
    
    

> [!NOTE]
> Due to the cloud architecture behind Outlook for iOS and Android, the result of a remote device wipe is not reported back to Exchange. Even when the wipe is successful, the status will display as **Pending**. This is a known issue and a solution is being developed. 
  
    
    


## Device identifiers and access control

Due to the cloud-based architecture of Outlook for iOS and Android, Outlook connections appear as a single mobile device identifier (ID) for each user in Exchange. This means mobile device access controls for each user are applied to all devices associated with this device ID. This implementation creates two conditions that are different from how traditional Exchange ActiveSync device access controls work. 
  
    
    

- **Block**: a block rule blocks Outlook on all devices and supported operating systems. You cannot block individual devices or operating systems. 
    
  
- **Quarantine**: the quarantine process works on a per-user basis, rather than a per-device basis. Once a user has a device released from quarantine, they can install and configure Outlook on as many additional devices as they like. Because the user has been released from quarantine, any new devices associated with that user will not be quarantined.
    
  
When mobile device mailbox policies are in place, they apply to all associated devices. Therefore, if you enforce a PIN lock for a specific mailbox, all devices that connect to that mailbox will require a PIN.
  
    
    

> [!NOTE]
> Because device IDs are not governed by any  *physical device*  ID, they can change without notice. When this happens, it can cause unintended consequences when device IDs are used for managing user devices, as existing 'allowed' devices may be unexpectedly blocked or quarantined by Exchange. Therefore, we recommend administrators only set mobile device policies that allow/block devices based on device type or device model.
  
    
    


## Device management with Exchange ActiveSync FAQ

The following are frequently asked questions about passwords, PINs, and encryption policies for devices running Outlook for iOS and Android.
  
    
    

### The native Mail application on iOS enforces Exchange ActiveSync policies for password length and complexity requirements. Why doesn't Outlook?

Outlook takes advantage of the third-party application developer controls that are available to Microsoft. We will continue to improve this capability as Apple makes more controls available to developers.
  
    
    

### Why does Outlook for iOS and Android enforce PINs at the device level, rather than the app level?

After evaluating the capabilities available in iOS and Android, Microsoft believes a device-level PIN delivers the best experience for customers, in terms of both convenience and security. An app-level PIN means users have to enter two different PINs in order to access email, which may not be desirable. Further, a device- level PIN means we can take advantage of features like native device encryption, TouchID on iOS, and Smart Lock on Android. Remote wipe is still implemented at the app level, which means users' personal applications and data will not be affected when Outlook is wiped.
  
    
    

### I was able to cancel out of Android device encryption. How come?

If requested by the mobile device mailbox policy, encryption on Android devices will be encouraged and the step-by-step walkthrough will ask the user to set device encryption. Because availability and implementation of this process varies by Android OS version and device manufacturer, we allow the user to cancel out during the encryption process. Even if the Android device is unencrypted and an attacker is in possession of the device, as long as a device PIN is enabled, the Outlook database remains inaccessible. This is true even with USB debugging enabled and the Android SDK installed. If an attacker attempts to root the device to bypass the PIN to gain access to this information, the rooting process wipes all device storage and removes all Outlook data. If the device is unencrypted and rooted by the user prior to being stolen, it is possible for an attacker to gain access to the Outlook database by enabling USB debugging on the device and plugging the device into a computer with the Android SDK installed.
  
    
    

