---
title: "Create dialing rules for users"
ms.author: tonysmit
author: tonysmit
manager: scotv
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: c11e3d62-3eb1-4d7e-8741-9bede593e2df
description: "Dialing rule groups consist of dialing rule entries. Dialing rules are used to modify a phone number before sending it to an on-premises telephone system (PBX) or IP PBX for outgoing calls. Dialing rules serve two purposes:"
---

# Create dialing rules for users

Dialing rule groups consist of dialing rule entries. Dialing rules are used to modify a phone number before sending it to an on-premises telephone system (PBX) or IP PBX for outgoing calls. Dialing rules serve two purposes: 
  
- They specify the numbers that can be dialed for outgoing calls. When you create a dialing rule, you specify the number formats that can be dialed. Any number that doesn't match one of the formats you specified is rejected. If you don't set any dialing rules, callers can place calls within your organization but can't make any outgoing calls.
    
- They transform the numbers dialed before sending them out to your on-premises telephone system. Dialing rules can strip numbers from or add numbers to the number dialed. For example, you can use dialing rules to add the outside line access code for your telephone system or to add or remove the in-country/region code for long-distance or local numbers. 
    
To specify the types of outgoing calls you want to allow for a UM dial plan, you create a dialing rule group with dialing rules and then use them to authorize outgoing calls for Outlook Voice Access users and callers that dial into a UM auto attendant. You create separate dialing rule groups for in-country/region and for international calls. 
  
> [!NOTE]
> If you are integrating UM with Microsoft Lync Server, we recommend that you create at least one dialing rule group and authorize that dialing rule group on the SIP URI dial plans, UM mailbox policies, and UM auto attendants to allow all outgoing calls to be forwarded to Lync Servers. 
  
For other management tasks for outdialing, see [Allowing users to make calls procedures](allow-users-to-make-calls-procedures.md).
  
## Examples of commonly used dialing rules

||||
|:-----|:-----|:-----|
|**Number pattern** <br/> |**Dialed number** <br/> |**When would you use this dialing rule?** <br/> |
|\*  <br/> |\*  <br/> |Allow all outgoing calls.  <br/> |
|1425xxxxxxx  <br/> |91425xxxxxxx  <br/> |Prevent users from getting an internal extension or an error when they forget to dial the outside access line number.  <br/> |
|1xxxxxxxxxx  <br/> |1xxxxxxxxxx  <br/> |Allow all numbers that start with 1.  <br/> |
|xxxxxxx  <br/> |1425xxxxxxx  <br/> |Add 1 and the local area code 425 to 7-digit numbers.  <br/> |
   
## What do you need to know before you begin?

- Estimated time to complete: Less than 3 minutes.
    
- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "UM dial plans" entry in the [Unified Messaging Permissions](http://technet.microsoft.com/library/d326c3bc-8f33-434a-bf02-a83cc26a5498.aspx) topic. 
    
- Before you perform these procedures, confirm that a UM dial plan has been created. For detailed steps, see [Create a UM dial plan](../../voice-mail-unified-messaging/connect-voice-mail-system/create-um-dial-plan.md).
    
- If you will be applying dialing rule groups to UM mailbox policies, you will need to confirm that a UM mailbox policy is created. For detailed steps, see [Create a UM mailbox policy](../../voice-mail-unified-messaging/set-up-voice-mail/create-um-mailbox-policy.md).
    
- If you will be applying dialing rule groups to UM auto attendants, you will need to confirm that a UM auto attendant is created. For detailed steps, see [Create a UM auto attendant](../../voice-mail-unified-messaging/automatically-answer-and-route-calls/create-a-um-auto-attendant.md).
    
- For information about keyboard shortcuts that may apply to the procedures in this topic, see **Keyboard shortcuts in the Exchange admin center**.
    
> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612),[Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351).. 
  
## Use the EAC to create a dialing rule

1. In the EAC, navigate to **Unified Messaging** \> **UM dial plans**. In the list view, select the UM dial plan you want to change, and then click **Edit**![Edit icon](../../media/ITPro_EAC_EditIcon.gif). 
    
2. On the **UM Dial Plan** page, click **Configure**.
    
3. On the **UM Dial Plan** page \> **Dialing rules**, click **Add**![Add Icon](../../media/ITPro_EAC_AddIcon.gif) under **In-country/region dialing rules** or **International dialing rules**.
    
4. On the **New Dialing Rule** page, enter the following information: 
    
  - **Dialing rule name** Enter the name of the dialing rule group you want this rule to be a part of. To combine it with other rules, use the same group name. To create a new dialing rule group, enter a new unique name. 
    
  - **Number pattern to transform (number mask)** Enter the number pattern to transform before dialing, for example, 91425xxxxxxx. If a caller dials a number that matches, UM transforms it to the dialed number before placing the call. Enter only numbers and the wildcard (x). The number pattern is also called a number mask.
    
  - **Dialed number ** Enter the number to dial. Use only numbers and the wildcard (x), as in the number pattern 9xxxxxxx. Wildcards (x) are substituted with the digits from the original number dialed by the user. Make sure the number of wildcards in the dialed number is the same as the number of wildcards in the number pattern. 
    
  - **Comment ** Enter a comment or description for this dialing rule. You can use the comment to describe what the rule does, for example, "Add a 9 to outgoing calls." 
    
5. Click **OK** to save the dialing rule. You can continue to enter rules, using the same dialing rule group name for rules that you want to authorize together. 
    

