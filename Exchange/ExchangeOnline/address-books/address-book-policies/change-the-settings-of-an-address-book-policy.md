---
title: "Change the settings of an address book policy"
ms.author: kwekua
author: kwekua
manager: scotv
ms.date: 3/30/2016
ms.audience: ITPro
ms.topic: article
ms.service: exchange-online
localization_priority: Normal
ms.assetid: ba1ca350-71c2-4c60-a612-33bfa9320b5e
description: "After you create an address book policy (ABP), you can view or modify the name and the assigned global address list (GAL), offline address book (OAB), room list, and address lists."
---

# Change the settings of an address book policy

After you create an address book policy (ABP), you can view or modify the name and the assigned global address list (GAL), offline address book (OAB), room list, and address lists.
  
For additional management tasks related to ABPs, see [Managing Address Book Policies](http://technet.microsoft.com/library/1204db89-ee4b-459a-8c14-e8d60dd6c4a4.aspx).
  
## What do you need to know before you begin?

- Estmated time to complete: Less than 5 minutes.
    
- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Address book policies" entry in the [Email Address and Address Book Permissions](http://technet.microsoft.com/library/1c1de09d-16ef-4424-9bfb-eb7edffbc8c2.aspx) topic. 
    
- Creating an ABP for an organization is a multi-step process that requires planning. For more information, see [Scenario: Deploying Address Book Policies](http://technet.microsoft.com/library/6ac3c87d-161f-447b-afb2-149ae7e3f1dc.aspx)
    
- You can't use the Exchange Administration Center (EAC) to configure ABPs. You must use the Shell.
    
- For information about keyboard shortcuts that may apply to the procedures in this topic, see **Keyboard shortcuts in the Exchange admin center**.
    
- Having problems? Ask for help in the Exchange forums. Visit the forums at [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612),[Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351).
    
## What do you want to do?

### Change the OAB, room list, and GAL for an ABP
<a name="UseShell"> </a>

This example changes the OAB, room list, and GAL that will be used by mailbox users who are assigned the ABP named All Fabrikam ABP. 
  
```
Set-AddressBookPolicy -Identity "All Fabrikam ABP" -OfflineAddressBook \Fabrikam-OAB-2 -GlobalAddressList "\All Fabrikam GAL" -RoomList "\All Fabrikam Rooms"
```

### Replace address lists in an ABP
<a name="UseShell"> </a>

The address lists that you specify for an existing ABP replace all address lists in the ABP.
  
This example replaces the existing address lists with the address lists named GovernmentAgencyA-Atlanta and GovernmentAgencyA-Moscow for the ABP named Government Agency A.
  
```
Set-AddressBookPolicy -Identity "Government Agency A" -AddressLists "GovernmentAgencyA-Atlanta","GovernmentAgencyA-Moscow"
```

### Add address lists to an ABP
<a name="UseShell"> </a>

To preserve address lists that are already defined in an ABP, you need to specify those address lists when you add new ones to the ABP.
  
This example adds the address list named Contoso-Chicago to the ABP named ABP Contoso, which is already configured to use the address list named Contoso-Seattle.
  
```
Set-AddressBookPolicy -Identity "ABP Contoso" -AddressLists "Contoso-Chicago","Contoso-Seattle"
```

### Remove address lists from an ABP
<a name="UseShell"> </a>

To remove existing address lists that are already defined in an ABP, you need to specify the address lists that you want to keep.
  
For example, the ABP named ABP Fabrikam uses the address lists named Fabrikam-HR and Fabrikam-Finance. To remove the Fabrikam-HR address list from the ABP, specify the Fabrikam-Finance address list that you want to keep.
  
```
Set-AddressBookPolicy -Identity "ABP Fabrikam" -AddressLists Fabrikam-Finance
```

## For more information

For detailed syntax and parameter information, see [Set-AddressBookPolicy](http://technet.microsoft.com/library/c0dc5fff-af06-4008-9173-629d1f901c69.aspx).
  

