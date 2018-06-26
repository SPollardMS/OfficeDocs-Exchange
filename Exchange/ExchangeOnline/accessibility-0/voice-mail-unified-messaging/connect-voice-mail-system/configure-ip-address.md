---
title: "Configure the IP address"
ms.author: tonysmit
author: tonysmit
manager: scotv
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 100541c1-2297-4c46-9602-b304736541a8
description: "Before you create a Unified Messaging (UM) IP gateway, you must first set the IP address or the fully qualified domain name (FQDN) on the VoIP gateway, IP PBX, or session border controller (SBC) that you're using. Then, when you create the UM IP gateway, you set the IP address or FQDN. You can change the IP address or FQDN later."
---

# Configure the IP address

Before you create a Unified Messaging (UM) IP gateway, you must first set the IP address or the fully qualified domain name (FQDN) on the VoIP gateway, IP PBX, or session border controller (SBC) that you're using. Then, when you create the UM IP gateway, you set the IP address or FQDN. You can change the IP address or FQDN later. 
  
You can configure the IP address or FQDN using either the EAC or the Shell. In the EAC, the **Address** box on the **UM IP gateway** page can accept an IPv4 IP address, an IPv6 address, or an FQDN. You can also use the  _Address_ parameter on the **Set-UMIPGateway** cmdlet in the Shell to set an IPv4 IP address, an IPv6 address, or an FQDN. If you create a UM IP gateway using an FQDN, you must create the appropriate HOST A records in your DNS forward lookup zone. If the DNS configuration for the UM IP gateway is changed, you must disable and then enable the UM IP gateway to make sure that its configuration information is updated correctly. 
  
For additional management tasks related to UM IP gateways, see [UM IP gateway procedures](um-ip-gateway-procedures.md).
  
## What do you need to know before you begin?

- Estimated time to complete: 2 minutes.
    
- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "UM IP gateways" entry in the [Unified Messaging Permissions](http://technet.microsoft.com/library/d326c3bc-8f33-434a-bf02-a83cc26a5498.aspx) topic. 
    
- Before you perform these procedures, confirm that a UM dial plan has been created. For detailed steps, see [Create a UM dial plan](create-um-dial-plan.md).
    
- Before you perform these procedures, confirm that a UM IP gateway has been created. For detailed steps, see [Create a UM IP gateway](create-um-ip-gateway.md).
    
- For information about keyboard shortcuts that may apply to the procedures in this topic, see **Keyboard shortcuts in the Exchange admin center**.
    
> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612),[Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351).. 
  
## What do you want to do?

### Use the EAC to configure the IP address on a UM IP gateway

1. In the EAC, navigate to **Unified Messaging** \> **UM IP Gateways**, select the UM IP gateway that you want to modify, and then click **Edit**![Edit icon](../../media/ITPro_EAC_EditIcon.gif).
    
2. On the **UM IP gateway** page, in the **Address** box, enter the IP address for the VoIP gateway, IP PBX, or session border controller (SBC). 
    
3. Click **Save** to save your changes. 
    
> [!IMPORTANT]
> If you use an FQDN instead of an IP address on the UM IP gateway, verify that the correct DNS records have been created. 
  
### Use the Shell to configure the IP address on a UM IP gateway

This example configures a UM IP gateway named  `MyUMIPGateway` with an IP address of 10.10.10.1. 
  
```
Set-UMIPGateway -Identity MyUMIPGateway -Address 10.10.10.1
```

This example configures a UM IP gateway named  `MyUMIPGateway` with an IP address of 10.10.10.10 and listens for SIP requests on TCP port 5061. 
  
```
Set-UMIPGateway -Identity MyUMIPGateway -Address 10.10.10.10 -Port 5061
```

This example prevents the UM IP gateway named  `MyUMIPGateway` from accepting incoming and outgoing calls, sets an IPv6 address, and allows the UM IP gateway to use IPv4 and IPV6 addresses. 
  
```
Set-UMIPGateway -Identity MyUMIPGateway -Address fe80::39bd:88f7:6969:d223%11 -IPAddressFamily Any -Status Disabled -OutcallsAllowed $false
```


