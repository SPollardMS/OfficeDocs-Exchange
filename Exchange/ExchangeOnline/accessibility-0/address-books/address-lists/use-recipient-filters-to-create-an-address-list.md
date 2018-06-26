---
title: "Create an address list by using recipient filters"
ms.author: kwekua
author: kwekua
manager: scotv
ms.date: 12/16/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 8eabea64-97c6-40af-b61c-9b6a125cbdf1
description: "This topic explains how to create an address list by using recipient filters. To learn more about address lists, see Address lists."
---

# Create an address list by using recipient filters

This topic explains how to create an address list by using recipient filters. To learn more about address lists, see [Address lists](address-lists.md). 
  
For additional management tasks related to address lists, see [Managing Address Lists](http://technet.microsoft.com/library/44c87349-964b-4700-9ce9-87bd4cb2249e.aspx).
  
## What do you need to know before you begin?

- Estimated time to complete each procedure: 5 minutes.
    
- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Address lists" entry in the [Email Address and Address Book Permissions](http://technet.microsoft.com/library/1c1de09d-16ef-4424-9bfb-eb7edffbc8c2.aspx) topic. 
    
- By default in Exchange Online, the Address List role isn't assigned to any role groups. To use any cmdlets that require the Address List role, you need to add the role to a role group. For more information, see the "Add a role to a role group" section in the topic, **Manage role groups**.
    
- To use the  _RecipientFilter_ parameter to create a custom filter, you must specify a string for the filter. The Shell uses OPATH for the filtering syntax. OPATH is a querying language designed to query object data sources. 
    
- You can't use the Exchange Administration Center (EAC) to perform this procedure. You must use the Shell.
    
- For information about keyboard shortcuts that may apply to the procedures in this topic, see **Keyboard shortcuts in the Exchange admin center**.
    
> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612),[Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351). 
  
## Use the Shell to create an address list by using recipient filters

This example creates an address list for all users with Exchange mailboxes who reside in Washington or Oregon.
  
```
New-AddressList -Name "Pacific Northwest Mailboxes" -RecipientFilter {((RecipientType -eq 'UserMailbox') -and ((StateOrProvince -eq 'Washington') -or (StateOrProvince -eq 'Oregon')))}
```

This example creates an address list for all users with Exchange mailboxes who have  `AgencyB` as the value for the  _CustomAttribute15_ parameter. 
  
```
New-AddressList -Name "AgencyB" -RecipientFilter {(RecipientType -eq 'UserMailbox') -and (CustomAttribute15 -like *AgencyB*)}
```

For detailed syntax and parameter information, see [New-AddressList](http://technet.microsoft.com/library/2bcee6db-01d4-40ad-9595-33356a4025c5.aspx).
  

