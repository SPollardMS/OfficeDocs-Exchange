---
title: "Change the audio codec"
ms.author: tonysmit
author: tonysmit
manager: scotv
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.service: exchange-online
localization_priority: Normal
ms.assetid: 139b2ccd-28c5-46c0-9050-777f4f59aade
description: "Unified Messaging can use one of four codecs for creating voice mail messages: MP3, Windows Media Audio (WMA), Group System Mobile (GSM) 06.10, and G.711 Pulse Code Modulation (PCM) Linear. By default, when you create a Unified Messaging (UM) dial plan, the UM dial plan uses the MP3 audio codec to record voice messages. The MP3 audio format is a popular audio format that is used across multiple operating systems, email clients, and MP3 players. After the UM dial plan is created, you can configure the UM dial plan to use one of the other audio formats including the WMA, GSM 06.10, or G.711 PCM Linear audio codecs. To listen to the voice message, a mobile phone or computer must have a compatible audio software application installed."
---

# Change the audio codec

Unified Messaging can use one of four codecs for creating voice mail messages: MP3, Windows Media Audio (WMA), Group System Mobile (GSM) 06.10, and G.711 Pulse Code Modulation (PCM) Linear. By default, when you create a Unified Messaging (UM) dial plan, the UM dial plan uses the MP3 audio codec to record voice messages. The MP3 audio format is a popular audio format that is used across multiple operating systems, email clients, and MP3 players. After the UM dial plan is created, you can configure the UM dial plan to use one of the other audio formats including the WMA, GSM 06.10, or G.711 PCM Linear audio codecs. To listen to the voice message, a mobile phone or computer must have a compatible audio software application installed.
  
For additional tasks related to UM dial plans, see [UM Dial Plan Procedures](http://technet.microsoft.com/library/1bda77c8-c4e2-4ae0-a001-76ae029bf843.aspx).
  
## What do you need to know before you begin?

- Estimated time to complete: Less than 1 minute.
    
- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "UM dial plans" entry in the [Unified Messaging Permissions](http://technet.microsoft.com/library/d326c3bc-8f33-434a-bf02-a83cc26a5498.aspx) topic. 
    
- Before you perform these procedures, confirm that a UM dial plan has been created. For detailed steps, see [Create a UM dial plan](create-um-dial-plan.md).
    
- For information about keyboard shortcuts that may apply to the procedures in this topic, see **Keyboard shortcuts in the Exchange admin center**.
    
> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612),[Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351).. 
  
## What do you want to do?

### Use the EAC to change the audio codec on a Unified Messaging dial plan

1. In the EAC, navigate to **Unified Messaging** \> **UM dial plans**.
    
2. In the list view, select the UM dial plan you want to modify, and then click **Edit**![Edit icon](../../media/ITPro_EAC_EditIcon.gif).
    
3. On the **UM dial plan** page, click **Configure**.
    
4. In **Settings**, under **Audio codec**, use the drop-down list to select one the following:
    
  - MP3 
    
  - WMA
    
  - GSM
    
  - G711
    
5. Click **Save**.
    
### Use the Shell to change the audio codec on a Unified Messaging dial plan

This example sets the audio codec on a UM dial plan named  `MyUMDialPlan` to G.711. 
  
```
Set-UMDialPlan -Identity MyUMDialPlan -AudioCodec G711
```

This example sets the audio codec on a UM dial plan named  `MyUMDialPlan` to WMA. 
  
```
Set-UMDialPlan -Identity MyUMDialPlan -AudioCodec Wma
```


