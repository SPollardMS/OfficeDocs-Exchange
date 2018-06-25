---
title: "Shared free/busy in Exchange hybrid deployments"
ms.author: dstrome
author: dstrome
manager: laurawi
ms.date: 4/30/2016
ms.audience: Developer
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.collection: Ent_O365_Hybrid
ms.assetid: bd3884de-80ee-4ff2-a8a3-eacd5aa3e51b
description: "Sharing free/busy (calendar availability) information between users located on-premises and in the Exchange Online organization is one of the primary benefits of a hybrid deployment. Users in both organizations can view each other's calendars just as if they were located in the same physical organization. This makes scheduling meetings and resources easy and efficient."
---

# Shared free/busy in Exchange hybrid deployments

Sharing free/busy (calendar availability) information between users located on-premises and in the Exchange Online organization is one of the primary benefits of a hybrid deployment. Users in both organizations can view each other's calendars just as if they were located in the same physical organization. This makes scheduling meetings and resources easy and efficient.
  
Several components in a hybrid deployment are required to enable the shared free/busy feature between your on-premises Exchange organization and Exchange Online.
  
- **Federation trust** Both the on-premises and Office 365 service organizations need to have a federation trust established with the Azure AD authentication system. A federation trust is a one-to-one relationship with the Azure AD authentication system that defines parameters for your Exchange organization. The system uses these parameters when acting as a trust broker between your on-premises and Office 365 service organization to exchange free/busy information between on-premises and Exchange Online organization users. 
    
    A federation trust with the system is automatically configured for your Office 365 service organization when the account is created. The Hybrid Configuration wizard automatically checks to see if there is an existing federation trust with the Azure AD authentication system for the on-premises organization. If present, the existing federation trust is used to support the hybrid deployment. If not present, the wizard creates a federation trust for the on-premises organization with the Azure AD authentication system. The wizard also adds any domains selected within the Hybrid Configuration wizard to the on-premises organization federation trust.
    
    Learn more at [Understanding Federated Sharing](http://technet.microsoft.com/library/09e6732a-4e99-44d0-801d-9463fdc57a9b.aspx).
    
- **Organization relationships** Organization relationships are needed for both the on-premises and Exchange Online organization and are configured automatically by the Hybrid Configuration wizard. An organization relationship defines the level of free/busy information shared for an organization. 
    
    By default, the free/busy data access sharing level is **Free/busy access with time, plus subject and location** for both the on-premises and Exchange Online organization relationships. If you want to modify the free/busy sharing access between your on-premises and Exchange Online organization users, you can manually configure the organization relationship access level after the Hybrid Configuration wizard has completed. 
    
    Learn more at [Understanding Federated Sharing](http://technet.microsoft.com/library/09e6732a-4e99-44d0-801d-9463fdc57a9b.aspx).
    
When configuring your organization for a hybrid deployment, configuring shared free/busy calendar access is automatically configured by the Hybrid Configuration wizard in all scenarios. Creating a federation trust with the Azure AD authentication system and configuring organization relationships for the on-premises and Exchange Online organization are hybrid deployment requirements. If you don't want to allow free/busy sharing between your on-premises and Exchange Online organization users in the hybrid deployment, you can manually disable free/busy sharing by using the Exchange Management Shell and the [Set-HybridConfiguration](http://technet.microsoft.com/library/64bd673d-0f1c-4ed5-91dc-f19328942d71.aspx) cmdlet after the Hybrid Configuration wizard has completed. 
  
The hybrid deployment features shown in the following table have a dependency on federation trusts and organization relationships.
  
|**Messaging area**|**Feature**|
|:-----|:-----|
|Email client  <br/> | Message tracking  <br/>  MailTips  <br/>  Multi-mailbox search  <br/> |
|Compliance  <br/> | Exchange Online Archiving  <br/>  Exchange In-place eDiscovery  <br/> |
   

