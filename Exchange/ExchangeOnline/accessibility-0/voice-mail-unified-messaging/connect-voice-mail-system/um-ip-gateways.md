---
title: "UM IP gateways"
ms.author: tonysmit
author: tonysmit
manager: scotv
ms.date: 6/24/2018
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 991d77e0-3995-44ab-bedf-52ff7a0301ab
description: "A Unified Messaging (UM) IP gateway represents a physical Voice over IP (VoIP) gateway, IP Private Branch eXchange (PBX), or session border controller (SBC) hardware device. Before a VoIP gateway, IP PBX, or SBC can be used to answer incoming calls and send outgoing calls for voice mail users, a UM IP gateway must be created in the directory service."
---

# UM IP gateways

A Unified Messaging (UM) IP gateway represents a physical Voice over IP (VoIP) gateway, IP Private Branch eXchange (PBX), or session border controller (SBC) hardware device. Before a VoIP gateway, IP PBX, or SBC can be used to answer incoming calls and send outgoing calls for voice mail users, a UM IP gateway must be created in the directory service.
  
## Overview of UM IP gateways
<a name="overview"> </a>

Traditionally, gateway is a term that describes a physical device that connects two incompatible networks. With Exchange Unified Messaging and other unified messaging solutions, the VoIP gateway is used to translate between the Public Switched Telephone Network (PSTN)/Time Division Multiplex (TDM) or circuit-switched based telephony network and an IP or packet-switched data network. An IP PBX also translates between the PSTN network and a packet-switched network, so when an IP PBX is used, a VoIP gateway isn't required. A VoIP gateway is only required if you are connecting a legacy PBX hardware device to your UM deployment. 
  
> [!NOTE]
> A packet-switched network is a network in which packets (messages or fragments of messages) are individually routed between devices such as routers, switches, VoIP gateway, IP PBXs and SBCs. This contrasts with a circuit-switched network that sets up a dedicated connection between the two nodes for their exclusive use for the duration of the communication. 
  
 Exchange Unified Messaging relies on the ability of the VoIP gateway to translate TDM or telephony circuit-switched based protocols, such as Integrated Services Digital Network (ISDN) or QSIG, from a PBX to protocols based on VoIP or IP, such as Session Initiation Protocol (SIP), Realtime Transport Protocol (RTP), or T.38 for real-time facsimile transport. 
  
IP PBXs are also used when connecting a circuit-switched telephony network to a data or packet-switched network. They are also used to translate circuit-switched protocols to protocols based on VoIP or IP, such as SIP, RTP, and Secure RTPC (SRTP).
  
Session Border Controllers (SBCs) are somewhat different than VoIP gateways and IP PBXs. Instead of connecting a circuit-switched network to a packet-switched network, they're used to connect two data networks over a public network like the Internet or over a private WAN connection. In Unified Messaging, SBCs are used in a hybrid deployment of UM in which UM uses some components that are located on-premises and others, such as mailboxes, that are located in the cloud.
  
### VoIP device configurations

Although there are many types and manufacturers of PBXs, VoIP gateways, IP PBXs, and SBCs, there are basically three types of VoIP device configurations: 
  
- **IP PBX** A single device that translates between the PSTN/TDM or circuit-switched based telephony network and an IP or packet-switched data network 
    
- **PBX (legacy) and a VoIP gateway** Two separate components that together translate between the PSTN/TDM or circuit-switched telephony network and an IP or packet-switched data network 
    
- **SBC** Single or multiple devices that connect two types of IP-based networks such as a LAN and a datacenter. 
    
To support Unified Messaging, one or both types of IP/VoIP device configurations are used when connecting a telephony network infrastructure to a data network infrastructure or connecting an on-premises deployment with a UM deployment in the cloud.
  
## UM IP gateways
<a name="ipgatewayobjects"> </a>

The UM IP gateway contains one or more UM hunt groups and configuration settings. UM hunt groups are used to link a UM IP gateway to a UM dial plan. The combination of the UM IP gateway and a UM hunt group establishes a link between a VoIP gateway, IP PBX, or SBC and a UM dial plan. By creating multiple UM hunt groups, you can associate a single UM IP gateway with multiple UM dial plans.
  
After you create a UM IP gateway, the Exchange servers linked to the UM IP gateway will send a SIP OPTIONS request to the VoIP gateway, IP PBX, or SBC to ensure that the device is responsive. If the VoIP gateway, IP PBX, or SBC doesn't respond to the request, an Exchange server will log an event with ID 1400 stating that the request failed. If this happens, make sure that the VoIP gateway, IP PBX, or SBC is available and online and that the Unified Messaging configuration is correct.
  
A Mailbox server communicates only with VoIP gateways, IP PBXs, or SBCs listed as trusted SIP peers. In some cases, if two VoIP gateways, IP PBXs, or SBCs are configured to use the same IP address, an event with ID 1175 will be logged. Unified Messaging protects against unauthorized requests by retrieving the internal URL of the Unified Messaging Web services virtual directory and then uses the URL to build the list of FQDNs for the trusted SIP peers. When two FQDNs are resolved to the same IP address, this event is logged.
  
## IPv6 support for UM IP gateways
<a name="ipv6"> </a>

Internet Protocol version 6 (IPv6) is the most recent version of the Internet Protocol (IP). IPv6 is intended to correct many of the shortcomings of IPv4, which was the previous version of the IP. In Microsoft Exchange Server 2010 on-premises and hybrid deployments, IPv6 was supported only when IPv4 was also used.
  
In Exchange 2013 on-premises and hybrid deployments, UM-related components and speech services run only on Client Access and Mailbox servers. Because the UM architecture has changed and now requires Unified Communications Managed API (UCMA) v4.0 to support both IPv4 and IPv6 as well as other Exchange features, the Client Access and Mailbox servers that have Unified Messaging components and services fully support IPv6 networks and doesn't require IPv4.
  
In on-premises, hybrid, and Exchange Online deployments, both enterprise and Exchange Online UM administrators can use IPv6 when they connect UM to IPv6-capable devices, including devices such as routers, IP gateways, IP PBXs, and Microsoft Office Communications Server 2007 R2 and Microsoft Lync servers. However, for interoperability and backward compatibility, IPv4 can be used instead without additional configuration changes if the  _IPAddressFamily_ parameter is set to  `Any` on UM IP gateways. 
  
Exchange UM must still communicate directly with SIP peers (VoIP gateways, IP PBXs, and SBCs) that may not support IPv6 in their software or firmware. If they don't support IPv6, UM must be able to communicate directly with SIP peers that use IPv4. For hosted voice mail, UM communicates with customer equipment through SBCs, Lync Server 2010, or Lync Server 2013. In hosted environments, IPv6 SIP-aware clients such as SBCs and Lync servers can be deployed to handle the IPv6-to-IPv4 conversion process.
  
For on-premises and hybrid deployments after you install your Client Access and Mailbox servers, and for Exchange Online UM deployments, you need to create UM IP gateways. If you need your UM IP gateways to support IPv6, you must also:
  
1. Create a new UM IP gateway or configure an existing UM IP gateway with an IPv6 address for each of the IP gateways, IP PBXs, or SBCs on your network. When you're creating and configuring the required UM IP gateways, you must add the IPv6 address or the Fully Qualified Domain Name (FQDN) for the UM IP gateway. If you're adding the FQDN to the UM IP gateway, you must have created the correct DNS records to resolve the UM IP gateway FQDN to the IPv6 address. If you have an existing UM IP gateway, you can use the **Set-UMIPgateway** cmdlet to configure the IPv6 address or FQDN. 
    
2. Configure the  _IPAddressFamily_ parameter on each UM IP gateway. To enable the VoIP gateway to accept IPv6 packets, you must set the UM IP gateway to either accept both IPv4 and IPv6 connections, or accept only IPv6 connections, by using the **Set-UMIPgateway** cmdlet. 
    
3. After you've configured your UM IP gateways, you must also configure the VoIP gateways, IP PBXs, and SBCs on your network to support IPv6. For details, see your hardware vendor for a list of devices that support IPv6 and how to correctly configure them.
    
> [!NOTE]
> The maximum number of UM IP gateways per dial plan is 200. If you create more than 200 the UM service won't start. 
  
## Enabling and disabling a UM IP gateway
<a name="enabledisable"> </a>

By default, a UM IP gateway is left in an enabled state after it's created. However, the UM IP gateway can be enabled or disabled. If you disable a UM IP gateway, you can set it to force all Exchange servers to drop existing calls. Alternatively, you can set it to force the Exchange servers associated with the UM IP gateway to stop handling any new calls presented by the VoIP gateway, IP PBX, or SBC.
  
If you're integrating Unified Messaging with Office Communications Server R2 or Microsoft Lync Server, you must allow only one UM IP gateway to make outgoing calls for users, and disable outbound calling on all other UM IP gateways associated with your SIP URI dial plans. Use either the Shell or the EAC to disable outbound calling.
  
When selecting the UM IP gateway through which to allow outgoing calls for on-premises and hybrid deployments, choose the one that's likely to handle the most traffic. Don't allow outgoing traffic through a UM IP gateway that connects to a pool of Lync Server Directors. This is necessary to ensure that outbound calls to external users placed by a Mailbox server running the Microsoft Exchange Unified Messaging service (for example, in Play-on-Phone scenarios) reliably traverse the corporate firewall.
  

