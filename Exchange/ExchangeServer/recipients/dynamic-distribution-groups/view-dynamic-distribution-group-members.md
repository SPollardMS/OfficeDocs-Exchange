---
title: "View members of a dynamic distribution group"
ms.author: dmaguire
author: msdmaguire
manager: serdars
ms.date: 6/8/2018
ms.audience: ITPro
ms.topic: article
ms.prod: exchange-server-itpro
localization_priority: Normal
ms.assetid: 40b100c6-864e-4c82-9f98-08dd5c83e378
description: "Summary: Learn how to use the Exchange Management Shell to view dynamic distribution group membership."
---

# View members of a dynamic distribution group

 **Summary**: Learn how to use the Exchange Management Shell to view dynamic distribution group membership.
  
Dynamic distribution groups are distribution groups whose membership is based on specific recipient filters rather than a defined set of recipients. For more information, see [Manage dynamic distribution groups](dynamic-distribution-groups.md).
  
You can't use the Exchange admin center (EAC) to view the members of a dynamic distribution group. You can only use the Exchange Management Shell.
  
## What do you need to know before you begin?

- Estimated time to complete: 2 minutes.
    
- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Dynamic distribution groups" entry in the [Recipients Permissions](../../permissions/feature-permissions/recipient-permissions.md) topic.
    
- For information about keyboard shortcuts that may apply to the procedures in this topic, see [Keyboard shortcuts in the Exchange admin center](../../about-documentation/exchange-admin-center-keyboard-shortcuts.md).
    
> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at: [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351)..
  
## Use the Exchange Management Shell to view the members of a dynamic distribution group
<a name="Shell"> </a>

This example returns the list of members for the dynamic distribution group named Full Time Employees. The first command stores the dynamic distribution group object in the variable `$FTE`. The second command uses the **Get-Recipient** cmdlet to list the recipients that match the criteria defined for the dynamic distribution group.
  
```
$FTE = Get-DynamicDistributionGroup "Full Time Employees"
```

```
Get-Recipient -RecipientPreviewFilter $FTE.RecipientFilter -OrganizationalUnit $FTE.RecipientContainer
```

For detailed syntax and parameter information, see [Get-DynamicDistributionGroup](http://technet.microsoft.com/library/d97ee738-dfa1-464b-855a-4242e8065473.aspx) and [Get-Recipient](http://technet.microsoft.com/library/2ce6250f-0ad3-4b29-870c-e1d6e1e154bc.aspx).
  

