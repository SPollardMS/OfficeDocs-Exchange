---
title: "Set up a UM auto attendant"
ms.author: tonysmit
author: tonysmit
manager: scotv
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.service: exchange-online
localization_priority: Normal
ms.assetid: 0a3492f8-8aba-4904-96fd-6e023175012a
description: "In addition to allowing users access to voice mail, Unified Messaging (UM) allows you to create one or more UM auto attendants depending on the needs of your organization. UM auto attendants can be used to create a voice menu system for an organization that lets external and internal callers locate, place, or transfer calls to company users or departments in an organization."
---

# Set up a UM auto attendant

In addition to allowing users access to voice mail, Unified Messaging (UM) allows you to create one or more UM auto attendants depending on the needs of your organization. UM auto attendants can be used to create a voice menu system for an organization that lets external and internal callers locate, place, or transfer calls to company users or departments in an organization.
  
For additional management tasks related to UM auto attendants, see [UM auto attendant procedures](um-auto-attendant-procedures.md).
  
## Auto attendants

In telephony or Unified Messaging environments, an automated attendant or auto attendant menu system transfers callers to the extension of a user or department without the intervention of a receptionist or an operator. In many auto attendant systems, a receptionist or operator can be reached by pressing or saying zero. Some auto attendant systems use message-only information menus and voice menus so an organization can provide business hours, directions to the premises, information about job opportunities, and answers to other frequently asked questions. After the message plays, callers are forwarded to the receptionist or operator, or they can return to the main menu.
  
Although auto attendants can be very useful, if they aren't designed and configured correctly, they can confuse and frustrate callers. For example, especially in large organizations, when auto attendants aren't designed correctly, callers can be led through a lengthy series of questions and menu prompts before they're finally transferred to a person to answer their questions.
  
## How do I set up an auto attendant?

In the Exchange Administration Center (EAC), you set up and manage UM auto attendants to automatically answer calls to your organization and allow callers to self-select different options using the keys on their telephone. You can have just one UM auto attendant that provides basic menu navigation for callers to your organization, or you can have multiple nested and branching auto attendants that provide a richer experience for your callers. However, in both cases, you must plan and set up your auto attendants carefully.
  
To plan and create a new UM auto attendant structure, you need to do the following:
  
1. Decide whether you want to allow users to interact with the auto attendant using speech inputs.
    
2. Decide which language you want to use for your main auto attendant and whether you need to create other auto attendants to support more languages.
    
3. Decide on the business and non-business hours for the auto attendant and set the business hours using **Business hours**. Though it's not required, you can also decide on the holiday schedule for this auto attendant.
    
    > [!NOTE]
    > You should also set the time zone on the attendant. 
  
4. Decide whether you want standard system-generated business and non-business hours greetings or to create custom recordings for them.
    
    If you want to use custom greetings, plan and record your business and non-business hour greetings to play to callers during business and non-business hours. If you need to, you can also create a custom informational announcement greeting. For example, for your business hours greeting you could use "Welcome to Contoso. For English, press or say 1, for Spanish, press or say 2." For your non-business hours greeting, you could record the following script: "Welcome to Contoso. Our office is currently closed. We will be open on Monday at 8:00 am."
    
5. Plan your auto attendant structure based on your business needs. For example, one organization may be a multinational business with offices in both Germany and the UK, and thus need an auto attendant structure based on multiple languages. Another organization might have its corporate office at one site, Sales located at another site, and Customer Service located at a third site, and thus need an auto attendant that directly relates to the structure of the organization.
    
6. Decide if you'll need DTMF fallback auto attendants or other auto attendants to use when auto attendant voice commands don't work.
    
7. Plan the menu navigation for business hours and non-business hours. For each auto attendant, including DTMF auto attendants, you'll need to plan and configure menu prompts and menu navigation entries. You'll need to do this for both business and non-business hours.
    
8. The following is an example of a worksheet you could use to plan non-business hours menu navigation.
    
|****Key****|****Prompt/Navigation menu entry name****|****Response to record****|
|:-----|:-----|:-----|
|1  <br/> |Language selection to use English.  <br/> |"Press or say 1 to use English."  <br/> |
|2  <br/> |Account balance  <br/> |"Press or say 2 to get your account balance."  <br/> |
|3  <br/> |Transfer to Sales  <br/> |"Press or say 3 to be transferred to our sales department."  <br/> |
|4  <br/> |Transfer to customer service  <br/> |"Press or say 4 to be transferred to the next customer service representative."  <br/> |
|5  <br/> |Business hours  <br/> |No response needed.  <br/> |
|6  <br/> |Business location  <br/> |No response needed.  <br/> |
   
9. Using your menu navigation plan, record prompts that inform callers what they can do. For example, depending on the auto attendant structure for the non-business hours menu navigation shown in the table, you might record the following script: "To leave a message for Sales, press one. For our business hours, press two. For our address, press three."
    
10. Determine how callers will access your organization. Consider how they will search for and contact users in your organization. Also consider how to transfer callers, including how they'll get to a live person or organization representative, and whether callers will access an operator during business and non-business hours.
    
11. Determine what calls you'll allow callers to make when they're using a specific auto attendant. For example, whether you want to allow callers to make calls to users in a single dial plan, to any extension, or whether you'll allow them to make calls outside your organization.
    
12. After you've planned your auto attendant settings, greetings and menu navigation, and created audio files that contain your recorded greetings, menu navigation prompts, and menu navigation responses, you're ready to create and configure your auto attendant. Here's how:
    
  - [Create a UM auto attendant](create-a-um-auto-attendant.md)
    
  - [Manage a UM auto attendant](manage-um-auto-attendant.md)
    
13. If you've created the auto attendant structure and settings, enable the UM auto attendant so it can start accepting calls.
    

