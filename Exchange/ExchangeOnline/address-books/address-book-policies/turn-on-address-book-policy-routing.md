---
title: "Turn on address book policy routing"
ms.author: kwekua
author: kwekua
manager: scotv
ms.date: 4/29/2016
ms.audience: ITPro
ms.topic: article
ms.service: exchange-online
localization_priority: Normal
ms.assetid: 5627b8ac-0551-4558-b3b6-25c402698426
description: "Estimated time to complete: 5 minutes"
---

# Turn on address book policy routing

 **Estimated time to complete: 5 minutes**
  
Address book policy (ABP) routing controls how users in one virtual organization view the users of a different virtual organization. Your virtual organization is determined by the global address list (GAL) you reside in. When ABP routing is turned on, users that are assigned to different GALs appear as external recipients and won't be able to view external recipients' contact cards. 
  
Looking for the Exchange Server version of this topic? See [Install and Configure the Address Book Policy Routing Agent](http://technet.microsoft.com/library/20e8a43d-4508-4388-a2c9-aa3073593cc2.aspx).
  
> [!NOTE]
> By default, the Address List role isn't assigned to any role groups. To use any cmdlets that require the Address List role, you need to add the role to a role group. For details, see the "Add a role to a role assignment policy" section of **Manage role assignment policies**. 
  
## Use the Exchange Management Shell to turn on ABP routing

You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Transport configuration" entry in the [Mail flow permissions](http://technet.microsoft.com/library/f49f4fb5-af75-43cb-900f-c5f7b8cfa143.aspx) topic. 
  
> [!NOTE]
> You can't use the Exchange admin center (EAC) to perform this procedure. You must use the Exchange Management Shell. 
  
This example turns on ABP routing for the entire Exchange organization:
  
```
Set-TransportConfig -AddressBookPolicyRoutingEnabled $true
```

For detailed syntax and parameter information, see [Set-TransportConfig](http://technet.microsoft.com/library/ad3910a5-2227-47a2-8ccc-a208ce6210bb.aspx).
  
## For more information

> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612),[Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351). 
  
For information about keyboard shortcuts that may apply to the procedures in this topic, see **Keyboard shortcuts in the Exchange admin center**.
  

