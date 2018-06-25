---
title: "Apply a retention policy to mailboxes"
ms.author: markjjo
author: markjjo
manager: scotv
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 6ccc80db-d201-44f7-8d4b-473a89c14b2f
description: "You can use retention policies to group one or more retention tags and apply them to mailboxes to enforce message retention settings. A mailbox can't have more than one retention policy."
---

# Apply a retention policy to mailboxes

You can use retention policies to group one or more retention tags and apply them to mailboxes to enforce message retention settings. A mailbox can't have more than one retention policy. 
  
> [!CAUTION]
> Messages are expired based on settings defined in the retention tags linked to the policy. These settings include actions such moving messages to the archive or permanently deleting them. Before applying a retention policy to one or more mailboxes, we recommended that you test the policy and inspect each retention tag associated with it. 
  
For additional management tasks related to messaging records management (MRM), see [Messaging Records Management Procedures](http://technet.microsoft.com/library/bc2ff408-4a2b-4202-9515-e3e922a6320d.aspx).
  
## What do you need to know before you begin?

- Estimated time to complete: 5 minutes.
    
- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Applying retention policies" entry in the [Messaging Policy and Compliance Permissions](http://technet.microsoft.com/library/ec4d3b9f-b85a-4cb9-95f5-6fc149c3899b.aspx) topic. 
    
- For information about keyboard shortcuts that may apply to the procedures in this topic, see **Keyboard shortcuts in the Exchange admin center**.
    
> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612),[Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351). 
  
## What do you want to do?

### Use the EAC to apply a retention policy to a single mailbox

1. Navigate to **Recipients** \> **Mailboxes**.
    
2. In the list view, select the mailbox to which you want to apply the retention policy, and then click **Edit**![Edit icon](../../media/ITPro_EAC_EditIcon.gif).
    
3. In **User Mailbox**, click **Mailbox features**.
    
4. In the **Retention policy** list, select the policy you want to apply to the mailbox, and then click **Save**.
    
### Use the EAC to apply a retention policy to multiple mailboxes

1. Navigate to **Recipients** \> **Mailboxes**.
    
2. In the list view, use the Shift or Ctrl keys to select multiple mailboxes.
    
3. In the details pane, click **More options**.
    
4. Under **Retention Policy**, click **Update**.
    
5. In **Bulk Assign Retention Policy**, select the retention policy you want to apply to the mailboxes, and then click **Save**.
    
### Use the Shell to apply a retention policy to a single mailbox

This example applies the retention policy RP-Finance to Morris's mailbox.
  
```
Set-Mailbox "Morris" -RetentionPolicy "RP-Finance"
```

For detailed syntax and parameter information, see [Set-Mailbox](http://technet.microsoft.com/library/a0d413b9-d949-4df6-ba96-ac0906dedae2.aspx).
  
### Use the Shell to apply a retention policy to multiple mailboxes

This example applies the new retention policy New-Retention-Policy to all mailboxes that have the old policy Old-Retention-Policy.
  
```
$OldPolicy={Get-RetentionPolicy "Old-Retention-Policy"}.distinguishedName
Get-Mailbox -Filter {RetentionPolicy -eq $OldPolicy} -Resultsize Unlimited | Set-Mailbox -RetentionPolicy "New-Retention-Policy"
```

This example applies the retention policy RetentionPolicy-Corp to all mailboxes in the Exchange organization.
  
```
Get-Mailbox -ResultSize unlimited | Set-Mailbox -RetentionPolicy "RetentionPolicy-Corp"
```

This example applies the retention policy RetentionPolicy-Finance to all mailboxes in the Finance organizational unit.
  
```
Get-Mailbox -OrganizationalUnit "Finance" -ResultSize Unlimited | Set-Mailbox -RetentionPolicy "RetentionPolicy-Finance"
```

For detailed syntax and parameter information, see [Get-Mailbox](http://technet.microsoft.com/library/8a5a6eb9-4a75-47f9-ae3b-a3ba251cf9a8.aspx) and [Set-Mailbox](http://technet.microsoft.com/library/a0d413b9-d949-4df6-ba96-ac0906dedae2.aspx).
  
## How do you know this worked?

To verify that you have applied the retention policy, run the [Get-Mailbox](http://technet.microsoft.com/library/8a5a6eb9-4a75-47f9-ae3b-a3ba251cf9a8.aspx) cmdlet to retrieve the retention policy for the mailbox or mailboxes. 
  
This example retrieves the retention policy for Morris's mailbox.
  
```
Get-Mailbox Morris | Select RetentionPolicy
```

This command retrieves all mailboxes that have the retention policy RP-Finance applied.
  
```
Get-Mailbox -ResultSize unlimited | Where-Object {$_.RetentionPolicy -eq "RP-Finance"} | Format-Table Name,RetentionPolicy -Auto
```


