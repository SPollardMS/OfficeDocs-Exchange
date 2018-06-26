---
title: "Enable a customized business hours greeting"
ms.author: tonysmit
author: tonysmit
manager: scotv
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: a2272b7d-de88-4d3f-81e6-ad81f0ee6c5e
description: "You can enable a customized business hours greeting for a Unified Messaging (UM) auto attendant. The business hours greeting is the first thing callers hear when a UM auto attendant answers their call during business hours. You'll probably want to customize the greeting."
---

# Enable a customized business hours greeting

You can enable a customized business hours greeting for a Unified Messaging (UM) auto attendant. The business hours greeting is the first thing callers hear when a UM auto attendant answers their call during business hours. You'll probably want to customize the greeting.
  
 Unified Messaging includes a default system prompt for use during business hours. Although the default system prompt mustn't be replaced or changed, you may want to provide an customized greeting. You can create a customized greeting in the .wav or .wma file format to be used when callers call in to a UM auto attendant during business hours. For example, "You've reached Woodgrove Bank." 
  
If you want to include the name of your organization or business as part of the default greeting, you can enter the name in the **Business name** box on the UM auto attendant. For details, see [Enter a business name](enter-a-business-name.md).
  
For additional management tasks related to UM auto attendants, see [UM auto attendant procedures](um-auto-attendant-procedures.md).
  
## What do you need to know before you begin?

- Estimated time to complete: 5 minutes.
    
- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "UM auto attendants" entry in the [Unified Messaging Permissions](http://technet.microsoft.com/library/d326c3bc-8f33-434a-bf02-a83cc26a5498.aspx) topic. 
    
- Before you perform these procedures, confirm that a UM dial plan has been created. For detailed steps, see [Create a UM dial plan](../../voice-mail-unified-messaging/connect-voice-mail-system/create-um-dial-plan.md).
    
- Before you perform these procedures, confirm that a UM auto attendant has been created. For detailed steps, see [Create a UM auto attendant](create-a-um-auto-attendant.md).
    
- Create a .wav or .wma file to be used for the greeting.
    
- For information about keyboard shortcuts that may apply to the procedures in this topic, see **Keyboard shortcuts in the Exchange admin center**.
    
> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612),[Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351).. 
  
## What do you want to do?

### Use the EAC to enable a customized business hours greeting

1. In the EAC, navigate to **Unified Messaging** \> **UM dial plans**. In the list view, select the UM dial plan you want to change, and then click **Edit**![Edit icon](../../media/ITPro_EAC_EditIcon.gif).
    
2. On the **UM Dial Plan** page, under **UM Auto Attendants**, select the UM auto attendant for which you want to enable a customized business hours greeting, and then click **Edit**![Edit icon](../../media/ITPro_EAC_EditIcon.gif).
    
3. On the **UM Auto Attendant** page, \> **Greetings**, under **Business hours greeting** click **Change**, and then click **Browse** to locate the customized business hours greeting file you created before you started this procedure. 
    
    > [!IMPORTANT]
    > The file you use for the greeting must be a .wav or .wma file. 
  
4. After you've located the file, click **Open**, and then click **Save**.
    
### Use the Shell to enable a customized business hours greeting

This example enables the business hours greeting that uses a customized greeting named  `GreetingFile.wav` for the UM auto attendant  `MyUMAutoAttendant`.
  
```
Set-UMAutoAttendant -Identity MyUMAutoAttendant -BusinessHoursWelcomeGreetingEnabled $true -BusinessHoursWelcomeGreetingFilename GreetingFile.wav
```

This example configures a UM auto attendant named  `MyUMAutoAttendant` to have business hours configured to be 10:45 to 13:15 (Sunday), 09:00 to 17:00 (Monday), and 09:00 to 16:30 (Saturday) and holiday times and their associated greetings configured to be "  `New Year`" on January 2, 2013, and " `Building Closed for Construction`" from April 24, 2013 through April 28, 2013.
  
```
Set-UMAutoAttendant -Identity MyUMAutoAttendant -BusinessHoursSchedule 0.10:45-0.13:15,1.09:00-1.17:00,6.09:00-6.16:30 -HolidaySchedule "New Year,newyrgrt.wav,1/2/2013","Building Closed for Construction,construction.wav,4/24/2013,4/28/2013"
```

This example configures a UM auto attendant named  `MyAutoAttendant` and enables business hours key mappings so that when callers press 1, they're forwarded to another UM auto attendant named  `SalesAutoAttendant`. When they press 2, they're forwarded to extension number 12345 for  `Support`, and when they press 3, they're sent to another auto attendant that plays an audio file. 
  
```
Set-UMAutoAttendant -Identity MyAutoAttendant - BusinessHoursKeyMappingEnabled $true -BusinessHoursKeyMapping "1,Sales,,SalesAutoAttendant","2,Support,12345","3,Directions,,,directions.wav"
```


