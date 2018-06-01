---
title: "Default settings for Exchange virtual directories"
ms.author: dmaguire
author: msdmaguire
manager: serdars
ms.date: 4/19/2018
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: d2d89ce6-4721-4737-a325-fba5ad9422e0
description: "Summary: Learn about default settings for Client Access services on Mailbox servers in Exchange 2016."
---

# Default settings for Exchange virtual directories

 **Summary**: Learn about default settings for Client Access services on Mailbox servers in Exchange 2016.
  
Exchange 2016 automatically configures multiple Internet Information Services (IIS) virtual directories during installation. The tables that follow show the Exchange 2016 settings for the Client Access services on Mailbox servers and the default IIS authentication and Secure Sockets Layer (SSL) settings.
  
## Client Access services on Mailbox servers

The following table lists the default settings on a stand-alone Exchange 2016 Mailbox server running Client Access services.
  
**Default Mailbox server running Client Access services IIS authentication and SSL settings**

|**Virtual directory**|**Authentication method**|**SSL settings**|**Management method**|
|:-----|:-----|:-----|:-----|
|Default website  <br/> | Anonymous  <br/> | Required  <br/> |IIS management console  <br/> |
|aspnet_client  <br/> | Anonymous authentication  <br/> | SSL required  <br/>  Requires 128-bit encryption  <br/> |IIS management console  <br/> |
|Autodiscover  <br/> | Anonymous authentication  <br/>  Basic authentication  <br/>  Windows authentication  <br/> | SSL required  <br/>  Requires 128-bit encryption  <br/> |Exchange Management Shell  <br/> |
|ecp  <br/> | Anonymous authentication  <br/>  Basic authentication  <br/> | SSL required  <br/>  Requires 128-bit encryption  <br/> |Exchange admin center (EAC) or Exchange Management Shell  <br/> |
|EWS  <br/> | Anonymous authentication  <br/>  Windows authentication  <br/> | SSL required  <br/>  Requires 128-bit encryption  <br/> |Exchange Management Shell  <br/> |
|Microsoft-Server-ActiveSync  <br/> | Basic authentication  <br/> | SSL required  <br/>  Requires 128-bit encryption  <br/> |EAC or Exchange Management Shell  <br/> |
|OAB  <br/> | Windows authentication  <br/> | Not required  <br/> |EAC or Exchange Management Shell  <br/> |
|OWA  <br/> | Basic authentication  <br/> | SSL required  <br/>  Requires 128-bit encryption  <br/> |EAC or Exchange Management Shell  <br/> |
|PowerShell  <br/> | Anonymous authentication  <br/> | Not required  <br/> |Exchange Management Shell  <br/> |
|Rpc  <br/> | Basic authentication  <br/>  Windows authentication  <br/> | SSL required  <br/>  Requires 128-bit encryption  <br/> |Exchange Management Shell  <br/> |
|RpcWithCert  <br/> |By default, all authentication methods are disabled.  <br/> | Required  <br/> | <br/> |
   
## Mailbox server

The following table lists the default settings on a stand-alone Exchange 2016 Mailbox server.
  
**Default Mailbox server IIS authentication and SSL settings**

|**Virtual directory**|**Authentication method**|**SSL settings**|**Management method**|
|:-----|:-----|:-----|:-----|
|Default website  <br/> | Anonymous authentication  <br/> | SSL required  <br/>  Requires 128-bit encryption  <br/> |This virtual directory can't be configured by the user.  <br/> |
|PowerShell  <br/> | Anonymous authentication  <br/> | Not required  <br/> |Exchange Management Shell  <br/> |
   
## See also

[Virtual directory management](http://technet.microsoft.com/library/1af30fd5-621c-4acb-b6df-d8fa64d719ba.aspx)

