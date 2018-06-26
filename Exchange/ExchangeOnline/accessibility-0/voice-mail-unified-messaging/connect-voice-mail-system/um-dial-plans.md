---
title: "UM dial plans [ONP]"
ms.author: tonysmit
author: tonysmit
manager: scotv
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: ed7afc03-94af-4b23-8745-6a61f203c149
description: "Unified Messaging (UM) dial plans are the main component of Unified Messaging and are required to successfully deploy Unified Messaging voice mail on your network. The following sections discuss UM dial plans and how they're used in a UM deployment."
---

# UM dial plans [ONP]

Unified Messaging (UM) dial plans are the main component of Unified Messaging and are required to successfully deploy Unified Messaging voice mail on your network. The following sections discuss UM dial plans and how they're used in a UM deployment. 
  
## Overview of UM dial plans

A UM dial plan represents a set of Private Branch eXchanges (PBXs) or IP PBXs that share common user extension numbers. All users' extensions hosted on PBXs or IP PBXs within a dial plan contain the same number of digits. Users can dial one another's telephone extensions without appending a special number to the extension or dialing a full telephone number.
  
A UM dial plan mirrors a telephony dial plan. A telephony dial plan is configured on PBXs or IP PBXs.
  
In Unified Messaging, the following UM dial plan topologies can exist:
  
- A single dial plan that represents a subset of extensions or all extensions for an organization with one PBX or IP PBX.
    
- A single dial plan that represents a subset of extensions or all extensions for an organization with multiple networked PBXs or IP PBXs.
    
- Multiple dial plans that represent a subset of extensions or all extensions for an organization with one PBX or IP PBX.
    
- Multiple dial plans that represent a subset of extensions or all extensions for an organization with multiple PBXs or IP PBXs.
    
Users who belong to the same dial plan have these characteristics: 
  
- An extension number that uniquely identifies the user mailbox in the dial plan.
    
- The ability to call or send voice messages to other members in the dial plan using only the extension number.
    
For more information about how to enable a user for Unified Messaging, see [Enable a user for voice mail](../../voice-mail-unified-messaging/set-up-voice-mail/enable-a-user-for-voice-mail.md).
  
UM dial plans are used in Unified Messaging to make sure that user telephone extensions are unique. In some telephony networks, multiple PBXs or IP PBXs exist. In these telephony networks, there could be two users who have the same telephone extension number. UM dial plans resolve this situation. Putting the two users into two separate UM dial plans makes their extensions unique.
  
## How dial plans work

When you integrate a telephony network with Unified Messaging, there must be one or more hardware devices called Voice over IP (VoIP) gateways or IP PBXs that connect your telephony network to your IP-based packet switched network. VoIP gateways convert circuit-switched protocols from a PBX found in a telephony network to a data-switched protocol such as IP. IP PBXs also convert circuit-switched protocols to a data-switched protocol. Session Border Controllers (SBCs) enable you to connect two IP based networks together over a public or private WAN and are found in UM hybrid or online deployments. Each VoIP gateway, IP PBX, or Session Border Controller (SBC) in your organization is represented by a UM IP gateway. For more information about UM IP gateways, see [UM IP gateways](um-ip-gateways.md).
  
Unified Messaging requires that you create at least one UM dial plan. Whether you create one or more dial plans, all the Exchange servers in your organization will answer incoming calls. There must also be a single or multiple UM IP gateways associated with the dial plan. In on-premises and hybrid deployments, after you install your Exchange servers and associate a UM IP gateway, all the Exchange servers will answer incoming calls for all dial plans. However, for on-premises or hybrid deployments, when you're integrating Exchange and Lync Server, you must create SIP URI dial plans.
  
> [!IMPORTANT]
> Each time you create a UM dial plan, a default UM mailbox policy is also created. The UM mailbox policy is named \< _Dial Plan Name_\> Default Policy. This UM mailbox policy can be deleted or configured differently. 
  
When you create the first UM IP gateway and specify a UM dial plan at the time you create it, a default UM hunt group is also created. Creating these components enables the Exchange servers to receive calls from a VoIP gateway, IP PBX, or SBC and then process those incoming calls for users who are associated with the UM dial plan. In on-premises or hybrid deployments, when a call comes in to the VoIP gateway, IP PBX, or SBC, it forwards the call to a Client Access server. The Client Access server then forwards the call to a Mailbox server and the Mailbox server tries to match the extension number of the user to the associated UM dial plan.
  
## Types of dial plans

A Uniform Resource Identifier (URI) is a string of characters (numbers or alphabetic) that's used to identify or name a resource. In Unified Messaging, the main purpose of a URI is to enable VoIP devices to communicate with other devices using specific protocols. A URI defines the naming and numbering format or scheme used for the calling and called party information contained within a Session Initiation Protocol (SIP) header for an incoming or outgoing call. 
  
The types of UM dial plans you create in Unified Messaging will depend on the URI types supported by the VoIP gateways or IP PBXs in your organization. The URI type is the type of string that's sent from the PBX or IP PBX. When you create a dial plan, you should know the specific URI types that are supported by your PBXs or IP PBXs. There are three formats or URI types that can be configured on UM dial plans:
  
- Telephone Extension (TeleExtn)
    
- SIP URI
    
- E.164
    
By default, each time you create a dial plan in Unified Messaging, the dial plan will be created to use the telephone extension URI type. After you create a dial plan, you won't be able to change the URI type. You must delete the existing dial plan and create another one with the correct URI type.
  
### Telephone Extension URI type

The Telephone Extension URI type is the most common type of UM dial plan and is used with IP PBXs and PBXs. When you configure a telephone extension (TelExtn) dial plan, the VoIP gateways, PBXs, and IP PBXs you use must support the TelExtn URI type. Today, most PBXs and IP PBXs support this URI type. 
  
When a call is received by a PBX and the UM-enabled user isn't available to answer the call, the PBX will forward the call to a VoIP gateway. The VoIP gateway—or the IP PBX, if one is used—will translate the call from a circuit-based protocol to an IP based protocol. In the header for the SIP packet received from the VoIP gateway or IP PBX, the calling and called party information will be listed in one of the following formats: 
  
- Tel:512345 
    
- 512345@\< _IP address_\>
    
The telephone extension (TelExtn) format used is based on the configuration of the VoIP gateway or IP PBX.
  
### SIP URI type

Session Initiation Protocol (SIP) is a standard protocol for initiating interactive user sessions that involve multimedia elements such as video, voice, chat, and gaming. SIP is a request-to-response based protocol that answers requests from clients and responses from servers. Clients are identified by SIP URIs. Requests can be sent through any transport protocol, such as UDP or TCP. SIP determines the endpoint to be used for the session by selecting the communication media and media parameters.
  
When you create a new dial plan, you have the option of creating a SIP URI dial plan if your environment has Microsoft Office Communications Server 2007 R2 or Microsoft Lync Server deployed. You can also create a SIP URI dial plan if your organization has IP PBXs or SIP-enabled PBXs. In the latter case, your organization must also support SIP URIs and SIP routing.
  
A SIP URI is a user's SIP phone number. The SIP URI resembles an email address and is written in the following format: sip _:\<user name\>@\<domain or IP address\>_: _Port_. When a SIP-enabled IP PBX or PBX is used to send a call to the Exchange servers, the device will send the SIP URI for the calling and called party in the SIP header and will not include extension numbers.
  
### E.164 URI type

E.164 is a standard numbering format that defines the international public telecommunication numbering plan used in the Public Switched Telephone Network (PSTN) and some data networks. E.164 defines the format of telephone numbers. E.164 numbers can have a maximum of 15 digits and are usually written with a plus sign (+) before the digits of the telephone number. To dial an E.164-formatted telephone number from a telephone, the appropriate international call prefix must be included in the number dialed. In an E.164 numbering plan for public telephone systems, each assigned number contains a country code (CC), a national destination code (NDC), and a subscriber number (SN). 
  
When you create a new dial plan, you have the option to create an E.164 dial plan. However, if you create and configure an E.164 dial plan, the PBXs and IP PBXs must support E.164 routing. The SIP header received from a VoIP gateway associated with an E.164 dial plan will include the E.164-formatted telephone number and information about the calling and called party and will be listed in the following format: Tel:+14255550123. For Exchange Online deployments with Exchange Unified Messaging and Lync Server, you must use correctly formatted E.164 numbers for Outlook Voice Access and auto attendant numbers.
  
## VoIP security

Exchange servers communicate with VoIP gateways, IP PBXs, and other Exchange computers in either Unsecured, SIP secured, or Secured mode, depending on how the UM dial plan is configured. In on-premises and hybrid deployments, Client Access and Mailbox servers can operate in any mode configured on a dial plan because the servers listen on TCP port 5060 for Unsecured requests and TCP port 5061 for Secured requests at the same time if they're configured to start in dual mode. Client Access and Mailbox servers answer all incoming calls for all UM dial plans, but these dial plans can have different VoIP security settings.
  
In on-premises and hybrid deployments, by default, when you create a UM dial plan, it will communicate in Unsecured mode, and the Client Access and Mailbox servers will send and receive data from VoIP gateways, IP PBXs, and SBCs without using encryption. In Unsecured mode, neither the Realtime Transport Protocol (RTP) media channel nor the SIP signaling information is encrypted. You can use the **Get-UMDialPlan** cmdlet in the Shell to determine the security setting for a specific UM dial plan. 
  
In on-premises and hybrid deployments, you can configure a Client Access and Mailbox server to use mutual Transport Layer Security (mutual TLS) to encrypt the SIP and RTP traffic sent and received from other devices and servers. When you configure the dial plan to use SIP secured mode, only the SIP signaling traffic will be encrypted, and the RTP media channels will still use TCP, which isn't encrypted. However, when you configure the dial plan to use Secured mode, both the SIP signaling traffic and the RTP media channels are encrypted. An encrypted signaling media channel that uses Secure Realtime Transport Protocol (SRTP) also uses mutual TLS to encrypt the VoIP data.
  
You can configure the VoIP security mode either when you're creating a new dial plan or after you've created a dial plan using the EAC or the **Set-UMDialPlan** cmdlet in the Shell. When you configure the UM dial plan to use SIP secured or Secured mode, Client Access and Mailbox servers will encrypt the SIP signaling traffic or the RTP media channels or both. However, to be able to send encrypted data to and from Exchange servers, you must correctly configure the UM dial plan, and VoIP devices such as VoIP gateways, IP PBXs, and SBCs must support mutual TLS. 
  
## Outlook Voice Access

There are two types of callers who access the voice mail system using the Outlook Voice Access number configured on a UM dial plan: unauthenticated callers and authenticated callers. When callers dial the Outlook Voice Access number configured on a dial plan, they're considered anonymous or unauthenticated until they input information including their voice mail extension and a PIN. The only option available to anonymous or unauthenticated callers is the directory search feature. After callers input their voice mail extension and their PIN, they'll be authenticated and given access to their mailbox. After they gain access to the voice mail system, they're using the Outlook Voice Access feature. 
  
Outlook Voice Access is a series of voice prompts that give the caller access to email, voice mail, calendar, and other information. Outlook Voice Access lets authenticated callers navigate their personal information in their mailbox, place calls, or locate users using dual tone multi-frequency (DTMF), also known as touchtone, inputs or voice inputs.
  
### Outlook Voice Access numbers

After you've created a UM dial plan, you need to add at least one Outlook Voice Access number. Outlook Voice Access numbers are also called dial plan pilot numbers. This number is used by Outlook Voice Access users to access their mailboxes and lets them search the directory. 
  
By default, when you create a UM dial plan, no Outlook Voice Access number is configured. To enable users to use the Outlook Voice Access feature, you must configure at least one telephone or extension number. The number of alphanumeric characters in the Outlook Voice Access number can't exceed 20. After you configure this number on the dial plan, the number will be displayed in the voice mail options in Microsoft Outlook, and in Outlook Web App. 
  
You can use the **Outlook Voice Access numbers** box on the UM dial plan to add a telephone number or extension that a user will call to access the voice mail system using Outlook Voice Access. In most cases, you'll enter an extension number or an external telephone number. However, because this field accepts alphanumeric characters, a SIP URI can be used if you're using an IP PBX, a SIP-enabled PBX, Office Communications Server 2007 R2 or Microsoft Lync Server. 
  
Depending on the needs of your organization, you may want to configure one or more Outlook Voice Access number. You can have a single Outlook Voice Access number configured on a single UM dial plan or you can have multiple Outlook Voice Access numbers in a single UM dial plan, but you can't have a single Outlook Voice Access number that spans multiple UM dial plans.
  

