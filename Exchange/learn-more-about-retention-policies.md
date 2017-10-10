---
title: Learn more about retention policies
ms.prod: EXCHANGE
ms.assetid: 8988ffc7-038c-4762-badb-0a2ef84a80a8
---


# Learn more about retention policies

Retention policies are the  [Messaging records management in Exchange 2016](messaging-records-management-in-exchange-2016.md) (MRM) feature in Microsoft Exchange Server 2013 that helps you manage email lifecycle. Use retention policies to group retention tags, which specify message retention settings and can be applied to mailbox folders or items. A retention policy can contain the following retention tags:
  
    
    


- A default policy tag (DPT) to delete messages
    
  
- A DPT to delete Unified Messaging voice mail items
    
  
- A DPT to move messages to user's archive mailbox
    
  
- A retention policy tag (RPT) for each default folder
    
  
- Any number of personal tags that users can apply to folders or messages
    
  

After creating a retention policy and adding retention tags to it, you can apply the policy to users. You can create a single retention policy for all users in your organization or apply a different policy to different groups of users. You can create as many retention policies as you need. You can add or remove retention tags from a retention policy at any time. Retention policies are applied when the Managed Folder Assistant processes a mailbox.
  
    
    

Exchange 2013 Setup creates a default retention policy called **Default MRM Policy**. This policy is automatically applied to a user when you create a mailbox with an archive or archive-enable an existing mailbox user. You can replace the default policy with any retention policies you create. You can also customize the Default MRM Policy by adding or removing retention tags from it or modifying settings of the tags.
## For more information

 [Retention tags and retention policies in Exchange 2016](retention-tags-and-retention-policies-in-exchange-2016.md)
  
    
    
 [Checklist: Deploying Retention Policies](http://technet.microsoft.com/library/59e299fd-b6a8-48f5-88ae-dc20dbe32e90.aspx)
  
    
    

