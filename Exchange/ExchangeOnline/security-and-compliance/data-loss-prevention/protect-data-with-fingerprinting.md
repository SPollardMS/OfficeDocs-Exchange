---
title: "Protect form data with document fingerprinting"
ms.author: stephow
author: stephow-msft
manager: nesuexws
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.service: exchange-online
localization_priority: Normal
ms.assetid: 110c839b-7693-42f6-aa5d-58ce64f4c357
description: "If your organization uses forms to collect sensitive information, users might try emailing those forms to outside contacts, which creates a security risk. Data loss prevention (DLP) in Exchange helps you protect that information by detecting it with Document Fingerprinting. To use document fingerprinting, simply upload a blank form, such as an intellectual property document, government form, or other standard form used in your organization. Then, add the resulting document fingerprint to a DLP policy or transport rule. Here's how."
---

# Protect form data with document fingerprinting

If your organization uses forms to collect sensitive information, users might try emailing those forms to outside contacts, which creates a security risk. Data loss prevention (DLP) in Exchange helps you protect that information by detecting it with [Document Fingerprinting](document-fingerprinting.md). To use document fingerprinting, simply upload a blank form, such as an intellectual property document, government form, or other standard form used in your organization. Then, add the resulting document fingerprint to a DLP policy or transport rule. Here's how.
  
> [!VIDEO https://www.microsoft.com/videoplayer/embed/0f803e16-397a-4b83-8a85-06cd4264aaca?autoplay=false]
  
## Use the EAC to create a document fingerprint

![Path to Document Fingerprinting in EAC highlighted](../../media/EAC_Compliance_Management_DLP.png)
  
1. In the Exchange Administration Center EAC, go to **compliance management** \> **data loss prevention**.
    
2. Click **Manage document fingerprints**.
    
3. On the document fingerprints page, click **New**![Add Icon](../../media/ITPro_EAC_AddIcon.gif) to create a new document fingerprint. 
    
4. Give the document fingerprint a **Name** and **Description**. (The name you choose will appear in the sensitive information types list.)
    
5. To upload a form, click **Add**![Add Icon](../../media/ITPro_EAC_AddIcon.gif).
    
6. Choose a form, and click **Open**. (Make sure that the file you upload contains text, isn't password protected, and is in one of the file types that are supported in transport rules. For a list of supported file types, see [Use mail flow rules to inspect message attachments in Office 365](../../security-and-compliance/mail-flow-rules/inspect-message-attachments.md). Otherwise, you'll get an error when you try creating the fingerprint.) Repeat for any additional files you want to add to the document list for this document fingerprint. You can also add or remove files from this document fingerprint later if you want.
    
7. Click **Save**.
    
The document fingerprint is now part of your sensitive information types, and you can add it to a DLP policy or add it to a transport rule via the **The message contains sensitive information…** condition. 
  
!["Apply this rule if" condition highlighted](../../media/EAC_Compliance_Management_DLP_new_rule.png)
  
For more information about adding rules to a DLP policy, see the "Change a DLP policy" section of [Manage DLP Policies](http://technet.microsoft.com/library/ba81fabd-7f7f-4ef7-968f-ce851ada9d70.aspx), and for more information about modifying transport rules, see [Integrating sensitive information rules with transport rules](integrate-sensitive-information-rules.md). If you want to create a new policy, see [Create a DLP policy from a template](create-dlp-policy-from-template.md).
  
## Use the Shell to create a classification rule package based on document fingerprinting

> [!TIP]
> Even though you can create and modify classification rule packages in the Shell, you might find that creating document fingerprints is a little simpler in the EAC. We recommend you try it there before trying this procedure in the Shell. 
  
DLP uses classification rule packages to detect sensitive content in messages. To create a classification rule package based on a document fingerprint, use the **New-Fingerprint** and **New-DataClassification** cmdlets. Because the results of **New-Fingerprint** aren't stored outside the data classification rule, you always run **New-Fingerprint** and **New-DataClassification** or **Set-DataClassification** in the same PowerShell session. The following example creates a new document fingerprint based on the file C:\My Documents\Contoso Employee Template.docx. You store the new fingerprint as a variable so you can use it with the **New-DataClassification** cmdlet in the same PowerShell session. 
  
```
$Employee_Template = Get-Content "C:\My Documents\Contoso Employee Template.docx" -Encoding byte
$Employee_Fingerprint = New-Fingerprint -FileData $Employee_Template -Description "Contoso Employee Template"
```

Now, let's create a new data classification rule named "Contoso Employee Confidential" that uses the document fingerprint of the file C:\My Documents\Contoso Customer Information Form.docx.
  
```
$Employee_Template = Get-Content "C:\My Documents\Contoso Customer Information Form.docx" -Encoding byte
$Customer_Fingerprint = New-Fingerprint -FileData $Customer_Form -Description "Contoso Customer Information Form"
New-DataClassification -Name "Contoso Customer Confidential" -Fingerprints $Customer_Fingerprint -Description "Message contains Contoso customer information." 
```

You can now use the **Get-DataClassification** cmdlet to find all DLP data classification rule packages, and in this example, "Contoso Customer Confidential" is part of the data classification rule packages list. 
  
Finally, add the "Contoso Customer Confidential" data classification rule package to a DLP policy.
  
```
New-TransportRule -Name "Notify :External Recipient Contoso confidential" -NotifySender NotifyOnly -Mode Enforce -SentToScope NotInOrganization -MessageContainsDataClassification @{Name=" Contoso Customer Confidential"}

```

The DLP agent now detects documents that match the Contoso Customer Form.docx document fingerprint.
  
For syntax and parameter information, see [New-Fingerprint](http://technet.microsoft.com/library/b579682a-9922-4db0-b524-bcea0d2cef9b.aspx), [New-DataClassification](http://technet.microsoft.com/library/3c1e90e7-cf49-4a8b-a0c4-c189ab8ab166.aspx), [Set-DataClassification](http://technet.microsoft.com/library/6d40df36-18c7-46f5-b373-69c840a5599b.aspx), and [Get-DataClassification](http://technet.microsoft.com/library/7f1daf42-8805-4313-831c-f473ddfd6371.aspx).
  
## For more information

[Document Fingerprinting](document-fingerprinting.md)
  
[Manage DLP Policies](http://technet.microsoft.com/library/ba81fabd-7f7f-4ef7-968f-ce851ada9d70.aspx)
  
[Integrating sensitive information rules with transport rules](integrate-sensitive-information-rules.md)
  

