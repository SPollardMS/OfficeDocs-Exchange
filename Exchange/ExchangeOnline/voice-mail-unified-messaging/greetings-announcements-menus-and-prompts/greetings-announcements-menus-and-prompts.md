---
title: "Voice mail greetings, announcements, menus, and prompts in Exchange Online"
ms.author: tonysmit
author: tonysmit
manager: scotv
ms.date: 6/24/2018
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 7a518db5-2ece-48a8-b745-477928e32283
description: "When you install Unified Messaging (UM), a common set of default audio files used for the voice mail system and for menu prompts, greetings, and informational announcements is installed. Although you can create a fully functional UM auto attendant or dial plan that uses only the default audio prompts, these prompts are too generic to serve as an acceptable public interface for many companies. This topic discusses the system and menu prompts, greetings, and informational announcements that are used by UM dial plans and auto attendants and how they're used when callers access the voice mail system."
---

# Voice mail greetings, announcements, menus, and prompts in Exchange Online

When you install Unified Messaging (UM), a common set of default audio files used for the voice mail system and for menu prompts, greetings, and informational announcements is installed. Although you can create a fully functional UM auto attendant or dial plan that uses only the default audio prompts, these prompts are too generic to serve as an acceptable public interface for many companies. This topic discusses the system and menu prompts, greetings, and informational announcements that are used by UM dial plans and auto attendants and how they're used when callers access the voice mail system.
  
## Overview of audio prompts and greetings
<a name="overview"> </a>

These system audio files or prompts should never be replaced. However, UM enables you to customize UM dial plan and auto attendant welcome greetings, main menu prompts, and informational announcements.
  
The following table summarizes the prompts and greetings used with UM dial plans.
  
**Audio prompts for UM dial plans**

|**Prompts and greetings**|**Description**|
|:-----|:-----|
|System prompts  <br/> |Must not be modified.  <br/> |
|Welcome greeting  <br/> |The default welcome greeting is a system prompt that is played by default. However, you can use a customized greeting file that you create.  <br/> |
|Informational announcement  <br/> |By default, informational announcements are disabled. If you enable an informational announcement, you must specify a customized greeting file.  <br/> |
   
The following table summarizes the prompts and greetings used with UM auto attendants.
  
**Audio prompts for UM auto attendants**

|**Prompts and greetings**|**Description**|
|:-----|:-----|
|System prompts  <br/> |Must not be modified.  <br/> |
|Business hours menu prompts  <br/> |By default, business hours menu prompts are enabled and a system prompt is played. However, you can use a customized greeting file that you create.  <br/> |
|Non-business hours menu prompts  <br/> |By default, non-business hours menu prompts are enabled and a system prompt is played. However, you can use a customized greeting file that you create.  <br/> |
|Business hours greeting  <br/> |By default, a business hours greeting is enabled and a system prompt is played. However, you can use a customized greeting file that you create. This is also known as a welcome greeting.  <br/> |
|Non-business hours greeting  <br/> |By default, a non-business hours greeting is enabled and a system prompt is played. However, you can use a customized greeting file that you create. This is also known as a welcome greeting.  <br/> |
|Informational announcement  <br/> |By default, informational announcements are disabled. If you enable an informational announcement, you must specify a customized greeting file.  <br/> |
   
## System prompts
<a name="systemprompts"> </a>

Unified Messaging uses a set of default audio prompts for Outlook Voice Access, dial plans, and auto attendants. Hundreds of system prompts for each language are available. Unified Messaging plays the audio files for these system prompts to callers when they access the voice mail system. The following are some examples of these system prompts:
  
- "Please enter your PIN."
    
- "To access your mailbox, enter your extension."
    
- "To contact someone, press the # key."
    
- "Spell the name of the person you are calling, last name first." 
    
- "To reach a specific person, just tell me the name."
    
> [!CAUTION]
> Modifying any UM system prompts isn't supported. 
  
## UM dial plan greetings and announcements
<a name="greetandannounce"> </a>

After you create a UM dial plan, you have the option to use the audio files for the default system prompts or to create customized audio files that can be used with UM dial plans.
  
UM dial plans have a welcome greeting and an optional informational announcement you can modify. The welcome greeting is used when an Outlook Voice Access user or another caller calls an Outlook Voice Access number. The callers hear a default welcome greeting that says, "Welcome, you are connected to Microsoft Exchange." You might want to change this default greeting and provide an alternative welcome greeting specific to your company, for example, "Welcome to Outlook Voice Access for Woodgrove Bank." If you customize this greeting, you can record the customized greeting and save it as a .wav file, and then you can configure the dial plan to use this customized greeting. 
  
Unified Messaging allows for an informational announcement to follow the welcome greeting. By default, there is no informational announcement configured. However, you may want to provide one for callers. You can use the informational announcement for general announcements that change more often than the welcome greeting or for announcements required by corporate compliance policies. When it's important that the whole informational announcement is heard, you can configure it to be uninterruptible. This prevents a caller from pressing a key or speaking a command to interrupt and stop the informational announcement.
  
The following table describes the UM dial plan greetings and informational announcements.
  
**UM dial plan greetings and informational announcements**

|**Greeting**|**Default example**|**Customized example**|
|:-----|:-----|:-----|
|Welcome greeting  <br/> |"Welcome, you are connected to Microsoft Exchange."  <br/> |"Welcome to Outlook Voice Access for Woodgrove Bank."  <br/> |
|Informational announcement  <br/> |By default, an informational announcement isn't configured.  <br/> |"By using this system you agree to adhere to all corporate policies when you are accessing this system."  <br/> |
   
When you are customizing and configuring greetings and announcements, make sure the language setting configured on the UM dial plan is the same as the language of the custom prompts you create. If not, a caller may hear a message or greeting in one language and another message or greeting in a different language.
  
## UM auto attendant greetings, announcements, and menu prompts
<a name="menuprompts"> </a>

As with UM dial plans, UM auto attendants have a welcome greeting, an optional informational announcement, and an optional custom menu prompt. You can configure different versions of the welcome greeting and menu prompt for business hours and non-business hours. You can modify all of them. 
  
The welcome greeting is the first thing a caller hears when a UM auto attendant answers the call. By default, this says, "Welcome to the Microsoft Exchange auto attendant." The audio file that is played for the call is the default system prompt for the UM auto attendant. However, you may want to provide an alternative greeting specific to your company, for example, "Thank you for calling Woodgrove Bank." To customize this welcome greeting, record the customized greeting and save it as a .wav file, and then configure the auto attendant to use this customized greeting. As with the welcome greetings, you can also customize the menu prompts. 
  
Unified Messaging also allows for an informational announcement to follow a business hours greeting or a non-business hour greeting. By default, no informational announcement is configured, but you may want to provide one to callers. The informational announcement can announce your company's business hours, for example, "Our business hours are 8:00 A.M. to 5:00 P.M., Monday through Friday, and 8:30 A.M. to 1:00 P.M. on Saturday." The informational announcement can also provide information required for compliance with corporate policies, for example, "Calls may be monitored for training purposes." When it's important that the whole informational announcement is heard, you can configure it to be uninterruptible. This prevents the caller from pressing a key or speaking a command to interrupt and stop the informational announcement.
  
The following table describes the UM auto attendant greetings and informational announcements.
  
**UM auto attendant greetings, informational announcement, and menu prompts**

|**Greeting**|**Default example**|**Customized example**|
|:-----|:-----|:-----|
|Business hours greeting  <br/> |"Welcome to the Microsoft Exchange auto attendant."  <br/> |"Thank you for calling Woodgrove Bank."  <br/> |
|Non-business hours greeting  <br/> |No default non-business hours greeting is played until you configure the business hours for the auto attendant. However, the business hours greeting is played for callers during all times of the day.  <br/> |"You have reached Woodgrove Bank after business hours. Our business hours are from 8:00 A.M. until 5:00 P.M., Monday through Friday."  <br/> |
|Informational announcement  <br/> |By default, informational announcements aren't configured.  <br/> |"Calls may be monitored for training purposes."  <br/> |
|Business hours main menu prompt  <br/> |No default business hours main menu prompt will be played until you configure key mappings on the auto attendant.  <br/> |"For technical support, press or say 1. For corporate offices and administration, press or say 2. For sales, press or say 3."  <br/> |
|Non-business hours main menu prompt  <br/> |No default non-business hours main menu prompt will be played until you configure key mappings and the business hours schedule on the auto attendant.  <br/> |"Your call is very important to us. However, you have reached Woodgrove Bank after business hours. If you want to leave a message, please press or say 1, and we will return your call as soon as possible."  <br/> |
   
As with UM dial plans, make sure the language setting configured on the UM auto attendant is the same as the language of the custom greetings you create and is set to the same language as the UM dial plan. If not, a caller may hear a message or greeting in one language and another message or greeting in a different language.
  
## Customizing greetings, announcements, and menu prompts, and navigation menus
<a name="customizing"> </a>

By default, when you create a UM auto attendant, the business and non-business hours greetings or prompts aren't configured and no key mappings are defined for business or non-business hours main menu prompts. To correctly configure customized greetings and prompts for an auto attendant, you must:
  
- Configure business and non-business hours on the **Business hours** page. 
    
- Create the greeting audio (.wav or .wma) files that will be used for the business and non-business hours welcome greetings.
    
- Configure the business and non-business hours welcome greetings on the **Greetings** page. 
    
- Create the greeting files that will be used for the business and non-business hours main menu prompt greetings.
    
- Configure the business and non-business hours main menu prompt greetings on the **Greetings** page. 
    
- Enable and configure the business and non-business hours menu navigation on the **Menu navigation** page. 
    

