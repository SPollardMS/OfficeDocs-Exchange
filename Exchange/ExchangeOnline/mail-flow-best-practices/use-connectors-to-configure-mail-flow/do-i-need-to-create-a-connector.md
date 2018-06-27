---
title: "Do I need to create a connector?"
ms.author: supotter
author: supotter
manager: scotv
ms.date: 6/29/2015
ms.audience: ITPro
ms.topic: article
f1_keywords:
- 'ms.exch.eac.ConnectorIsConnectorNeeded'
ms.service: exchange-online
localization_priority: Normal
ms.assetid: 16731ae9-c909-49dd-bffc-a46e6151fc29

description: "Find your mail flow scenario to see if you need to create a connector for your organization."
---

# Do I need to create a connector?

Find your mail flow scenario to see if you need to create a connector for your organization. 
  
|
|
|****Scenario****|****What does this mean?****|****Connector required?****|****When creating the connectors, select these options****|
|:-----|:-----|:-----|:-----|
|You have a standalone Exchange Online Protection (EOP) subscription.  <br/> |You have your own email servers (also called on-premises servers), and you subscribe to EOP only for email protection services.  <br/> For details, check **Exchange Online Protection overview** and [How do Office 365 connectors work with my own email servers (also called "on-premises servers")?](set-up-connectors-to-route-mail.md#HowdoconnectorsinEOP) .  <br/> |Yes  <br/> |**Connector for incoming email:**         From: Your organization's email server          To: Office 365  <br/> **Connector for outgoing email**:           From: Office 365          To: Your organization mail server  <br/> |
|You have an Exchange Online subscription, and some of your mailboxes are on your email servers.  <br/> |Some of your mailboxes are in Microsoft Exchange Online, and some are on your email servers (also called on-premises servers). Before you set up connectors, check whether you only need connectors or if an Exchange hybrid deployment better meets your business needs.  <br/> For details, check [What if I have EOP or Exchange Online and my own email servers?](use-connectors-to-configure-mail-flow.md#WhatifIhave1) and **Exchange Server Hybrid Deployments**.  <br/> |Yes  <br/> |**Connector for incoming email:**         From: Your organization's email server          To: Office 365  <br/> **Connector for outgoing email:**         From: Office 365          To: Your organization's email server  <br/> |
|You have an Exchange Online subscription, and your organization needs to send email messages from non-mailboxes, such as printers.  <br/> |You don't have email servers (also called on-premises servers), but you want to let people send email messages from sources such as printers, fax machines, or apps.  <br/> For details, check **How to Allow a Multi-function Device or Application to Send E-mail through Office 365 Using SMTP**.  <br/> |Optional  <br/> |**Only one connector needed:**         From: Your organization's email server          To: Office 365  <br/> |
|You often exchange email with business partners, and you want to apply certain security restrictions.  <br/> |When your users exchange email messages with people in partner organizations, you want to make sure that any shared sensitive information is protected. You can do this by using Transport Layer Security (TLS) or by limiting the mail's source destination.  <br/> For details, check [Set up connectors for secure mail flow with a partner organization](set-up-connectors-for-secure-mail-flow-with-a-partner.md).  <br/> |Optional  <br/> |**Connector for incoming email:**         From: Partner organization          To: Office 365  <br/> **Connector for outgoing email:**         From: Office 365          To: Partner organization  <br/> |
   
> [!NOTE]
> For more information about these scenarios, see [Configure mail flow using connectors in Office 365](use-connectors-to-configure-mail-flow.md). 
  

