---
title: "Remove an organization relationship in Exchange Online"
ms.author: dstrome
author: dstrome
manager: scotv
ms.date: 4/29/2016
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 3de9e885-73f5-4743-9b55-38ef59a387f2
description: "An organization relationship lets users in your Office 365 organization share calendar free/busy information with other Office 365 or on-premises Exchange organizations. You can remove an organization relationship to disable calendar sharing with the other organization."
---

# Remove an organization relationship in Exchange Online

An organization relationship lets users in your Office 365 organization share calendar free/busy information with other Office 365 or on-premises Exchange organizations. You can remove an organization relationship to disable calendar sharing with the other organization.
  
To learn more about organization relationships, see [Organization relationships in Exchange Online](organization-relationships-0.md).
  
## What do you need to know before you begin?

- Estimated time to complete: 5 minutes.
    
- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the [Permissions in Exchange Online](../../permissions/permissions.md) topic. 
    
## What do you want to do?

### Use the Exchange admin center to remove an organization relationship
<a name="BKMK_EAC"> </a>

1. From the Office 365 admin center go to **Admin** \> **Exchange**.
    
2. Go to **organization** \> **sharing**.
    
3. Under **Organization Sharing**, select an organization relationship, and then click **Delete**![Delete icon](../../media/ITPro_EAC_DeleteIcon.gif).
    
4. In the warning that appears, click **yes**.
    
### Use the Exchange Management Shell to remove an organization relationship
<a name="BKMK_Shell"> </a>

This example removes the organization relationship Contoso. 
  
```
Remove-OrganizationRelationship -Identity "Contoso"
```

For detailed syntax and parameter information, see [Remove-OrganizationRelationship](http://technet.microsoft.com/library/fd646344-c783-45b2-b666-f50e823cba58.aspx).
  
## How do you know this worked?

To verify that you have successfully removed the organization relationship, do one of the following:
  
- In the Exchange admin center, go to **organization** \> **sharing** and verify that the organization relationship isn't displayed in the list view under **Organization Sharing**.
    
- Run the following Exchange Management Shell command to verify the organization relationship information is removed.
    
  ```
  Get-OrganizationRelationship | Format-List
  ```

> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612),[Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351). 
  

