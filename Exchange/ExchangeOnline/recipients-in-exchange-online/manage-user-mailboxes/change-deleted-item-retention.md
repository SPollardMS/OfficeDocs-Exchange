---
title: "Change how long permanently deleted items are kept for an Exchange Online mailbox"
ms.author: kwekua
author: kwekua
manager: scotv
ms.date: 12/9/2016
ms.audience: ITPro
ms.topic: article
ms.service: exchange-online
localization_priority: Normal
ms.assetid: ce17f1ec-b96c-4c9e-b20a-507fe0afc684
description: "If you've permanently deleted an item in Microsoft Outlook or Outlook Web App, the item is moved to a folder (Recoverable Items \> Deletions) and kept there for 14 days, by default. You can change how long items are kept, up to a maximum of 30 days."
---

# Change how long permanently deleted items are kept for an Exchange Online mailbox

If you've  *permanently*  deleted an item in Microsoft Outlook or Outlook Web App, the item is moved to a folder ( **Recoverable Items** \> **Deletions**) and kept there for 14 days, by default. You can change how long items are kept, up to a maximum of 30 days. 
  
> [!NOTE]
> You must use the Exchange Management Shell (PowerShell) to make the change. Unfortunately, you can't currently do this directly in the Outlook or OWA. 
  
What do you want to do?
  
- [Change how long permanently deleted items are kept](change-deleted-item-retention.md#BKMK_ChangeSteps) to change how long permanently deleted items are kept. 
    
- [Change how long regular deleted items are kept](../../security-and-compliance/messaging-records-management/create-a-retention-policy.md) in the **Deleted Items** folder. 
    
- [More about deleted items and retention time](change-deleted-item-retention.md#BKMK_MoreAbout), including regular deleted items, permanently deleted items, and the folders they're in.
    
## Change how long permanently deleted items are kept
<a name="BKMK_ChangeSteps"> </a>

> [!NOTE]
> You'll need to use PowerShell to change the retention period. Need help? [Steps for using PowerShell with Exchange Online](change-deleted-item-retention.md#BKMK_UsePS)
  
In these examples, we increase the retention period to 30 days, the maximum for Exchange Online mailboxes. But you can set the number to whatever you like, up to that limit. 
  
Need help using Exchange Management Shell? See the [Steps for using PowerShell with Exchange Online](change-deleted-item-retention.md#BKMK_UsePS), or check out [this article](https://go.microsoft.com/fwlink/?LinkId=816875) for all the details. 
  
 **Example 1:** Set Emily Maier's mailbox to keep deleted items for 30 days. In Exchange Management Shell, run the following command. 
  
```
Set-Mailbox -Identity "Emily Maier" -RetainDeletedItemsFor 30
```

 **Example 2:** Set all user mailboxes in the organization to keep deleted items for 30 days. In Exchange Management Shell, run the following command. 
  
```
Get-Mailbox -ResultSize unlimited -Filter {(RecipientTypeDetails -eq 'UserMailbox')} | Set-Mailbox -RetainDeletedItemsFor 30
```

Need more details about using these commands? See the Exchange Management Shell Help topic [Set-Mailbox](http://technet.microsoft.com/library/a0d413b9-d949-4df6-ba96-ac0906dedae2.aspx). 
  
> [!TIP]
> Need to keep deleted items for longer than 30 days? To do this, place the mailbox on In-Place Hold or Litigation Hold. This works because when a mailbox is placed on hold, deleted items are kept and retention settings for deleted items are ignored. See [In-Place Hold and Litigation Hold](../../security-and-compliance/in-place-and-litigation-holds.md). 
  
## Check to be sure the value is changed
<a name="BKMK_ChangeSteps"> </a>

> [!NOTE]
> You'll need to use PowerShell to check the value. Need help? [Steps for using PowerShell with Exchange Online](change-deleted-item-retention.md#BKMK_UsePS)
  
To check for one mailbox, run the following command:
  
```
Get-Mailbox <Name> | FL RetainDeletedItemsFor
```

Or to check for all mailboxes, run the following command:
  
```
Get-Mailbox -ResultSize unlimited -Filter {(RecipientTypeDetails -eq 'UserMailbox')} | FL Name,RetainDeletedItemsFor
```

## Steps for using PowerShell with Exchange Online
<a name="BKMK_UsePS"> </a>

These steps assume you're using Windows 10 or Windows 8 (or 8.1). (Have an earlier version of Windows? See the [detailed steps](https://go.microsoft.com/fwlink/?LinkId=816875).)
  
1. **Open the PowerShell window:**
    
  - On your computer, type Windows PowerShell in the taskbar search box. 
    
  - When you see the result appear, right-click it, and select **Run as administrator**. (Why? Because you have to run commands in an "elevated" Windows PowerShell window.)
    
  - When you're prompted to "let this app make changes to your PC," click **Yes**.
    
    You'll see a Windows PowerShell window with a prompt like **PS C:\WINDOWS\system32\>**.
    
2. **Make sure PowerShell can run signed scripts:**
    
  - At the prompt in the PowerShell window, run the following command:
    
  ```
  Set-ExecutionPolicy RemoteSigned
  ```

3. **Connect to Exchange Online with your credentials:**
    
  - At the prompt in the PowerShell window, run the following command: 
    
  ```
  $UserCredential = Get-Credential
  ```

  - In the **Windows PowerShell Credential Request** dialog box, type your Office 365 user name and password, and then click **OK**.
    
  - At the prompt in the PowerShell window, run the following command. You can use the "Copy" option to copy it from this page, then just paste it into the PowerShell window.
    
  ```
  $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell-liveid/ -Credential $UserCredential -Authentication Basic -AllowRedirection
  ```

    Note: If you are an Office 365 operated by 21Vianet customer in China, use the following value for the ConnectionUri parameter: https://partner.outlook.cn/PowerShell.
    
  - Finally, run this command:
    
  ```
  Import-PSSession $Session
  ```

Now you're ready to run the command to [Change how long permanently deleted items are kept](change-deleted-item-retention.md#BKMK_ChangeSteps) for permanently deleted Outlook items. 
  
## Be aware of the following
<a name="BKMK_BeAware"> </a>

- Estimated time to complete: Assuming you've got PowerShell set up and connected to Exchange Online, this update is really quick—about 2 minutes. If you need to get PowerShell set up, add extra time for that.
    
- If you want to place a mailbox on [In-Place Hold and Litigation Hold](../../security-and-compliance/in-place-and-litigation-holds.md) so the retention limit is ignored, make sure the mailbox has an Exchange Online (Plan 2) user license. 
    
- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Recipient Provisioning Permissions" section in the [Mailbox Permissions](http://technet.microsoft.com/library/5b690bcb-c6df-4511-90e1-08ca91f43b37.aspx) topic. 
    
- You can only use the Shell to perform this procedure. To learn how to use Windows PowerShell to connect to Exchange Online, see [Connect to Exchange Online PowerShell](https://go.microsoft.com/fwlink/p/?linkid=396554).
    
- For information about keyboard shortcuts that may apply to the procedures in this topic, see **Keyboard shortcuts in the Exchange admin center**.
    
> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612),[Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351). 
  
## More about deleted items and retention time
<a name="BKMK_MoreAbout"> </a>

When a user permanently deletes a mailbox item (such as an email message, a contact, a calendar appointment, or a task) in Microsoft Outlook and Outlook Web App, the item is moved to the **Recoverable Items** folder, and into a subfolder named **Deletions**. 
  
A mailbox item is deleted and moved to the **Recoverable Items** folder when a user does one of the following: 
  
- Deletes an item from the Deleted Items folder
    
- Empties the Deleted Items folder
    
- Permanently deletes an item by selecting it and pressing **Shift+Delete**
    
 How long deleted items are kept in the **Deletions** folder depends on the deleted item retention period that is set for the mailbox. An Exchange Online mailbox keeps deleted items for 14 days, by default. Use the Exchange Management Shell, as shown above, to change this setting, to increase the period up to a maximum of 30 days. 
  
Users can recover, or purge, deleted items before the retention time for a deleted item expires. To do so, they use the **Recover Deleted Items** feature in Outlook or Office Outlook Web App. See the following "Recover deleted items" topics: for [Outlook](https://go.microsoft.com/fwlink/p/?linkId=198206) or for [Outlook Web App](https://go.microsoft.com/fwlink/p/?LinkId=524924).
  
Additional help:
  
- If a user purges a deleted item, you can recover it before the deleted item retention period expires. For details, see [Recover deleted messages in a user's mailbox](recover-deleted-messages.md).
    
- To learn more about deleted item retention, the Recoverable Items folder, In-Place Hold, and Litigation Hold, see [Understanding Recoverable Items](http://technet.microsoft.com/library/efc48fb4-2ed8-4d05-93af-f3505fbc389d.aspx).
    

