---
title: "Enable or disable Exchange ActiveSync for a mailbox"
ms.author: kwekua
author: kwekua
manager: scotv
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: dcf7c05b-b1b9-4b0f-800d-fec9f2ddc9e4
description: "You can use the EAC or the Shell to enable or disable Microsoft Exchange ActiveSync for a user mailbox. Exchange ActiveSync is a client protocol that lets users synchronize a mobile device with their Exchange mailbox. Exchange ActiveSync is enabled by default when a user mailbox is created. To learn more, see Exchange ActiveSync."
---

# Enable or disable Exchange ActiveSync for a mailbox

You can use the EAC or the Shell to enable or disable Microsoft Exchange ActiveSync for a user mailbox. Exchange ActiveSync is a client protocol that lets users synchronize a mobile device with their Exchange mailbox. Exchange ActiveSync is enabled by default when a user mailbox is created. To learn more, see [Exchange ActiveSync](http://technet.microsoft.com/library/5fafaff3-eb37-4fdb-95f0-e56c45ea5884.aspx).
  
## What do you need to know before you begin?

- Estimated time to complete: 2 minutes.
    
- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Exchange ActiveSync settings" entry in the [Clients and Mobile Devices Permissions](http://technet.microsoft.com/library/57eca42a-5a7f-4c65-89f0-7a84f2dbea19.aspx) topic. 
    
- For information about keyboard shortcuts that may apply to the procedures in this topic, see **Keyboard shortcuts in the Exchange admin center**.
    
> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612),[Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351).. 
  
## What do you want to do?

### Use the EAC to enable or disable Exchange ActiveSync

1. In the EAC, navigate to **Recipients** \> **Mailboxes**.
    
2. In the list of user mailboxes, click the mailbox that you want to enable or disable Exchange ActiveSync for, and then click **Edit**![Edit icon](../../media/ITPro_EAC_EditIcon.gif).
    
3. On the mailbox properties page, click **Mailbox Features**.
    
4. Under **Mobile Devices**, do one of the following:
    
  - To disable Exchange ActiveSync click **Disable Exchange ActiveSync**.
    
    A warning appears asking if you're sure you want to disable Exchange ActiveSync. Click **Yes**.
    
  - To enable Exchange ActiveSync, click **Enable Exchange ActiveSync**.
    
5.  Click **Save** to save your change. 
    
> [!NOTE]
> You can enable and disable Exchange ActiveSync for multiple user mailboxes by using the EAC bulk edit feature. For more information about how to do this, see the "Bulk edit user mailboxes" section in [Manage user mailboxes](manage-user-mailboxes.md). 
  
### Use the Shell to enable or disable Exchange ActiveSync

This example disables Exchange ActiveSync for the mailbox of Yan Li.
  
```
Set-CASMailbox -Identity "Yan Li" -ActiveSyncEnabled $false
```

This example enables Exchange ActiveSync for the mailbox of Elly Nkya.
  
```
Set-CASMailbox -Identity Ellyn@contoso.com -ActiveSyncEnabled $true
```

For detailed syntax and parameter information, see [Set-CASMailbox](http://technet.microsoft.com/library/ff7d4dc5-755e-4005-a0a3-631eed3f9b3b.aspx).
  
## How do you know this worked?

To verify that you've successfully enabled or disabled Exchange ActiveSync for a user mailbox, do one of the following:
  
- In the EAC, navigate to **Recipients** \> **Mailboxes**, click the mailbox, and then click **Edit**![Edit icon](../../media/ITPro_EAC_EditIcon.gif).
    
- On the mailbox properties page, click **Mailbox Features**.
    
- Under **Mobile Devices**, verify whether Exchange ActiveSync is enabled or disabled.
    
Or
  
- Run the following command in the Shell.
    
  ```
  Get-CASMailbox <identity>
  ```

    If Exchange ActiveSync is enabled, the value for the  _ActiveSyncEnabled_ property is  `True`. If Exchange ActiveSync is disabled, the value is  `False`.
    

