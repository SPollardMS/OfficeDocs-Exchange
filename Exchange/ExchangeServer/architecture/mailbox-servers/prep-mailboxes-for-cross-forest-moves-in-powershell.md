---
title: "Prepare mailboxes for cross-forest moves using the Exchange Management Shell"
ms.author: serdars
author: SerdarSoysal
manager: serdars
ms.date: 6/8/2018
ms.audience: ITPro
ms.topic: article
ms.prod: exchange-server-itpro
localization_priority: Normal
ms.assetid: 2cea59fb-69b7-4a2f-833f-de4d93cf1810
description: "Summary: Learn how to manage cross-forest mailbox moves and migrations in Exchange 2016 by using the Prepare-MoveRequest.ps1 script in the Exchange Management Shell."
---

# Prepare mailboxes for cross-forest moves using the Exchange Management Shell

 **Summary**: Learn how to manage cross-forest mailbox moves and migrations in Exchange 2016 by using the Prepare-MoveRequest.ps1 script in the Exchange Management Shell.
  
Exchange 2016 supports mailbox moves and migrations using the Exchange Management Shell **New-MoveRequest** and **New-MigrationBatch** cmdlets. You can also move the mailbox in the Exchange admin center (EAC). You can move an Exchange 2010, Exchange 2013, or Exchange 2016 mailbox from a source Exchange forest to a target Exchange 2016 forest.
  
To run the **New-MoveRequest** and **New-MigrationBatch** cmdlets, a mail user must exist in the target Exchange forest, and the mail user must have a minimum set of required Active Directory attributes.
  
The sample Windows PowerShell script described in this topic supports this task by synchronizing mailbox users from an Exchange source forest to Exchange 2016 target forests as mail-enabled users. The script copies the Active Directory attributes of the mailbox users in the source forest to the target forest, and then uses the **Update-Recipient** cmdlet to turn the target objects into mail-enabled users.
  
For more information about using and writing scripts, see [Scripting with the Exchange Management Shell](http://technet.microsoft.com/library/94c22e59-7460-4563-af20-79544c2bc2ff.aspx). For more information about preparing for cross-forest moves, see [Prepare mailboxes for cross-forest move requests](prep-mailboxes-for-cross-forest-moves.md).
  
Looking for other management tasks related to remote move requests? Check out [Manage on-premises mailbox moves in Exchange 2016](manage-mailbox-moves.md).
  
## What do you need to know before you begin?

- Locate the script in the following location: Program Files\Microsoft\Exchange Server\V15\Scripts
    
- To run the sample script, you need the following:
    
  - An Exchange source forest, where the mailbox currently resides. This can be an Exchange 2010, Exchange 2013, or Exchange 2016 mailbox.
    
  - A target forest with Exchange 2016 installed, where the mailbox will be moved to.
    
> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at: [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351).
  
## Use the Prepare-MoveRequest.ps1 script to prepare mailboxes for cross-forest moves

Run the script from the Exchange Management Shell on a server role running Exchange 2016 in the target Exchange 2016 forest. The script copies the mailbox attributes from the source forest.
  
To assign a specific authentication credential for the remote forest domain controller, you must first run the Windows PowerShell **Get-Credential** cmdlet and store the user input in a temporary variable. When you run the **Get-Credential** cmdlet, the cmdlet asks for the user name and password of the account used during authentication with the remote forest domain controller. You can then use the temporary variable in the Prepare-MoveRequest.ps1 script. For more information about the **Get-Credential** cmdlet, see [Get-Credential](https://go.microsoft.com/fwlink/p/?LinkId=142122).
  
> [!NOTE]
> Make sure that you use two separate credentials for the local forest and the remote forest when calling this script.
  
1. Run the following commands to get the local forest and remote forest credentials.
    
  ```
  $LocalCredentials = Get-Credential
  ```

  ```
  $RemoteCredentials = Get-Credential
  ```

2. Run the following commands to pass the credential information to the _LocalForestCredential_ and _RemoteForestCredential_ parameters in the `Prepare-MoveRequest.ps1` script.
    
  ```
  Prepare-MoveRequest.ps1 -Identity JohnSmith@Fabrikan.com -RemoteForestDomainController DC001.Fabrikam.com -RemoteForestCredential $RemoteCredentials -LocalForestDomainController DC001.Contoso.com -LocalForestCredential $LocalCredentials
  ```

### Parameter set of the script

The following table describes the parameter set for the script.
  
**Parameter set of the Prepare-MoveRequest.ps1 script**

|**Parameter**|**Required**|**Description**|
|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |The _Identity_ parameter uniquely identifies a mailbox in the source forest. Identity can be any of the following values: Common name (CN), Alias, **proxyAddress** property, **objectGuid** property, or **DisplayName** property  <br/> |
| _RemoteForestCredential_ <br/> |Required  <br/> |The _RemoteForestCredential_ parameter specifies the administrator who has permissions to copy data from the source forest Active Directory.  <br/> |
| _RemoteForestDomainController_ <br/> |Required  <br/> |The _RemoteForestDomainController_ parameter specifies a domain controller in the source forest where the mailbox resides.  <br/> |
| _DisableEmailAddressPolicy_ <br/> |Optional  <br/> |The _DisableEmailAddressPolicy_ parameter specifies whether the Email Address Policy (EAP) should be disabled when creating a **MailUser** object in the target forest.  <br/> When you specify this parameter, the EAP in the target forest won't be applied.  <br/> **Note**: When you specify this parameter, the **MailUser** object won't have e-mail address mapping in the local forest domain stamped. This is usually stamped by the EAP.  <br/> |
| _LinkedMailUser_ <br/> |Optional  <br/> |The _LinkedMailUser_ switch specifies whether to create a linked MailUser in the local forest for the mailbox user in the remote forest.  <br/> If the switch is provided, the script creates a target **MailUser** object linked to the source mailbox. If the switch is omitted, the script creates a regular target **MailUser** object.  <br/> |
| _LocalForestCredential_ <br/> |Optional  <br/> |The _LocalForestCredential_ parameter specifies the administrator with permissions to write data to the target forest Active Directory.  <br/> We recommend that you explicitly specify this parameter to avoid Active Directory permission issues.  <br/> If the remote forest and the local forest have a trusted relationship configured, don't use a user account from the remote forest as the local forest credential, even though the remote user account may have permission to modify Active Directory in the local forest.  <br/> |
| _LocalForestDomainController_ <br/> |Optional  <br/> |The _LocalForestDomainController_ parameter specifies a domain controller in the target forest where the mail-enabled user will be created.  <br/> We recommend that you specify this parameter to avoid possible domain controller replication delay issues in the local forest that could occur if a random domain controller is selected.  <br/> |
| _MailboxDeliveryDomain_ <br/> |Optional  <br/> |The _MailboxDeliveryDomain_ parameter specifies an authoritative domain of the source forest so that the script can select the correct source mailbox user's **proxyAddress** property as the target mail-enabled user's **targetAddress** property.  <br/> By default, the primary SMTP address of the source mailbox user is set as the **targetAddress** property of the target mail-enabled user.  <br/> |
| _OverWriteLocalObject_ <br/> |Optional  <br/> |The _OverWriteLocalObject_ parameter is used for users created by the Active Directory Migration Tool. The properties are copied from the existing mail contact to the newly created mail user. However, after this copy, the script also copies the properties from the source forest user to the newly created mail user.  <br/> |
| _TargetMailUserOU_ <br/> |Optional  <br/> |The _TargetMailuserOU_ parameter specifies the organizational unit (OU) under which the target mail-enabled user will be created.  <br/> |
| _UseLocalObject_ <br/> |Optional  <br/> |The _UseLocalObject_ parameter specifies whether to convert the existing local object to the required target mail-enabled user if the script detects an object in the local forest that conflicts with the to-be-created mail-enabled user.  <br/> |
   
## Examples

This section contains several examples of how you can use the Prepare-MoveRequest.ps1 script.
  
### Example: Single linked mail-enabled user

This example provisions a single linked mail-enabled user in the local forest, when there is forest trust between the remote forest and local forest.
  
1. Run the following commands to get the local forest and remote forest credentials.
    
  ```
  $LocalCredentials = Get-Credential
  ```

  ```
  $RemoteCredentials = Get-Credential
  ```

2. Run the following command to pass the credential information to the _LocalForestCredential_ and _RemoteForestCredential_ parameters in the Prepare-MoveRequest.ps1 script.
    
  ```
  Prepare-MoveRequest.ps1 -Identity JamesAlvord@Contoso.com -RemoteForestDomainController DC001.Fabrikam.com -RemoteForestCredential $RemoteCredentials -LocalForestDomainController DC001.Contoso.com -LocalForestCredential $LocalCredentials -LinkedMailUser
  ```

### Example: Pipelining

This example supports pipelining if you supply a list of mailbox identities.
  
1. Run the following command.
    
  ```
  $UserCredentials = Get-Credential
  ```

2. Run the following command to pass the credential information to the _RemoteForestCredential_ parameter in the Prepare-MoveRequest.ps1 script.
    
  ```
  "IanP@Contoso.com", "JoeAn@Contoso.com" | Prepare-MoveRequest.ps1 -RemoteForestDomainController DC001.Fabrikam.com -RemoteForestCredential $UserCredentials
  ```

### Example: Use a .csv file to bulk-create mail-enabled users

You can generate a .csv file containing a list of mailbox identities from the source forest, which allows you to pipe the content of this file into the script to bulk-create the target mail-enabled users.
  
For example, the content of the .csv file can be:
  
```
Identity
Ian@contoso.com
John@contoso.com
Cindy@contoso.com
```

This example calls a .csv file to bulk create the target mail-enabled users.
  
1. Run the following command to get the remote forest credentials.
    
  ```
  $UserCredentials = Get-Credential
  ```

2. Run the following command to pass the credential information to the _RemoteForestCredential_ parameter in the Prepare-MoveRequest.ps1 script.
    
  ```
  Import-Csv Test.csv | Prepare-MoveRequest.ps1 -RemoteForestDomainController DC001.Fabrikam.com -RemoteForestCredential $UserCredentials
  ```

## Script behavior per target object

This section describes how the script performs in relation to several scenarios for target objects.
  
### Duplicate target mail-enabled object

When the script attempts to create a target mail-enabled user from the source mailbox user, and it detects a duplicate local mail-enabled object, it uses the following logic:
  
- If the source mailbox user's **masterAccountSid** attribute equals any target object's **objectSid** or **masterAccountSid** attribute: 
    
  - If the target object isn't mail-enabled, the script returns an error because the script doesn't support converting an object that isn't mail-enabled to a mail-enabled user.
    
  - If the target object is mail-enabled, the target object is a duplicate.
    
- If an address in the source mailbox user's **proxyAddress** properties (smtp/x500 only) equals an address in a target object's **proxyAddress** properties (smtp/x500 only), the target object is a duplicate.
    
The script prompts the user about the duplicate objects.
  
If the target mail-enabled object is a mail-enabled user or contact, which is most likely created by a cross-forest (Identity Lifecycle Management 2007 Service Pack 1-based) global address list (GAL) synchronization deployment, the user can run the script again with the _UseLocalObject_ parameter to use the target mail-enabled object for mailbox migration.
  
### Mail-enabled user

If the target object is a mail-enabled user, the script copies the following attributes from the source mailbox user to the target mail-enabled user:
  
- **msExchMailboxGUID**
    
- **msExchArchiveGUID**
    
- **msExchArchiveName**
    
If the _LinkedMailUser_ parameter is set, the script copies the source **objectSid** / **masterAccountSid** attribute.
  
### Mail-enabled contact

If the target object is a mail-enabled contact, the script deletes the existing contact and copies all its attributes to a new mail-enabled user. The script also copies the following attributes from the source mailbox user:
  
- **msExchMailboxGUID**
    
- **msExchArchiveGUID**
    
- **msExchArchiveName**
    
- **sAMAccountName**
    
- **userAccountControl** (set to 514; equivalent to `0x202, ACCOUNTDISABLE | NORMAL_ACCOUNT`)
    
- **userPrincipalName**
    
If the _LinkedMailUser_ parameter is set, the script copies the source **objectSid** / **masterAccountSid** attribute.
  
### LegacyExchangeDN attribute

When the **Update-Recipient** cmdlet is called to convert the target object into a mail-enabled user, a new **LegacyExchangeDN** attribute is generated for the target mail-enabled user. The script copies the **LegacyExchangeDN** attribute of the target mail-enabled user as an x500 address to the **proxyAddress** properties of the source mailbox user.
  

