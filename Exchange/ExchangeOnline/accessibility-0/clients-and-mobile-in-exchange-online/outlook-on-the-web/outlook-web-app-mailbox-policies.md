---
title: "Outlook Web App mailbox policies"
ms.author: dmaguire
author: msdmaguire
manager: laurawi
ms.date: 6/25/2018
ms.audience: ITPro
ms.topic: overview
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 213b8b7a-1c29-49ee-8c98-d0364ddf4f9d
description: "Use Microsoft Outlook Web App mailbox policies to create organization-level policies to manage access to features in Outlook Web App."
---

# Outlook Web App mailbox policies

Use Microsoft Outlook Web App mailbox policies to create organization-level policies to manage access to features in Outlook Web App.
  
## Outlook Web App mailbox policies
<a name="OWA"> </a>

In Exchange 2013, you can create multiple Outlook Web App mailbox policies and apply them to individual mailboxes. When an Outlook Web App mailbox policy is applied to a mailbox, it will override the settings of the virtual directory.
  
Outlook Web App features can also be managed by configuring the Outlook Web App virtual directories. Virtual directory settings will be used for any mailbox that a mailbox policy hasn't been applied to.
  
## Creating or deleting Outlook Web App mailbox policies
<a name="Create"> </a>

A default Outlook Web App mailbox policy is created automatically when Exchange is installed. By default, all options are enabled on the default Outlook Web App mailbox policy. You can create as many Outlook Web App mailbox policies as necessary to meet the needs of your organization.
  
> [!NOTE]
> The default Outlook Web App mailbox policy isn't automatically applied to any mailboxes. 
  
For information about creating or removing mailbox policies, see [Create an Outlook Web App mailbox policy](create-outlook-web-app-mailbox-policy.md) and [Remove an Outlook Web App mailbox policy from Exchange](remove-outlook-web-app-mailbox-policy.md).
  
## Configuring Outlook Web App mailbox policies
<a name="Configuring"> </a>

The default Outlook Web App mailbox policy has all options enabled by default. For information about configuring Outlook Web App mailbox policies, see [View or configure Outlook Web App mailbox policy properties](configure-outlook-web-app-mailbox-policy-properties.md).
  
## Applying Outlook Web App mailbox policies
<a name="Applying"> </a>

Only one Outlook Web App mailbox policy can be applied to a mailbox.
  
If there's no Outlook Web App mailbox policy applied to a mailbox, the settings defined on the virtual directory will be applied.
  
An Outlook Web App mailbox policy can be applied to a mailbox by using the Exchange Administration Center (EAC) to modify an existing mailbox, or by using the Shell and the [Set-CASMailbox](http://technet.microsoft.com/library/ff7d4dc5-755e-4005-a0a3-631eed3f9b3b.aspx) cmdlet to apply a mailbox policy. For more information, see [Apply or remove an Outlook Web App mailbox policy on a mailbox](apply-or-remove-outlook-web-app-mailbox-policy.md).
  

