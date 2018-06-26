---
title: "Mobile device mailbox policies in Exchange Online"
ms.author: dmaguire
author: msdmaguire
manager: laurawi
ms.date: 4/29/2016
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: fa618cd2-29d0-42b3-a7a0-0ecd1aee6c20
description: "In Office 365, you can create mobile device mailbox policies to apply a common set of policies or security settings to a collection of users. A default mobile device mailbox policy is created in every Office 365 organization."
---

# Mobile device mailbox policies in Exchange Online

In Office 365, you can create mobile device mailbox policies to apply a common set of policies or security settings to a collection of users. A default mobile device mailbox policy is created in every Office 365 organization. 
  
## Overview of mobile device mailbox policies

You can use mobile device mailbox policies to manage many different settings. These include the following: 
  
- Require a password
    
- Specify the minimum password length
    
- Allow a numeric PIN or require special characters in the password
    
- Designate how long a device can be inactive before requiring the user to re-enter a password
    
- Wipe a device after a specific number of failed password attempts
    
## Managing Exchange ActiveSync mailbox policies

Mobile device mailbox policies can be created in the Exchange Administration Center (EAC) or the Exchange Management Shell. If you create a policy in the EAC, you can configure only a subset of the available settings. You can configure the rest of the settings using the Exchange Management Shell. 
  
## Mobile device mailbox policy settings

The following table summarizes the settings you can specify using mobile device mailbox policies.
  
**Mobile device mailbox policy settings**

|**Setting**|**Description**|
|:-----|:-----|
|Allow Bluetooth  <br/> |This setting specifies whether a mobile device allows Bluetooth connections. The available options are Disable, HandsFree Only, and Allow. The default value is Allow.  <br/> |
|Allow Browser  <br/> |This setting specifies whether Pocket Internet Explorer is allowed on the mobile device. This setting doesn't affect third-party browsers installed on the mobile device. The default value is  `$true`.  <br/> |
|Allow Camera  <br/> |This setting specifies whether the mobile device camera can be used. The default value is  `$true`.  <br/> |
|Allow Consumer EMail  <br/> |This setting specifies whether the mobile device user can configure a personal email account (either POP3 or IMAP4) on the mobile device. The default value is  `$true`. This setting doesn't control access to email accounts that are using third-party mobile device email programs.  <br/> |
|Allow Desktop Sync  <br/> |This setting specifies whether the mobile device can synchronize with a computer through a cable, Bluetooth, or IrDA connection. The default value is  `$true`.  <br/> |
|Allow External Device Management  <br/> |This setting specifies whether an external device management program is allowed to manage the mobile device.  <br/> |
|Allow HTML Email  <br/> |This setting specifies whether email synchronized to the mobile device can be in HTML format. If this setting is set to  `$false`, all email is converted to plain text.  <br/> |
|Allow Internet Sharing  <br/> |This setting specifies whether the mobile device can be used as a modem for a desktop or a portable computer. The default value is  `$true`.  <br/> |
|AllowIrDA  <br/> |This setting specifies whether infrared connections are allowed to and from the mobile device.  <br/> |
|Allow Mobile OTA Update  <br/> |This setting specifies whether the mobile device mailbox policy settings can be sent to the mobile device over a cellular data connection. The default value is  `$true`.  <br/> |
|Allow non-provisionable devices  <br/> |This setting specifies whether mobile devices that may not support application of all policy settings are allowed to connect to Office 365 by using Exchange ActiveSync. Allowing non-provisionable mobile devices has security implications. For example, some non-provisionable devices may not be able to implement an organization's password requirements.  <br/> |
|Allow POPIMAPEmail  <br/> |This setting specifies whether the user can configure a POP3 or an IMAP4 email account on the mobile device. The default value is  `$true`. This setting doesn't control access by third-party email programs.  <br/> |
|Allow Remote Desktop  <br/> |This setting specifies whether the mobile device can initiate a remote desktop connection. The default value is  `$true`.  <br/> |
|Allow simple password  <br/> |This setting enables or disables the ability to use a simple password such as 1111 or 1234. The default value is  `$true`.  <br/> |
|Allow S/MIME encryption algorithm negotiation  <br/> |This setting specifies whether the messaging application on the mobile device can negotiate the encryption algorithm if a recipient's certificate doesn't support the specified encryption algorithm.  <br/> |
|Allow S/MIME software certificates  <br/> |This setting specifies whether S/MIME software certificates are allowed on the mobile device.  <br/> |
|Allow storage card  <br/> |This setting specifies whether the mobile device can access information that's stored on a storage card.  <br/> |
|Allow text messaging  <br/> |This setting specifies whether text messaging is allowed from the mobile device. The default value is  `$true`.  <br/> |
|Allow unsigned applications  <br/> |This setting specifies whether unsigned applications can be installed on the mobile device. The default value is  `$true`.  <br/> |
|Allow unsigned installation packages  <br/> |This setting specifies whether an unsigned installation package can be run on the mobile device. The default value is  `$true`.  <br/> |
|Allow Wi-Fi  <br/> |This setting specifies whether wireless Internet access is allowed on the mobile device. The default value is  `$true`.  <br/> |
|Alphanumeric password required  <br/> |This setting requires that a password contains numeric and non-numeric characters. The default value is  `$true`.  <br/> |
|Approved Application List  <br/> |This setting stores a list of approved applications that can be run on the mobile device.  <br/> |
|Attachments enabled  <br/> |This setting enables attachments to be downloaded to the mobile device. The default value is  `$true`.  <br/> |
|Device encryption enabled  <br/> |This setting enables encryption on the mobile device. Not all mobile devices can enforce encryption. For more information, see the device and mobile operating system documentation.  <br/> |
|Device policy refresh interval  <br/> |This setting specifies how often the mobile device mailbox policy is sent from the server to the mobile device.  <br/> |
|IRM enabled  <br/> |This setting specifies whether Information Rights Management (IRM) is enabled on the mobile device.  <br/> |
|Max attachment size  <br/> |This setting controls the maximum size of attachments that can be downloaded to the mobile device. The default value is Unlimited.  <br/> |
|Max calendar age filter  <br/> | This setting specifies the maximum range of calendar days that can be synchronized to the mobile device. The following values are accepted:  <br/>  All  <br/>  OneDay  <br/>  ThreeDays  <br/>  OneWeek  <br/>  TwoWeeks  <br/>  OneMonth  <br/> |
|Max email age filter  <br/> | This setting specifies the maximum number of days of email items to synchronize to the mobile device. The following values are accepted:  <br/>  All  <br/>  OneDay  <br/>  ThreeDays  <br/>  OneWeek  <br/>  TwoWeeks  <br/>  OneMonth  <br/> |
|Max email body truncation size  <br/> |This setting specifies the maximum size at which email messages are truncated when synchronized to the mobile device. The value is in kilobytes (KB).  <br/> |
|Max email HTML body truncation size  <br/> |This setting specifies the maximum size at which HTML email messages are truncated when synchronized to the mobile device. The value is in kilobytes (KB).  <br/> |
|Max inactivity time lock  <br/> |This value specifies the length of time that the mobile device can be inactive before a password is required to reactivate it. You can enter any interval between 30 seconds and 1 hour. The default value is 15 minutes.  <br/> |
|Max password failed attempts  <br/> |This setting specifies the number of attempts a user can make to enter the correct password for the mobile device. You can enter any number from 4 through 16. The default value is 8.  <br/> |
|Min password complex characters  <br/> |This setting specifies the minimum number of complex characters required in the mobile device's password. A complex character is a character that is not a letter.  <br/> |
|Min password length  <br/> |This setting specifies the minimum number of characters in the mobile device password. You can enter any number from 1 through 16. The default value is 4.  <br/> |
|Password enabled  <br/> |This setting enables the mobile device password.  <br/> |
|Password expiration  <br/> |This setting enables the administrator to configure a length of time after which a mobile device password must be changed.  <br/> |
|Password history  <br/> |This setting specifies the number of past passwords that can be stored in a user's mailbox. A user can't reuse a stored password.  <br/> |
|Password recovery enabled  <br/> |When this setting is enabled, the mobile device generates a recovery password that's sent to the server. If the user forgets their mobile device password, the recovery password can be used to unlock the mobile device and enable the user to create a new mobile device password.  <br/> |
|Require device encryption  <br/> |This setting specifies whether device encryption is required. If set to  `$true`, the mobile device must be able to support and implement encryption to synchronize with the server.  <br/> |
|Require encrypted S/MIME messages  <br/> |This setting specifies whether S/MIME messages must be encrypted. The default value is  `$false`.  <br/> |
|Require encryption S/MIME algorithm  <br/> |This setting specifies what required algorithm must be used when encrypting S/MIME messages.  <br/> |
|Require manual synchronization while roaming  <br/> |This setting specifies whether the mobile device must synchronize manually while roaming. Allowing automatic synchronization while roaming will frequently lead to larger-than-expected data costs for the mobile device data plan.  <br/> |
|Require signed S/MIME algorithm  <br/> |This setting specifies what required algorithm must be used when signing a message.  <br/> |
|Require signed S/MIME messages  <br/> |This setting specifies whether the mobile device must send signed S/MIME messages.  <br/> |
|Require storage card encryption  <br/> |This setting specifies whether the storage card must be encrypted. Not all mobile device operating systems support storage card encryption. For more information, see your mobile device and mobile operating system documentation.  <br/> |
|Unapproved InROM application list  <br/> |This setting specifies a list of applications that cannot be run in ROM.  <br/> |
   

