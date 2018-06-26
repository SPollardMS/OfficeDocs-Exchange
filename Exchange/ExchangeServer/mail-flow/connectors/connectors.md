---
title: "Connectors"
ms.author: chrisda
author: chrisda
manager: serdars
ms.date: 6/7/2018
ms.audience: ITPro
ms.topic: hub-page
ms.prod: exchange-server-itpro
localization_priority: Normal
ms.assetid: 73559b0c-fc0e-41fd-84df-d07442137a0c
description: "Summary: Learn how connectors are used in Exchange 2016 for incoming and outgoing mail flow in your organization."
---

# Connectors

 **Summary**: Learn how connectors are used in Exchange 2016 for incoming and outgoing mail flow in your organization.
  
Exchange uses connectors to enable incoming and outgoing mail flow on Exchange servers, and also between services in the transport pipeline on the local Exchange server.
  
These are the types of connectors that are available in Exchange.
  
****

|**Connector**|**Description**|
|:-----|:-----|
|Receive connectors  <br/> |Receive connectors control incoming SMTP mail flow. They listen for incoming connections that match the configuration of the connector. Multiple default Receive connectors are created when you install Exchange.  <br/> For more information, see [Receive connectors](receive-connectors.md).  <br/> |
|Send connectors  <br/> |Send connectors control outgoing SMTP mail flow. A Send connector is chosen based on the message recipients and the configuration of the connector. No default Send connectors for external mail flow are created when you install Exchange, but implicit and invisible Send connectors exist, and are used to route mail between internal Exchange servers.  <br/> For more information, see [Receive connectors](receive-connectors.md).  <br/> |
|Delivery agents and Delivery Agent Connectors  <br/> |Delivery agents and Delivery Agent connectors control outgoing mail flow to non-SMTP systems. Outgoing messages are put into message queues for delivery to the non-SMTP system. Delivery agents and Delivery agent connectors are preferred over Foreign connectors due to their improved performance and management.  <br/> For more information, see [Delivery Agents and Delivery Agent Connectors](http://technet.microsoft.com/library/38c942ee-b59d-47ec-87eb-bebad441ada5.aspx).  <br/> |
|Foreign connectors  <br/> |Foreign connectors control outgoing mail flow to non-SMTP systems. Outgoing messages are written to files in a location called the Drop directory to be picked up by the non-SMTP system.  <br/> For information, see [Foreign Connectors](http://technet.microsoft.com/library/21c6a7a9-f4d2-4359-9ac9-930701b63a4e.aspx).  <br/> |
   

