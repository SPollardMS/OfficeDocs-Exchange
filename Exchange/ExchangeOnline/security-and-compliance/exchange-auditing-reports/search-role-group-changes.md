---
title: "Search the role group changes or administrator audit logs"
ms.author: markjjo
author: markjjo
manager: scotv
ms.date: 6/23/2018
ms.audience: ITPro
ms.topic: article
ms.service: exchange-online
localization_priority: Normal
ms.assetid: c7188d53-e672-492b-b57d-cd711379ddb3
description: "You can search the administrator audit logs to discover who made changes to organization, server, and recipient configuration. This can be helpful when you're trying to track the cause of unexpected behavior, to identify a malicious administrator, or to verify that compliance requirements are being met. For more information about administrator audit logging, see Administrator audit logging."
---

# Search the role group changes or administrator audit logs

You can search the administrator audit logs to discover who made changes to organization, server, and recipient configuration. This can be helpful when you're trying to track the cause of unexpected behavior, to identify a malicious administrator, or to verify that compliance requirements are being met. For more information about administrator audit logging, see [Administrator audit logging](http://technet.microsoft.com/library/22b17eb8-d8ee-4599-b202-d6a7928c20d9.aspx).
  
If you want to search the mailbox audit log, see [Mailbox Audit Logging](http://technet.microsoft.com/library/29b67d58-eef9-4ad4-863f-562405ea8794.aspx).
  
> [!TIP]
> In Exchange Online, you can use the EAC to view entries in the administrator audit log. For more information, see [View the administrator audit log](view-administrator-audit-log.md). 
  
## What do you need to know before you begin?

- Estimated time to complete each procedure: less than 5 minutes
    
- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "View-only administrator audit logging" entry in the [Exchange and Shell Infrastructure Permissions](http://technet.microsoft.com/library/3646a4e8-36b2-41fb-89a4-79b0963fcb11.aspx) topic. 
    
- Administrator audit logging is enabled by default. To verify that it's enabled, run the following command: 
    
  ```
  Get-AdminAuditLogConfig | FL AdminAuditLogEnabled
  ```

    A value of  `True` indicates that administrator audit logging is enabled. A value of  `False` indicates that it's disabled. If you need to enable administrator audit logging for an on-premises Exchange organization, run the following command: 
    
  ```
  Set-AdminAuditLogConfig -AdminAuditLogEnabled $true
  ```

    > [!NOTE]
    > The **Set-AdminAuditLogConfig** cmdlet isn't available in Exchange Online. 
  
    For more information, see [Configure Administrator Audit Logging](http://technet.microsoft.com/library/15c284c0-b8e6-42ca-9913-7c59fdb6885d.aspx).
    
- For information about keyboard shortcuts that may apply to the procedures in this topic, see **Keyboard shortcuts in the Exchange admin center**.
    
> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612),[Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351). 
  
## What do you want to do?

### Use the EAC to run the management role group changes report
<a name="EACRGReport"> </a>

If you want to know what changes to management role group membership have been made to role groups in your organization, you can use the Administrator Role Group report in the Exchange Administration Center (EAC). Using the Administrator Role Group report, you can view a list of role groups that have changed during a specified date range. You can also select the specific role groups you want to view changes for.
  
1. In the EAC, select **Compliance management** \> **Auditing**, and then click **Run an administrator role group report**.
    
2. Select a date range using the **Start date** and **End date** fields. 
    
3. Click **Select role groups**, and then select the role groups you want to show changes for or leave this field blank to search for changes in all role groups.
    
4. Click **Search**.
    
If any changes are found using the criteria you specified, a list of changes will be displayed in the results pane. Clicking a role group displays the changes to the role group in the details pane. 
  
### Use the EAC to export the administrator audit log
<a name="EACAdminReport"> </a>

If you want to create an XML file that contains changes made to your organization, you can use the Export Administrator Audit Log report in the EAC. Using the Export Administrator Audit Log report, you can specify a date range to search for audit log entries that contain changes made by users you specify. The XML file is then sent to a recipient as an email attachment. The maximum size of the XML file is 10 megabytes (MB).
  
> [!NOTE]
> Outlook Web App doesn't allow you to open XML attachments by default. You can either configure Exchange to allow XML attachments to be viewed using Outlook Web App, or you can use another email client, such as Microsoft Outlook, to view the attachment. For information about how to configure Outlook Web App to allow you to view an XML attachment, see **View or configure Outlook Web App virtual directories**. 
  
1. In the EAC, select **Compliance management** \> **Auditing**, and then click **Export the administrator audit log**. 
    
2. Select a date range using the **Start date** and **End date** fields. 
    
3. In the **Send the auditing report to** field, click **Select users** and then select the recipient you want to send the report to. 
    
4. Click **Export**.
    
If any log entries are found using the criteria you specified, an XML file will be created and sent as an email attachment to the recipient you specified.
  
### Use the Shell to search for audit log entries
<a name="SearchAdminAuditLog"> </a>

You can use the Shell to search for audit log entries that meet the criteria you specify. For a list of search criteria, see [Administrator audit logging](http://technet.microsoft.com/library/22b17eb8-d8ee-4599-b202-d6a7928c20d9.aspx). This procedure uses the **Search-AdminAuditLog** cmdlet and displays search results in the Shell. You can use this cmdlet when you need to return a set of results that exceeds the limits defined on the **New-AdminAuditLogSearch** cmdlet or in the EAC Audit Reporting reports. 
  
If you want to send audit log search results in an email attachment to a recipient, see **Use the Shell to search for audit log entries and send results to a recipient** later in this topic. 
  
To search the audit log for criteria you specify, use the following syntax.
  
```
Search-AdminAuditLog - Cmdlets <cmdlet 1, cmdlet 2, ...> -Parameters <parameter 1, parameter 2, ...> -StartDate <start date> -EndDate <end date> -UserIds <user IDs> -ObjectIds <object IDs> -IsSuccess <$True | $False >
```

> [!NOTE]
> The **Search-AdminAuditLog** cmdlet returns a maximum of 1,000 log entries by default. Use the  _ResultSize_ parameter to specify up to 250,000 log entries. Or, use the value  `Unlimited` to return all entries. 
  
This example performs a search for all audit log entries with the following criteria:
  
- **Start date** 08/04/2012 
    
- **End date** 10/03/2012 
    
- **User IDs** davids, chrisd, kima 
    
- **Cmdlets** **Set-Mailbox**
    
- **Parameters** _ProhibitSendQuota_,  _ProhibitSendReceiveQuota_,  _IssueWarningQuota_,  _MaxSendSize_,  _MaxReceiveSize_
    
```
Search-AdminAuditLog -Cmdlets Set-Mailbox -Parameters ProhibitSendQuota, ProhibitSendReceiveQuota, IssueWarningQuota, MaxSendSize, MaxReceiveSize -StartDate 08/04/2012 -EndDate 10/03/2012 -UserIds davids, chrisd, kima
```

This example searches for changes made to a specific mailbox. This is useful if you're troubleshooting or you need to provide information for an investigation. The following criteria are used:
  
- **Start date** 05/01/2012 
    
- **End date** 10/03/2012 
    
- **Object ID** contoso.com/Users/DavidS 
    
```
Search-AdminAuditLog -StartDate 05/01/2012 -EndDate 10/03/2012 -ObjectID contoso.com/Users/DavidS
```

If your searches return many log entries, we recommend that you use the procedure provided in **Use the Shell to search for audit log entries and send results to a recipient** later in this topic. The procedure in that section sends an XML file as an email attachment to the recipients you specify, enabling you to more easily extract the data you're interested in. 
  
For detailed syntax and parameter information, see [Search-AdminAuditLog](http://technet.microsoft.com/library/87a0cd2d-dd59-4098-b740-75f0cc7bf8e7.aspx).
  
#### View details of audit log entries

The **Search-AdminAuditLog** cmdlet returns the fields described in the "Audit log contents section of [Administrator audit logging](http://technet.microsoft.com/library/22b17eb8-d8ee-4599-b202-d6a7928c20d9.aspx). Of the fields returned by the cmdlet, two fields, **CmdletParameters** and **ModifiedProperties**, contain additional information that isn't viewable by default. 
  
To view the contents of the **CmdletParameters** and **ModifiedProperties** fields, use the following steps. Or, you can use the procedure in **Use the Shell to search for audit log entries and send results to a recipient** later in this topic to create an XML file. 
  
This procedure uses the following concepts:
  
- [Arrays](http://technet.microsoft.com/library/599ed6d7-553a-41be-b4a3-aa75ab9dbb5d.aspx)
    
- [User-Defined Variables](http://technet.microsoft.com/library/8af62634-2e0b-4da0-ae94-a890f6f24d8a.aspx)
    
1. Decide the criteria you want to search for, run the **Search-AdminAuditLog** cmdlet, and store the results in a variable using the following command. 
    
  ```
  $Results = Search-AdminAuditLog <search criteria>
  ```

2. Each audit log entry is stored as an array element in the variable  `$Results`. You can select an array element by specifying its array element index. Array element indexes start at zero (0) for the first array element. For example, to retrieve the 5th array element, which has an index of 4, use the following command.
    
  ```
  $Results[4]
  ```

3. The previous command returns the log entry stored in array element 4. To see the contents of the **CmdletParameters** and **ModifiedProperties** fields for this log entry, use the following commands. 
    
  ```
  $Results[4].CmdletParameters
  $Results[4].ModifiedProperties
  ```

4. To view the contents of the **CmdletParameters** or **ModifiedParameters** fields in another log entry, change the array element index. 
    
### Use the Shell to search for audit log entries and send results to a recipient
<a name="NewAdminAuditLogSearch"> </a>

You can use the Shell to search for audit log entries that meet the criteria you specify, and then send those results to a recipient you specify as an XML file attachment. The results are sent to the recipient within 15 minutes. For a list of search criteria, see [Administrator audit logging](http://technet.microsoft.com/library/22b17eb8-d8ee-4599-b202-d6a7928c20d9.aspx). 
  
> [!NOTE]
> Outlook Web App doesn't allow you to open XML attachments by default. You can either configure Exchange to allow XML attachments to be viewed using Outlook Web App, or you can use another email client, such as Microsoft Outlook, to view the attachment. For information about how to configure Outlook Web App to allow you to view an XML attachment, see **View or configure Outlook Web App virtual directories**. 
  
To search the audit log for criteria you specify, use the following syntax.
  
```
New-AdminAuditLogSearch -Cmdlets <cmdlet 1, cmdlet 2, ...> -Parameters <parameter 1, parameter 2, ...> -StartDate <start date> -EndDate <end date> -UserIds <user IDs> -ObjectIds <object IDs> -IsSuccess <$True | $False > -StatusMailRecipients <recipient 1, recipient 2, ...> -Name <string to include in subject>
```

This example performs a search for all audit log entries with the following criteria:
  
- **Start date** 08/04/2012 
    
- **End date** 10/03/2012 
    
- **User IDs** davids, chrisd, kima 
    
- **Cmdlets** **Set-Mailbox**
    
- **Parameters** _ProhibitSendQuota_,  _ProhibitSendReceiveQuota_,  _IssueWarningQuota_,  _MaxSendSize_,  _MaxReceiveSize_
    
The command sends the results to the davids@contoso.com SMTP address with "Mailbox limit changes" included in the subject line of the message.
  
```
New-AdminAuditLogSearch -Cmdlets Set-Mailbox -Parameters ProhibitSendQuota, ProhibitSendReceiveQuota, IssueWarningQuota, MaxSendSize, MaxReceiveSize -StartDate 08/04/2012 -EndDate 10/03/2012 -UserIds davids, chrisd, kima -StatusMailRecipients davids@contoso.com -Name "Mailbox limit changes"
```

> [!NOTE]
> The report that the **New-AdminAuditLogSearch** cmdlet generates can be a maximum of 10 MB in size. If the search you perform returns a report larger than 10 MB, change the search criteria you specified. For example, reduce the size of the date range and run multiple reports, each with a portion of the original date range. 
  
For more information about the format of the XML file, see [Administrator Audit Log Structure](http://technet.microsoft.com/library/87e259c9-c884-4d53-bd78-d13f2300d73e.aspx).
  
For detailed syntax and parameter information, see [New-AdminAuditLogSearch](http://technet.microsoft.com/library/52a221e0-ded1-44dc-a626-ca264eca4113.aspx).
  

