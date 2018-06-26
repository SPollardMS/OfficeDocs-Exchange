---
title: "Add retention tags to or remove retention tags from a retention policy"
ms.author: markjjo
author: markjjo
manager: scotv
ms.date: 6/23/2018
ms.audience: End User
ms.topic: article
ms.service: exchange-online
localization_priority: Normal
ms.assetid: 3a5196ce-2764-453d-9bc1-5ec22d06b40d
description: "You can add retention tags to a retention policy when the policy is created or any time thereafter. For details about how to create a retention policy, including how to simultaneously add retention tags, see Create a Retention Policy."
---

# Add retention tags to or remove retention tags from a retention policy

You can add retention tags to a retention policy when the policy is created or any time thereafter. For details about how to create a retention policy, including how to simultaneously add retention tags, see [Create a Retention Policy](create-a-retention-policy.md).
  
A retention policy can contain the following retention tags:
  
- One or more retention policy tags (RPTs) for supported default folders
    
- One default policy tag (DPT) with the **Move to Archive** action 
    
- One DPT with the **Delete and Allow Recovery** or the **Permanently Delete** action 
    
- One DPT for voice mail
    
- Any number of personal tags
    
For more information about retention tags, see [Retention tags and retention policies](retention-tags-and-policies.md).
  
## What do you need to know before you begin?

- Estimated time to completion: 10 minutes.
    
- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Messaging records management" entry in the [Mailbox Permissions](http://technet.microsoft.com/library/5b690bcb-c6df-4511-90e1-08ca91f43b37.aspx) topic. 
    
- Retention tags aren't applied to a mailbox until they're linked to a retention policy and the Managed Folder Assistant processes the mailbox. To start the Managed Folder Assistant so that it processes a mailbox, see [Configure and run the Managed Folder Assistant in Exchange 2016](http://technet.microsoft.com/library/9fcfb9b6-bd24-4218-a163-bc599cd5476a.aspx).
    
- For information about keyboard shortcuts that may apply to the procedures in this topic, see **Keyboard shortcuts in the Exchange admin center**.
    
> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612),[Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351). 
  
## What do you want to do?

### Use the EAC to add or remove retention tags

1. Go to **Compliance management** \> **Retention policies**.
    
2. In the list view, select the retention policy to which you want to add retention tags and then click **Edit**![Edit icon](../../media/ITPro_EAC_EditIcon.gif).
    
3. In **Retention Policy**, use the following settings:
    
  - **Add**![Add Icon](../../media/ITPro_EAC_AddIcon.gif) Click this button to add a retention tag to the policy. 
    
  - **Remove**![Remove icon](../../media/ITPro_EAC_RemoveIcon.gif) Select a tag from the list, and then click this button to remove the tag from the policy. 
    
### Use the Shell to add or remove retention tags

This example adds the retention tags VPs-Default, VPs-Inbox, and VPs-DeletedItems to the retention policy RetPolicy-VPs, which doesn't already have retention tags linked to it.
  
> [!CAUTION]
> If the policy has retention tags linked to it, this command replaces the existing tags. 
  
```
Set-RetentionPolicy -Identity "RetPolicy-VPs" -RetentionPolicyTagLinks "VPs-Default","VPs-Inbox","VPs-DeletedItems"
```

This example adds the retention tag VPs-DeletedItems to the retention policy RetPolicy-VPs, which already has other retention tags linked to it.
  
```
$TagList = (Get-RetentionPolicy "RetPolicy-VPs").RetentionPolicyTagLinks
$TagList.Add((Get-RetentionPolicyTag 'VPs-DeletedItems').DistinguishedName)
Set-RetentionPolicy "RetPolicy-VPs" -RetentionPolicyTagLinks $TagList
```

This example removes the retention tag VPs-Inbox from the retention policy RetPolicy-VPs.
  
```
$TagList = (Get-RetentionPolicy "RetPolicy-VPs").RetentionPolicyTagLinks
$TagList.Remove((Get-RetentionPolicyTag 'VPs-Inbox').DistinguishedName)
Set-RetentionPolicy "RetPolicy-VPs" -RetentionPolicyTagLinks $TagList
```

For detailed syntax and parameter information, see [set-RetentionPolicy](http://technet.microsoft.com/library/34fbc099-4f41-4f57-867c-ad1e08513c51.aspx) and [get-RetentionPolicy](http://technet.microsoft.com/library/7a05203e-894b-4109-9647-ca7afc44a08f.aspx).
  
## How do you know this worked?

To verify that you have successfully added or removed a retention tag from a retention policy, use the [get-RetentionPolicy](http://technet.microsoft.com/library/7a05203e-894b-4109-9647-ca7afc44a08f.aspx) cmdlet to verify the  _RetentionPolicyTagLinks_ property. 
  
This example use the **Get-RetentionPolicy** cmdlet to retrieve retention tags added to the Default MRM Policy and pipes them to the **Format-Table** cmdlet to output only the name property of each tag. 
  
```
(Get-RetentionPolicy "Default MRM Policy").RetentionPolicyTagLinks | Format-Table name
```


