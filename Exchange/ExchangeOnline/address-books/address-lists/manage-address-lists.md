---
title: "Manage address lists in Exchange Online"
ms.author: kwekua
author: kwekua
manager: scotv
ms.date: 3/8/2016
ms.audience: ITPro
ms.topic: article
ms.service: exchange-online
localization_priority: Normal
ms.assetid: cac74760-7bd1-482c-8d43-b0165e988ec0
description: "Address lists are a collection of mail-enabled objects in your organization. Mail-enabled objects are any object in your organization that has an email address. Each address list can contain one or more types of objects (for example, users, contacts, groups, public folders, and room and equipment mailboxes). Address lists also provide a way to partition mail-enabled objects for the benefit of specific groups of users. This topic explains how to manage address lists in Exchange Online."
---

# Manage address lists in Exchange Online

Address lists are a collection of mail-enabled objects in your organization. Mail-enabled objects are any object in your organization that has an email address. Each address list can contain one or more types of objects (for example, users, contacts, groups, public folders, and room and equipment mailboxes). Address lists also provide a way to partition mail-enabled objects for the benefit of specific groups of users. This topic explains how to manage address lists in Exchange Online.
  
For additional management tasks related to manage address lists, see [Address list procedures in Exchange Online](address-list-procedures.md).
  
Looking for the Exchange 2013 version of this topic? See [Create an Address List](http://technet.microsoft.com/library/e86ba1b7-c41c-4050-bc29-13996cf53c59.aspx).
  
## What do you need to know before you begin?

- Estimated time to complete each procedure: 5 minutes.
    
- You can only use the Shell to perform this procedure. To learn how to use Windows PowerShell to connect to Exchange Online, see [Connect to Exchange Online PowerShell](https://go.microsoft.com/fwlink/p/?linkid=396554).
    
- In Exchange Online, the **\*-AddressList** cmldets are only available in the Address Lists management role. By default in Exchange Online, the Address List role isn't assigned to any role groups. To use any cmdlets that require the Address List role, you need to add the role to a role group. For more information, see the "Add a role to a role group" section in the topic, **Manage role groups**.
    
- For information about keyboard shortcuts that may apply to the procedures in this topic, see **Keyboard shortcuts in the Exchange admin center**.
    
> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612),[Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351). 
  
## What do you want to do?

### Create an address list

This example creates the address list named Oregon and Washington Users by using the  _RecipientFilter_ parameter and includes recipients that are mailbox users and have **StateOrProvince** set to  `Washington` or  `Oregon`.
  
```
New-AddressList -Name "Oregon and Washington" -RecipientFilter {((RecipientType -eq 'UserMailbox') -and ((StateOrProvince -eq 'Washington') -or (StateOrProvince -eq 'Oregon')))}
```

This example creates the child address list Building 34 Meeting Rooms in the All Rooms parent container, using built-in conditions.
  
```
New-AddressList -Name "Building 34 Meeting Rooms" -Container "\All Rooms" -IncludedRecipients Resources -ConditionalCustomAttribute1 "Building 34"
```

For detailed syntax and parameter information, see [New-AddressList](http://technet.microsoft.com/library/2bcee6db-01d4-40ad-9595-33356a4025c5.aspx).
  
### Update an address list

The **Update-AddressList** cmdlet isn't available in Exchange Online. If users that should appear an address list do not, change the required property value for those users to a temporary value, and then back to the value that's required by the address list. You can update the user property values in the EAC or PowerShell, but it's quicker to do bulk operations in PowerShell. 
  
For example, suppose the address list named Oregon and Washington Users uses the filter  `{((RecipientType -eq 'UserMailbox') -and ((StateOrProvince -eq 'Washington') -or (StateOrProvince -eq 'Oregon')))}`, but the address list doesn't include everyone whose **StateOrProvince** property values are set correctly. To update the address list, perform the following steps: 
  
1. Use the query from the address list to find all users that should be in the address list. For example:
    
  ```
  $Before = Get-User -Filter {((RecipientType -eq 'UserMailbox') -and ((StateOrProvince -eq 'Oregon') -or (StateOrProvince -eq 'Washington')))} -ResultSize Unlimited
  ```

2. Change the required property to a temporary value. For example, change the **StateOrProvince** values from  `Oregon` to  `OR`, and  `Washington` to  `WA`:
    
  ```
  $Before | where {$_.StateOrProvince -eq 'Oregon'} | foreach {Set-User $_.Identity -StateOrProvince OR}
  ```

  ```
  $Before | where {$_.StateOrProvince -eq 'Washington'} | foreach {Set-User $_.Identity -StateOrProvince WA}
  ```

3. Find those same users again by using the temporary property values. For example:
    
  ```
  $After = Get-User -Filter {((RecipientType -eq 'UserMailbox') -and ((StateOrProvince -eq 'OR') -or (StateOrProvince -eq 'WA')))} -ResultSize Unlimited
  ```

4. Change the temporary value back to the required value. For example, change the **StateOrProvince** values from  `OR` to  `Oregon`, and  `WA` to  `Washington`:
    
  ```
  $After | where {$_.StateOrProvince -eq 'OR'} | foreach {Set-User $_.Identity -StateOrProvince Oregon}
  ```

  ```
  $After | where {$_.StateOrProvince -eq 'WA'} | foreach {Set-User $_.Identity -StateOrProvince Washington}
  ```

 **Notes:**
  
- Some properties require the **Get-User** and **Set-User** cmdlets, while others require the **Get-Mailbox** and **Set-Mailbox** cmdlets (for example, **CustomAttribute1-15** ). For more information, see the following topics: 
    
  - [Get-User](http://technet.microsoft.com/library/2a33c9e6-33da-438c-912d-28ce3f4c9afb.aspx)
    
  - [Set-User](http://technet.microsoft.com/library/56d7fc86-2ac3-4e28-bc7a-761e91ac655a.aspx)
    
  - [Get-Mailbox](http://technet.microsoft.com/library/8a5a6eb9-4a75-47f9-ae3b-a3ba251cf9a8.aspx)
    
  - [Set-Mailbox](http://technet.microsoft.com/library/a0d413b9-d949-4df6-ba96-ac0906dedae2.aspx)
    
- The previous example shows the worst case scenario where no one appears in the address list. If a only small number of users don't appear in the address list, you can modify the required property value for each user. For example:
    
1. Set a temporary property value for the user:
    
  ```
  Set-User <Identity> -StateOrProvince WA
  ```

2. Change the temporary value back to the required value:
    
  ```
  Set-User <Identity> -StateOrProvince Washington
  ```

### Delete an address list

This example removes the address list Sales Department, which doesn't contain child address lists.
  
```
Remove-AddressList -Identity "Sales Department"
```

Type Y to confirm that you want to remove this address list, and then press ENTER. 
  
For detailed syntax and parameter information, see [Remove-AddressList](http://technet.microsoft.com/library/b628738c-ebbf-4116-ba85-b1dbd273df40.aspx).
  

