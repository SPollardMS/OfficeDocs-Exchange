---
title: Availability service in Exchange 2016
ms.prod: EXCHANGE
ms.assetid: 9722dea2-2bf8-437c-85c0-3ab65b8a07b9
---


# Availability service in Exchange 2016
 **Summary**: Learn about the improvements to reliability that the Availability service offers in Exchange 2016 .
The Exchange 2016 Availability service makes free/busy information available to Outlook and Outlook on the web (previously known as Outlook Web App) clients. The Availability service improves information workers' calendaring and meeting scheduling experience by providing secure, consistent, and up-to-date free/busy information.
  
    
    

Outlook and Outlook on the web use the Availability service to perform the following tasks:
- Retrieve current free/busy information for Exchange 2016 mailboxes
    
  
- Retrieve current free/busy information from other Exchange 2016 organizations
    
  
- Retrieve published free/busy information from public folders for mailboxes on servers that have previous versions of Exchange 
    
  
- View attendee working hours
    
  
- Show meeting time suggestions
    
  

## How the availability service works in Exchange 2016
<a name="overview"> </a>

The Availability service retrieves free/busy information directly from the target mailbox for users on Exchange 2016Exchange 2016, Exchange 2010, or Exchange 2007 and can be configured to retrieve free/busy information for users on earlier versions of Exchange. For topologies that have Exchange 2007, Exchange 2010, or Exchange 2016 mailboxes in which all clients are running Outlook 2007 or higher, the Availability service is used to retrieve free/busy information.
  
    
    
Outlook uses the Exchange Autodiscover service to obtain the URL of the Availability service. For more information about the Autodiscover service, see  [Autodiscover service](autodiscover-service.md).
  
    
    
You can use the Exchange Management Shell to configure the Availability service. You can't use the Exchange admin center (EAC) to configure the Availability service.
  
    
    
The Availability service is part of the Exchange 2016 programming interface. It's available as a web service to let developers write third-party tools for integration purposes.
  
    
    

## Availability service and automatic reply messages
<a name="infoaboutawaystatus"> </a>

The Availability service provides access to automatic-reply messages that users send when they are out of the office or away for an extended period of time.
  
    
    
Information workers use the Automatic Replies feature (formerly known as Out of Office) in Outlook and Outlook on the web to alert others when they're unavailable to respond to email messages. This functionality makes it easier to set and manage automatic-reply messages for both information workers and administrators.
  
    
    

## Methods used to retrieve free/busy information
<a name="methodstoretrivefbinfo"> </a>

The following table lists the methods used to retrieve free/busy information in different single-forest topologies.
  
    
    


|**Client**|**Mailbox retrieving free/busy information is running**|**Target mailbox is running**|**Free/busy retrieval method**|
|:-----|:-----|:-----|:-----|
|Outlook 2016 or Outlook 2013  <br/> |Exchange 2016,Exchange 2013, or Exchange 2010  <br/> |Exchange 2016, Exchange 2013, or Exchange 2010  <br/> |The Availability service reads free/busy information from the target mailbox.  <br/> |
|Outlook on the web  <br/> |Exchange 2016, Exchange 2013, or Exchange 2010  <br/> |Exchange 2016, Exchange 2013, or Exchange 2010  <br/> |Outlook Web App in Exchange 2010 calls the Availability service API, which reads the free/busy information from the target mailbox.  <br/> |
   

