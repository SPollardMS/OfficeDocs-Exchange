---
title: Learn more about UM IP gateways
ms.prod: EXCHANGE
ms.assetid: 1eebbb3e-4869-43dd-a88e-452cc13a5647
---


# Learn more about UM IP gateways

You must configure Voice over IP (VoIP) gateway devices—including VoIP gateways, IP Private Branch eXchanges (PBXs), and Session Border Controllers (SBCs)—correctly when you deploy Unified Messaging (UM) for your organization. To do this, you need to configure the IP interface of the VoIP gateways, IP PBXs, or SBCs you're using to communicate with the Client Access servers that are running the Microsoft Exchange Unified Messaging Call Router service and Mailbox servers that are running the Microsoft Exchange Unified Messaging service. 
  
    
    


## VoIP and UM IP gateways

You must configure several types of ports or interfaces to enable communication between a VoIP gateway, IP PBX, or SBC and the Client Access and Mailbox servers on your network. When you configure a VoIP gateway, IP PBX, or SBC, you must consider whether the VoIP gateway device is analog, digital, or both analog and digital. If the VoIP gateway interface that connects to a PBX is analog, you must configure the appropriate settings to enable the VoIP gateway to communicate with the Client Access and Mailbox servers. For your Client Access and Mailbox servers to communicate with the VoIP gateways, you must configure the network interfaces to communicate with your PBXs, IP PBXs, or SBCs, and you must configure the LAN connection or network interface for the device.
  
    
    
After you install a VoIP gateway, IP PBX, or SBC, you must create a UM IP gateway to represent it. The combination of the UM IP gateway and a UM hunt group establishes a link between a VoIP gateway, IP PBX, or SBC and a UM dial plan. After you create a UM IP gateway, the Client Access and Mailbox servers associated with the UM IP gateway send a SIP OPTIONS request to make sure that the VoIP gateway, IP PBX, or SBC that the UM IP gateway represents is responsive. If the VoIP gateway, IP PBX, or SBC doesn't respond to the SIP OPTIONS request from the Client Access and Mailbox servers, you must make sure the VoIP gateway, IP PBX, or SBC is available and online and the UM configuration is correct.
  
    
    
After the UM IP gateway is created, the VoIP gateway, IP PBX, or SBC can be linked to or associated with a single or multiple UM hunt groups and UM dial plans. The UM hunt group provides a link between the UM IP gateway and a UM dial plan. By creating multiple UM hunt groups, you can associate a single UM IP gateway with multiple UM dial plans. 
  
    
    

## For more information

 [UM IP Gateways](http://technet.microsoft.com/library/991d77e0-3995-44ab-bedf-52ff7a0301ab.aspx)
  
    
    
 [Manage a UM IP Gateway](http://technet.microsoft.com/library/387e540f-8c59-42d2-a423-99fcf97e00aa.aspx)
  
    
    
 [Create a Unified Messaging IP Gateway](http://technet.microsoft.com/library/542d6b50-147b-4cec-b54d-61c7b8fc0fc7.aspx)
  
    
    

