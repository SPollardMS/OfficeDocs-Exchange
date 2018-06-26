---
title: "Voice mail for users"
ms.author: tonysmit
author: tonysmit
manager: scotv
ms.date: 6/24/2018
ms.audience: ITPro
ms.topic: article
ms.service: exchange-online
localization_priority: Normal
ms.assetid: 48e1f43b-fb7e-4a52-a2cb-0fb5da6ca65f
description: "With Unified Messaging (UM), users in an Exchange organization can receive all their email and voice messages in one mailbox. The Unified Messaging functionality and voice mail features increase user productivity and enable more flexible messaging throughout an organization."
---

# Voice mail for users

With Unified Messaging (UM), users in an Exchange organization can receive all their email and voice messages in one mailbox. The Unified Messaging functionality and voice mail features increase user productivity and enable more flexible messaging throughout an organization.
  
When you're adding a user to your organization, you're given the option of creating a mailbox or connecting the user to an existing mailbox. After the mailbox is created for the user or the user is connected to an existing mailbox, you can enable the mailbox for Unified Messaging so the user can use the voice mail system and the features included with voice mail. After the user is enabled for Unified Messaging, all email, voice mail, and fax messages will be delivered to the user's mailbox. By using Microsoft Office Outlook 2007 or later versions, Outlook Web App, a mobile phone enabled for Microsoft Exchange ActiveSync, or a regular or mobile phone, users can access their email, voice messages, personal contacts, and calendaring information.
  
## Voice mail user properties
<a name="umuserproperties"> </a>

A user must have a mailbox before they can be enabled for Unified Messaging. But, by default, a user who has a mailbox isn't enabled for Unified Messaging. After the user is UM-enabled, you can manage, modify, and configure the UM properties and voice mail features for them. You can enable a user for Unified Messaging using EAC or the Shell. For details, see [Enable a user for voice mail](enable-a-user-for-voice-mail.md). To enable multiple UM users, use the EAC or the **Enable-UMMailbox** cmdlet in the Exchange Management Shell. 
  
## The relationship between a voice mail user and other UM components
<a name="umuserandotheradobjects"> </a>

When you enable a user for Unified Messaging, the user must be associated with or linked to an existing UM mailbox policy, and you must provide an extension number for them. You can associate a user with a UM mailbox policy by using the **Enable-UMMailbox** cmdlet in the Shell or by selecting the UM mailbox policy when you enable the user for Unified Messaging. By default, when you create a UM dial plan, a new UM mailbox policy is created. This policy can be modified or another policy can be created and linked to the dial plan to determine what features or settings will be applied to a user or group of users. 
  
A UM mailbox policy contains settings such as the dialing restrictions and PIN policies for a user. When a UM mailbox policy is created, it must be associated with only one UM dial plan. Any Exchange server can answering incoming calls and provide voice mail services for any UM-enabled users who are linked with the UM dial plan. After the user is enabled for Unified Messaging, the settings from a UM mailbox policy are applied to the UM-enabled user.
  
## Extension numbers and SIP addresses
<a name="extensionnumberssipaddresses"> </a>

When you enable a user for Unified Messaging, you must define at least one extension number that Unified Messaging will use when voice mail is submitted to the user's mailbox. After you enable the user for Unified Messaging, you can add secondary extension numbers to the user's mailbox, or modify or remove them by configuring the Exchange Unified Messaging proxy address (EUM proxy address) on the user's mailbox or add or remove additional or secondary extensions for the user in the EAC. You can remove the primary extension number in the EAC by removing the EUM proxy address, but it's recommended that you don't remove it. Removing the primary extension number won't allow calls to be forwarded correctly to the user's mailbox.
  
> [!NOTE]
> There's no limit to the number of secondary extension numbers that you can add for a UM-enabled user but there can only be one primary extension number per user. 
  
The mailbox of a UM-enabled user can be associated with only one UM dial plan. The UM-enabled user can be assigned the following:
  
- A single primary extension number, Session Initiation Protocol (SIP) address, or E.164 address on a single dial plan.
    
- Multiple secondary extension numbers, SIP addresses, or E.164 addresses on a single dial plan.
    
- Multiple primary extension numbers, SIP addresses, or E.164 addresses on two separate dial plans.
    
> [!NOTE]
> Each extension number, SIP address, and E.164 number must be unique within a dial plan and the number of digits in the dial plan will used for all users that are linked with the dial plan. 
  
For example, a UM-enabled user travels frequently from New York to Tokyo. The user's mailbox is associated with the New York dial plan and a single extension number is configured on the user's mailbox. A second extension number is configured on the user's mailbox for the Tokyo dial plan. When callers dial either extension number and leave a voice message for the user, the voice message will be delivered to the same UM-enabled mailbox.
  
## Using the EAC to enable a user for UM and voice mail
<a name="eac"> </a>

After you create an Exchange mailbox for the user, you can configure the UM mailbox settings by using **View Details** under **Unified Messaging** in the EAC. When you enable a user, there are several settings that you need to configure: 
  
1. **SIP address** This is the SIP address for the user. You'll see this setting if the user that you're enabling for UM is assigned to a UM mailbox policy that's linked to a SIP URI dial plan. SIP URI dial plans are used when you're integrating Office Communications Server 2007 R2 or Microsoft Lync Server. When you assign the user to a UM mailbox policy that's linked to a SIP URI or E.164 dial plan, you must still also enter an extension number for the user. The primary extension number is used by the user to access Outlook Voice Access. 
    
2. **Extension number** You must manually enter the extension number for the user you're enabling for UM. 
    
    You must provide a valid extension number for the user and match the number of digits specified on the dial plan. You can only enter numeric characters or digits from 1 through 20. The typical extension number is 3 to 7 digits long, and is configured on the dial plan with which the UM mailbox policy is linked and assigned to the user.
    
3. **PIN settings for the user:**
    
  - **Automatically generate PIN** This setting automatically generates a PIN for the UM-enabled user to use for voice mail access via Outlook Voice Access. This is the default setting. When you click this button, a PIN is automatically generated based on the PIN policies configured on the UM mailbox policy assigned to the user. We recommend that you use this setting to help protect the user's PIN. The PIN is sent to the user in the welcome message they receive after they're enabled for UM. By default, they'll have to change this PIN when they first sign in to their mailbox to get their voice mail. 
    
  - **Type a PIN** This setting enables you to manually specify a PIN that the user will use to access the voice mail system. 
    
    The PIN must comply with the PIN policy settings configured on the UM mailbox policy associated with this UM-enabled user. For example, if the UM mailbox policy is configured to accept only PINs that contain seven or more digits, the PIN you enter in this box must be at least seven digits long.
    
  - **Require the user to reset their PIN the first time they sign in** This setting forces the user to reset their voice mail PIN when they access the voice mail system from a telephone using Outlook Voice Access for the first time. They will be prompted to enter a PIN that's more familiar to them.It's a security best practice to force UM-enabled users to change their PIN when they first sign in to help protect against unauthorized access to their data and Inbox. This check box is selected by default. 
    
## Using the Shell to enable a user for UM and voice mail
<a name="shell"> </a>

This example enables Unified Messaging and voice mail on the mailbox for tonysmith@contoso.com, sets the extension and manually sets the PIN for the user, and then assigns the user to a UM mailbox policy named  `MyUMMailboxPolicy`.
  
```
Enable-UMMailbox -Identity tonysmith@contoso.com -UMMailboxPolicy MyUMMailboxPolicy -Extensions 51234 -PIN 5643892 -PINExpired $true
```

This example enables Unified Messaging and voice mail on a mailbox for tonysmith@contoso.com, assigns the user to a UM mailbox policy named  `MyUMMailboxPolicy`, and sets the extension number, SIP address, and manually sets the PIN for the user.
  
```
Enable-UMMailbox -Identity tonysmith@contoso.com -UMMailboxPolicy MyUMMailboxPolicy -Extensions 51234 -PIN 5643892 -SIPResourceIdentifier "tonysmith@contoso.com" -PINExpired $true
```

## Disabling UM for a user
<a name="disablingumforuser"> </a>

When you disable Unified Messaging for a user, the user's account may still be listed when a caller performs a directory search using a UM auto attendant menu or using Outlook Voice Access. Callers may be able to locate a user in the directory, but when they try to contact the user, they're taken back to the main menu in Unified Messaging. This may cause callers to become frustrated with the system. You can prevent callers from using a directory search to contact a user who's been disabled for Unified Messaging by connecting the user to another voice mail system, removing the user from the UM auto attendant directory search, or removing the user's account.
  
After a UM-enabled user account is disabled for Unified Messaging, the user may still have access to the individual UM-enabled mailbox using Outlook Voice Access or Microsoft Outlook. This can occur when all the changes aren't consistent in the directory. To lessen the risk of a user gaining access to the mailbox even though the account has been disabled for Unified Messaging, you can manually force replication to occur or remove all Unified Messaging information from the user's mailbox when the user is disabled for Unified Messaging. 
  

