---
title: "Disable a UM IP gateway"
ms.author: tonysmit
author: tonysmit
manager: scotv
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: fe3a8797-1230-49cb-a839-ccec238266b6
description: "By default, when you create a Unified Messaging (UM) IP gateway, the status of the UM IP gateway is enabled. After the UM IP gateway is created, you can disable the operation of the gateway by setting its status to disabled. After you disable the UM IP gateway, the Voice over IP (VoIP) gateway, IP Private Branch eXchange (PBX), or session border controller (SBC) that it's configured to use can no longer process incoming Unified Messaging calls."
---

# Disable a UM IP gateway

By default, when you create a Unified Messaging (UM) IP gateway, the status of the UM IP gateway is enabled. After the UM IP gateway is created, you can disable the operation of the gateway by setting its status to disabled. After you disable the UM IP gateway, the Voice over IP (VoIP) gateway, IP Private Branch eXchange (PBX), or session border controller (SBC) that it's configured to use can no longer process incoming Unified Messaging calls.
  
 For additional management tasks related to UM IP gateways, see [UM IP gateway procedures](um-ip-gateway-procedures.md).
  
## What do you need to know before you begin?

- Estimated time to complete: Less than 1 minute.
    
- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "UM IP gateways" entry in the [Unified Messaging Permissions](http://technet.microsoft.com/library/d326c3bc-8f33-434a-bf02-a83cc26a5498.aspx) topic. 
    
- Before you perform these procedures, confirm that a UM dial plan has been created. For detailed steps, see [Create a UM dial plan](create-um-dial-plan.md).
    
- Before you perform these procedures, confirm that a UM IP gateway has been created and is enabled. For detailed steps, see [Create a UM IP gateway](create-um-ip-gateway.md) and [Enable a UM IP gateway](enable-um-ip-gateway.md).
    
- For information about keyboard shortcuts that may apply to the procedures in this topic, see **Keyboard shortcuts in the Exchange admin center**.
    
> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612),[Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351).. 
  
## What do you want to do?

### Use the EAC to disable a UM IP gateway

1. In the EAC, navigate to **Unified Messaging** \> **UM IP Gateways**, select the UM IP gateway you want to disable, and then click the **Down arrow**![Down Arrow Icon](../../media/ITPro_EAC_DownArrowIcon.gif).
    
2. On the **Warning** page, click **Yes**.
    
### Use the Shell to disable a UM IP gateway

This example disables a UM IP gateway named  `MyUMIPGateway` and stops it from accepting incoming calls from a VoIP gateway, IP PBX, or SBC. 
  
```
Disable-UMIPGateway -Identity MyUMIPGateway
```

This example disables a UM IP gateway named  `MyUMIPGateway` and disconnects all current calls immediately. 
  
```
Disable-UMIPGateway -Identity MyUMIPGateway -Immediate $true
```


