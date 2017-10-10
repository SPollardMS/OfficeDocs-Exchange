---
title: Learn more about UM dial plans
ms.prod: EXCHANGE
ms.assetid: 70e911da-ae48-4601-899e-e2b28e460200
---


# Learn more about UM dial plans

A Unified Messaging (UM) dial plan contains configuration information related to your telephony network. A UM dial plan establishes a link from the telephone extension number of a user to their UM-enabled mailbox. When you create a UM dial plan, you can configure the number of digits in the extension numbers, the Uniform Resource Identifier (URI) type, and the Voice over IP (VoIP) security setting for the dial plan. Each time that you create a UM dial plan, a UM mailbox policy is also created. The UM mailbox policy is named < _DialPlanName_> Default Policy.
  
    
    


## Overview of UM dial plans

UM dial plans are the central component of the Unified Messaging voice mail system. They represent sets of Private Branch eXchanges (PBXs) or IP PBXs that share common user extension numbers. All users' extensions hosted on PBXs or IP PBXs within a dial plan contain the same number of digits. A user can dial another user's extension in the same dial plan without appending a special number to the extension or dialing a full telephone number. 
  
    
    
The following UM dial plan topologies can exist:
  
    
    

- A single dial plan that represents a subset of extensions or all extensions for an organization with one PBX or IP PBX.
    
  
- A single dial plan that represents a subset of extensions or all extensions for an organization with multiple networked PBXs or IP PBXs.
    
  
- Multiple dial plans that represent a subset of extensions or all extensions for an organization with one PBX or IP PBX.
    
  
- Multiple dial plans that represent a subset of extensions or all extensions for an organization with multiple PBXs or IP PBXs.
    
  

## How dial plans work

When you integrate a telephony network with Unified Messaging, there must be a hardware device called a VoIP gateway with a PBX or IP PBX that connects your telephony network to your IP-based network. VoIP gateways and IP PBXs convert the circuit-switched protocols found in a telephony network to a data-switched protocol such as IP. Each VoIP gateway, IP PBX, or Session Border Controller (SBC) in your organization is represented by a UM IP gateway. For more information about UM IP gateways, see  [UM IP Gateways](http://technet.microsoft.com/library/991d77e0-3995-44ab-bedf-52ff7a0301ab.aspx).
  
    
    
When deploying Unified Messaging, you must create and configure at least one UM dial plan that has a UM IP gateway associated with it. When you create the first UM IP gateway and specify a UM dial plan at the time you create it, a default UM hunt group is also created. Creating and associating these UM components enables the Client Access servers that are running the Microsoft Exchange Unified Messaging Call Router service and the Mailbox servers that are running the Microsoft Exchange Unified Messaging service to receive calls from the VoIP gateway, IP PBX, or SBC and process incoming calls for users who are associated with the UM dial plan. When a call comes in to the VoIP gateway, IP PBX, or SBC, it forwards the call to a Client Access server. The Client Access server then forwards the call to a Mailbox server, which tries to match the extension number of the user to the associated UM dial plan.
  
    
    

## Types of dial plans

A URI is a string of characters that's used to identify or name a resource. In UM, the main purpose of a URI is to enable VoIP devices to communicate with other devices using specific protocols. A URI defines the naming and numbering format or scheme used for the calling and called party information contained within a Session Initiation Protocol (SIP) header for an incoming or outgoing call. In simple terms, the URI type is set on a PBX or IP PBX and is the format type that is expected to be sent to Client Access and Mailbox servers.
  
    
    
The types of UM dial plans you create will depend on the URI types supported by the VoIP gateways, PBXs, IP PBXs, and SBCs in your organization. Three formats or URI types can be configured on UM dial plans:
  
    
    

- Telephone Extension
    
  
- SIP URI
    
  
- E.164
    
  

## VoIP security

Client Access and Mailbox servers can communicate with VoIP gateways, IP PBXs, and SBCs in Unsecured, SIP secured, or Secured mode, depending on how the UM dial plan is configured. Client Access and Mailbox servers can operate in any mode configured on a dial plan because they can be configured to listen on TCP port 5060 for unsecured requests and TCP port 5061 for secured requests at the same time, if the  _UMStartUpMode_ is set to _Dual_ mode. By default, TCP mode is configured on both Client Access and Mailbox servers. However, Client Access and Mailbox servers will answer all incoming calls if the UMStartupMode is set to TCP, TLS, or Dual.
  
    
    

## Outlook Voice Access

Two types of callers access the UM or voice mail system using the subscriber access number or Outlook Voice Access number configured on a UM dial plan: unauthenticated callers and authenticated callers. When callers dial an Outlook Voice Access number configured on a dial plan, they are considered anonymous or unauthenticated until they input information including their voice mail extension and a PIN. The only option available to anonymous or unauthenticated callers is the directory search feature. After Outlook Voice Access callers input their voice mail extension, if needed, and their PIN, they will be authenticated and given access to their mailbox. After they gain access to the system, they are using the Outlook Voice Access feature. Outlook Voice Access is a series of voice prompts that give the caller access to email, voice mail, calendar, and other information. Outlook Voice Access lets authenticated callers navigate their personal information in their mailbox, place calls, or locate users using dual tone multi-frequency (DTMF), also known as touchtone, inputs or voice inputs. 
  
    
    

## For more information
<a name="fmi"> </a>

 [Manage a UM Dial Plan](http://technet.microsoft.com/library/a89735e4-36ec-49fb-ad0f-192fad37e801.aspx)
  
    
    

