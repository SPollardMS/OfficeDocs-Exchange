---
title: "Select the language for an auto attendant"
ms.author: tonysmit
author: tonysmit
manager: scotv
ms.date: 6/24/2018
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 3a1c1ec0-c726-41fb-a294-59faab205609
description: "You can configure the default prompt language setting on a Unified Messaging (UM) auto attendant. The language setting available on a UM auto attendant enables you to configure the default prompt language on the auto attendant. When you're using the default system prompts for the auto attendant, this is the language that the caller hears when the auto attendant answers the incoming call. This language setting affects only the default system prompts that are provided after you have installed the Mailbox server that is running the Microsoft Exchange Unified Messaging service. This setting doesn't affect custom prompts that are configured on an auto attendant. The languages that are available are based on the Unified Messaging language packs that are installed on the Mailbox server."
---

# Select the language for an auto attendant

You can configure the default prompt language setting on a Unified Messaging (UM) auto attendant. The language setting available on a UM auto attendant enables you to configure the default prompt language on the auto attendant. When you're using the default system prompts for the auto attendant, this is the language that the caller hears when the auto attendant answers the incoming call. This language setting affects only the default system prompts that are provided after you have installed the Mailbox server that is running the Microsoft Exchange Unified Messaging service. This setting doesn't affect custom prompts that are configured on an auto attendant. The languages that are available are based on the Unified Messaging language packs that are installed on the Mailbox server.
  
Each auto attendant you create will initially use English (en-US) as the default language. The English (en-US) language pack is installed by default on all versions of Microsoft Exchange 2013 and can't be removed. If you want to select another language, for example, German (de-DE), you must first download the German UM language pack .exe file from [Exchange Server 2013 UM Language Packs](https://go.microsoft.com/fwlink/?LinkId=266542) and install the UM language pack on the Mailbox server by using the UMLanguagePack.de-de.exe installation file. After you've installed the UM language pack, you can set the default language to a language other than English (en-US) on UM auto attendants. 
  
## What do you need to know before you begin?

- Estimated time to complete: Less than 1 minute.
    
- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "UM auto attendants" entry in the [Unified Messaging Permissions](http://technet.microsoft.com/library/d326c3bc-8f33-434a-bf02-a83cc26a5498.aspx) topic. 
    
- Before you perform these procedures, confirm that a UM dial plan has been created. For detailed steps, see [Create a UM dial plan](../../voice-mail-unified-messaging/connect-voice-mail-system/create-um-dial-plan.md).
    
- Before you perform these procedures, confirm that a UM auto attendant has been created. For detailed steps, see [Create a UM auto attendant](../../voice-mail-unified-messaging/automatically-answer-and-route-calls/create-a-um-auto-attendant.md).
    
- For information about keyboard shortcuts that may apply to the procedures in this topic, see **Keyboard shortcuts in the Exchange admin center**.
    
> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612),[Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351).. 
  
## What do you want to do?

### Use the EAC to configure the default language setting

1. In the EAC, navigate to **Unified Messaging** \> **UM dial plans**.
    
2. In the list view, select the UM dial plan you want to modify, and then on the toolbar, click **Edit**![Edit icon](../../media/ITPro_EAC_EditIcon.gif).
    
3. On the **UM dial plan** page, under **UM Auto Attendants**, select the UM auto attendant you want to change, and then click **Edit**![Edit icon](../../media/ITPro_EAC_EditIcon.gif).
    
4. On the **General** page, under **Language for automated voice interface**, select the required language from the drop-down list.
    
5. Click **Save** to accept your changes. 
    
### Use the Shell to configure the default language setting

This example sets the default language on the UM auto attendant  `MyUMAutoAttendant` to English (Great Britain). 
  
```
Set-UMAutoAttendant -Identity MyUMAutoAttendant -Language en-GB
```

This example sets the default language on the UM auto attendant  `MyUMAutoAttendant` to German. 
  
```
Set-UMAutoAttendant -Identity MyUMAutoAttendant -Language de-DE
```


