---
title: "Organization relationships in Exchange Online"
ms.author: dstrome
author: dstrome
manager: scotv
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.service: exchange-online
localization_priority: Normal
ms.assetid: 58ac4338-b883-404f-a6be-eca38ccd8088
description: "Set up an organization relationship to share calendar information with an external business partner. Office 365 admins can set up an organization relationship with another Office 365 organization or with an Exchange on-premises organization. If you want to share calendars with an on-premises Exchange organization, the on-premises Exchange administrator has to set up an authentication relationship with the cloud (also known asfederation) and must meet minimum software requirements."
---

# Organization relationships in Exchange Online

Set up an organization relationship to share calendar information with an external business partner. Office 365 admins can set up an organization relationship with another Office 365 organization or with an Exchange on-premises organization. If you want to share calendars with an on-premises Exchange organization, the on-premises Exchange administrator has to set up an authentication relationship with the cloud (also known as "federation") and must meet minimum software requirements. 
  
An organization relationship is a one-to-one relationship between businesses to allow users in each organization to view calendar availability information. When you set up the organization relationship, you are setting up your side of the relationship and specifying the level of information that the users in the external organization can view. The external organization may set up the same or different settings on their side. For example, if Contoso creates an organization relationship with Tailspin Toys, the users at Tailspin Toys will be able to schedule meetings with the users at Contoso by adding their email address to the meeting invitation. The availability of the invited Contoso user would display to the Tailspin Toys user. However, before Contoso can also see availability for users at Tailspin Toys, their administrator needs to set up an organization relationship with Contoso.
  
There are three of levels of access that you can specify:
  
- No access
    
- Access to availability (free/busy) time only
    
- Access to free/busy, including time, subject, and location
    
> [!NOTE]
> If users don't want to share their free/busy information with others, they can change the Default permission entry in Outlook. To do this, users go to the **Calendar Properties** \> **Permissions** tab, select the **Default** permission, and select **None** from the **Permission Level** list. Their free/busy information won't be seen by internal or external users, even if an organization relationship exists. The permissions set by the user will apply. 
  
The following topics will help you configure and manage organization relationships:
  
[Create an organization relationship in Exchange Online](create-an-organization-relationship.md)
  
[Modify an organization relationship in Exchange Online](modify-an-organization-relationship.md)
  
[Remove an organization relationship in Exchange Online](remove-an-organization-relationship.md)
  

