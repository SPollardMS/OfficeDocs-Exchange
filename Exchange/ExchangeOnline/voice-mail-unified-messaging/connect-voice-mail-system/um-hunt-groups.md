---
title: "UM hunt groups"
ms.author: tonysmit
author: tonysmit
manager: scotv
ms.date: 6/24/2018
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 026129a1-b0b5-410a-bed6-2d49f85205b3
description: "A telephony hunt group provides a way to distribute telephone calls from a single number to multiple extensions or telephone numbers. In Unified Messaging (UM), a UM hunt group is a logical representation of a telephony hunt group, and it links a UM IP gateway to a UM dial plan."
---

# UM hunt groups

 A telephony hunt group provides a way to distribute telephone calls from a single number to multiple extensions or telephone numbers. In Unified Messaging (UM), a UM hunt group is a logical representation of a telephony hunt group, and it links a UM IP gateway to a UM dial plan. 
  
Looking for management tasks related to Unified Messaging hunt groups? See [UM hunt group procedures](um-hunt-group-procedures.md).
  
## What is a hunt group?
<a name="whatisahuntgroup"> </a>

Hunt group is a term used to describe a group of Private Branch eXchange (PBX) or IP PBX extension numbers that are shared by users. Hunt groups are used to efficiently distribute calls into or out of a specific business unit. Creating and defining a hunt group minimizes the chance that a caller who places an incoming call will receive a busy signal when the call is received. 
  
Hunt groups are used to locate an open line, extension, or channel when an incoming call is received. Calls are "rolled over" to the next available line when a primary phone line is busy or isn't answered. The calling party gets a busy signal or is sent to voice mail only if no extensions in the group are open. For example, a PBX or IP PBX might be configured to have 10 extension numbers for the sales department. The 10 sales extension numbers would be configured as one hunt group. 
  
The settings for a simple hunt group include a name, an extension number, a list of available group members, and a hunt group selection method. The hunt group selection method determines the order in which incoming calls are presented to the members of the hunt group.
  
There are multiple algorithms or methods that a PBX or IP PBX can use to locate an open line, extension, or channel. These include:
  
- **Group hunt or ring all extensions** When an incoming call is received on the hunt group extension number, the PBX or IP PBX rings all extension numbers in the group. 
    
- **Start with lowest number or linear hunting** This is the default setting on most PBXs and IP PBXs. With this method, calls are routed to the first idle line in sequential order, starting with the first line in the group. This configuration is most often found on multiline phones at small businesses. 
    
- **Round-robin or circular hunting** With this method, calls are routed to the first idle line, starting with the line after the one that last handled a call. When calls are distributed using the "round-robin" method, if a call is delivered to line 1, the next call goes to line 2, the next to line 3, and so on. This process continues even if one of the previous lines becomes free. When the end of the hunt group is reached, the hunting starts over at the first line. Lines are skipped only if they are still busy on a previous call. Circular or round-robin hunting spreads call disruption evenly throughout all the calls, minimizing the possibility for a major disruption in service. 
    
- **Most-idle or uniform-distribution hunting** With this method, the call is routed to the first available line in the group that has been idle the longest. This method uses the length of time that the person taking the call has been busy instead of whether the line is available. This method is typically used in large call centers where the incoming calls are being answered by people and the load is distributed evenly across the group of extension numbers. 
    
You can configure one or more hunt groups. Each hunt group must include a minimum of two lines. If a number is already being used in one hunt group, it won't be available in another.
  
Following are examples of simple telephony hunt groups and how they work.
  
 **Example 1**
  
Extension 300 (pilot number) is programmed so that when a call comes in, it rings extension 301, then 302, then 303, then 304.
  
1. Extension 301 is busy. 
    
2. Extension 302 rings and isn't answered.
    
3. Extension 303 answers the call.
    
4. Extension 304 is free and waiting for an incoming call.
    
 **Example 2**
  
Extension 1000 (pilot number) is programmed so that when a call comes in, it rings all the extensions 2000 through 2003 at the same time:
  
1. Extension 2000 is free.
    
2. Extension 2001 is free.
    
3. Extension 2002 is free.
    
4. Extension 2003 answers the incoming call.
    
## What is a pilot number?
<a name="pilotnumber"> </a>

In a telephony network, a PBX or an IP PBX can be configured to have a single hunt group or multiple hunt groups. Each hunt group created on a PBX or IP PBX must have an associated pilot number. Using a pilot number helps to eliminate busy signals and to route incoming calls to the extension numbers that are available. The PBX or IP PBX uses the pilot number to locate the hunt group and in turn to locate the telephone extension number on which the incoming call was received and the extensions that are assigned to the hunt group. Without a defined pilot number, the PBX or IP PBX can't locate where the incoming call was received. 
  
A pilot number is the address, extension, or location of the hunt group inside the PBX or IP PBX. It's generally a blank extension number or one extension number from a hunt group of extension numbers that doesn't have a person or telephone associated with it. For example, you might configure a hunt group on a PBX or IP PBX to contain extension numbers 4100, 4101, 4102, 4103, 4104, and 4105. The pilot number for the hunt group is configured as extension 4100. When a call is received on extension number 4100, the PBX or IP PBX looks for the next available extension number to determine where to deliver the call. In this example, the PBX or IP PBX will use its programmed search algorithm to look at extension numbers 4101, 4102, 4103, 4104, and 4105.
  
Using a pilot number helps eliminate busy signals and helps route incoming calls to the extension numbers that are available. In Unified Messaging, the PBX or IP PBX pilot number is used as the target. If none of the extension numbers in the hunt group answer an incoming call, the call is routed to a Mailbox server running the Microsoft Exchange Unified Messaging service.
  
## What is a UM hunt group?
<a name="umhuntgroups"> </a>

Unified Messaging hunt groups are critical to the operation of the UM system. A UM hunt group is a logical representation of an existing PBX or IP PBX hunt group. It's used to link a UM IP gateway with a UM dial plan. A single UM hunt group can also link multiple UM IP gateways with a UM dial plan. By default, when you create a UM IP gateway and associate it with a UM dial plan, a UM hunt group is created, and you can also create other hunt groups. You must create at least one UM hunt group.
  
UM hunt groups are used to locate the PBX or IP PBX hunt group from which an incoming call is received. A pilot number defined for a hunt group on the PBX or IP PBX must also be defined for the UM hunt group. The pilot number is used to match the information presented for incoming calls using the Session Initiation Protocol (SIP) signaling information on the voice message. The pilot number enables Exchange servers to interpret the call together with the correct dial plan so that the call can be routed correctly. The absence of a hunt group prevents Exchange servers from knowing the location of the incoming call. Knowing the location of incoming calls enables the Exchange servers to accept the call header information that's passed from the VoIP gateway, IP PBX, or SIP-enabled PBX. It's very important that you configure your UM hunt groups correctly, because incoming calls that don't match the pilot number defined on the UM hunt group won't be answered, and routing of incoming calls will fail.
  
In on-premises and hybrid deployments when you create a UM hunt group, you're enabling all Client Access and Mailbox servers, regardless of whether they've been added to a UM dial plan, to communicate with a VoIP gateway, IP PBX, or SIP-enabled PBX. This is because all Client Access and Mailbox servers answer incoming calls for all dial plans, instead of for a specific UM dial plan like the UM server did in previous versions of Exchange. If you delete the UM hunt group, the associated UM IP gateway won't be able to answer incoming calls from a VoIP gateway, IP PBX, or SIP-enabled PBX or place outgoing calls through the VoIP gateway, IP PBX or SIP-enabled PBX using the specified pilot number.
  
However, for on-premises and hybrid deployments if you're integrating UM with Microsoft Office Communications Server 2007 R2 or Microsoft Lync Server, you must add all Client Access and Mailbox servers to all SIP URI dial plans that have been created to work with Communications Server 2007 R2 or Lync Server. This enables call routing and outdialing to work correctly.
  
For more information about UM IP gateways, see [UM IP gateways](um-ip-gateways.md).
  

