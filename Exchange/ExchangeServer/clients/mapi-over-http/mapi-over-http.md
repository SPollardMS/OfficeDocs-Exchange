---
title: "MAPI over HTTP in Exchange 2016"
ms.author: dmaguire
author: msdmaguire
manager: serdars
ms.date: 6/8/2018
ms.audience: ITPro
ms.topic: conceptual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 4663b5db-5b30-4a5a-a302-be6fef7fe5da
description: "Summary: Learn about the benefits and requirements for MAPI over HTTP in Exchange Server 2016."
---

# MAPI over HTTP in Exchange 2016

 **Summary**: Learn about the benefits and requirements for MAPI over HTTP in Exchange Server 2016.
  
Messaging Application Programming Interface (MAPI) over HTTP is a transport protocol that improves the reliability and stability of the Outlook and Exchange connections by moving the transport layer to the industry-standard HTTP model. This allows a higher level of visibility of transport errors and enhanced recoverability. Additional functionality includes support for an explicit pause-and-resume function. This enables supported clients to change networks or resume from hibernation while maintaining the same server context.
  
Implementing MAPI over HTTP does not mean that it is the only protocol that can be used for Outlook to access Exchange. Outlook clients that are not MAPI over HTTP capable can still use Outlook Anywhere (RPC over HTTP) to access Exchange through a MAPI-enabled Client Access server.
  
In Exchange 2016, MAPI over HTTP can be applied across your entire organization, or at the individual mailbox level.
  
## Benefits of MAPI over HTTP

MAPI over HTTP offers the following benefits to clients that support it:
  
- Enables future innovation in authentication by using an HTTP based protocol.
    
- Provides faster reconnection times after a communications break because only TCP connections—not RPC connections—need to be rebuilt. Examples of a communication break include:
    
  - Device hibernation
    
  - Changing from a wired network to a wireless or cellular network
    
- Offers a session context that is not dependent on the connection. The server maintains the session context for a configurable period of time—even if the user changes networks.
    
## Upgrading MAPI over HTTP to Exchange 2016

In Exchange Server 2016, MAPI over HTTP is enabled by default at the organization level, although you still need to configure virtual directories as described in [Configure MAPI over HTTP](configure-mapi-over-http.md) for users to take advantage of it . The same is true if you are upgrading to Exchange 2016 from Exchange 2010, or if you have a mixed environment consisting of both Exchange 2010 and Exchange 2016 servers. 
  
While upgrading from Exchange 2013 to Exchange 2016, or from a mixed Exchange 2010 and Exchange 2013 environment to Exchange 2016, administrators will receive a readiness check warning them that [MAPI over HTTP isn't enabled [WarnMapiHttpNotEnabled]](../../plan-and-deploy/deployment-ref/ms-exch-setupreadiness-warnmapihttpnotenabled.md), and it is recommended that they enable it post-installation. In any organization containing Exchange 2013 servers, MAPI over HTTP won't be enabled by default, and administrators will have to follow the steps in [Configure MAPI over HTTP](configure-mapi-over-http.md).
  
## Supportability and Prerequisites

Consider the following requirements to enable MAPI over HTTP.
  
### Supportability

Use the following matrix to verify that your clients and servers support MAPI over HTTP.
  
|**Product**|**Exchange 2016 RTM**|**Exchange 2013 SP1**|**Exchange 2013 RTM**|**Exchange 2010 SP3**|
|:-----|:-----|:-----|:-----|:-----|
|Outlook 2016 RTM  <br/> |MAPI over HTTP  <br/> Outlook Anywhere  <br/> |MAPI over HTTP  <br/> Outlook Anywhere  <br/> |Outlook Anywhere  <br/> |RPC  <br/> Outlook Anywhere  <br/> |
|Outlook 2013 SP1  <br/> |MAPI over HTTP  <br/> Outlook Anywhere  <br/> |MAPI over HTTP  <br/> Outlook Anywhere  <br/> |Outlook Anywhere  <br/> |RPC  <br/> Outlook Anywhere  <br/> |
|Outlook 2013 RTM  <br/> |Outlook Anywhere  <br/> |Outlook Anywhere  <br/> |Outlook Anywhere  <br/> |RPC  <br/> Outlook Anywhere  <br/> |
|Outlook 2010 SP2 and updates KB2956191 and KB2965295 (April 14, 2015)  <br/> |MAPI over HTTP  <br/> Outlook Anywhere  <br/> |MAPI over HTTP  <br/> Outlook Anywhere  <br/> |Outlook Anywhere  <br/> |RPC  <br/> Outlook Anywhere  <br/> |
|Outlook 2010 SP2 and earlier  <br/> |Outlook Anywhere  <br/> |Outlook Anywhere  <br/> |Outlook Anywhere  <br/> |RPC  <br/> Outlook Anywhere  <br/> |
|Outlook 2007  <br/> |Outlook Anywhere  <br/> |Outlook Anywhere  <br/> |Outlook Anywhere  <br/> |RPC  <br/> Outlook Anywhere  <br/> |
   
### Prerequisites

The following software and conditions are required for clients and servers to support MAPI over HTTP with Exchange Server 2016. Once the following prerequisites are in place, see [Configure MAPI over HTTP](configure-mapi-over-http.md) to enable it in your organization. 
  
- Supported Outlook clients are Outlook 2016, Outlook 2013 SP1 or later, or Outlook 2010 SP2 with updates KB2956191 and KB2965295 (April 14, 2015).
    
- For any of your Exchange 2016 servers that aren't running on Windows Server 2012 R2, you need to upgrade the Microsoft .NET Framework to 4.5.1. For more information see [Installing the .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868).
    
- Install one of the following hotfix rollups for the .NET Framework 4.5.1 on all Exchange 2016 servers.
    
  - **Windows Server 2012 R2**: [KB 2908387](https://go.microsoft.com/fwlink/p/?LinkId=399152)
    
  - **Windows Server 2012**: [KB 2908385](https://go.microsoft.com/fwlink/p/?LinkId=399008)
    
  - **Windows Server 2008 R2 Service Pack 1**: [KB 2908383](https://go.microsoft.com/fwlink/p/?LinkId=399009)
    

