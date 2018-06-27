---
title: "Prevent Message Waiting Indicator (MWI) on a UM IP gateway"
ms.author: tonysmit
author: tonysmit
manager: scotv
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.service: exchange-online
localization_priority: Normal
ms.assetid: 7af6d094-199f-4134-a25d-9fc7e9c05fe1
description: "You can prevent voice mail notifications to users for calls received by a Unified Messaging (UM) IP gateway. If you enable this setting, the UM IP gateway can receive and send SIP NOTIFY messages for users. Message Waiting Indicator (MWI) is enabled by default and allows message waiting notifications to be sent to users, but you can turn it off depending on your needs."
---

# Prevent Message Waiting Indicator (MWI) on a UM IP gateway

You can prevent voice mail notifications to users for calls received by a Unified Messaging (UM) IP gateway. If you enable this setting, the UM IP gateway can receive and send SIP NOTIFY messages for users. Message Waiting Indicator (MWI) is enabled by default and allows message waiting notifications to be sent to users, but you can turn it off depending on your needs. 
  
A message waiting indicator notifies a user about a new or unheard voice message. It appears in the Inbox in clients such as Outlook and Outlook Web App. It can also be a text (SMS) message sent to a registered mobile phone, an outgoing call made from an Exchange server to a number that's been configured for playing new messages, or a lighted lamp on a user's desktop phone. 
  
> [!TIP]
> MWI notifications can also be enabled and disabled on a UM mailbox policy for a group of users. 
  
For additional management tasks related to UM IP gateways, see [UM IP gateway procedures](../../voice-mail-unified-messaging/connect-voice-mail-system/um-ip-gateway-procedures.md).
  
## What do you need to know before you begin?

- Estimated time to complete: Less than 1 minute.
    
- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "UM IP gateways" entry in the [Unified Messaging Permissions](http://technet.microsoft.com/library/d326c3bc-8f33-434a-bf02-a83cc26a5498.aspx) topic. 
    
- Before you perform these procedures, confirm that a UM dial plan has been created. For detailed steps, see [Create a UM dial plan](../../voice-mail-unified-messaging/connect-voice-mail-system/create-um-dial-plan.md).
    
- Before you perform these procedures, confirm that a UM IP gateway has been created. For detailed steps, see [Create a UM IP gateway](../../voice-mail-unified-messaging/connect-voice-mail-system/create-um-ip-gateway.md).
    
- For information about keyboard shortcuts that may apply to the procedures in this topic, see **Keyboard shortcuts in the Exchange admin center**.
    
> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612),[Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351).. 
  
## What do you want to do?

### Use the EAC to prevent Message Waiting Indicator

1. In the EAC, navigate to **Unified Messaging** \> **UM IP Gateways**, select the UM IP gateway you want to change, and then click **Edit**![Edit icon](../../media/ITPro_EAC_EditIcon.gif).
    
2. On the **UM IP Gateway** page, clear the check box next to **Allow message waiting indicator**.
    
3. Click **Save**.
    
### Use the Shell to prevent Message Waiting Indicator

This example prevents the message waiting indicator from appearing for users who are associated with the UM IP gateway named  `MyUMIPGateway` with an IP address of 10.10.10.1. 
  
```
Set-UMIPGateway -Identity MyUMIPGateway -Address 10.10.10.1 -MessageWaitingIndicatorAllowed $false
```


