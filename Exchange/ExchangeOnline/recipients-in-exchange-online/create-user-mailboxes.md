---
title: "Create user mailboxes in Exchange Online"
ms.author: kwekua
author: kwekua
manager: scotv
ms.date: 12/9/2016
ms.audience: ITPro
ms.topic: article
ms.service: exchange-online
localization_priority: Normal
ms.assetid: 6ed2f969-6c03-4b45-8e2d-05de787de48d
description: "You have to use the Office 365 admin center or the Exchange Management Shell to create an Exchange Online user mailbox. You can't create new user mailboxes using the Exchange admin center (EAC). However, after Exchange Online mailboxes are created, you can manage them using the EAC."
---

# Create user mailboxes in Exchange Online

You have to use the Office 365 admin center or the Exchange Management Shell to create an Exchange Online user mailbox. You can't create new user mailboxes using the Exchange admin center (EAC). However, after Exchange Online mailboxes are created, you can manage them using the EAC.
  
> [!NOTE]
> After you create a new mailbox using the Exchange Management Shell, you have to assign it an Exchange Online license or it will be disabled when the 30-day grace period ends. 
  
## What do you need to know before you begin?

- Estimated time to complete: 3 minutes.
    
- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Recipient Provisioning Permissions" section in the [Mailbox Permissions](http://technet.microsoft.com/library/5b690bcb-c6df-4511-90e1-08ca91f43b37.aspx) topic. 
    
- It's a good idea to use strong passwords that are at least eight characters long, and combine uppercase and lowercase letters, numbers, and symbols.
    
- To learn how to use Windows PowerShell to connect to Exchange Online, see [Connect to Exchange Online PowerShell](https://go.microsoft.com/fwlink/p/?linkid=396554).
    
- For information about keyboard shortcuts that may apply to the procedures in this topic, see **Keyboard shortcuts in the Exchange admin center**.
    
> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612),[Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351).. 
  
## What do you want to do?

### Use the Office 365 admin center to create a new mailbox

You can use the Office 365 admin center to create a new user account. When you assign the user account a license for Exchange Online, a mailbox is automatically created for the user. To create new user accounts in the Office 365 admin center, see the following topics:
  
- [Create or edit users](https://go.microsoft.com/fwlink/p/?LinkId=276796)
    
- [Add multiple users with a CSV file](https://go.microsoft.com/fwlink/p/?LinkId=279605)
    
### Use the Exchange Management Shell to create a new mailbox

This example creates an Exchange Online mailbox and Office 365 user account for Holly Holt. The optional parameter  _ResetPasswordOnNextLogon_ will require the user to reset their password the first time they sign in to Office 365. 
  
```
New-Mailbox -Alias hollyh -Name hollyh -FirstName Holly -LastName Holt -DisplayName "Holly Holt" -MicrosoftOnlineServicesID hollyh@corp.contoso.com -Password (ConvertTo-SecureString -String 'P@ssw0rd' -AsPlainText -Force) -ResetPasswordOnNextLogon $true
```

After you create a mailbox by running the previous command, an Office 365 user account is also created. You have to activate this user account by assigning a license. To assign a license in the Office 365 admin center, see [Assign or remove a license](https://go.microsoft.com/fwlink/p/?LinkId=276798).
  
## How do you know this worked?

To verify that you've successfully created a new mailbox, do one of the following:
  
- In the EAC, navigate to **Recipients** \> **Mailboxes**. The new user mailbox is displayed in the mailbox list. Under **Mailbox Type**, the type is **User**.
    
    Click **Refresh**![Refresh Icon](../media/ITPro_EAC_RefreshIcon.gif) if the new mailbox isn't displayed at first. 
    
- In the Office 365 admin center, verify that the new user account is listed and that it's been assigned an Exchange Online license.
    
- In the Exchange Management Shell, run the following command to display information about the new user mailbox.
    
  ```
  Get-Mailbox <Name> | FL Name,RecipientTypeDetails,PrimarySmtpAddress,SKUAssigned
  ```

    If a license is assigned to the mailbox, the value for the  _SKUAssigned_ property is  `True`. If a license hasn't been assigned, the value is blank.
    

