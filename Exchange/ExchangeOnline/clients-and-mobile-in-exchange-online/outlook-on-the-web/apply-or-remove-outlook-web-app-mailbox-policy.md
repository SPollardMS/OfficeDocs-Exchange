---
title: "Apply or remove an Outlook Web App mailbox policy on a mailbox"
ms.author: dmaguire
author: msdmaguire
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 51d8e269-b0d5-4bc7-9b3d-0460871e54fa
description: "You can apply an Outlook Web App mailbox policy to one or more mailboxes or remove one using either the EAC or the Shell."
---

# Apply or remove an Outlook Web App mailbox policy on a mailbox

You can apply an Outlook Web App mailbox policy to one or more mailboxes or remove one using either the EAC or the Shell.
  
## What do you need to know before you begin?

- Estimated time to complete each procedure: 10 minutes.
    
- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Outlook Web App mailbox policies" entry in the [Clients and mobile devices permissions](http://technet.microsoft.com/library/57eca42a-5a7f-4c65-89f0-7a84f2dbea19.aspx) topic. 
    
- For information about keyboard shortcuts that may apply to the procedures in this topic, see **Keyboard shortcuts in the Exchange admin center**.
    
> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612),[Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351).. 
  
## What do you want to do?

### Apply an Outlook Web App mailbox policy

#### Use the EAC to apply an Outlook Web App mailbox policy

1. In the EAC, click **Recipients** \> **Mailboxes**.
    
2. In the work pane, click to select the mailbox that you want to apply an Outlook Web App mailbox policy to. You can also select multiple mailboxes.
    
3. **If you've selected one mailbox:**
    
1. Scroll down in the details pane to **Email Connectivity** and click **View Details**.
    
2. Click **Browse** to view and select from the available mailbox policies. 
    
3. Click **Save** to assign the selected policy to the selected mailbox. 
    
    **If you've selected more than one mailbox:**
    
1. Scroll down in the details pane to **Outlook Web App** and click **Assign a policy**.
    
2. Click **Browse** to view and select from the available mailbox policies. 
    
3. Click **Save** to assign the selected policy to the selected mailboxes. 
    
#### Use the Shell to apply an Outlook Web App mailbox policy to an existing mailbox

This example applies the Outlook Web App mailbox policy named "Calendar" to the mailbox of the user tony@contoso.com.
  
```
Set-CASMailbox -Identity tony@contoso.com -OwaMailboxPolicy:Calendar
```

For more information about syntax and parameters, see [Set-CASMailbox](http://technet.microsoft.com/library/ff7d4dc5-755e-4005-a0a3-631eed3f9b3b.aspx).
  
### Remove an Outlook Web App mailbox policy

#### Use the EAC to remove an Outlook Web App mailbox policy

1. In the EAC, click **Recipients** \> **Mailboxes**.
    
2. In the work pane, click to select the mailbox that you want to remove an Outlook Web App mailbox policy from. 
    
3. Scroll down in the details pane to **Email Connectivity** and click **View details**.
    
    If a mailbox policy has been assigned, click **Clear** to remove it from the mailbox. 
    
4. Click **Save** to save your changes. 
    
#### Use the Shell to remove an Outlook Web App mailbox policy from an existing mailbox.

This example removes the Outlook Web App mailbox policy from mailbox of the user tony@contoso.com.
  
```
Set-CASMailbox -Identity tony@contoso.com -OwaMailboxPolicy:$null
```

For more information about syntax and parameters, see [Set-CASMailbox](http://technet.microsoft.com/library/ff7d4dc5-755e-4005-a0a3-631eed3f9b3b.aspx).
  

