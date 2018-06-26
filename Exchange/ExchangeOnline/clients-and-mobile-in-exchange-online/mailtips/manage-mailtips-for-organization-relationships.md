---
title: "Manage MailTips for organization relationships"
ms.author: dmaguire
author: msdmaguire
manager: laurawi
ms.date: 4/8/2015
ms.audience: ITPro
ms.topic: article
ms.service: exchange-online
localization_priority: Normal
ms.assetid: 6e6b48ef-c41c-47ad-8063-66901765c2a5
description: "You can use the Exchange Management Shell to configure custom settings for MailTips between various organizations."
---

# Manage MailTips for organization relationships

You can use the Exchange Management Shell to configure custom settings for MailTips between various organizations.
  
By establishing an organizational relationship, you can enhance the user experience for both organizations by sharing free/busy data, configuring secure message flow, and enabling message tracking. For more information about organizational relationships, see [MailTips over organization relationships](mailtips-over-organization-relationships.md).
  
You can use various settings to control how MailTips are used between two organizations that have established an organizational relationship. The procedures in this section illustrate these various controls. In all examples, the on-premises organization is contoso.com, the remote organization is online.contoso.com, and the organizational relationship is named Contoso Online.
  
You use the **Set-OrganizationRelationship** cmdlet to configure these settings. 
  
## What do you need to know before you begin?

- Estimated time to complete each procedure: 5 minutes
    
- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "MailTips" entry in the [Mail flow permissions](http://technet.microsoft.com/library/f49f4fb5-af75-43cb-900f-c5f7b8cfa143.aspx) topic. 
    
- You can only use the Shell to perform this procedure.
    
- For information about keyboard shortcuts that may apply to the procedures in this topic, see **Keyboard shortcuts in the Exchange admin center**.
    
> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612),[Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351). 
  
## What do you want to do?

### Use the Shell to enable or disable MailTips between two organizations

This example configures the organizational relationship so that MailTips are returned to senders in the remote organization when composing messages to recipients in your organization. 
  
```
Set-OrganizationRelationship "Contoso Online" -MailTipsAccessEnabled $true
```

This example configures the organizational relationship to prevent MailTips from being returned to senders in the remote organization when composing messages to recipients in your organization. 
  
```
Set-OrganizationRelationship "Contoso Online" -MailTipsAccessEnabled $false
```

For detailed syntax and parameter information, see [Set-OrganizationRelationship](http://technet.microsoft.com/library/4e3b9d1d-cf41-4fd0-97e3-a0bbc816cf87.aspx).
  
### Use the Shell to configure which MailTips are returned to the remote organization

For each organizational relationship, you can determine which set of MailTips are returned to senders in the other organization. This example configures the organizational relationship so that all MailTips are returned.
  
```
Set-OrganizationRelationship "Contoso Online" -MailTipsAccessLevel All
```

This example configures the organizational relationship so that only the Automatic Replies, Oversize Message, Restricted Recipient, and Mailbox Full MailTips are returned.
  
```
Set-OrganizationRelationship "Contoso Online" -MailTipsAccessLevel Limited
```

This example configures the organizational relationship so that no MailTips are returned. 
  
> [!NOTE]
> Don't use this method to disable MailTips for this relationship. To disable MailTips, set the  _MailTipsAccessEnabled_ parameter to  `$false`. 
  
```
Set-OrganizationRelationship "Contoso Online" -MailTipsAccessLevel None
```

For detailed syntax and parameter information, see [Set-OrganizationRelationship](http://technet.microsoft.com/library/4e3b9d1d-cf41-4fd0-97e3-a0bbc816cf87.aspx).
  
### Use the Shell to configure a specific group of users for whom recipient-specific MailTips are returned

You can restrict the return of recipient-specific MailTips to a specific group of users. By default, when you enable MailTips for an organizational relationship, the following recipient-specific MailTips are returned for all users:
  
- Automatic Replies
    
- Mailbox Full
    
- Custom MailTip
    
You can specify a MailTips access group on the organizational relationship. After you specify a group, the recipient-specific MailTips are returned only for mailboxes, mail contacts, and mail users that are members of that group. This example configures the organizational relationship to return recipient-specific MailTips only for members of the ShareMailTips@contoso.com group.
  
```
Set-OrganizationRelationship "Contoso Online" -MailTipsAccessScope ShareMailTips@contoso.com
```

For detailed syntax and parameter information, see [Set-OrganizationRelationship](http://technet.microsoft.com/library/4e3b9d1d-cf41-4fd0-97e3-a0bbc816cf87.aspx).
  

