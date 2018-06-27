---
title: "Setting up Outlook Voice Access"
ms.author: tonysmit
author: tonysmit
manager: scotv
ms.date: 6/24/2018
ms.audience: ITPro
ms.topic: article
ms.service: exchange-online
localization_priority: Normal
ms.assetid: 5ce8c877-35f3-4e55-a65e-5ca469aeae99
description: "Microsoft Outlook Voice Access lets users who are enabled for Exchange Unified Messaging (UM) access their mailboxes by using analog, digital, or cellular telephones."
---

# Setting up Outlook Voice Access

Microsoft Outlook Voice Access lets users who are enabled for Exchange Unified Messaging (UM) access their mailboxes by using analog, digital, or cellular telephones. 
  
An Outlook Voice Access user (also called a subscriber), is a user in an organization who's enabled for Unified Messaging. Subscribers use Outlook Voice Access to access their mailboxes by telephone to retrieve email, voice mail messages, personal contacts, and calendar information. 
  
## Outlook Voice Access overview
<a name="BKMK_OutlookVoiceAccessoverview"> </a>

In Microsoft Exchange UM, a UM-enabled user can call in to an internal or external telephone number that's configured on a UM dial plan to access their mailbox and use the Outlook Voice Access menu system. Using this menu, UM-enabled users can read email, listen to voice messages, interact with their Outlook calendar, access their personal contacts, and perform tasks such as configuring their Outlook Voice Access PIN and recording their voice mail greetings. 
  
Two types of users, authenticated and unauthenticated, can call in to an Outlook Voice Access number. When an unauthenticated user calls into an Outlook Voice Access number that is set on a UM dial plan, they are only able to do directory searches for users. Authenticated users, those that input their PIN, can perform directory searches and sign in to their mailbox to listen to email, calendar items, and voice mail, and to search personal contacts. When they are searching for a user in the directory or personal contacts, after the user is located, they can transfer calls to a user or ring the user's extension.
  
## Outlook Voice Access interfaces
<a name="BKMK_OutlookVoiceAccessinterfaces"> </a>

Two Unified Messaging user interfaces are available to Outlook Voice Access users: the telephone user interface (TUI) and the voice user interface (VUI) that uses Automatic Speech Recognition (ASR). 
  
Before users can use the VUI in Outlook Voice Access, it must be enabled on the UM dial plan and on the UM mailbox policy and also be enabled for the user. By default, when you create a dial plan and a UM mailbox policy and enable voice mail for a user, the user can use ASR or the Outlook Voice Access VUI to navigate menus, messages, and other options. However, even if the user is able to use the VUI, they will have to use the telephone key pad to enter their PIN, navigate personal options, and perform a directory search. The default settings are listed in the following table.
  
|**UM component**|**Default setting**|**Exchange Management Shell example to enable VUI access**|
|:-----|:-----|:-----|
|UM dial plan  <br/> |Enabled  <br/> | `Set-UMDialPlan -id MyUMDialPlan -AutomaticSpeechRecognitionEnabled $true` <br/> |
|UM mailbox policy  <br/> |Enabled  <br/> | `Set-UMMaiboxPolicy -id MyUMPolicy -AllowAutomaticSpeechRecognition $true` <br/> |
|User's mailbox  <br/> |Enabled  <br/> | `Set-UMMailbox -id tonysmith -AutomaticSpeechRecognitionEnabled $true` <br/> |
   
The following section includes scenarios that describe the VUI functionality.
  
## Outlook Voice Access scenarios
<a name="BKMK_OutlookVoiceAccessscenarios"> </a>

Here are examples of how Outlook Voice Access can be used from a telephone:
  
- **Access email** An Outlook Voice Access user places a call to an Outlook Voice Access number from a telephone and wants to access their email. The voice prompt says, "Welcome. You're connected to Microsoft Exchange. To access your mailbox, please enter your extension. To contact someone, press the pound key." After the user enters a mailbox extension number, the voice prompt says, "Please enter your PIN and press the pound key." After the user enters a PIN, the voice prompt says, "You have two new voice mails, 10 new email messages, and your next meeting is at 10:00 A.M. Please say voice mail, email, calendar, personal contacts, directory, or personal options." When the user says "Email," the voice mail system reads the message header and then the name, subject, time, and priority for the messages that are in the user's mailbox. 
    
- **Access calendar** An Outlook Voice Access user places a call to an Outlook Voice Access number from a telephone and wants to access their calendar. The voice prompt says, "Welcome. You're connected to Microsoft Exchange. To access your mailbox, please enter your extension. To contact someone, press the pound key." After the user enters a mailbox extension number, the voice prompt says, "Please enter your PIN and press the pound key." After the user enters a PIN, the voice prompt says, "You have two new voice mails, 10 new email messages, and your next meeting is at 10:00 A.M. Please say voice mail, email, calendar, personal contacts, directory, or personal options." When the user says "Calendar," the voice mail system says, "Sure, and which day should I open?" The user says, "Today's calendar." The voice mail system responds by saying, "Opening today's calendar." The voice mail system reads each calendar appointment for that day for the user. 
    
    > [!NOTE]
    > If a Mailbox server running the Microsoft Exchange Unified Messaging service encounters a corrupted calendar item in a user's mailbox, it will fail to read the item, return the caller to the Outlook Voice Access main menu, and skip reading any additional meetings that may be scheduled for the rest of the day. 
  
- **Access voice mail** An Outlook Voice Access user places a call to an Outlook Voice Access number from a telephone and wants to access voice mail. The voice prompt says, "Welcome. You're connected to Microsoft Exchange. To access your mailbox, please enter your extension. To contact someone, press the pound key." After the user enters a mailbox extension number, the voice prompt says, "Please enter your PIN and press the pound key." After the user enters a PIN, the voice prompt says, "You have two new voice mails, 10 new email messages, and your next meeting is at 10:00 A.M. Please say voice mail, email, calendar, personal contacts, directory, or personal options." The user says "Voice mail," and the voice mail system reads the message header and then the name, subject, time, and priority for the voice messages that are in the user's mailbox. 
    
    > [!NOTE]
    > If speech recognition is enabled, users can access their UM-enabled mailbox using speech input. Subscribers can also use touchtone, also known as dual tone multi-frequency (DTMF), by pressing 0. Speech recognition isn't enabled for PIN input. 
  
- **Locate a user in the directory** An Outlook Voice Access user places a call to an Outlook Voice Access number from a telephone and wants to locate a person in the directory by spelling their email alias. The voice prompt says, "Welcome. You're connected to Microsoft Exchange. To contact someone, press the pound key." The user presses the pound key, and then uses touchtone inputs to spell the SMTP address of the person. 
    
    > [!NOTE]
    > The directory search feature with an Outlook Voice Access number isn't speech-enabled. Users can spell the name of the person they want to contact only by using touchtone inputs. 
  
    > [!IMPORTANT]
    > In some companies (especially in East Asia), office telephones may not have letters on the keys of the telephone. This makes the spell-the-name feature that uses the touchtone interface almost impossible to use without a working knowledge of the key mappings. By default, Unified Messaging uses the E.161 key mapping. For example, 2=ABC, 3=DEF, 4=GHI, 5=JKL, 6=MNO, 7=PQRS, 8=TUV, 9=WXYZ. 
  
    When inputting a combination of letters and numbers, for example, Mike1092, the numeric digits are mapped to themselves. For an email alias of Mike1092 to be entered correctly, the user must press the numbers 64531092. Also, for characters other than A-Z and 0-9, there isn't a telephone key equivalent. Therefore, these characters shouldn't be entered. For example, the email alias jim.wilson would be entered as 546945766. Even though there are 10 characters to be input, the user enters only 9 digits because there's no digit equivalent for the period (.).
    
## Distribution groups and contact groups
<a name="BKMK_Distributiongroupsandcontactgroups"> </a>

Users can use Outlook Voice Access to send or forward a voice message, an email message, or a meeting request. They can send or forward the message or meeting request to any of the following:
  
- A person in their personal Contacts folder
    
- A person in their organization's shared address book
    
- A contact group they've created in their Contacts folder
    
- A distribution group included in their organization's shared address book
    
They can send messages and meeting requests by using the VUI (if ASR has been turned on) or by using touchtone inputs on their telephone keypad. They can also use Outlook Voice Access to listen to details about a group, including the members of the group.
  
> [!NOTE]
> If a user tries to send a message to a group (either a distribution group in their shared address book or a contact group in their personal Contacts folder) that doesn't include any members, the voice mail system won't give them the option to send or forward the message or meeting request. If they try to add a group with no members as one of the recipients of a message or meeting request that they're creating over the phone, the voice mail system won't add the group to the message, and will say "The message could not be sent because the contact does not appear to have a valid email address." 
  
## Choosing a language
<a name="BKMK_Choosingalanguage"> </a>

Users can't change the language that Outlook Voice Access uses to speak to them and that they use when they reply to it. The voice mail system tries to find and use the best match for the language the user chose when they signed in to Microsoft Outlook Web App or the language they chose on the regional settings in Outlook Web App. If the language they chose isn't supported by Outlook Voice Access, the voice mail system will use the same language that callers hear when they're prompted to leave a voice message.
  
## Controlling Outlook Voice Access features
<a name="BKMK_ControllingOutlookVoiceAccessfeatures"> </a>

By default, when users dial in to Outlook Voice Access, they can use the telephone to access their calendar, email, and personal contacts, and to search the directory. You can use the Shell to prevent users from accessing one or more of these features when they use Outlook Voice Access to access their mailbox. When you modify Outlook Voice Access features on a UM mailbox policy, your changes affect all users who are associated with the UM mailbox policy. You can also disable some features on a single user's mailbox, although other features can only be disabled on a UM mailbox policy and aren't available on an individual mailbox.
  
> [!NOTE]
> You can use only the Shell to modify the Outlook Voice Access TUI settings for UM-enabled mailboxes or UM mailbox policies. 
  
 **UM mailbox policy settings** You can disable users' access to the following Outlook Voice Access features on a UM mailbox policy: 
  
- Automatic Speech Recognition
    
- PIN-less access to voice mail
    
- Voice responses to other messages
    
- TUI access to their calendar
    
- TUI access to the directory
    
- TUI access to their email
    
- TUI access to their personal Contacts
    
 **UM-enabled mailbox settings** You can disable a user's access to the following Outlook Voice Access features on the user's mailbox: 
  
- TUI access to the calendar
    
- TUI access to email
    
- Automatic Speech Recognition
    
You can prevent users from receiving voice mail, but let them retain the ability to access their mailbox using Outlook Voice Access. You can enable a user for UM and configure the user's mailbox with an extension number that isn't currently being used by another user in the organization.
  

