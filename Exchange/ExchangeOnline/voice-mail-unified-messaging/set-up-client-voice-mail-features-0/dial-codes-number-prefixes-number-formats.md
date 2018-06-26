---
title: "Dial codes, number prefixes, and number formats"
ms.author: tonysmit
author: tonysmit
manager: scotv
ms.date: 6/24/2018
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 26d61e55-f8dd-4d25-81f1-78a87cf88bad
description: "You can configure several dialing codes that Unified Messaging (UM) uses to dial internal and external calls for UM-enabled users. Frequently, you want to configure a dial plan together with the dialing or access codes, a national number prefix, or in-country/region or international number formats so that you can control outdialing for users in your organization. This topic discusses dial codes, number prefixes, and number formats and how you can use them to control outdialing for your organization."
---

# Dial codes, number prefixes, and number formats

You can configure several dialing codes that Unified Messaging (UM) uses to dial internal and external calls for UM-enabled users. Frequently, you want to configure a dial plan together with the dialing or access codes, a national number prefix, or in-country/region or international number formats so that you can control outdialing for users in your organization. This topic discusses dial codes, number prefixes, and number formats and how you can use them to control outdialing for your organization.
  
## Overview
<a name="overview"> </a>

Outdialing is the process in which users call in to a UM dial plan or UM auto attendant and then place a call to an internal or external telephone number. When a user calls in to a UM dial plan or a UM auto attendant and then places a call, Unified Messaging uses the settings configured on the dial plan, auto attendant, and UM mailbox policies to place the call. UM places an outgoing call in the following situations: 
  
- When it places a call to an external telephone number for a caller
    
- When it transfers a call to an auto attendant
    
- When it transfers a call to a user (either UM-enabled or not) in your organization
    
- When a UM-enabled user uses the Play on Phone feature
    
Two types of users use outdialing: authenticated users and unauthenticated users. Unauthenticated users call in to an Outlook Voice Access number configured on a UM dial plan but don't sign in to their mailbox. Unauthenticated users also call in to a number configured on a UM auto attendant. Authenticated users call in to an Outlook Voice Access number and successfully sign in to their mailbox. When users call in to an Outlook Voice Access number, they are initially considered unauthenticated because they haven't provided their extension number and PIN and signed in to their mailbox. They are authenticated after they provide their extension number and PIN and successfully sign in to their mailbox.
  
When an unauthenticated user calls in to a UM auto attendant and places a call using outdialing, the outdialing settings configured on the UM dial plan and the auto attendant are used. When an unauthenticated user calls in to an Outlook Voice Access number configured on a dial plan, only the settings configured on the dial plan are used. When a user has successfully signed in to their mailbox, configuration settings from the dial plan and the UM mailbox policy associated with the authenticated user are applied to the authenticated user.
  
You need to configure several settings to control outdialing for your organization. To control outdialing, you need to configure the UM dial plans, auto attendants, and UM mailbox policies in Unified Messaging. The following settings can be configured on UM dial plans, auto attendants, and UM mailbox policies to control outdialing:
  
- Outside line, in-country/region, and international access codes
    
- National number prefixes
    
- In-country/region and international number formats
    
- In-country/region and international dialing rule groups
    
- Allowed in-country/region and international dialing rule groups
    
- Dialing rule entries
    
You configure access codes, number prefixes, and number formats on a UM dial plan on the **Dial Codes** page in the Exchange admin center (EAC). You can also configure the settings using the **Set-UMDialPlan** cmdlet in the Exchange Management Shell. You can choose to configure all the settings, none of the settings, or only some of the settings. Each setting controls a specific part of the outdialing process. 
  
UM uses access codes, number prefixes, and number formats to determine the correct number to dial. They can be configured to restrict outgoing calls for users who dial in to a UM auto attendant associated with a UM dial plan or who dial in to the Outlook Voice Access number configured on the dial plan. 
  
For more information about outdialing in Unified Messaging, see [Dial codes, number prefixes, and number formats](dial-codes-number-prefixes-number-formats.md).
  
## Outside line access code
<a name="outsidelineaccesscode"> </a>

You can configure an outside line access code, also known as a trunk access code, on each dial plan that you create. This is the number used to gain access to an outside telephone line. This number is also configured on the Private Branch eXchanges (PBXs) or IP PBXs in your organization. In most telephony networks, users dial the number 9 to gain access to an outside line and place a call to an external telephone number.
  
You should configure an outside line access code on each dial plan that you create. This dialing code will apply to all users who are linked with a UM mailbox policy that's linked with the UM dial plan. When a caller who's linked with the dial plan places a call and the dial plan dials the outgoing call, UM adds the outside line access code (usually 9) in front of the dialed number string so that the PBX or IP PBX can dial the number correctly. If you don't configure the outside line access code, the PBX or IP PBX may not recognize the number that's sent.. For example, as stated earlier, in many organizations, the access code that users dial to gain access to an outside line is 9, and this is configured on a PBX or IP PBX. Unified Messaging must add the outside line access code (9) before the telephone number string for the PBX or IP PBX to correctly dial the outgoing number. If you configure the dialing code so that Unified Messaging will add the outside line access code, Unified Messaging will be able to use the outside line access code to access an outside line before it dials the external telephone number string. The dialing code that you configure will apply to all users who are linked with a UM mailbox policy linked with the UM dial plan.
  
## National number prefix
<a name="nationalnumberprefix"> </a>

The national number prefix and the country/region code can also be configured on a UM dial plan. Unified Messaging uses the number you enter to dial the correct national number prefix or country/region code when a user dials an outgoing call destined within the same country/region or an international call. For example, when a user from North America places an outgoing international call to Europe, UM will add the national number prefix before the number string that it sends to the PBX or IP PBX to place the outgoing call. The number 1 is used as the national number prefix for North America.
  
## In-Country/region access code
<a name="countryregionaccesscode"> </a>

A country/region code can be configured on a UM dial plan. The country/region access code consists of the digits associated with a specific country or region. Unified Messaging uses the country/region access code to dial the correct telephone number when a call is placed to a telephone number from inside the same country or region. UM will add this number before the number string that it sends to the PBX or IP PBX when it places the outgoing call. For example, UM will add the number 1 to a call placed from the United States and destined for the United States. For the United Kingdom, the country/region code is 44.
  
## International access code
<a name="internationalaccesscode"> </a>

An international access code can be configured on a UM dial plan. The international access code consists of the digits used to access international telephone numbers. Unified Messaging uses the international access code to dial the correct international access code when a call is placed from a telephone number within a country/region and the number being dialed is located in another country/region. UM will add this number before the number string that it sends to the PBX or IP PBX when it places the outgoing call. For example, UM will use 011 as the international access code for the United States. For Europe, the international access code is 00.
  
## In-Country/region and international number formats
<a name="incountryregionandintlfmts"> </a>

You can configure the incoming call configuration for country/region and international number formats on a UM dial plan. After you configure these settings, Unified Messaging will be able to recognize incoming calls from inside a country/region and internationally between UM dial plans within the same organization. You can also add number formats for incoming calls that are placed within a single dial plan. Configuring these options enables your organization to save money by preventing outgoing calls that shouldn't be made by users from inside your organization, and helps to prevent toll fraud. UM will use the information that you configure to examine the number format of the incoming call and verify that the number pattern matches before it accepts the call. For example, you may have multiple dial plans inside an organization. If you have one dial plan for the United States and another for the United Kingdom, you may want to let users in the United States dial plan have UM place calls to users who are located in the United Kingdom dial plan, but not let the users in the United States dial plan place calls directly to other countries/regions or internationally.
  

