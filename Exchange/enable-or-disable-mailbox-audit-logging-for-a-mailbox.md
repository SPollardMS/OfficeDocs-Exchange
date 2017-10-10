---
title: Enable or disable mailbox audit logging for a mailbox
ms.prod: EXCHANGE
ms.assetid: c4bbfd52-6196-49c7-8c31-777fbbee11f2
---


# Enable or disable mailbox audit logging for a mailbox
Learn how to configure mailbox audit logging on mailboxes in Exchange 2016.
With mailbox audit logging in Exchange Server 2016, you can track logons to a mailbox as well as what actions are taken while the user is logged on. When you enable mailbox audit logging for a mailbox, some actions performed by administrators and delegates are logged by default. None of the actions performed by the mailbox owner are logged by default. To learn more about mailbox audit logging and what actions can be logged, see  [Mailbox audit logging in Exchange 2016](mailbox-audit-logging-in-exchange-2016.md).
  
    
    


> [!CAUTION]
> Auditing of mailbox owner actions can generate a large number of mailbox audit log entries and is therefore disabled by default. We recommend that you only enable auditing of specific owner actions needed to meet business or compliance requirements. 
  
    
    


## Before you begin
<a name="top"> </a>


- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Mailbox audit logging" entry in the  [Messaging policy and compliance permissions in Exchange 2016](messaging-policy-and-compliance-permissions-in-exchange-2016.md) topic.
    
  
- Entries in the mailbox audit log are retained for 90 days, by default. See the  [More information](enable-or-disable-mailbox-audit-logging-for-a-mailbox.md#moreinfo) section change how long entries are retained.
    
  
- You can't use the Exchange admin center (EAC) to enable or disable mailbox audit logging. You have to use the Exchange Management Shell. To learn how to open the Exchange Management Shell in your on-premises Exchange organization, see **Open the Exchange Management Shell**.
    
  
- An administrator who has been assigned the Full Access permission to a user's mailbox is considered a delegate user.
    
  
-  Mailboxes are considered to be accessed by an administrator only in the following scenarios:
    
  - In-Place eDiscovery is used to search a mailbox.
    
  
  - The **New-MailboxExportRequest** cmdlet is used to export a mailbox.
    
  
  - Microsoft Exchange Server MAPI Editor is used to access the mailbox.
    
  

## Enable or disable mailbox audit logging
<a name="top"> </a>

You can use the Exchange Management Shell to enable or disable mailbox audit logging for a mailbox. This enables or disables logging of all operations specified for administrator, delegates, and the mailbox owner.
  
    
    
This example enables mailbox audit logging for Ben Smith's mailbox.
  
    
    



```

Set-Mailbox -Identity "Ben Smith" -AuditEnabled $true
```

This example enables mailbox audit logging for all user mailboxes in your organization.
  
    
    



```
Get-Mailbox -ResultSize Unlimited -Filter {RecipientTypeDetails -eq "UserMailbox"} | Set-Mailbox -AuditEnabled $true
```

This example disables mailbox audit logging for Ben Smith's mailbox.
  
    
    



```
Set-Mailbox -Identity "Ben Smith" -AuditEnabled $false
```

For detailed syntax and parameter information, see  [Set-Mailbox](http://technet.microsoft.com/library/a0d413b9-d949-4df6-ba96-ac0906dedae2.aspx).
  
    
    

## Configure mailbox audit logging settings for administrator, delegate, and owner access
<a name="top"> </a>

When mailbox audit logging is enabled for a mailbox, only the administrator, delegate, and owner actions specified in the audit logging configuration for the mailbox are logged.
  
    
    
This example specifies that the  `MessageBind` and `FolderBind` actions performed by administrators will be logged for Ben Smith's mailbox.
  
    
    



```
Set-Mailbox -Identity "Ben Smith" -AuditAdmin MessageBind,FolderBind -AuditEnabled $true
```

This example specifies that the  `SendAs` or `SendOnBehalf` actions performed by delegate users will be logged for Ben Smith's mailbox.
  
    
    



```
Set-Mailbox -Identity "Ben Smith" -AuditDelegate SendAs,SendOnBehalf -AuditEnabled $true
```

This example specifies that the  `HardDelete` action performed by the mailbox owner will be logged for Ben Smith's mailbox.
  
    
    



```
Set-Mailbox -Identity "Ben Smith" -AuditOwner HardDelete -AuditEnabled $true
```

For detailed syntax and parameter information, see  [Set-Mailbox](http://technet.microsoft.com/library/a0d413b9-d949-4df6-ba96-ac0906dedae2.aspx).
  
    
    
 [Before you begin](enable-or-disable-mailbox-audit-logging-for-a-mailbox.md#top)
  
    
    

## How do you know this worked?
<a name="top"> </a>

To verify that you have successfully enabled mailbox audit logging for a mailbox and specified the correct logging settings for administrator, delegate, or owner access, use the  [Get-Mailbox](http://technet.microsoft.com/library/8a5a6eb9-4a75-47f9-ae3b-a3ba251cf9a8.aspx) cmdlet to retrieve the mailbox audit logging settings for that mailbox.
  
    
    
This example retrieves Ben Smith's mailbox settings and pipes the specified audit settings, including the audit log age limit, to the **Format-List** cmdlet.
  
    
    



```
Get-Mailbox "Ben Smith" | Format-List Audit*
```

A value of  `True` for the **AuditEnabled** property verifies that audit logging is enabled.
  
    
    
This example retrieves the auditing settings for all user mailboxes in your organization.
  
    
    



```
Get-Mailbox -ResultSize Unlimited -Filter {RecipientTypeDetails -eq "UserMailbox"} | Format-List Name,Audit*
```


## More information
<a name="moreinfo"> </a>


- The actions that are audited for each type of user may not all be displayed when you run the **Get-Mailbox** cmdlet. But you can run the following commands to display all the audited actions for a specific user logon type.
    
  ```
  Get-Mailbox <identity of mailbox> | Select-Object -ExpandProperty AuditAdmin
  ```


  ```
  Get-Mailbox <identity of mailbox> | Select-Object -ExpandProperty AuditDelegate
  ```


  ```
  Get-Mailbox <identity of mailbox> | Select-Object -ExpandProperty AuditOwner
  ```

- By default, entries in the mailbox audit log are kept for 90 days. When an entry is older than 90 days, it's deleted. You can use the **Set-Mailbox** cmdlet to change this setting so items are kept for a longer (or shorter) period of time.
    
    This example increases the age limit for mailbox audit log entries in Pilar Pinilla's mailbox to 180 days.
    


  ```
  Set-Mailbox -Identity "Pilar Pinilla" -AuditLogAgeLimit 180
  ```


    This example decreases the age limit for mailbox audit log entries for all user mailboxes in your organization to 60 days.
    


  ```
  Get-Mailbox -ResultSize Unlimited -Filter {RecipientTypeDetails -eq "UserMailbox"} | Set-Mailbox -AuditLogAgeLimit 60
  ```

 [Before you begin](enable-or-disable-mailbox-audit-logging-for-a-mailbox.md#top)
  
    
    

