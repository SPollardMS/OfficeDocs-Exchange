---
title: "Default Retention Policy in Exchange Online and Exchange Server"
ms.author: markjjo
author: markjjo
manager: scotv
ms.date: 3/9/2015
ms.audience: Admin
ms.topic: overview
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: bcf31b2d-463b-4623-b488-c8ac40f14f62
description: "Exchange creates the retention policy Default MRM Policy in your Exchange Online and on-premises Exchange organization. The policy is automatically applied to new users in Exchange Online. In on-premises organizations, the policy is applied when you create an archive for the mailbox. You can change the retention policy applied to a user at any time."
---

# Default Retention Policy in Exchange Online and Exchange Server

Exchange creates the retention policy Default MRM Policy in your Exchange Online and on-premises Exchange organization. The policy is automatically applied to new users in Exchange Online. In on-premises organizations, the policy is applied when you create an archive for the mailbox. You can change the retention policy applied to a user at any time. 
  
You can modify tags included in the Default MRM Policy, for example by changing the retention age or retention actions, disable a tag, or modify the policy by adding or removing tags from it. The updated policy is applied to mailboxes the next time they're processed by the Managed Folder Assistant
  
## Retention tags linked to the Default MRM Policy

The following table lists the default retention tags linked to the Default MRM Policy.
  
|**Name**|**Type**|**Retention age (days)**|**Retention action**|
|:-----|:-----|:-----|:-----|
|Default 2 years move to archive  <br/> |Default Policy Tag (DPT)  <br/> |730  <br/> |Move to Archive  <br/> |
|Recoverable Items 14 days move to archive  <br/> |Recoverable Items folder  <br/> |14  <br/> |Move to Archive  <br/> |
|Personal 1 year move to archive  <br/> |Personal tag  <br/> |365  <br/> |Move to Archive  <br/> |
|Personal 5 year move to archive  <br/> |Personal tag  <br/> |1,825  <br/> |Move to Archive  <br/> |
|Personal never move to archive  <br/> |Personal tag  <br/> |Not applicable  <br/> |Move to Archive  <br/> |
|1 Week Delete  <br/> |Personal tag  <br/> |7  <br/> |Delete and Allow Recovery  <br/> |
|1 Month Delete  <br/> |Personal tag  <br/> |30  <br/> |Delete and Allow Recovery  <br/> |
|6 Month Delete  <br/> |Personal tag  <br/> |180  <br/> |Delete and Allow Recovery  <br/> |
|1 Year Delete  <br/> |Personal tag  <br/> |365  <br/> |Delete and Allow Recovery  <br/> |
|5 Year Delete  <br/> |Personal tag  <br/> |1,825  <br/> |Delete and Allow Recovery  <br/> |
|Never Delete  <br/> |Personal tag  <br/> |Not applicable  <br/> |Delete and Allow Recovery  <br/> |
   
## What you can do with the Default MRM Policy

|**You can…**|**In Exchange Online…**|**In Exchange Server…**|
|:-----|:-----|:-----|
|Apply the Default MRM Policy automatically to new users  <br/> |Yes, applied by default. No action is required.  <br/> |Yes, applied by default if you also create an archive for the new user.  <br/> If you create an archive for the user later, the policy is applied automatically only if the user doesn't have an existing Retention Policy.  <br/> |
|Modify the retention age or retention action of a retention tag linked to the policy  <br/> |Yes  <br/> |Yes  <br/> |
|Disable a retention tag linked to the policy  <br/> |Yes  <br/> |Yes  <br/> |
|Add a retention tag to the policy  <br/> |Yes  <br/> |Yes  <br/> |
|Remove a retention tag from the policy  <br/> |Yes  <br/> |Yes  <br/> |
|Set another policy as the default retention policy to be applied automatically to new users  <br/> |No  <br/> |No  <br/> |
   
## More information

- A Retention Tag can be linked to more than one Retention Policy. For details about managing [Retention tags and retention policies](retention-tags-and-policies.md), see [Messaging Records Management Procedures](http://technet.microsoft.com/library/bc2ff408-4a2b-4202-9515-e3e922a6320d.aspx).
    
- The Default MRM Policy doesn't include a DPT to automatically delete items (but it does contain personal tags with the delete retention action that users can apply to mailbox items). If you want to automatically delete items after a specified period, you can create a DPT with the required delete action and add it to the policy. For details, see [Create a Retention Policy](create-a-retention-policy.md) and [Add retention tags to or remove retention tags from a retention policy](add-or-remove-retention-tags.md).
    
- Retention policies are applied to mailbox users. The same policy applies to the user's mailbox and archive.
    

