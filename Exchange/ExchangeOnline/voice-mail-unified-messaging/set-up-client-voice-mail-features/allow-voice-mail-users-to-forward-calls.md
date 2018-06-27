---
title: "Allow voice mail users to forward calls"
ms.author: tonysmit
author: tonysmit
manager: scotv
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.service: exchange-online
localization_priority: Normal
ms.assetid: 1f8e0a53-3d9d-4f8c-9be3-9f1e2a4347a3
description: "The Call Answering Rules feature was first introduced in Exchange 2010. Using this feature, users who are enabled for voice mail can control how their incoming calls should be handled. Call answering rules are applied to incoming calls similar to the way Inbox rules are applied to incoming email messages."
---

# Allow voice mail users to forward calls

The Call Answering Rules feature was first introduced in Exchange 2010. Using this feature, users who are enabled for voice mail can control how their incoming calls should be handled. Call answering rules are applied to incoming calls similar to the way Inbox rules are applied to incoming email messages. 
  
Call answering rules are created and configured by a voice mail-enabled user using Outlook or Outlook Web App. The rules are stored along with other voice settings in the user's mailbox. A total of nine call answering rules can be set up for each UM-enabled mailbox. These rules are independent of the Inbox rules that are set up by users, and don't take up part of the Inbox rules storage quota for the user.
  
By default, when a user is enabled for Unified Messaging (UM) and voice mail, no call answering rules are configured. If an incoming call is answered by the voice mail system, the caller is prompted to leave a voice message or if the caller doesn't get prompted, the caller will also be able to leave a voice message for the user.
  
If your users want to have the voice mail system just answer their incoming calls and record a voice message, you don't have to create any call answering rules. However, if you decide that you want to set up conditions or actions, you can set them up by using the **Call Answering Rules** section on the **Voice Mail** page in Outlook Web App. Use the **Call Answering Rules** section to create, edit, and delete call answering rules. 
  
## Anatomy of call answering rules

A call answering rule consists of two parts: conditions and actions. You can associate one or more conditions with a single call answering rule. The call answering rule will only be processed if all the conditions for the rule are met. You can also associate one or more actions with a single call answering rule. These actions determine what options will be offered to the caller when the call answering rule is processed. 
  
Call Answering Rules supports the following conditions:
  
- Who the incoming call is from
    
- The time of day
    
- Calendar free/busy status
    
- Whether automatic replies are turned on for email
    
The following actions are supported:
  
- Find me
    
- Transfer the caller to someone else
    
- Leave a voice message
    
If a user records a custom greeting for a call answering rule, they must include the menu option as part of the custom greeting when they configure the call answering rule. If they don't, Unified Messaging won't generate a menu prompt that lets the caller know what his or her choices are. After the custom greeting is played, the server will wait for the caller's input. If a menu option isn't included in the greeting, the caller won't input anything and the server will prompt them, asking "Are you still there?"
  
## Conditions

Conditions are rules that you can apply to call answering rules. By using a combination of conditions, you can create multiple call answering rules that will trigger when the conditions are met. To create a default rule that will be applied to every call, you create a rule that doesn't contain any conditions.
  
There are three conditions that can be used when you set up call answering rules, including:
  
- Caller ID
    
- Time-of-the-day
    
- Free/busy status
    
## Actions

Actions are used to define what you want to happen when a condition is met. The two kinds of actions are:
  
- Find Me
    
- Call Transfer
    
 **Adding a Find Me action**
  
When a caller selects Find Me, the voice mail system will attempt to locate you at up to two different phone numbers, and then connect the caller to you if you're available at one of the phone numbers.
  
- You can specify text that will be read to the caller. For example, if you enter "Urgent Matters" to inform your callers that they should only select this action if they have important things to discuss with you, the voice mail system will say "For Urgent Matters, press the 1 key."
    
- You have to associate the Find Me action with the number on the telephone keypad that the caller will press to select this action. In the example above, the **1** telephone key is the number callers will press to reach you at one of the phone number or numbers you specify. 
    
- Next, you have to specify the one or two phone numbers that the voice mail system will dial. If you specify two telephone numbers, the second number will be dialed if you're not available at the first. Each phone number that you specify has an associated duration. The duration is the time period during which the voice mail system will try to dial the phone number before it moves on to the next number. Or, if you can't be contacted, the voice mail system will go back to the options menu.
    
- After you've entered this information, click **Apply** to save the Find Me settings. 
    
 **Adding Call Transfer actions**
  
By setting a Call Transfer action, you provide callers with the option to be transferred to another person's phone number. There are several options that are available when you want to transfer an incoming call to another phone or contact.
  
- You can specify text that will be read to the caller. For example, you can enter "Important Matters" to inform your callers that they should choose this option if they have an important matter to discuss and need to speak to someone.
    
- You have to associate the **Call Transfer** action with the number on the telephone keypad that the caller will press to select this action. 
    
- When you choose the Call Transfer action, you have to specify a person or phone number for the caller to be transferred to. You can choose a phone number or select a contact to be called when the caller presses the correct key on the telephone keypad. If you specify a contact who's within your company directory, the voice mail system will try to transfer the call to the extension number of that contact. 
    
- In addition to specifying a person or number for the caller to be transferred to, you also need to specify the number on the telephone keypad that the caller will press to select the Call Transfer action.
    
- After you've entered this information, click **Apply** to save the Call Transfer settings. 
    
## Selecting a call answering rule for each incoming call

After you create and configure Call Answering Rules, Unified Messaging will:
  
1. Determine whether the user has created any call answering rules. If not, UM will offer the caller the option of leaving a voice message.
    
2. If one or more call answering rules have been configured, UM will evaluate each of these rules. The first rule whose conditions are met will be processed.
    
3. After evaluating all the rules, if UM doesn't find a rule whose conditions are met, UM will ask the caller to leave a voice message.
    
## Dialing rules

Depending on how a call answering rule is configured, an incoming call may result in a call transfer. When this happens, the transfer target phone number will be subject to the dialing rules and restrictions on the UM mailbox policy that the called party is associated with. For more information about outdialing and dialing rules and restrictions, see [Allow users to make calls](allow-users-to-make-calls.md). 
  
### Enabling/disabling Call Answering Rules

By default, Call Answering Rules is automatically enabled for UM-enabled users. However, you can disable call answering rules for users by disabling the feature on a UM mailbox policy or the user's mailbox. For details about how to enable or disable Call Answering Rules, see the following topics:
  
- [Call answering rules in the same mailbox policy](call-answering-rules-in-the-same-mailbox-policy.md)
    
- [Call answering rules](call-answering-rules.md)
    

