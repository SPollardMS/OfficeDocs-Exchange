---
title: "Enable or disable directory lookups"
ms.author: tonysmit
author: tonysmit
manager: scotv
ms.date: 5/10/2016
ms.audience: ITPro
ms.topic: article
ms.service: exchange-online
localization_priority: Normal
ms.assetid: c0768815-8578-4385-8d4c-7d1e40304cec
description: "You can enable directory lookups so that callers who call in to a Unified Messaging (UM) auto attendant can look up names in the directory using their telephone keypad but not be able to search the directory using voice inputs. This setting is enabled by default. If this setting is disabled, callers won't be able to search the directory for a specific person using touchtone or voice commands."
---

# Enable or disable directory lookups

You can enable directory lookups so that callers who call in to a Unified Messaging (UM) auto attendant can look up names in the directory using their telephone keypad but not be able to search the directory using voice inputs. This setting is enabled by default. If this setting is disabled, callers won't be able to search the directory for a specific person using touchtone or voice commands.
  
For additional management tasks related to UM auto attendants, see [UM auto attendant procedures](um-auto-attendant-procedures.md).
  
> [!NOTE]
> Outlook Voice Access users can't use Automatic Speech Recognition (ASR) or speech inputs to locate users in the directory, they can only use DTMF or touchtone inputs. 
  
## What do you need to know before you begin?

- Estimated time to complete: Less than 1 minute.
    
- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "UM auto attendants" entry in the [Unified Messaging Permissions](http://technet.microsoft.com/library/d326c3bc-8f33-434a-bf02-a83cc26a5498.aspx) topic. 
    
- Before you perform these procedures, confirm that a UM dial plan has been created. For detailed steps, see [Create a UM dial plan](../../voice-mail-unified-messaging/connect-voice-mail-system/create-um-dial-plan.md).
    
- Before you perform these procedures, confirm that a UM auto attendant has been created. For detailed steps, see [Create a UM auto attendant](create-a-um-auto-attendant.md).
    
- For information about keyboard shortcuts that may apply to the procedures in this topic, see **Keyboard shortcuts in the Exchange admin center**.
    
> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612),[Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351).. 
  
## What do you want to do?

### Use the EAC to enable or disable directory lookups

1. In the EAC, navigate to **Unified Messaging** \> **UM dial plans**. In the list view, select the UM dial plan you want to change, and then click **Edit**![Edit icon](../../media/ITPro_EAC_EditIcon.gif).
    
2. On the **UM Dial Plan** page, under **UM Auto Attendants**, select the UM auto attendant for which you want to enable or disable directory lookups, and then click **Edit**![Edit icon](../../media/ITPro_EAC_EditIcon.gif).
    
3. On the **UM Auto Attendant** page \> **Address book and operator access**, under **Options for searching the address book**, select the check box next to **Allow callers to search for users by name or alias** to enable callers to search for users. To disable callers from searching for users, clear this check box. 
    
4. Click **Save**.
    
### Use the Shell to enable or disable directory lookups

This example disables directory lookups on a UM auto attendant named  `MyUMAutoAttendant`.
  
```
Set-UMAutoAttendant -Identity MyUMAutoAttendant -NameLookupEnabled $false
```


