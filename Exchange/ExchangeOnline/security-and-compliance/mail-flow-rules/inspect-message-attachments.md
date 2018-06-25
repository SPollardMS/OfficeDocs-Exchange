---
title: "Use mail flow rules to inspect message attachments in Office 365"
ms.author: stephow
author: stephow
manager: scotv
ms.date: 1/26/2018
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 874d1c78-a8ec-4938-b388-d3208c2fa971
description: "You can inspect email attachments in your Office 365 organization by setting up mail flow rules (also known as transport rules). Exchange Online offers mail flow rules that provide the ability to examine email attachments as a part of your messaging security and compliance needs. When you inspect attachments, you can then take action on the messages that were inspected based on the content or characteristics of those attachments. Here are some attachment-related tasks you can do by using mail flow rules:"
---

# Use mail flow rules to inspect message attachments in Office 365

You can inspect email attachments in your Office 365 organization by setting up mail flow rules (also known as transport rules). Exchange Online offers mail flow rules that provide the ability to examine email attachments as a part of your messaging security and compliance needs. When you inspect attachments, you can then take action on the messages that were inspected based on the content or characteristics of those attachments. Here are some attachment-related tasks you can do by using mail flow rules:
  
- Search for files with text that matches a pattern you specify, and add a disclaimer to the end of the message.
    
- Inspect content within attachments and, if there are any keywords you specify, redirect the message to a moderator for approval before it's delivered.
    
- Check for messages with attachments that can't be inspected and then block the entire message from being sent.
    
- Check for attachments that exceed a certain size and then notify the sender of the issue if you choose to prevent the message from being delivered.
    
- Check whether the properties of an attached Office document match the values that you specify. With this condition, you can integrate the requirements of your mail flow rules and DLP policies with a third-party classification system, such as SharePoint Server 2013 or Windows Server 2012 R2 File Classification Infrastructure (FCI).
    
- Create notifications that alert users if they send a message that has matched a mail flow rule.
    
- Block all messages containing attachments. For examples, see [Common attachment blocking scenarios for mail flow rules](common-attachment-blocking-scenarios.md).
    
> [!NOTE]
> All of these conditions will scan compressed archive attachments. 
  
Exchange Online admins can create mail flow rules in the Exchange admin center (EAC) at **Mail flow** \> **Rules**. You need to be assigned permissions before you can perform this procedure. After you start to create a new rule, you can see the full list of attachment-related conditions by clicking **More options** \> **Any attachment** under **Apply this rule if**. The attachment-related options are shown in the following diagram.
  
![List of conditions for attachments](../../media/c8ab24df-dbb6-4760-bfb0-b62938bfb447.png)
  
 For more information about mail flow rules, including the full range of conditions and actions that you can choose, see [Mail flow rules (transport rules) in Exchange Online](mail-flow-rules.md). Exchange Online Protection (EOP) and hybrid customers can benefit from the mail flow rules best practices provided in [Best Practices for Configuring EOP](http://technet.microsoft.com/library/faf1efd1-3b0c-411a-804d-17f37292eac0.aspx). If you're ready to start creating rules, see [Manage mail flow rules](manage-mail-flow-rules.md).
  
## Inspect the content within attachments

You can use the mail flow rule conditions in the following table to examine the content of attachments to messages. For these conditions, only the first one megabyte (MB) of text extracted from an attachment is inspected. Note that the 1 MB limit refers to the extracted text, not the file size of the attachment. For example, a 2 MB file may contain less than 1 MB of text, so all of the text would be inspected.
  
In order to start using these conditions when inspecting messages, you need to add them to a mail flow rule. Learn about creating or changing rules at [Manage mail flow rules](manage-mail-flow-rules.md).
  
|**Condition name in the EAC**|**Condition name in Exchange Online PowerShell**|**Description**|
|:-----|:-----|:-----|
|**Any attachment's content includes** <br/> **Any attachment** \> **content includes any of these words** <br/> | _AttachmentContainsWords_ <br/> |This condition matches messages with supported file type attachments that contain a specified string or group of characters.  <br/> |
|**Any attachment's content matches** <br/> **Any attachment** \> **content matches these text patterns** <br/> | _AttachmentMatchesPatterns_ <br/> |This condition matches messages with supported file type attachments that contain a text pattern that matches a specified regular expression.  <br/> |
|**Any attachment's content can't be inspected** <br/> **Any attachment** \> **content can't be inspected** <br/> | _AttachmentIsUnsupported_ <br/> |Mail flow rules only can inspect the content of supported file types. If the mail flow rule encounters an attachment that isn't supported, the  _AttachmentIsUnsupported_ condition is triggered. The supported file types are described in the next section.  <br/> |
   
 **Notes**:
  
> The conditions names in Exchange Online PowerShell are parameters names on the **New-TransportRule** and **Set-TransportRule** cmdlets. For more information, see [New-TransportRule](http://technet.microsoft.com/library/eb3546bf-ca37-474e-9c22-962fe95af276.aspx).
    
> Learn more about property types for these conditions at [Mail flow rule conditions and exceptions (predicates) in Exchange Online](conditions-and-exceptions.md) and [Mail flow rule conditions and exceptions (predicates) in Exchange Online Protection](http://technet.microsoft.com/library/04edeaba-afd4-4207-b2cb-51bcc44e483c.aspx).
    
> To learn how to use Windows PowerShell to connect to Exchange Online, see [Connect to Exchange Online PowerShell](https://go.microsoft.com/fwlink/p/?linkid=396554).
    
### Supported file types for mail flow rule content inspection
<a name="supported"> </a>

The following table lists the file types supported by mail flow rules. The system automatically detects file types by inspecting file properties rather than the actual file name extension, thus helping to prevent malicious hackers from being able to bypass mail flow rule filtering by renaming a file extension. A list of file types with executable code that can be checked within the context of mail flow rules is listed later in this topic.
  
|**Category**|**File extension**|**Notes**|
|:-----|:-----|:-----|
|Office 2007 and later  <br/> |.docm, .docx, .pptm, .pptx, .pub, .one, .xlsb, .xlsm, .xlsx  <br/> |Microsoft OneNote and Microsoft Publisher files aren't supported by default.  <br/> The contents of any embedded parts contained within these file types are also inspected. However, any objects that aren't embedded (for example, linked documents) aren't inspected.  <br/> |
|Office 2003  <br/> |.doc, .ppt, .xls  <br/> |None  <br/> |
|Additional Office files  <br/> |.rtf, .vdw, .vsd, .vss, .vst  <br/> |None  <br/> |
|Adobe PDF  <br/> |.pdf  <br/> |None  <br/> |
|HTML  <br/> |.html  <br/> |None  <br/> |
|XML  <br/> |.xml, .odp, .ods, .odt  <br/> |None  <br/> |
|Text  <br/> |.txt, .asm, .bat, .c, .cmd, .cpp, .cxx, .def, .dic, .h, .hpp, .hxx, .ibq, .idl, .inc, inf, .ini, inx, .js, .log, .m3u, .pl, .rc, .reg, .txt, .vbs, .wtx  <br/> |None  <br/> |
|OpenDocument  <br/> |.odp, .ods, .odt  <br/> |No parts of .odf files are processed. For example, if the .odf file contains an embedded document, the contents of that embedded document aren't inspected.  <br/> |
|AutoCAD Drawing  <br/> |.dxf  <br/> |AutoCAD 2013 files aren't supported.  <br/> |
|Image  <br/> |.jpg, .tiff  <br/> |Only the metadata text associated with these image files is inspected. There is no optical character recognition.  <br/> |
|Compressed archive files  <br/> |.bz2, cab, .gz, .rar, .tar, .zip, .7z  <br/> |The content of these files, which were originally in a supported file type format, are inspected and processed in a manner similar to messages that have multiple attachments. The properties of the compressed archive file itself are not inspected. For example, if the container file type supports comments, that field isn't inspected.  <br/> |
   
## Inspect the file properties of attachments

The following conditions can be used in mail flow rules to inspect different properties of files that are attached to messages. In order to start using these conditions when inspecting messages, you need to add them to a mail flow rule. For more information about creating or changing rules, see [Manage mail flow rules](manage-mail-flow-rules.md).
  
|**Condition name in the EAC**|**Condition name in Exchange Online PowerShell**|**Description**|
|:-----|:-----|:-----|
|**Any attachment's file name matches** <br/> **Any attachment** \> **file name matches these text patterns** <br/> | _AttachmentNameMatchesPatterns_ <br/> |This condition matches messages with attachments whose file name contains the characters you specify.  <br/> |
|**Any attachment's file extension matches** <br/> **Any attachment** \> **file extension includes these words** <br/> | _AttachmentExtensionMatchesWords_ <br/> |This condition matches messages with attachments whose file name extension matches what you specify.  <br/> |
|**Any attachment is greater than or equal to** <br/> **Any attachment** \> **size is greater than or equal to** <br/> | _AttachmentSizeOver_ <br/> |This condition matches messages with attachments when those attachments are greater than or equal to the size you specify.  <br/> |
|**The message didn't complete scanning** <br/> **Any attachment** \> **didn't complete scanning** <br/> | _AttachmentProcessingLimitExceeded_ <br/> |This condition matches messages when an attachment is not inspected by the mail flow rules agent.  <br/> |
|**Any attachment has executable content** <br/> **Any attachment** \> **has executable content** <br/> | _AttachmentHasExecutableContent_ <br/> |This condition matches messages that contain executable files as attachments. The supported file types are listed here.  <br/> |
|**Any attachment is password protected** <br/> **Any attachment** \> **is password protected** <br/> | _AttachmentIsPasswordProtected_ <br/> |This condition matches messages with attachments that are protected by a password. Password detection only works for Office documents and .zip files.  <br/> |
|**Any attachment has these properties, including any of these words** <br/> **Any attachment** \> **has these properties, including any of these words** <br/> | _AttachmentPropertyContainsWords_ <br/> |This condition matches messages where the specified property of the attached Office document contains specified words. A property and its possible values are separated with a colon. Multiple values are separated with a comma. Multiple property/value pairs are also separated with a comma.  <br/> |
   
 **Notes**:
  
> The conditions names in Exchange Online PowerShell are parameters names on the **New-TransportRule** and **Set-TransportRule** cmdlets. For more information, see [New-TransportRule](http://technet.microsoft.com/library/eb3546bf-ca37-474e-9c22-962fe95af276.aspx).
    
> Learn more about property types for these conditions at [Mail flow rule conditions and exceptions (predicates) in Exchange Online](conditions-and-exceptions.md) and [Mail flow rule conditions and exceptions (predicates) in Exchange Online Protection](http://technet.microsoft.com/library/04edeaba-afd4-4207-b2cb-51bcc44e483c.aspx).
    
> To learn how to use Windows PowerShell to connect to Exchange Online, see [Connect to Exchange Online PowerShell](https://go.microsoft.com/fwlink/p/?linkid=396554).
    
### Supported executable file types for mail flow rule inspection

The mail flow rules use true type detection to inspect file properties rather than merely the file extensions. This helps to prevent malicious hackers from being able to bypass your rule by renaming a file extension. The following table lists the executable file types supported by these conditions. If a file is found that is not listed here, the  `AttachmentIsUnsupported` condition is triggered. 
  
|**Type of file**|**Native extension**|
|:-----|:-----|
|32-bit Windows executable file with a dynamic link library extension.  <br/> |.dll  <br/> |
|Self-extracting executable program file.  <br/> |.exe  <br/> |
|Uninstallation executable file.  <br/> |.exe  <br/> |
|Program shortcut file.  <br/> |.exe  <br/> |
|32-bit Windows executable file.  <br/> |.exe  <br/> |
|Microsoft Visio XML drawing file.  <br/> |.vxd  <br/> |
|OS/2 operating system file.  <br/> |.os2  <br/> |
|16-bit Windows executable file.  <br/> |.w16  <br/> |
|Disk-operating system file.  <br/> |.dos  <br/> |
|European Institute for Computer Antivirus Research standard antivirus test file.  <br/> |.com  <br/> |
|Windows program information file.  <br/> |.pif  <br/> |
|Windows executable program file.  <br/> |.exe  <br/> |
   
> [!IMPORTANT]
> **.rar** (self-extracting archive files created with the WinRAR archiver), **.jar** (Java archive files), and **.obj** (compiled source code, 3D object, or sequence files) files are **not** considered to be executable file types. To block these files, you can use mail flow rules that look for files with these extensions as described earlier in this topic, or you can configure an antimalware policy that blocks these file types (the common attachment types filter). For more information, see [Configure Anti-Malware Policies](http://technet.microsoft.com/library/b0cfc21f-e3c6-41b6-8670-feb2b2e252e5.aspx). 
  
## Data loss prevention policies and attachment mail flow rules

To help you manage important business information in email, you can include any of the attachment-related conditions along with the rules of a data loss prevention (DLP) policy.
  
DLP policies and attachment-related conditions can help you enforce your business needs by defining those needs as mail flow rule conditions, exceptions, and actions. When you include the sensitive information inspection in a DLP policy, any attachments to messages are scanned for that information only. However, attachment-related conditions such as size or file type are not included until you add the conditions listed in this topic. DLP is not available with all versions of Exchange; learn more at [Data loss prevention](../../security-and-compliance/data-loss-prevention/data-loss-prevention.md).
  
## For more information

For information on broadly blocking email with attachments, regardless of malware status, see [Reducing Malware Threats Through File Attachment Blocking in Exchange Online Protection](http://technet.microsoft.com/library/c4fb4a86-b772-49d0-8773-e8ee897e175d.aspx).
  

