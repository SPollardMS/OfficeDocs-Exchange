---
title: "Connect a disabled mailbox"
ms.author: serdars
author: SerdarSoysal
manager: serdars
ms.date: 4/19/2018
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: a8abd399-75fd-4ee2-b2e4-634b55e4f79f
description: "Summary: Learn how you can use the Exchange admin center(EAC) or the Exchange Management Shell in Exchange to connect a disabled mailbox to an Active Directory user account."
---

# Connect a disabled mailbox

 **Summary**: Learn how you can use the Exchange admin center(EAC) or the Exchange Management Shell in Exchange to connect a disabled mailbox to an Active Directory user account.
  
 When you disable a mailbox, Exchange retains the mailbox in the mailbox database and switches the mailbox to a disabled state. The Exchange attributes are also removed from the corresponding Active Directory user account, but the user account is retained. The mailbox is retained until the deleted mailbox retention period expires, which is 30 days by default, before it's then deleted permanently (or purged) from the mailbox database.
  
Until a disabled mailbox is permanently deleted from the Exchange mailbox database, you can use the EAC or the Exchange Management Shell to reconnect it to the original Active Directory user account.
  
To learn more about disconnected mailboxes and perform other related management tasks, see the following topics:
  
- [Understanding Disconnected Mailboxes](http://technet.microsoft.com/library/508ebe2b-387d-4867-bdb0-028ef351ce56.aspx)
    
- [Disable or delete a mailbox in Exchange 2016](disable-or-delete-a-mailbox.md)
    
- [Connect or restore a deleted mailbox](restore-deleted-mailbox.md)
    
- [Permanently delete a mailbox](permanently-delete-a-mailbox.md)
    
## What do you need to know before you begin?

- Estimated time to complete: 2 minutes.
    
- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Recipient Provisioning Permissions" section in the [Recipients Permissions](../../permissions/feature-permissions/recipients.md) topic. 
    
- Run the **Get-User** cmdlet in theExchange Management Shell to verify that the Active Directoryuser account that you want to connect the disabled mailbox to exists and that it isn't already associated with another mailbox. To connect a disabled mailbox to a user account, the account must exist and the value for the  _RecipientType_ property has to be  `User`, which indicates that the account isn't already mailbox-enabled.
    
    For on-premises Exchange organizations, you can also verify this information in Active Directory Users and Computers.
    
- Run the following command to verify that the disabled mailbox that you want to connect a user account to exists in the mailbox database and isn't a soft-deleted mailbox.
    
  ```
  Get-MailboxDatabase | Get-MailboxStatistics | Where { $_.DisplayName -eq "<display name>" } | fl DisplayName,Database,DisconnectReason
  ```

    To be able to connect a disabled mailbox, the mailbox has to exist in the mailbox database and the value for the  _DisconnectReason_ property has to be  `Disabled`. If the mailbox has been purged from the database, the command won't return any results.
    
- For information about keyboard shortcuts that may apply to the procedures in this topic, see [Keyboard shortcuts in the Exchange admin center](../../about-documentation/keyboard-shortcuts-in-eac.md).
    
> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at: [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351).. 
  
## What do you want to do?

### Use the EAC to connect a disabled mailbox

The following procedure shows how to connect a disabled user mailbox. You can also reconnect disabled linked mailboxes and disabled shared mailboxes to the corresponding user account.
  
1. In the EAC, navigate to **Recipients** > **Mailboxes**.
    
2. Click **More**![More Options icon](../../media/ITPro_EAC_MoreOptionsIcon.png), and then click **Connect a mailbox**.
    
    A list of mailboxes that are disconnected on the selected Exchange server in your Exchange organization will be displayed.
    
    > [!NOTE]
    > This list of disconnected mailboxes includes disabled mailboxes, deleted mailboxes, and soft-deleted mailboxes. 
  
3. Click the disabled mailbox that you want to reconnect, and then click **Connect**.
    
4. In the window that asks if you're sure that you want to reconnect the mailbox, click **Yes**.
    
    Exchange will reconnect the disabled mailbox to the corresponding user account.
    
### Use the Exchange Management Shell to connect a disabled mailbox

Use the **Connect-Mailbox** cmdlet in the Exchange Management Shell to connect a user account to a disabled mailbox. You have to specify the type of mailbox that you're connecting. The following examples show the syntax for reconnecting user, linked, and shared mailboxes. 
  
This example connects a user mailbox. The  _Identity_ parameter specifies the disconnected mailbox in the Exchange database. The  _User_ parameter specifies the Active Directory user account to reconnect the mailbox to. 
  
```
Connect-Mailbox -Identity "Jeffrey Zeng" -Database MBXDB01 -User "Jeffrey Zeng"
```

This example connects a linked mailbox. The  _Identity_ parameter specifies the disconnected mailbox in the Exchange database. The  _LinkedMasterAccount_ parameter specifies the Active Directory user account in the account forest that you want to reconnect the mailbox to. The  _Alias_ parameter specifies the alias, which is the portion of the email address on the left side of the at (@) symbol, for the reconnected mailbox. 
  
```
Connect-Mailbox -Identity "Kai Axford" -Database MBXDB02 -LinkedDomainController FabrikamDC01 -LinkedMasterAccount kai.axford@fabrikam.com -Alias kaia
```

This example connects a shared mailbox.
  
```
Connect-Mailbox -Identity "Corporate Shared Mailbox" -Database "Mailbox Database 03" -User "Corporate Shared Mailbox" -Alias corpshared -Shared
```

> [!NOTE]
> If you don't include the  _Alias_ parameter when you run the **Connect-Mailbox** cmdlet, the value specified in the  _User_ or  _LinkedMasterAccount_ parameter is used to create the email address alias for the reconnected mailbox. 
  
For detailed syntax and parameter information, see [Connect-Mailbox](http://technet.microsoft.com/library/48757062-abe5-4c61-acc5-5884569c1d8b.aspx).
  
## How do you know this worked?

To verify that you've successfully connected a disabled mailbox to a user account, do one of the following:
  
- In the EAC, click **Recipients**, navigate to the appropriate page for the mailbox type that you reconnected, click **Refresh**![Refresh icon](../../media/ITPro_EAC_RefreshIcon.png), and verify that the mailbox is listed.
    
- In Active Directory Users and Computers, right-click the user account whose mailbox you disabled, and then click **Properties**. On the **General** tab, notice that the **E-mail** box is populated with the email address for the reconnected mailbox. 
    
- In theExchange Management Shell, run the following command.
    
  ```
  Get-User <identity>
  ```

    The **UserMailbox** value for the  _RecipientType_ property indicates that the user account and the mailbox are connected. You can also run the **Get-Mailbox** cmdlet to verify that the mailbox exists. 
    

