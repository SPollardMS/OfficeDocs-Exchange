---
title: "Set the default language on a dial plan"
ms.author: tonysmit
author: tonysmit
manager: scotv
ms.date: 6/24/2018
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 7a1d2e7e-4053-40af-9ec1-ec714df12ad4
description: "You can set the default language for a Unified Messaging (UM) dial plan. Each dial plan you create will initially use English (en-US) as the default language. The English (en-US) language pack is installed on all versions of Microsoft Exchange Server 2013 and can't be removed."
---

# Set the default language on a dial plan

You can set the default language for a Unified Messaging (UM) dial plan. Each dial plan you create will initially use English (en-US) as the default language. The English (en-US) language pack is installed on all versions of Microsoft Exchange Server 2013 and can't be removed.
  
If you want to select another language as the default language, for example, German (de-DE), you must first download the German UM language pack .exe file from [Exchange Server 2013 UM Language Packs](https://go.microsoft.com/fwlink/p/?LinkID=266542) and install that language pack on the Mailbox server by using the UMLanguagePack.de-de.exe installation file. After you've installed the language pack, you can set the default language to a language other than English (en-US) on your UM dial plans. 
  
## What do you need to know before you begin?

- Estimated time to complete: Less than 1 minute.
    
- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "UM dial plans" entry in the [Unified Messaging Permissions](http://technet.microsoft.com/library/d326c3bc-8f33-434a-bf02-a83cc26a5498.aspx) topic. 
    
- Before you perform these procedures, confirm that a UM dial plan has been created. For detailed steps, see [Create a UM dial plan](../../voice-mail-unified-messaging/connect-voice-mail-system/create-um-dial-plan.md).
    
- For information about keyboard shortcuts that may apply to the procedures in this topic, see **Keyboard shortcuts in the Exchange admin center**.
    
> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612),[Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351).. 
  
## What do you want to do?

### Use the EAC to set the default language on a UM dial plan

1. In the EAC, navigate to **Unified Messaging** \> **UM dial plans**.
    
2. In the list view, select the UM dial plan that you want to modify, and then, on the toolbar, click **Edit**![Edit icon](../../media/ITPro_EAC_EditIcon.gif).
    
3. On the **UM dial plan** page, click **Configure**.
    
4. On the **Settings** page, under **Audio language**, select the language you want to set from the drop-down list.
    
5. Click **Save** to accept your changes. 
    
### Use the Shell to set the default language on a UM dial plan

This example sets the default language on a UM dial plan named  `MyUMDialPlan` to German. 
  
```
Set-UMDialPlan -Identity MyUMDialPlan -DefaultLanguage de-DE
```

This example sets the default language on a UM dial plan named  `MyUMDialPlan` to Japanese. 
  
```
Set-UMDialPlan -Identity MyUMDialPlan -DefaultLanguage ja-JP
```

This example sets the default language on a UM dial plan named  `MyUMDialPlan` to Australian English. 
  
```
Set-UMDialPlan -Identity MyUMDialPlan -DefaultLanguage en-AU
```


