---
title: "Enable or disable Outlook Web App for a mailbox"
ms.author: kwekua
author: kwekua
manager: scotv
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.service: exchange-online
localization_priority: Normal
ms.assetid: abc19646-6211-4f18-a060-e347452dcc53
description: "You can use the EAC or the Shell to enable or disable Outlook Web App for a user mailbox. When Outlook Web App is enabled, a user can use Outlook Web App to send and receive email. When Outlook Web App is disabled, the mailbox will continue to receive email messages, and a user can access it to send and receive email by using a MAPI client, such as Microsoft Outlook, or with a POP or IMAP email client, assuming that the mailbox is enabled to support access by those clients."
---

# Enable or disable Outlook Web App for a mailbox

You can use the EAC or the Shell to enable or disable Outlook Web App for a user mailbox. When Outlook Web App is enabled, a user can use Outlook Web App to send and receive email. When Outlook Web App is disabled, the mailbox will continue to receive email messages, and a user can access it to send and receive email by using a MAPI client, such as Microsoft Outlook, or with a POP or IMAP email client, assuming that the mailbox is enabled to support access by those clients.
  
> [!NOTE]
> Support for Outlook Web App and MAPI, POP3, and IMAP4 email clients is enabled by default when a user mailbox is created. 
  
For additional management tasks related to managing email client access to a mailbox, see the following topics:
  
- [Enable or disable MAPI for a mailbox](enable-or-disable-mapi.md)
    
- [Enable or Disable IMAP4 Access for a User](http://technet.microsoft.com/library/a685fae4-b6f1-42fe-8bdc-5f99f9617799.aspx)
    
- [Enable or Disable POP3 Access for a User](http://technet.microsoft.com/library/57e12f07-3b14-45bd-9a82-e6032d14214f.aspx)
    
## What do you need to know before you begin?

- Estimated time to complete: 2 minutes.
    
- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Client Access user settings" entry in the [Clients and Mobile Devices Permissions](http://technet.microsoft.com/library/57eca42a-5a7f-4c65-89f0-7a84f2dbea19.aspx) topic. 
    
- For information about keyboard shortcuts that may apply to the procedures in this topic, see **Keyboard shortcuts in the Exchange admin center**.
    
> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612),[Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351).. 
  
## What do you want to do?

### Use the EAC to enable or disable Outlook Web App

1. In the EAC, navigate to **Recipients** \> **Mailboxes**.
    
2. In the list of user mailboxes, click the mailbox that you want to enable or disable Outlook Web App for, and then click **Edit**![Edit icon](../../media/ITPro_EAC_EditIcon.gif).
    
3. On the mailbox properties page, click **Mailbox Features**.
    
4. Under **Email Connectivity**, do one of the following:
    
  - To disable Outlook Web App, under **Outlook Web App: Enabled**, click **Disable**.
    
    A warning appears asking if you're sure you want to disable Outlook Web App. Click **Yes**.
    
  - To enable Outlook Web App, under **Outlook Web App: Disabled**, click **Enable**.
    
5.  Click **Save** to save your change. 
    
> [!NOTE]
> You can enable and disable Outlook Web App for multiple user mailboxes by using the EAC bulk edit feature. For more information about how to do this, see the "Bulk edit user mailboxes" section in [Manage user mailboxes](manage-user-mailboxes.md). 
  
### Use the Shell to enable or disable Outlook Web App

This example disables Outlook Web App for the mailbox of Yan Li.
  
```
Set-CASMailbox -Identity "Yan Li" -OWAEnabled $false
```

This example enables Outlook Web App for the mailbox of Elly Nkya.
  
```
Set-CASMailbox -Identity Ellyn@contoso.com -OWAEnabled $true
```

For detailed syntax and parameter information, see [Set-CASMailbox](http://technet.microsoft.com/library/ff7d4dc5-755e-4005-a0a3-631eed3f9b3b.aspx).
  
## How do you know this worked?

To verify that you've successfully enabled or disabled Outlook Web App for a user mailbox, do one of the following:
  
- In the EAC, navigate to **Recipients** \> **Mailboxes**, click the mailbox, and then click **Edit**![Edit icon](../../media/ITPro_EAC_EditIcon.gif).
    
- On the mailbox properties page, click **Mailbox Features**.
    
- Under **Email Connectivity**, verify whether Outlook Web App is enabled or disabled.
    
Or
  
- Run the following command in the Shell.
    
  ```
  Get-CASMailbox <identity>
  ```

    If Outlook Web App is enabled, the value for the  _OWAEnabled_ property is  `True`. If Outlook Web App is disabled, the value is  `False`.
    

