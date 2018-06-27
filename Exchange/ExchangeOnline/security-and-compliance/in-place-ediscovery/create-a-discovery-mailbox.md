---
title: "Create a discovery mailbox"
ms.author: markjjo
author: markjjo
manager: scotv
ms.date: 6/23/2018
ms.audience: ITPro
ms.topic: article
ms.service: exchange-online
localization_priority: Normal
ms.assetid: bc20285d-35e2-4e49-9bd3-38abf96114ba
description: "Microsoft Exchange Server 2013 Setup creates a discovery mailbox by default. In Exchange Online, a discovery mailbox is also created by default. Discovery mailboxes are used as target mailboxes for In-Place eDiscovery searches in the Exchange admin center (EAC). You can create additional discovery mailboxes as required. After you create a new discovery mailbox, you will have to assign Full Access permissions to the appropriate users so they can access eDiscovery search results that are copied to the discovery mailbox."
---

# Create a discovery mailbox

Microsoft Exchange Server 2013 Setup creates a discovery mailbox by default. In Exchange Online, a discovery mailbox is also created by default. Discovery mailboxes are used as target mailboxes for [In-Place eDiscovery](in-place-ediscovery.md) searches in the Exchange admin center (EAC). You can create additional discovery mailboxes as required. After you create a new discovery mailbox, you will have to assign Full Access permissions to the appropriate users so they can access eDiscovery search results that are copied to the discovery mailbox. 
  
> [!CAUTION]
> After a discovery manager copies the results of an eDiscovery search to a discovery mailbox, the mailbox can potentially contain sensitive information. You should control access to discovery mailboxes and make sure only authorized users can access them. 
  
For more information, see [Discovery mailboxes](in-place-ediscovery.md#discmbxs).
  
## What do you need to know before you begin?

- Estimated time to complete: 3 minutes.
    
- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Creating discovery mailboxes" entry in [Messaging policy and compliance permissions](http://technet.microsoft.com/library/ec4d3b9f-b85a-4cb9-95f5-6fc149c3899b.aspx) topic. 
    
- Discovery mailboxes have a mailbox storage quota of 50 gigabytes (GB). This storage quota can't be increased.
    
- You can't use the EAC to create a discovery mailbox or assign permissions to access it. You have to use the Shell. In Office 365, use Remote PowerShell connected to your Exchange Online organization.
    
- For information about keyboard shortcuts that may apply to the procedures in this topic, see **Keyboard shortcuts in the Exchange admin center**.
    
> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612),[Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351). 
  
## What do you want to do?

### (Optional) Step 1: Connect to Exchange Online using remote PowerShell

You only need to perform this step if you have an Exchange Online or Office 365 organization. If you have an Exchange Server 2013 organization, go to the next step and run the command in the Exchange Management Shell.
  
1. On your local computer, open Windows PowerShell and run the following command.
    
  ```
  $UserCredential = Get-Credential
  ```

    In the **Windows PowerShell Credential Request** dialog box, type user name and password for an Office 365 global admin account, and then click **OK**.
    
2. Run the following command.
    
  ```
  $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell-liveid/ -Credential $UserCredential -Authentication Basic -AllowRedirection
  ```

3. Run the following command.
    
  ```
  Import-PSSession $Session
  ```

4. To verify that you're connected to your Exchange Online organization, run the following command to get a list of all the mailboxes in your organization.
    
  ```
  Get-Mailbox
  ```

For more information or if you have problems connecting to your Exchange Online organization, see [Connect to Exchange Online using remote PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=517283).
  
### Step 2: Create a discovery mailbox

This example creates a discovery mailbox named SearchResults.
  
```
New-Mailbox -Name SearchResults -Discovery 
```

For detailed syntax and parameter information, see [new-Mailbox](http://technet.microsoft.com/library/42dbb25a-0b23-4775-ae15-7af62c089565.aspx).
  
To display a list of all discovery mailboxes in an Exchange organization, run the following command:
  
```
Get-Mailbox -Resultsize unlimited -Filter {RecipientTypeDetails -eq "DiscoveryMailbox"}
```

For detailed syntax and parameter information, see [Get-Mailbox](http://technet.microsoft.com/library/8a5a6eb9-4a75-47f9-ae3b-a3ba251cf9a8.aspx).
  
### Step 3: Assign permissions to a discovery mailbox

You have to explicitly assign users or groups the necessary permissions to open a discovery mailbox that you've created. Use the following syntax to assign a user or group permissions to open a discovery mailbox and view search results:
  
```
Add-MailboxPermission <Name of the discovery mailbox> -User <Name of user or group> -AccessRights FullAccess -InheritanceType all

```

For example, the following command assigns the Full Access permission to the Litigation Managers group, so members of the group can open the Fabrikam Litigation discovery mailbox.
  
```
Add-MailboxPermission "Fabrikam Litigation" -User "Litigation Managers" -AccessRights FullAccess -InheritanceType all

```

For detailed syntax and parameter information, see [Add-MailboxPermission](http://technet.microsoft.com/library/a9aacbf5-5e6c-47ef-95d6-e24547e95d01.aspx).
  
## More information

- By default, members of the Discovery Management role group only have Full Access permission to the default Discovery Search Mailbox. You will have to explicitly assign the Full Access permission to the Discovery Management role group if you want members to open a discovery mailbox that you've created.
    
- Although visible in Exchange address lists, users can't send email to a discovery mailbox. Email delivery to discovery mailboxes is prohibited with delivery restrictions. This preserves the integrity of search results copied to a discovery mailbox.
    
- A discovery mailbox can't be repurposed or converted to another type of mailbox.
    
- You can remove a discovery mailbox as you would any other type of mailbox.
    

