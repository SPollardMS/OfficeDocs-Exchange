---
title: "Configure a dial plan for users who have similar names"
ms.author: tonysmit
author: tonysmit
manager: scotv
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.service: exchange-online
localization_priority: Normal
ms.assetid: 14783f45-95f5-49de-8215-0a3aef7dc034
description: "You can configure a Unified Messaging (UM) dial plan to specify the information that is provided for callers when users have the same or similar names. UM uses this setting to differentiate between users who have the same or similar names and provide this information to callers. When a caller or an Outlook Voice Access user is prompted to enter letters to find a particular user, sometimes more than one name matches the caller's input. You can use one of the available options for providing the caller with more information to help them locate the user they're trying to reach."
---

# Configure a dial plan for users who have similar names

You can configure a Unified Messaging (UM) dial plan to specify the information that is provided for callers when users have the same or similar names. UM uses this setting to differentiate between users who have the same or similar names and provide this information to callers. When a caller or an Outlook Voice Access user is prompted to enter letters to find a particular user, sometimes more than one name matches the caller's input. You can use one of the available options for providing the caller with more information to help them locate the user they're trying to reach.
  
You can set this setting on both UM dial plans and UM auto attendants. When a UM auto attendant is created, it inherits this setting from the dial plan associated with the auto attendant. By default, this setting isn't configured for dial plans, so no additional information will be given to callers to help them locate the correct user.
  
> [!NOTE]
> For the information that will be included for users with similar names to work correctly, you must provide the title, department, and location information for the recipients in your Microsoft Exchange organization. 
  
For additional management tasks related to UM dial plans, see [UM Dial Plan Procedures](http://technet.microsoft.com/library/1bda77c8-c4e2-4ae0-a001-76ae029bf843.aspx).
  
## What do you need to know before you begin?

- Estimated time to complete: Less than 1 minute.
    
- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "UM dial plans" entry in the [Unified Messaging Permissions](http://technet.microsoft.com/library/d326c3bc-8f33-434a-bf02-a83cc26a5498.aspx) topic. 
    
- Before you perform these procedures, confirm that a UM dial plan has been created. For detailed steps, see [Create a UM dial plan](create-um-dial-plan.md).
    
- For information about keyboard shortcuts that may apply to the procedures in this topic, see **Keyboard shortcuts in the Exchange admin center**.
    
> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612),[Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351).. 
  
## What do you want to do?

### Use the EAC to configure a UM dial plan for users with similar names

1. In the EAC, navigate to **Unified Messaging** \> **UM dial plans**. In the list view, select the UM dial plan you want to change, and then click **Edit**![Edit icon](../../media/ITPro_EAC_EditIcon.gif).
    
2. On the **UM dial plan** page, click **Configure** \> **Transfer &amp; search**, and under **Information to include for users with the same name**, select one of the following options:
    
  - **Title** The dial plan includes each user's title when it finds two or more users with similar names. 
    
  - **Department** The dial plan includes each user's department when it finds two or more users with similar names. 
    
  - **Location** The dial plan includes each user's location when it finds two or more users with similar names. 
    
  - **None** The dial plan won't include any additional information when users have similar names. Although this is the default setting, we recommend that you include one of the available options for callers. If you don't, callers won't be able to tell the difference between two or more users with similar names. 
    
  - **Prompt For alias** The dial plan prompts the caller for the user's alias. An alias is the part of the user's email or SMTP address that is before the at (@) symbol. 
    
3. Click **Save**.
    
### Use the Shell to configure a UM dial plan for users with similar names

This example sets the information to include with users with similar names to prompt for the user's alias on a UM dial plan named  `MyDialPlan`.
  
```
Set-UMDialplan -Identity MyDialPlan -MatchedNameSelectionMethod PromptForAlias
```

This example sets the information to include with users with similar names to department on a UM dial plan named  `MyDialPlan`.
  
```
Set-UMDialplan -Identity MyDialPlan -MatchedNameSelectionMethod Department
```

This example sets the information to include with users with similar names to location on a UM dial plan named  `MyDialPlan`.
  
```
Set-UMDialplan -Identity MyDialPlan -MatchedNameSelectionMethod Location
```


