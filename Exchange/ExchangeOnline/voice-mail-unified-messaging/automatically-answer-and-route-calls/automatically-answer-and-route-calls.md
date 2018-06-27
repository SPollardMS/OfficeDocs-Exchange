---
title: "Automatically answer and route incoming calls"
ms.author: tonysmit
author: tonysmit
manager: scotv
ms.date: 6/24/2018
ms.audience: ITPro
ms.topic: article
ms.service: exchange-online
localization_priority: Normal
ms.assetid: d3dcd488-bd57-44cc-bdd4-ddee42a69dde
description: "Microsoft Exchange Unified Messaging (UM) enables you to create a single or multiple UM auto attendants, depending on the needs of your organization. Unlike other Unified Messaging components, such as UM dial plans and UM IP gateways, you aren't required to create UM auto attendants. However, auto attendants help internal and external callers locate users or departments that exist in an organization and transfer calls to them. This topic discusses the UM auto attendant feature found in Unified Messaging."
---

# Automatically answer and route incoming calls

Microsoft Exchange Unified Messaging (UM) enables you to create a single or multiple UM auto attendants, depending on the needs of your organization. Unlike other Unified Messaging components, such as UM dial plans and UM IP gateways, you aren't required to create UM auto attendants. However, auto attendants help internal and external callers locate users or departments that exist in an organization and transfer calls to them. This topic discusses the UM auto attendant feature found in Unified Messaging.
  
## Auto attendants
<a name="autoattendants"> </a>

In telephony or Unified Messaging environments, an automated attendant or auto attendant menu system transfers callers to the extension of a user or department without the intervention of a receptionist or an operator. In many auto attendant systems, a receptionist or operator can be reached by pressing or saying zero. The automated attendant is a feature in most modern Private Branch eXchanges (PBXs), IP PBXs, and Unified Messaging solutions.
  
Some auto attendant systems use message-only information menus and voice menus so an organization can provide business hours, directions to the premises, information about job opportunities, and answers to other frequently asked questions. After the message plays, callers are forwarded to the receptionist or operator, or they can return to the main menu.
  
In more complex auto attendant systems, the menu system can be used to search for other auto attendant menus, locate a user in the system, or transfer to another outside telephone line. The menu system can also be used to let the caller interact with the system in certain situations, such as when a student enrolls for a college class or checks a grade, or when you activate a credit card over the telephone.
  
Although auto attendants can be very useful, if they aren't designed and configured correctly, they can confuse and frustrate callers. For example, specifically in large organizations, when auto attendants aren't designed correctly, callers can be led through a lengthy series of questions and menu prompts before they are finally transferred to a person to answer their questions.
  
## UM auto attendants
<a name="umaas"> </a>

Unified Messaging enables you to create one or more UM auto attendants depending on the needs of your organization. UM auto attendants can be used to create a voice menu system for an organization that lets external and internal callers move through the UM auto attendant menu system to locate and place or transfer calls to company users or departments in an organization.
  
When anonymous or unauthenticated users call an external business telephone number, or when internal callers call a defined extension number, they are presented with a series of voice prompts that help them place a call to a user or locate a user in the organization and then place a call to that user. The UM auto attendant is a series of voice prompts or .wav files that callers hear instead of a human operator when they call an organization that has Unified Messaging. The UM auto attendant lets callers move through the menu system, place calls, or locate users by using dual tone multi-frequency (DTMF) or voice inputs. However, for Automatic Speech Recognition (ASR) or voice inputs to be used, you must enable ASR on the UM auto attendant.
  
A UM auto attendant has the following features:
  
- It provides corporate or informational greetings.
    
- It provides custom corporate menus. You can customize these menus to have more than one level.
    
- It provides a directory search function that enables a caller to search the organization's directory for a name. 
    
- It enables a caller to connect to the telephone of, or leave a message for, members of the organization.
    
There is no limit to the number of UM auto attendants you can create. Each Unified Messaging auto attendant can support an unlimited number of extensions. A UM auto attendant can reference one, and only one, UM dial plan. UM auto attendants can also reference or link to other UM auto attendants.
  
An incoming call received from an external telephone number or an internal telephone extension is passed between Exchange servers, and then sent to a UM auto attendant. The UM auto attendant is configured by the administrator to use prerecorded voice (.wav) files that are played over the telephone to the caller and that enable the caller to move through the Unified Messaging menu system. You can customize all the .wav files used when you configure a UM auto attendant to meet the needs of your organization.
  
## Auto attendants with multiple languages
<a name="multiple"> </a>

There are situations in which you may have to provide callers with auto attendants that have different languages. The language setting available on a UM auto attendant enables you to configure the default prompt language on the auto attendant. When you are using the default system prompts for the auto attendant, this is the language that the caller will hear when the auto attendant answers the incoming call. This language setting affects only the default system prompts provided. This language setting doesn't affect custom prompts configured on an auto attendant. 
  
For on-premises and hybrid deployments, when you install the U.S. English version, U.S. English is the only language available to configure on UM auto attendants. If you install a localized version, for example, Japanese, you can configure the auto attendant that you create to use Japanese or U.S. English for the default language. Additional UM language packs can be installed on a Unified Messaging server to enable you to use other default languages on an auto attendant.
  
For example, if you have a business that's based in the United States but requires a menu system that gives callers the options of U.S. English, Spanish, and French, you must first install the UM language packs that you need. In this case, if you have installed the U.S. English version, you would install the UM language packs for Spanish and French. However, because a Unified Messaging auto attendant can have only one language configured at a time, you would create four auto attendants: a main auto attendant configured to use U.S. English and then one auto attendant for each language: U.S. English, Spanish, and French. You would then configure the main auto attendant to have the appropriate key mappings or menu navigation to access the other auto attendants that you created for each language. In this example, the main auto attendant would answer the incoming call and the caller would hear, "Welcome to Contoso, Ltd. For English, press or say 1. For Spanish, press or say 2. For French, press or say 3."
  
> [!TIP]
> In Exchange UM, authenticated and non-authenticated Outlook Voice Access users can't search for users in the directory using speech inputs in any language. However, callers that call into an auto attendant can use speech inputs in multiple languages to navigate auto attendant menus and search for users in the directory. 
  
## Non-business hours and business hours custom greetings
<a name="nonandbusinesshours"> </a>

After you create a UM auto attendant, a default system prompt will be used for the non-business hours main menu prompt greeting heard by callers after the non-business hours welcome greeting is played. Although the system prompts mustn't be replaced or changed, you probably want to customize the greetings and menu prompts used with UM auto attendants. Frequently, in addition to configuring a customized non-business hours welcome greeting, you also want to create and configure a custom non-business hours main menu prompt greeting. After you configure a custom non-business hours main menu prompt greeting, you must enable key mappings on the UM auto attendant for non-business hours. 
  
A custom non-business hours main menu prompt greeting is a list of options callers hear during non-business hours. To let callers hear a non-business hours main menu prompt greeting, you first must configure the business and non-business hours schedule by using the EAC or the **Set-UMAutoAttendant** cmdlet in the Shell. For example, "You have reached Trey Research after normal business hours. If you are experiencing a medical emergency, please hang up and dial 911. To leave a message for one of our doctors, press 1. To leave a message for one of our physical therapists, press 2. To leave a general message for one of our front office coordinators, press 3. To be connected with an after hours operator, press 0." 
  
By default, when you create a UM auto attendant, the business and non-business hours greetings or prompts aren't configured and no menu navigation entries are defined for business or non-business hours main menu prompts. To correctly configure customized non-business hours main menu greetings and prompts, you must:
  
1. Configure business and non-business hours on the ** Business hours ** page. 
    
2. Create the greeting file that will be used for the non-business hours welcome greeting.
    
3. Configure the non-business hours welcome greeting on the **Greetings** page. 
    
4. Create the greeting file that will be used for the non-business hours main menu prompt greeting.
    
5. Configure the non-business hours main menu prompt greeting on the **Greetings** page. 
    
6. Enable menu navigation and add menu navigation entries on the **Menu navigation** page. 
    
## Menu navigation entries
<a name="keymappings"> </a>

If you use the default main menu prompt greeting and define a menu navigation entry or multiple menu navigation entries, the UM Text-to-Speech (TTS) engine will synthesize a main menu prompt. However, the TTS engine will only synthesize a main menu prompt if the default greeting is configured and at least one menu navigation entry has been defined. The TTS engine will not synthesize a main menu prompt if you're using a custom main menu prompt, for example, "For the sales department, press 1. For the support department, press 2." To create this main menu prompt, you must create two menu navigation entries: one named "Sales Department" and another named "Support Department", and then configure the key mapping entry to play an audio file, transfer to an extension number, or send the caller to another auto attendant.
  
When you configure menu navigation entries, you define the options and the operations that will be performed if a caller speaks a phrase while they're using a speech-enabled auto attendant or presses a key on the telephone keypad while they're using an auto attendant that isn't speech-enabled. To configure menu navigation entries for an auto attendant, you must:
  
- Enable business hours menu navigation.
    
- Add menu navigation entries.
    
- Type the name of the menu navigation entry.
    
- Select an option in the **When this key is pressed** list, and use the **Play the following audio file** box to upload the audio file to play. 
    
- Configure the action you want performed:
    
  - Transfer to this extension
    
  - Transfer to this UM auto attendant
    
  - Leave a voice message for this user
    
  - Announce business location
    
  - Announce business hours
    
## Auto attendant examples
<a name="examples"> </a>

The following examples demonstrate how you can use UM auto attendants with Unified Messaging:
  
- **Example 1** At a company called Contoso, Ltd., external customers can use three external telephone numbers: 425-555-0111 (Corporate Offices), 425-555-0122 (Product Support), and 425-555-0133 (Sales). The Human Resources, Administration, and Accounting departments have internal telephone extensions and must be accessed from the Corporate Offices UM auto attendant. 
    
    To create a UM auto attendant structure that supports this scenario, create and configure three UM auto attendants that have the appropriate external telephone numbers. Create three other UM auto attendants for each department in the Corporate Offices. You then configure each UM auto attendant based on your requirements, such as the greeting type or other navigational information.
    
- **Example 2** At a company called Contoso, Ltd., external customers call one main number for the business, 425-555-0100. When an external caller calls the external number, the UM auto attendant answers and prompts the caller by saying, "Welcome to Contoso, Ltd. Please press or say "One" to be transferred to corporate administration. Please press or say "Two" to be transferred to product support. Please press or say "Three" to be transferred to corporate information. Please press or say "Zero" to be transferred to the operator." To create a UM auto attendant structure that supports this scenario, you create a UM auto attendant that has customized extensions that route the call to the appropriate extension number. 
    

