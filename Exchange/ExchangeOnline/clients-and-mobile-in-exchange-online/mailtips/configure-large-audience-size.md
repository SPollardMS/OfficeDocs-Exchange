---
title: "Configure the large audience size for your organization"
ms.author: dmaguire
author: msdmaguire
manager: laurawi
ms.date: 4/8/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 8a37911c-4339-4921-b5d3-0a5a774d4517
description: "You can use the Exchange Management Shell to configure various settings that define how you use MailTips in your organization."
---

# Configure the large audience size for your organization

You can use the Exchange Management Shell to configure various settings that define how you use MailTips in your organization.
  
## What do you need to know before you begin?

- Estimated time to complete: 5 minutes
    
- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "MailTips" entry in the [Mail flow permissions](http://technet.microsoft.com/library/f49f4fb5-af75-43cb-900f-c5f7b8cfa143.aspx) topic. 
    
- You can only use the Shell to perform this procedure.
    
- For information about keyboard shortcuts that may apply to the procedures in this topic, see **Keyboard shortcuts in the Exchange admin center**.
    
> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612),[Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351). 
  
## Use the Shell to configure the large audience size for your organization

You use the **Set-OrganizationConfig** cmdlet to configure the large audience size for your organization. When senders address messages to more recipients than the size you configure, they are shown the Large Audience MailTip. The large audience size is set to 25 by default. This example configures the large audience size to 50 in your organization. 
  
```
Set-OrganizationConfig -MailTipsLargeAudienceThreshold 50
```

For detailed syntax and parameter information, see [set-OrganizationConfig](http://technet.microsoft.com/library/3b6df0fe-27c8-415f-ad0c-8b265f234c1a.aspx).
  

