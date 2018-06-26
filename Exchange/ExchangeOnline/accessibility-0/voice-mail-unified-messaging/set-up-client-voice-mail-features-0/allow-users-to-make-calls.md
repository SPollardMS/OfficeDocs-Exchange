---
title: "Allow users to make calls"
ms.author: tonysmit
author: tonysmit
manager: scotv
ms.date: 6/24/2018
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: b6e696ce-c848-475b-a598-9035677497e2
description: "Outdialing is the process by which users call in to a UM dial plan using an Outlook Voice Access number and place or transfer a call to an internal or external telephone number. Unified Messaging uses many outdialing settings to dial calls for users. To configure outdialing, you must configure dialing rules, dialing rule groups, and dialing authorizations on Unified Messaging (UM) dial plans and then authorize outdialing on UM dial plans, UM mailbox policies, and auto attendants. You can also configure UM dial plans to have dialing or access codes, a national number prefix, and in-country/region or international number formats that enable you to control outdialing in your organization. This topic discusses dialing rules, dialing rule groups, and dialing authorizations and how they are used to authorize and control outdialing for your organization."
---

# Allow users to make calls

Outdialing is the process by which users call in to a UM dial plan using an Outlook Voice Access number and place or transfer a call to an internal or external telephone number. Unified Messaging uses many outdialing settings to dial calls for users. To configure outdialing, you must configure dialing rules, dialing rule groups, and dialing authorizations on Unified Messaging (UM) dial plans and then authorize outdialing on UM dial plans, UM mailbox policies, and auto attendants. You can also configure UM dial plans to have dialing or access codes, a national number prefix, and in-country/region or international number formats that enable you to control outdialing in your organization. This topic discusses dialing rules, dialing rule groups, and dialing authorizations and how they are used to authorize and control outdialing for your organization. 
  
## Overview
<a name="overview"> </a>

Outdialing happens when:
  
-  A call is placed to an external telephone number. 
    
- A call is transferred to an auto attendant.
    
- A call is transferred to a user in your organization.
    
- A UM-enabled user uses the Play on Phone feature.
    
For outdialing to work correctly, the following settings must be configured correctly: 
  
- **Dialing rules** Dialing rules define the number that is dialed by the UM-enabled user and the number that will be dialed by the Private Branch eXchange (PBX) or IP PBX. 
    
- **Dialing rule groups** Dialing rule groups determine the types of calls that users within a dialing group can make. 
    
- **Dialing authorizations** Dialing authorizations determine the restrictions that will be applied to prevent users from incurring unnecessary telephone charges or from dialing long-distance calls. 
    
To enable outdialing for users who call in to a dial plan or an auto attendant, you must:
  
- Make sure the VoIP gateways represented by a UM IP gateway that is linked with a dial plan will allow outgoing calls.
    
- Create dialing rule groups by creating dialing rules on the UM dial plan.
    
- Add dialing authorizations for in-country/region and international dialing rule groups on the UM dial plan, UM mailbox policy, or auto attendant associated with the same dial plan as the UM IP gateway.
    
## Types of users
<a name="umenabled"> </a>

Two types of users can use the outdialing feature in Unified Messaging: authenticated and unauthenticated. All users who call in to a UM auto attendant are unauthenticated. When users call in to an Outlook Voice Access number, they're considered unauthenticated because they haven't provided their extension number and PIN and signed in to their mailbox. Users are authenticated after they provide their extension number and PIN and successfully sign in to their mailbox.
  
When users call in to an Outlook Voice Access number configured on a UM dial plan and try to place or transfer a call without signing in to their mailbox, only the UM dial plan outdialing settings are applied to the call. When anonymous or unauthenticated users call in to a UM auto attendant, both the outdialing settings configured on the auto attendant and the outdialing settings configured on the dial plan associated with the auto attendant are applied to the call. 
  
When users call in to the Outlook Voice Access number configured on a dial plan and successfully sign in to their mailbox, they become authenticated users. When they're authenticated, the outdialing call settings use the dialing rules and dialing authorization settings on the UM mailbox policy that's linked to those users.
  
## Outdialing settings
<a name="settings"> </a>

You need to configure several settings to apply outdialing rules for your organization. In addition to configuring the UM dial plans, UM auto attendants, and UM mailbox policies that you've created with the correct dialing rules and dialing authorizations, you need to configure access codes, number prefixes, and number formats on the UM dial plans. The following outdialing settings are configured on dial plans, auto attendants, and UM mailbox policies:
  
- Outside line, country/region, and international access codes
    
- National number prefixes
    
- In-country/region and international number formats
    
- Configured in-country/region and international dialing rule groups
    
- Allowed in-country/region and international dialing rule groups
    
- Dialing rule entries
    
- Dialing authorizations
    
For you to successfully configure outdialing for your organization, you first need to understand how each component can be used with outdialing and how the component must be configured. The following table introduces each component that needs to be configured on UM dial plans, UM auto attendants, and UM mailbox policies before outdialing will work correctly.
  
**Outdialing components**

|**Component**|**Description**|
|:-----|:-----|
|Dial codes, number prefixes, and number formats  <br/> |UM uses dial codes, number prefixes, and number formats to determine the correct number to dial when placing an outgoing call. You can configure dial codes, number prefixes, and number formats to restrict outgoing calls for users who dial in to a UM auto attendant associated with a UM dial plan or for users who dial in to an Outlook Voice Access number configured on the dial plan.  <br/> |
|Dialing rule groups  <br/> |Dialing rule groups are created to enable telephone numbers to be modified before they're sent to the PBX for outgoing calls. Dialing rule groups remove numbers from or add numbers to telephone numbers being called by UM. For example, you can create a dialing rule group that automatically adds a 9 as a prefix to a 7-digit telephone number to provide access to an outside line. In this example, users who place outgoing calls don't have to dial the 9 before the telephone number to reach someone external to the organization.  <br/> Each dialing rule group contains dialing rules that determine the types of in-country/region and international calls that users within a dialing rule group can make. Dialing rule groups apply to the users who are associated with a UM dial plan or to UM auto attendants and UM mailbox policies associated with the UM dial plan. Each dialing rule group must contain at least one dialing rule.  <br/> |
|Dialing rule entries  <br/> |A dialing rule is used to determine the types of calls that users within a dialing rule group can make. When you create a dialing rule group, you configure one or more dialing rules.  <br/> When you configure each dialing rule, you must enter the dialing rule name, number pattern to transform (number mask), and dialed number. You can also enter a comment. Comments can be used to describe how the dialing rule will be used or to describe a group of users to whom the dialing rule will apply. When you add a number mask and the dialed number to a dialing rule, you can substitute the letter x for a digit in a telephone number, for example, 91425xxxxxxx. You can also use an asterisk (\*) symbol as a wildcard character, for example, 91425\*.  <br/> |
|Dialing authorizations  <br/> |A dialing authorization uses dialing rule groups to apply dialing restrictions for users who are associated with a specific UM mailbox policy, dial plan, or auto attendant. They can also be used when you want to let users place calls to in-country/region or international telephone numbers.  <br/> After you create dialing rules on a UM dial plan, you add the dialing rule group to a UM mailbox policy, dial plan, or auto attendant. After the dialing rule group is added to a UM mailbox policy, all settings or rules defined will apply to UM-enabled users who are linked with the UM mailbox policy.  <br/> |
   
## Configuring outdialing
<a name="configuring"> </a>

A dialing rule group is a collection of one or more dialing rules configured on a UM dial plan. Two types of dialing rule groups can be configured on a UM dial plan: in-country/region and international. In-country/region dialing rule groups apply to telephone numbers dialed within the same country or region. International dialing rule groups apply to international telephone numbers dialed from one country or region to another country or region. 
  
Each UM dial plan can contain one or more dialing rule groups. To apply a dialing rule group to a set of users, after you create the dialing rule group, you must add it to the list of allowed dialing rule groups on the UM dial plan and on the UM auto attendants and UM mailbox policies associated with the UM dial plan.
  
Dialing rule groups enable you to specify dialing rules that you want to apply to a group of UM-enabled users who fall into a specific category. For example, you can use dialing rule groups to specify which group of users can place international calls and which group can make only in-state or local calls. You can create a dialing rule group using the Exchange Administration Center (EAC) or the **Set-UMDialPlan** cmdlet in the Exchange Management Shell. When you create a dialing rule group, you must define at least one dialing rule for the group. 
  
When a user dials a telephone number, UM takes the number and looks for a match in the dialing rules. If a match is found, UM uses the dialing rule to determine the number to dial by looking at the telephone number or digits listed in the **Dialed Number** section of the dialing rule. The number listed in the **Dialed Number** box of the dialing rule will be dialed. 
  
The following table shows an example of dialing rule groups and dialing rules. In this example, Local-Calls-Only and Low-Rate are the dialing rule groups that have been created. The dialing rule group Local-Calls-Only has two dialing rules: 91425\* and 91206\*, and the dialing rule group Low-Rate also has two dialing rules: 91509\* and 91360\*.
  
**Dialing rule groups and dialing rules**

|**Name**|**NumberMask**|**DialedNumber**|**Comment**|
|:-----|:-----|:-----|:-----|
|Local-Calls-Only  <br/> |91425\*  <br/> |91\*  <br/> |Local calls  <br/> |
|Local-Calls-Only  <br/> |91206\*  <br/> |91\*  <br/> |Local calls  <br/> |
|Low-Rate  <br/> |91509\*  <br/> |9\*  <br/> |In-state calls  <br/> |
|Low-Rate  <br/> |91360\*  <br/> |9\*  <br/> |In-state calls  <br/> |
   
For example, when a user dials 9-1-425-555-1234, UM dials 4255551234. UM removes any nonnumeric characters (in this example, the hyphens) and applies the number mask from the dialing rule. In this example, UM applies the number mask 91\*. This tells UM not to dial the 9 or the 1, but to dial all the other numbers in the telephone number that appear to the right of the number 1. This includes all the numbers represented by the asterisk (\*).
  
You can use the EAC or the Shell to create and configure single or multiple in-country/region and international dialing rule groups and dialing rules. However, if you're creating many or complex dialing rule groups and dialing rules, you can use a comma-separated value (.csv) file in the Shell. You can import or export a list of dialing rule groups and dialing rules.
  
To import a list of dialing rule groups and dialing rules that you've defined in a .csv file, run the **Set-UMDialPlan** cmdlet, as follows. 
  
```
Set-UMDialPlan "MyUMDialPlan" -ConfiguredInCountryOrRegionGroups $(IMPORT-CSV c:\dialrules\InCountryRegion.csv)
```

To retrieve a list of the dialing rule groups configured on a UM dial plan, run the **Get-UMDialPlan** cmdlet, as follows. 
  
```
(Get-UMDialPlan -id "MyUMDialPlan").ConfiguredInCountryOrRegionGroups | EXPORT-CSV C:\incountryorregion.csv
```

The .csv file must be created and saved in the correct format. Each line in the .csv file represents one dialing rule. However, each dialing rule is configured on the same dialing rule group. Each rule in the file will have four sections separated by commas. These sections are name, number mask, dialed number, and comment. Each section is required, and you must enter the correct information in each section except for the comment section. There should be no spaces between the text entry and the comma for the next section, nor should there be any blank lines between the rules or at the end. The following is an example of a .csv file that can be used to create in-country/region dialing rule groups and dialing rules.
  
 **Name,NumberMask,DialedNumber,Comment**
  
 **Low-rate,91425xxxxxxx,9xxxxxxx,Local call**
  
 **Low-rate,9425xxxxxxx,9xxxxxxx,Local call**
  
 **Low-rate,9xxxxxxx,9xxxxxxx,Local call**
  
 **Any,91\*,91\*,Open access to in-country/region numbers**
  
 **Long-distance,91408\*,91408\*,long distance**
  
The following is an example of a .csv file that can be used to create international dialing rule groups and dialing rule entries.
  
 **Name,NumberMask,DialedNumber,Comment**
  
 **International, 901144\*, 901144\*, international call**
  
 **International, 901133\*, 901133\*, international call**
  
## Applying configured dialing rule groups
<a name="applying"> </a>

Dialing rule groups are created on a UM dial plan. You can create in-country/region or international dialing rule groups using the EAC or the **Set-UMDialPlan** cmdlet in the Shell. After you create the appropriate dialing rule groups on a UM dial plan and define the dialing rules, you can apply the dialing rule groups that you created to a UM dial plan, a UM auto attendant, or to users who are associated with a UM mailbox policy, and authorize outdialing depending on how the user accesses the voice mail system. 
  
You can apply the dialing rule groups that you created on a UM dial plan to the following:
  
- **Same dial plan** The settings will apply to all users who call in to an Outlook Voice Access number but don't sign in to their mailbox. To apply an in-country/region dialing rule group named  `MyAllowedDialRuleGroup` to the same dial plan, use the Shell **Set-UMDialPlan** cmdlet, as follows. 
    
  ```
  Set-UMDialPlan -Identity MyUMDialPlan -AllowedInCountryOrRegionGroups MyAllowedDialRuleGroup
  ```

- **Single or multiple UM mailbox policies ** The settings that are configured on a UM mailbox policy will apply to all users who are linked with that UM mailbox policy. The settings configured on a UM mailbox policy apply to users who call in to an Outlook Voice Access number and sign in to their mailbox. To apply an in-country/region dialing rule group named  `MyAllowedDialRuleGroup` to a single UM mailbox policy, use the **Dialing authorization** page on the UM mailbox policy in the EAC or use the **Set-UMMailboxPolicy** cmdlet in the Shell, as follows. 
    
  ```
  Set-UMMailboxPolicy -Identity MyUMMailboxPolicy -AllowedInCountryOrRegionGroups MyAllowedDialRuleGroup
  ```

- **Single or multiple auto attendants associated with the UM dial plan ** This will apply to all users who call in to a UM auto attendant. To apply the in-country/region dialing rule group named  `MyAllowedDialRuleGroup` to a single UM auto attendant, use the **Dialing authorization** page on the auto attendant in the EAC or the **Set-UMAutoAttendant** cmdlet in the Shell, as follows. 
    
  ```
  Set-UMAutoAttendant -Identity MyUMAutoAttendant -AllowedInCountryOrRegionGroups MyAllowedDialRuleGroup
  ```

The following table summarizes the way that dialing rule groups are applied in Unified Messaging.
  
**Applying outdialing rules**

|**Caller type**|**Scope**|**Outdialing settings applied**|
|:-----|:-----|:-----|
|Outlook Voice Access number  <br/> |User calls a dial plan Outlook Voice Access number and signs in to the mailbox  <br/> |UM mailbox policy  <br/> |
|Anonymous caller  <br/> |User calls a dial plan Outlook Voice Access number  <br/> |UM dial plan  <br/> |
|Anonymous caller  <br/> |User calls an auto attendant pilot or extension number  <br/> |UM auto attendant  <br/> |
|Caller from inside the organization  <br/> |User calls the Play on Phone number  <br/> |UM mailbox policy  <br/> |
   
## Applying dialing rules
<a name="applyingdialing"> </a>

The outdialing process happens when:
  
- Unified Messaging places a call to an external telephone number for a caller.
    
-  Unified Messaging transfers a call to an auto attendant. 
    
-  Unified Messaging transfers a call to a user in your organization. 
    
- A UM-enabled user uses the Play on Phone feature.
    
In each outdialing scenario, UM will apply the dialing rules that have been configured, and then place the call for the user. However, depending on the scenario and how the call is initiated by the user, UM may apply only some of the dialing rules to the telephone number being dialed. In other outdialing scenarios, UM may apply all the outdialing rules configured to the telephone number being dialed. 
  

