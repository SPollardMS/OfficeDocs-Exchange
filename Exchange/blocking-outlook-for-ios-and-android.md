---
title: Blocking Outlook for iOS and Android
ms.prod: EXCHANGE
ms.assetid: ca0cd3d3-6d1e-4c54-ac4d-7a66428e6b4e
---


# Blocking Outlook for iOS and Android
 **Summary**: If you don't want users in your Exchange on-premises organization to access data with Outlook for iOS and Android, this article explains how to block the app.
Every Exchange organization has different policies regarding security and device management. If an organization decides that Outlook for iOS and Android doesn't meet their needs or is not the best solution for them for any reason, administrators can block the app using Exchange ActiveSync device management policies. See  [Controlling Device Access](https://go.microsoft.com/fwlink/p/?LinkId=624009) for complete information on configuring Exchange ActiveSync. In Exchange ActiveSync management screens, the Outlook app is identified as **DeviceModel: 'Outlook for iOS and Android'** or **DeviceType: 'Outook'**.
  
    
    


> [!NOTE]
> Because device IDs are not governed by any  *physical device*  ID, they can change without notice. When this happens, it can cause unintended consequences when device IDs are used for managing user devices, as existing 'allowed' devices may be unexpectedly blocked or quarantined by Exchange. Therefore, we recommend administrators only set mobile device policies that allow/block devices based on device type or device model.
  
    
    


Exchange users in your organization can continue using Outlook on the web for iPhone/iPad/Android apps, or the built-in mail apps on iOS and Android, to access their Exchange mailboxes.
  
    
    

The following is an example of what a device rule looks like in PowerShell after it's created in the Exchange Admin Center.
  
    
    
![Example of device rule in PowerShell](images/6a4a8415-d844-476a-a6dc-e28d31bfe94c.png)
  
    
    

  
    
    

  
    
    

