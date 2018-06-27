---
title: "Authorize calls using dialing rules"
ms.author: tonysmit
author: tonysmit
manager: scotv
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.service: exchange-online
localization_priority: Normal
ms.assetid: 4c18bc07-f55c-42b7-81c1-729878aa93aa
description: "By default, users aren't able to place outgoing calls. To specify the kinds of calls users can make, you first create dialing rules, then authorize groups of these dialing rules on UM dial plans, UM mailbox policies, or UM auto attendants. Before you can authorize dialing rule groups, you have to define dialing rules on a UM dial plan. For details, see Create dialing rules for users."
---

# Authorize calls using dialing rules

By default, users aren't able to place outgoing calls. To specify the kinds of calls users can make, you first create dialing rules, then authorize groups of these dialing rules on UM dial plans, UM mailbox policies, or UM auto attendants. Before you can authorize dialing rule groups, you have to define dialing rules on a UM dial plan. For details, see [Create dialing rules for users](create-dialing-rules.md).
  
Each dialing rule that you create will contain the types of calls or number patterns that you want to give users access to. You can allow different types of users to make different types of calls. The calls you allow can be within a country or region, or they can be international. 
  
To authorize or restrict dialing, the following settings must be configured correctly: 
  
- **Dialing rules** Dialing rules define the number that UM-enabled users dial and the number that will be sent from Unified Messaging and dialed by the Private Branch eXchange (PBX) or IP PBX. You create a dialing rule group by adding a dialing rule. After you create a dialing rule group, you add it to the list of authorized calls for an in-country/region or international dialing rule group. 
    
- **Dialing rule groups** Dialing rule groups determine the types of calls that users within the dialing group can make. 
    
- **Dialing authorizations** Dialing authorizations are used to determine the restrictions that will be applied to prevent users from incurring unnecessary telephone charges or from dialing long-distance calls. 
    
## How do I authorize a dialing rule group?

Where you authorize dialing rule groups depends on the types of callers that you want to allow to make outgoing calls. For example, if you want only Outlook Voice Access users to place outgoing calls, you would create your dialing rules and then authorize those dialing rule groups to the UM mailbox policy that the Outlook Voice Access users are linked to. The following table shows how to authorize calls for different types of callers. 
  
|**Type of caller**|**Authorize dialing rule groups here**|
|:-----|:-----|
|Unauthenticated callers who call in to an Outlook Voice Access number and don't enter a PIN  <br/> |UM dial plan. For details, see [Authorize calls for users in a dial plan](authorize-calls-for-users-in-a-dial-plan.md).  <br/> |
|Authenticated callers who call in to an Outlook Voice Access number and enter a PIN  <br/> |UM mailbox policy for the caller. For details, see [Authorize calls for a group of users](authorize-calls-for-a-group-of-users.md).  <br/> |
|Unauthenticated callers who call in to a telephone number that's configured on a UM auto attendant  <br/> |UM auto attendant. For details, see [Authorize calls for auto attendant callers](authorize-calls-for-auto-attendant-callers.md).  <br/> |
   
Depending on which users you're authorizing to make outbound calls, you'll use the **Dialing authorization** page in the Exchange admin center (EAC) for the dial plan, the auto attendant, or the UM mailbox policy. 
  

