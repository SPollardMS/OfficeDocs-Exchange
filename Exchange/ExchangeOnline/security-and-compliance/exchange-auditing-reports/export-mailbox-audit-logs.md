---
title: "Export mailbox audit logs"
ms.author: markjjo
author: markjjo
manager: scotv
ms.date: 6/23/2018
ms.audience: ITPro
ms.topic: article
ms.service: exchange-online
localization_priority: Normal
ms.assetid: b458a95a-3321-4647-8884-cf97f8e7186a
description: "When mailbox auditing is enabled for a mailbox, Microsoft Exchange logs information in the mailbox audit log whenever a user other than the owner accesses the mailbox. Each log entry includes information about who accessed the mailbox and when, the actions performed by the non-owner, and whether the action was successful. Entries in the mailbox audit log are retained for 90 days by default. You can use the mailbox audit log to determine if a user other than the owner has accessed a mailbox."
---

# Export mailbox audit logs

When mailbox auditing is enabled for a mailbox, Microsoft Exchange logs information in the mailbox audit log whenever a user other than the owner accesses the mailbox. Each log entry includes information about who accessed the mailbox and when, the actions performed by the non-owner, and whether the action was successful. Entries in the mailbox audit log are retained for 90 days by default. You can use the mailbox audit log to determine if a user other than the owner has accessed a mailbox. 
  
When you export entries from mailbox audit logs, Microsoft Exchange saves the entries in an XML file and attaches it to an email message sent to the specified recipients.
  
## Before you begin
<a name="beforeyoubegin"> </a>

- Estimated time to complete each procedure: Times are variable. In Exchange Online, the mailbox audit log is sent within a few days after you export it.
    
- In Exchange Online, you have to use Remote Windows PowerShell to perform many of the procedures in this topic. For details, see [Connect to Exchange Online Using Remote PowerShell](http://technet.microsoft.com/library/c8bea338-6c1a-4bdf-8de0-7895d427ee5b.aspx).
    
- Procedures in this topic require specific permissions. See each procedure for its permissions information.
    
- For information about keyboard shortcuts that may apply to the procedures in this topic, see **Keyboard shortcuts in the Exchange admin center**.
    
> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612),[Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351).. 
  
## Configure mailbox audit logging
<a name="configmbxauditing"> </a>

You have to enable mailbox audit logging on each mailbox that you want to audit before you can export and view mailbox audit logs. You also have to configure Microsoft Outlook Web App to allow XML attachments to use Outlook Web App to access the audit log.
  
### Step 1: Enable mailbox audit logging

You have to enable mailbox audit logging for each mailbox that you want to run a non-owner mailbox access report for. If mailbox audit logging isn't enabled for a mailbox, you won't get any results for that mailbox when you export the mailbox audit log.
  
You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Mailbox audit logging" entry in the [Messaging policy and compliance permissions](http://technet.microsoft.com/library/ec4d3b9f-b85a-4cb9-95f5-6fc149c3899b.aspx) topic. 
  
To enable mailbox audit logging for a single mailbox, run the command in the Shell.
  
```
Set-Mailbox <Identity> -AuditEnabled $true
```

To enable mailbox audit logging for all user mailboxes in your organization, run the following commands.
  
```
$UserMailboxes = Get-mailbox -Filter {(RecipientTypeDetails -eq 'UserMailbox')}
```

```
$UserMailboxes | ForEach {Set-Mailbox $_.Identity -AuditEnabled $true}
```

### Step 2: Configure Outlook Web App to allow XML attachments

When you export the mailbox audit log, Microsoft Exchange attaches the audit log, which is an XML file, to an email message. However, Outlook Web App blocks XML attachments by default. To access the exported audit log, you have to use Microsoft Outlook or configure Outlook Web App to allow XML attachments.
  
You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Outlook Web App mailbox policies" entry in the [Client Access Permissions](http://technet.microsoft.com/library/57eca42a-5a7f-4c65-89f0-7a84f2dbea19.aspx) topic. 
  
Perform the following procedures to allow XML attachments in Outlook Web App. In Exchange Server 2013, use the value  `Default` for the  _Identity_ parameter. 
  
1. Run the following command to add XML to the list of allowed file types in Outlook Web App.
    
  ```
  Set-OwaMailboxPolicy -Identity OwaMailboxPolicy-Default -AllowedFileTypes @{add='.xml'}
  ```

2. Run the following command to remove XML from the list of blocked file types in Outlook Web App.
    
  ```
  Set-OwaMailboxPolicy -Identity OwaMailboxPolicy-Default -BlockedFileTypes @{remove='.xml'}
  ```

### How do you know this worked?

To verify that you've successfully configured mailbox audit logging, do the following:
  
1. Run the following command to verify that audit logging is configured for mailboxes.
    
  ```
  Get-Mailbox | FL Name,AuditEnabled
  ```

    A value of  `True` for the  _AuditEnabled_ property verifies that audit logging is enabled. 
    
2. Run the following command to verify that XML attachments are allowed in Outlook Web App.
    
  ```
  Get-OwaMailboxPolicy | Select-Object -ExpandProperty AllowedFileTypes
  ```

    Verify that  `.xml` is included in the list of allowed file types. 
    
3. Run the following command to verify that XML attachments are removed from the blocked file list in Outlook Web App.
    
  ```
  Get-OwaMailboxPolicy | Select-Object -ExpandProperty BlockedFileTypes
  ```

    Verify that  `.xml` isn't included in the list of blocked file types. 
    
## Export the mailbox audit log
<a name="exportauditlog"> </a>

You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "View-only administrator audit logging" entry in the [Shell Infrastructure Permissions](http://technet.microsoft.com/library/3646a4e8-36b2-41fb-89a4-79b0963fcb11.aspx) topic. 
  
1. In the Exchange admin center (EAC), go to **Compliance Management** \> **Auditing**.
    
2. Click **Export mailbox audit logs**.
    
3. Configure the following search criteria for exporting the entries from the mailbox audit log:
    
  - **Start and end dates** Select the date range for the entries to include in the exported file. 
    
  - **Mailboxes to search audit log for** Select the mailboxes to retrieve audit log entries for. 
    
  - **Type of non-owner access** Select one of the following options to define the type of non-owner access to retrieve entries for: 
    
  - **All non-owners** Search for access by administrators and delegated users inside your organization, and by Microsoft datacenter administrators in Exchange Online. 
    
  - **External users** Search for access by Microsoft datacenter administrators. 
    
  - **Administrators and delegated users** Search for access by administrators and delegated users inside your organization. 
    
  - **Administrators** Search for access by administrators in your organization. 
    
  - **Recipients** Select the users to send the mailbox audit log to. 
    
4. Click **Export**.
    
    Microsoft Exchange retrieves entries in the mailbox audit log that meet your search criteria, saves them to a file named SearchResult.xml, and then attaches the XML file to an email message sent to the recipients that you specified. 
    
### How do you know this worked?

Sign in to the mailbox where the mailbox audit log was sent. If you've successfully exported the audit log, you'll receive a message sent from Exchange. In Exchange Online, it may take a few days to receive this message. The mailbox audit log (named SearchResult.xml) will be attached to this message. If you've correctly configured Outlook Web App to allow XML attachments, you can download the attached XML file.
  
## View the mailbox audit log
<a name="viewauditlog"> </a>

You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "View-only administrator audit logging" entry in the [Shell Infrastructure Permissions](http://technet.microsoft.com/library/3646a4e8-36b2-41fb-89a4-79b0963fcb11.aspx) topic. 
  
To save and view the SearchResult.xml file:
  
1. Sign in to the mailbox where the mailbox audit log was sent.
    
2. In the Inbox, open the message with the XML file attachment sent by Microsoft Exchange. Notice that the body of the email message contains the search criteria.
    
3. Click the attachment and select to download the XML file.
    
4. Open the SearchResult.xml in Microsoft Excel.
    
## More information
<a name="moreinfo"> </a>

- **Entries in the mailbox audit log** The following example shows an entry from the mailbox audit log contained in the SearchResult.xml file. Each entry is preceded by the **\<Event\>** XML tag and ends with the **\</Event\>** XML tag. This entry shows that the administrator purged the message with the subject, " Notification of litigation hold" from the Recoverable Items folder in David's mailbox on April 30, 2010.
    
  ```
  <Event MailboxGuid="6d4fbdae-e3ae-4530-8d0b-f62a14687939" 
    Owner="PPLNSL-dom\david50001-1363917750" 
    LastAccessed="2010-04-30T11:01:55.140625-07:00" 
    Operation="HardDelete" 
    OperationResult="Succeeded" 
    LogonType="Admin"
   FolderId="0000000073098C3277988F4CB882F5B82EBF64610100A7C317F68C24304BBD18ABE1F185E79B00000026BD4F0000"
    FolderPathName="\Recoverable Items\Deletions"
    ClientInfoString="Client=OWA;Action=ViaProxy" 
    ClientIPAddress="10.196.241.168" 
    InternalLogonType="Owner"
    MailboxOwnerUPN="david@contoso.com"
    MailboxOwnerSid="S-1-5-21-290112810-296651436-1966561949-1151" 
    CrossMailboxOperation="false" 
    LogonUserDN="Administrator"
    LogonUserSid="S-1-5-21-290112810-296651436-1966561949-1149">
    <SourceItems>
     <ItemId="0000000073098C3277988F4CB882F5B82EBF64610700A7C317F68C24304BBD18ABE1F185E79B00000026BD4F0000A7C317F68C24304BBD18ABE1F185E79B00000026BD540"
      Subject="Notification of litigation hold"
      FolderPathName="\Recoverable Items\Deletions" /> 
    </SourceItems>
  </Event>
  ```

- **Useful fields in the mailbox audit log** Here's a description of useful fields in the mailbox audit log. They can help you identify specific information about each instance of non-owner access of a mailbox. 
    
|**Field**|**Description**|
|:-----|:-----|
|Owner <br/> |The owner of the mailbox that was accessed by a non-owner.  <br/> |
|LastAccessed <br/> |The date and time when the mailbox was accessed.  <br/> |
|Operation <br/> |The action that was performed by the non-owner. For more information, see the "What gets logged in the mailbox audit log?" section in [Run a Non-Owner Mailbox Access Report](http://technet.microsoft.com/library/18f52b7e-cd60-4a2f-b8a3-0c08747635bb.aspx).  <br/> |
|OperationResult <br/> |Whether the action performed by the non-owner succeeded or failed.  <br/> |
|LogonType <br/> |The type of non-owner access. These include administrator, delegate, and external.  <br/> |
|FolderPathName <br/> |The name of the folder that contained the message that was affected by the non-owner.  <br/> |
|ClientInfoString <br/> |Information about the mail client used by the non-owner to access the mailbox.  <br/> |
|ClientIPAddress <br/> |The IP address of the computer used by the non-owner to access the mailbox.  <br/> |
|InternalLogonType <br/> |The logon type of the account used by the non-owner to access this mailbox.  <br/> |
|MailboxOwnerUPN <br/> |The email address of the mailbox owner.  <br/> |
|LogonUserDN <br/> |The display name of the non-owner.  <br/> |
|Subject <br/> |The subject line of the email message that was affected by the non-owner.  <br/> |
   
    [When mailbox auditing is enabled for a mailbox, Microsoft Exchange logs information in the mailbox audit log whenever a user other than the owner accesses the mailbox. Each log entry includes information about who accessed the mailbox and when, the actions performed by the non-owner, and whether the action was successful. Entries in the mailbox audit log are retained for 90 days by default. You can use the mailbox audit log to determine if a user other than the owner has accessed a mailbox.When you export entries from mailbox audit logs, Microsoft Exchange saves the entries in an XML file and attaches it to an email message sent to the specified recipients.](#Introduction.md)
    

