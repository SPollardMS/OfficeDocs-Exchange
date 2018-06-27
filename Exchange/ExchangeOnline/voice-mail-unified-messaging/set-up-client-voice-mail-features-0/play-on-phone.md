---
title: "Play on Phone"
ms.author: tonysmit
author: tonysmit
manager: scotv
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.service: exchange-online
localization_priority: Normal
ms.assetid: 511e4950-340a-48cc-a020-35d11e76b993
description: "After a voice mail message arrives, users can choose either to listen to the voice mail message through their computer speakers or headphones or to use the Play on Phone feature. The Play on Phone feature is included with Microsoft Outlook and Outlook Web App, and settings for Play on Phone are available in the Play on phone section under Voice mail options. This topic discusses how a Unified Messaging (UM)-enabled user can use the Play on Phone feature."
---

# Play on Phone

After a voice mail message arrives, users can choose either to listen to the voice mail message through their computer speakers or headphones or to use the Play on Phone feature. The Play on Phone feature is included with Microsoft Outlook and Outlook Web App, and settings for Play on Phone are available in the **Play on phone** section under **Voice mail** options. This topic discusses how a Unified Messaging (UM)-enabled user can use the Play on Phone feature. 
  
## What is Play on Phone?

The Play on Phone feature lets UM-enabled users play voice messages over a telephone. If a UM-enabled user sits in an office cubicle, is using a public computer or a computer that's not enabled for multimedia, or is listening to a voice message that's confidential, the user might not want to—or be able to—listen to a voice message through their computer speakers. Alternatively, they can play back the voice mail message using any telephone, including home, office, or mobile phones. To review settings for Play on Phone, in Outlook, go to **File** \> **Info** \> **Manage voice mail**. Clicking the **Manage voice mail** button will automatically sign you in to Outlook Web App. or you can sign in to Outlook Web App using a web browser. In Outlook Web App, go to **Options** \> **Phone** \> **Voice Mail** \> **Play on Phone** section on the **Voice Mail** page. 
  
When the user clicks the Play on Phone toolbar option in the voice mail form, the **Play on Phone** dialog box appears. The **Play on Phone** box provides the controls for selecting or inputting the telephone number to use to play a voice message, starting and ending the call, and a status message for monitoring the call. If the user is linked to a SIP URI dial plan, their SIP address will appear in the **Dial** box. If they are linked to an E.164 dial plan, their full E.164 number will appear in the **Dial** box. 
  
> [!NOTE]
> Only one voice message can be played at a time. If the user tries to start a second Play on Phone call while a previous call is still in progress, an error message will appear. 
  
## Most recently used telephone number list

Users can see a list of telephone numbers they used most recently in the **Dial** box. The telephone number specified in the **Play on phone** section is always displayed as the top entry and is automatically selected for the user as the primary number. Users can use the drop-down menu to select other telephone numbers to dial instead of the telephone number that's configured as the primary number. 
  
> [!NOTE]
> To enable users who are using the Play on Phone feature to dial an external telephone number without using an outside line access code, for example 425-555-1234 instead of 9-425-555-1234, configure in-country/region dialing rules on a UM dial plan that include the following line: group1, 9xxxxxxxxxx, 91xxxxxxxxxx. After you've configured the in-country/region dialing rules, add this list to the UM mailbox policy. 
  
## Play on Phone buttons

The **Play on Phone** dialog box gives users the option to **Dial** and **Hang-up**. When the **Play on Phone** dialog box is first opened, the **Dial** button is enabled and the **Hang-up** button is disabled. After a call is placed, the **Dial** button becomes disabled until the call has ended. The call can be ended either by clicking the **Hang-up** button or by physically hanging up the telephone. Closing the **Play on Phone** dialog box using the **Close** button ends the call if one is in progress. The **Play on Phone** option and other options are also available in **Reading pane** preview in Outlook. If you open the voice mail message in a separate window, the **Play on Phone** button is on the toolbar. 
  
## Subject, sent, and status section

The bottom section of the **Play on Phone** dialog box displays the subject of the voice message, the date and time sent, and a message that displays the current state of the call. Any errors specific to the Play on Phone operation are displayed to the user in this section of the **Play on Phone** dialog box. 
  
## Phone number validation

Play on Phone performs only simple validation on input into the **Play on Phone** dialog box. Play on Phone does not validate telephone numbers. If a telephone number is not valid, Unified Messaging returns a meaningful error code to the user. 
  

