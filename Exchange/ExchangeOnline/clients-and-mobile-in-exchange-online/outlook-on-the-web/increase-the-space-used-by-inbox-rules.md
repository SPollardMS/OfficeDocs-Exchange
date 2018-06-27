---
title: "Increase the space used by Inbox rules"
ms.author: dmaguire
author: msdmaguire
manager: laurawi
ms.date: 4/29/2016
ms.audience: ITPro
ms.topic: article
ms.service: exchange-online
localization_priority: Normal
ms.assetid: 3f01edde-1cdc-4891-ad9d-7d01582664e9
description: "Outlook Web App and Outlook Inbox rules are limited to 64 KB. Each rule you create will take up space in your mailbox. The actual amount of space a rule uses depends on several factors, such as how long the name is and how many conditions you've applied. When you reach the 64-KB limit, you'll be warned that you can't create any more rules or that you can't update a rule. You can, however, increase the amount of space used by Inbox rules for a user in your organization."
---

# Increase the space used by Inbox rules

Outlook Web App and Outlook Inbox rules are limited to 64 KB. Each rule you create will take up space in your mailbox. The actual amount of space a rule uses depends on several factors, such as how long the name is and how many conditions you've applied. When you reach the 64-KB limit, you'll be warned that you can't create any more rules or that you can't update a rule. You can, however, increase the amount of space used by Inbox rules for a user in your organization.
  
> [!NOTE]
> There isn't a maximum number of rules that can be created. 
  
## Increase the limit for Inbox rules

To increase the limit:
  
1. Start a remote Exchange Management Shell session. You can only use the Exchange Management Shell to perform this procedure. To learn how to use Windows PowerShell to connect to Exchange Online, see [Connect to Exchange Online using remote PowerShell](http://technet.microsoft.com/library/c8bea338-6c1a-4bdf-8de0-7895d427ee5b.aspx).
    
2. Run the following command:  `Set-Mailbox -Identity -douglas@contoso.com -RulesQuota 256kb`
    
## What else do I need to know?

- Inbox rules are run from top to bottom in the order in which they appear in the **Rules** window. To change the order of rules, click the rule you want to move, and then click the up or down arrow to move the rule to the position you want in the list. 
    
- When you create a forwarding rule, you can add more than one address to forward to. The number of addresses you can forward to may be limited, depending on the settings for your account. If you add more addresses than are allowed, your forwarding rule won't work. If you create a forwarding rule with more than one address, test it to be sure it works.
    

