---
title: "Procedures for DSNs and NDRs in Exchange 2016"
ms.author: chrisda
author: chrisda
manager: serdars
ms.date: 5/16/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 23c9d844-6fc7-44c9-a308-587338281611
description: "Learn how to view default and custom NDRs, and how to create, modify, and delete custom NDRs in Exchange 2016."
---

# Procedures for DSNs and NDRs in Exchange 2016

Learn how to view default and custom NDRs, and how to create, modify, and delete custom NDRs in Exchange 2016.
  
Like previous versions of Exchange, Exchange 2016 uses delivery status notifications (also known as DSNs, non-delivery reports, NDRs, or bounce messages) to provide delivery status and failure notification messages to message senders. For more information about NDRs, see [DSNs and NDRs in Exchange 2016](ndrs.md).
  
You can use the default NDRs that are included in Exchange, or you can use the Exchange Management Shell to create NDRs with custom text to meet the needs of your organization. The custom NDR text replaces the default text for a given enhanced status code or quota event. If you remove the custom NDR, the default NDR text is used (you can't completely remove a default NDR). You can also disable custom NDRs to preserve them, but not use them (the default NDR text is used).
  
## What do you need to know before you begin?

- Estimated time to complete each procedure: less than 10 minutes.
    
- The main focus of this topic is custom NDR text that replaces the text of default NDRs that are used by Exchange. You can create new NDRs for other enhanced status code values (for example, 5.999.999), but no one will see these NDRs if the enhanced status code isn't used by Exchange. You can use a range of custom enhanced status codes as part of an action for a transport rule. For more information, see [Mail flow rule actions in Exchange 2016](../../messaging-policy-and-compliance/mail-flow-rules/actions.md).
    
- The procedures in this topic are available on Mailbox servers and Edge Transport servers.
    
- You can't use the Exchange admin center (EAC) for most of the procedures in this topic. You need to use the Exchange Management Shell. To learn how to open the Exchange Management Shell in your on-premises Exchange organization, see **Open the Exchange Management Shell**.
    
- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "DSNs" entry in the [Mail flow permissions](../../permissions/feature-permissions/mail-flow-perms.md) topic. 
    
- For information about keyboard shortcuts that may apply to the procedures in this topic, see [Keyboard shortcuts in the Exchange admin center](../../about-documentation/eac-keyboard-shortcuts.md).
    
> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at: [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351). 
  
## Use the Exchange Management Shell to view all default NDRs
<a name="ViewDefaultNDRs"> </a>

To output the list of all default NDRs in all languages to an HTML file named C:\My Documents\Default NDRs.html, run this command:
  
```
Get-SystemMessage -Original | Select-Object -Property Identity,DsnCode,Language,Text | ConvertTo-Html > "C:\My Documents\Default NDRs.html"
```

 **Note**: You should output the list to a file, because the list is very long, and you'll receive errors if you don't have the required language packs installed.
  
For detailed syntax and parameter information, see [Get-SystemMessage](http://technet.microsoft.com/library/54d3650c-fd80-43c0-a64f-41d57673ff8b.aspx).
  
## Use the Exchange Management Shell to view custom NDRs
<a name="ViewDefaultNDRs"> </a>

To view a summary list of all custom NDRs in your organization, run this command:
  
```
Get-SystemMessage
```

 **Note**: By default, there are no custom NDRs, so this command returns no results.
  
To view detailed information for a custom NDR, use this syntax:
  
```
Get-SystemMessage -Identity <NDRIdentity>
```

For an explanation of the available  _\<NDRIdentity\>_ values, see the [Identity values for NDRs](ndr-procedures.md#NDRIdentity) section in this topic. 
  
This example returns detailed information for the custom NDR for the enhanced status code 5.1.2 that's sent to internal senders in English. If there's no custom NDR for this combination of language, audience, and enhanced status code, you'll receive an error.
  
```
Get-SystemMessage En\Internal\5.1.2 | Format-List
```

This example returns detailed information for the custom English NDR for the **ProhibitSendReceive** quota on mailboxes. If there's no custom NDR for this combination of language and quota, you'll receive an error. 
  
```
Get-SystemMessage En\ProhibitSendReceiveMailBox | Format-List
```

For detailed syntax and parameter information, see [Get-SystemMessage](http://technet.microsoft.com/library/54d3650c-fd80-43c0-a64f-41d57673ff8b.aspx).
  
## Create custom NDRs
<a name="ViewDefaultNDRs"> </a>

### Use the Exchange Management Shell to create custom NDRs for enhanced status codes

To create a custom NDR for an enhanced status code, use this syntax:
  
```
New-SystemMessage -Internal <$true | $false> -Language <Locale> -DSNCode <x.y.z> -Text "<NDR text>"
```

The values are:
  
- **Internal** Controls whether the NDR is sent to internal or external senders. For internal senders, use the value  `$true`. For external senders, use the value  `$false`. For example, in the custom text for internal senders, you can include help desk contact information that you wouldn't want to include in NDRs for external senders.
    
- **Language** For the list of available languages, see the [Supported languages for NDRs](ndr-procedures.md#NDRLanguages) section in this topic. 
    
- **DSNCode** The enhanced status code. Valid values are 4.  _x_. _y_ or 5.  _x_. _y_ where  _x_ and  _y_ are one to three digit numbers. 
    
- **Text** You can use plain text or HTML formatting. For more information, see the [HTML tags and special characters in NDRs](ndr-procedures.md#NDRTags) section in this topic. 
    
This example creates a custom plain text NDR for the enhanced status code 5.1.2 that's sent to external senders in English.
  
```
New-SystemMessage -Internal $false -Language En -DSNCode 5.1.2 -Text "You tried to send a message to a disabled mailbox that's no longer accepting messages. Please contact your System Administrator for more information."
```

 This example creates a custom HTML NDR for the enhanced status code 5.1.2 that's sent to internal senders in English. 
  
```
New-SystemMessage -DSNCode 5.1.2 -Internal $true -Language En -Text 'You tried to send a message to a <B>disabled</B> mailbox. Please visit <A HREF="https://it.contoso.com">Internal Support</A> or contact &amp;quot;InfoSec&amp;quot; for more information.'
```

For detailed syntax and parameter information, see [New-SystemMessage](http://technet.microsoft.com/library/77b06405-076d-43cf-89b1-aa62b6565d8d.aspx).
  
### Use the Exchange Management Shell to create custom NDRs for quotas

To create a custom NDR for quotas, use this syntax:
  
```
New-SystemMessage -Language <Locale> -QuotaMessageType <Quota> -Text "<NDR text>"
```

The values are:
  
- **Language** For the list of available languages, see [Supported languages for NDRs](ndr-procedures.md#NDRLanguages).
    
- **QuotaMessageType** For a list of the available quotas, see [Identity values for NDRs](ndr-procedures.md#NDRIdentity).
    
- **Text** You can use plain text or HTML formatting. For more information, see [HTML tags and special characters in NDRs](ndr-procedures.md#NDRTags).
    
This example creates a custom English plain text NDR for the **ProhibitSendReceive** quota on mailboxes. 
  
```
New-SystemMessage -Language En -QuotaMessageType ProhibitSendReceiveMailBox -Text "Your mailbox is full, and can't send or receive messages. Delete any unwanted large messages (messages with attachments) and empty your Deleted Items folder"
```

For detailed syntax and parameter information, see [New-SystemMessage](http://technet.microsoft.com/library/77b06405-076d-43cf-89b1-aa62b6565d8d.aspx).
  
### How do you know this worked?

To verify that you have successfully created a custom NDR, do these steps:
  
- Run the following command and verify the property values:
    
  ```
  Get-SystemMessge | Format-List Identity,DsnCode,Language,Text
  ```

- Send a test message that will generate the custom NDR that you configured.
    
## Use the Exchange Management Shell to modify custom NDRs
<a name="ViewDefaultNDRs"> </a>

To modify custom NDRs, use this syntax:
  
```
Set-SystemMessage -Identity <NDRIdentity> [-Text "<NDR text>"] [-Original]
```

For an explanation of the available  _\<NDRIdentity\>_ values, see the [Identity values for NDRs](ndr-procedures.md#NDRIdentity) section in this topic. For an explanation of the  _\<NDR text\>_ values, see the [HTML tags and special characters in NDRs](ndr-procedures.md#NDRTags) section in this topic. 
  
This example changes the text in the custom NDR for the enhanced status code 5.1.2 that's sent to internal senders in English.
  
```
Set-SystemMessage -Identity En\Internal\5.1.2 -Text "The mailbox you tried to send an email message to is disabled and is no longer accepting messages. Please contact the Help Desk at extension 123 for assistance."
```

This example changes the text in the custom English NDR for the **ProhibitSendReceive** quota on mailboxes. 
  
```
Set-SystemMessage -Identity En\ProhibitSendReceiveMailBox -Text "Your mailbox is full. Delete large messages and empty your Deleted Items folder."
```

This example disables the specified custom NDR. The custom NDR is preserved, and appears in the results of **Get-SystemMessage**, but the default NDR is used instead. 
  
```
Set-SystemMessage -Identity En\Internal\5.1.2 -Original
```

 **Note**: If there's no corresponding default NDR, you receive an error when you use the  _Original_ switch. 
  
For detailed syntax and parameter information, see [Set-SystemMessage](http://technet.microsoft.com/library/53b76641-d341-42a8-b281-018a91af6a36.aspx).
  
### How do you know this worked?

To verify that you have successfully modified a custom NDR, replace  _\<NDRIdentity\>_ with the appropriate value, and run this command to verify the property values: 
  
```
Get-SystemMessage -Identity <NDRIdentity> | Format-List
```

## Use the Exchange Management Shell to remove custom NDRs
<a name="ViewDefaultNDRs"> </a>

To remove a custom NDR, use this syntax:
  
```
Remove-SystemMessage -Identity <NDRIdentity>
```

For an explanation of the available  _\<NDRIdentity\>_ values, see the [Identity values for NDRs](ndr-procedures.md#NDRIdentity) section in this topic. 
  
This example removes the custom NDR for the enhanced status code 5.1.2 that's sent to internal senders in English.
  
```
Remove-SystemMessage -Identity En\Internal\5.1.2
```

This example removes the custom English NDR for the **ProhibitSendReceive** quota on mailboxes. 
  
```
Remove-SystemMessage -Identity En\ProhibitSendReceiveMailBox
```

For detailed syntax and parameter information, see [Remove-SystemMessage](http://technet.microsoft.com/library/1566222b-407a-4e78-a0df-5190b23d53da.aspx).
  
### How do you know this worked?

To verify that you have successfully removed a custom NDR, run this command to verify the custom NDR isn't listed:
  
```
Get-SystemMessage
```

## Forward copies of NDRs to the Exchange recipient mailbox
<a name="ForwardNDRs"> </a>

You can configure your Exchange organization to send copies of NDRs to the Exchange recipient. However, by default, no mailbox is assigned to the Exchange recipient, so any messages that are sent to the Exchange recipient are discarded. To send copies of NDRs to the Exchange recipient mailbox, you need to:
  
1. Assign a mailbox to the Exchange recipient.
    
2. Specify the enhanced status codes that you want to monitor (not quotas).
    
### Step 1: Use the Exchange Management Shell to assign a mailbox to the Exchange recipient

 **Note**: Due to the high volume of messages, we recommend using a dedicated mailbox for the Exchange recipient. For more information about creating mailboxes, see [Create shared mailboxes in the Exchange admin center](../../collaboration/shared-mailboxes/create-shared-mailboxes.md) and [Create user mailboxes in Exchange 2016](../../recipients/create-user-mailboxes.md).
  
To assign a mailbox to the Exchange recipient, use this syntax:
  
```
Set-OrganizationConfig -MicrosoftExchangeRecipientReplyRecipient <MailboxIdentity>
```

This example assigns the existing mailbox named "Contoso System Mailbox" to the Exchange recipient.
  
```
Set-OrganizationConfig -MicrosoftExchangeRecipientReplyRecipient "Contoso System Mailbox"
```

### Step 2: Specify the ehnanced status codes that you want to monitor

- You can use the EAC or the Exchange Management Shell.
    
- By default, even though there are no enhanced status codes specified, NDRs for these codes are automatically sent to the Exchange recipient:
    
  -  `5.1.4`
    
  -  `5.2.0`
    
  -  `5.2.4`
    
  -  `5.4.4`
    
  -  `5.4.6`
    
  -  `5.4.8`
    
- You can only specify enhanced status codes. You can't specify quotas.
    
#### Use the EAC to specify the enhanced status codes to monitor

For more information about the EAC, see [Exchange admin center in Exchange 2016](../../architecture/cas/eac.md).
  
1. In the EAC, go to **Mail flow** > **Receive connectors**.
    
2. Click **More options** ( ![More Options icon](../../media/ITPro_EAC_MoreOptionsIcon.png)) and select **Organization transport settings**.
    
3. In the **Organization transport settings** window that opens, click the **Delivery** tab. In the **DSN codes** section, do one or more of these steps: 
    
  - To add entries, type the enhanced status code that you want to monitor (4. _\<y.z\>_ or 5.  _\<y.z\>_), and then click **Add** ( ![Add icon](../../media/ITPro_EAC_AddIcon.png)). Repeat this step as many times as you need to.
    
  - To modify an existing entry, select it click **Edit** ( ![Edit icon](../../media/ITPro_EAC_EditIcon.png)), and then modify it inline.
    
  - To remove an existing entry, select it and then click **Remove** ( ![Remove icon](../../media/ITPro_EAC_RemoveIcon.png)).
    
    When you're finished, click **Save**.
    
#### Use the Exchange Management Shell to specify the enhanced status codes to monitor

To add enhanced status codes to monitor, which replaces any existing values, use this syntax:
  
```
Set-TransportConfig -GenerateCopyOfDSNFor <x.y.z>,<x.y.z>...
```

This example configures the Exchange organization to forward all NDRs for the enhanced status code values 5.7.1, 5.7.2, and 5.7.3 to the Exchange recipient.
  
```
Set-TransportConfig -GenerateCopyOfDSNFor 5.7.1,5.7.2,5.7.3
```

To add or remove entries without modifying any existing values, use this syntax:
  
```
Set-TransportConfig -GenerateCopyOfDSNFor @{Add="<x.y.z>","<x.y.z>"...; Remove="<x.y.z>","<x.y.z>"...}
```

This example adds the enhanced status code 5.7.5 and removes 5.7.1 from the existing list of NDRs that are forwarded to the Exchange recipient.
  
```
Set-TransportConfig -GenerateCopyOfDSNFor @{Add="5.7.5"; Remove="5.7.1"}
```

### How do you know this worked?

To verify that you've successfully configured copies of NDRs to be sent to the Exchange recipient mailbox, 
  
- Run the following command and verify the property values:
    
  ```
  Get-TransportConfig | Format-List GenerateCopyOfDSNFor
  ```

- Monitor the Exchange recipient mailbox to see if NDRs that contain the specified enhanced status codes are delivered there.
    
## Identity values for NDRs
<a name="NDRIdentity"> </a>

The identity of an NDR uses one of these formats:
  
- **NDRs for enhanced status codes** _\<Language\>_&lt;Internal | External>\ _\<DSNcode\>_. For example,  `En\Internal\5.1.2` or  `Ja\External\5.1.2`.
    
  - ** _\<DSNcode\>_** Valid values are 4.  _x_. _y_ or 5.  _x_. _y_ where  _x_ and  _y_ are one to three digit numbers. To generate a list of the enhanced status codes that are used by Exchange, see the [Use the Exchange Management Shell to view all default NDRs](ndr-procedures.md#ViewDefaultNDRs) section earlier in this topic. 
    
  - **Internal or External** You can use different text in NDRs for internal or external senders. 
    
  - ** _\<Language\>_** For the list of supported languages, see the [Supported languages for NDRs](ndr-procedures.md#NDRLanguages) section in this topic. 
    
- **NDRs for quotas** _\<Language\>_\ _\<QuotaMessageType\>_. For example,  `En\ProhibitSendReceiveMailBox`.
    
  - ** _\<Language\>_** For the list of supported languages, see the [Supported languages for NDRs](ndr-procedures.md#NDRLanguages) section in this topic. 
    
  - ** _QuotaMessageType\>_** Valid values are: 
    
    Mailbox size quotas:
    
    **ProhibitSendReceiveMailBox**: A mailbox exceeds its  `ProhibitSendReceiveQuota` limit. 
    
    **ProhibitSendMailbox**: A mailbox exceeds its  `ProhibitSendQuota` limit. 
    
    **WarningMailbox**: A mailbox exceeds its  `IssueWarningQuota` limit when it has a  `ProhibitSendQuota` or  `ProhibitSendReceiveQuota` limit configured. 
    
    **WarningMailboxUnlimitedSize**: A mailbox exceeds its  `IssueWarningQuota` limit when it doesn't have a  `ProhibitSendQuota` or  `ProhibitSendReceiveQuota` limit configured. 
    
    Public folder size quotas:
    
    **ProhibitPostPublicFolder**: A public folder exceeds its  `ProhibitPostQuota` limit. 
    
    **WarningPublicFolder**: A public folder exceeds its  `IssueWarningQuota` limit when it has a  `ProhibitPostQuota` limit configured. 
    
    **WarningPublicFolderUnlimitedSize**: A public folder exceeds its  `IssueWarningQuota` limit when it doesn't have a  `ProhibitPostQuota` limit configured. 
    
    Maximum number of messages in a mailbox folder:
    
    **ProhibitReceiveMailboxMessagesPerFolderCount**: A mailbox exceeds its  `MailboxMessagesPerFolderCountReceiveQuota` limit. 
    
    **WarningMailboxMessagesPerFolderCount**: A mailbox exceeds its  `MailboxMessagesPerFolderCountWarningQuota` limit when it has a  `MailboxMessagesPerFolderCountReceiveQuota` limit configured. 
    
    **WarningMailboxMessagesPerFolderUnlimitedCount**: A mailbox exceeds its  `MailboxMessagesPerFolderCountWarningQuota` limit when it doesn't have a  `MailboxMessagesPerFolderCountReceiveQuota` limit configured. 
    
    Maximum number of subfolders in a mailbox folder:
    
    **ProhibitReceiveFolderHierarchyChildrenCountCount**: A mailbox exceeds its  `FolderHierarchyChildrenCountReceiveQuota` limit. 
    
    **WarningFolderHierarchyChildrenCount**: A mailbox exceeds its  `FolderHierarchyChildrenCountWarningQuota` limit when it has a  `FolderHierarchyChildrenCountReceiveQuota` limit configured. 
    
    **WarningFolderHierarchyChildrenUnlimitedCount**: A mailbox exceeds its  `FolderHierarchyChildrenCountWarningQuota` limit when it doesn't have a  `FolderHierarchyChildrenCountReceiveQuota` limit configured. 
    
    **ProhibitReceiveFoldersCount**: A mailbox exceeds its  `FoldersCountReceiveQuota` limit. 
    
    **WarningFoldersCount**: A mailbox exceeds its  `FoldersCountWarningQuota` limit when it has a  `FoldersCountReceiveQuota` limit configured. 
    
    **WarningFoldersCountUnlimited** A mailbox exceeds its  `FoldersCountWarningQuota` limit when it doesn't have a  `FoldersCountReceiveQuota` limit configured. 
    
    Maximum number of levels (depth) in a mailbox folder:
    
    **ProhibitReceiveFolderHierarchyDepth**: A mailbox exceeds its  `FolderHierarchyDepthWarningQuota` limit. 
    
    **WarningFolderHierarchyDepth**: A mailbox exceeds its  `FolderHierarchyDepthWarningQuota` limit when it has a  `FolderHierarchyDepthReceiveQuota` limit configured. 
    
    **WarningFolderHierarchyDepthUnlimited:**: A mailbox exceeds its  `FolderHierarchyDepthWarningQuota` limit when it doesn't have a  `FolderHierarchyDepthReceiveQuota` limit configured. 
    
## Supported languages for NDRs
<a name="NDRLanguages"> </a>

This table lists the supported language that codes you can use in custom NDRs.
  
|**Language code**|**Language**|
|:-----|:-----|
|af  <br/> |Afrikaans  <br/> |
|am-ET  <br/> |Amharic (Ethiopia)  <br/> |
|ar  <br/> |Arabic  <br/> |
|as-IN  <br/> |Assamese (India)  <br/> |
|bg  <br/> |Bulgarian  <br/> |
|bn-BD  <br/> |Bengali (Bangladesh)  <br/> |
|bn-IN  <br/> |Bengali (India)  <br/> |
|bs-Cyrl-BA  <br/> |Bosnian (Cyrillic, Bosnia and Herzegovina)  <br/> |
|bs-Latn-BA  <br/> |Bosnian (Latin, Bosnia and Herzegovina)  <br/> |
|ca  <br/> |Catalan  <br/> |
|cs  <br/> |Czech  <br/> |
|cy-GB  <br/> |Welsh (Great Britain)  <br/> |
|da  <br/> |Danish  <br/> |
|de  <br/> |German  <br/> |
|el  <br/> |Greek  <br/> |
|en  <br/> |English  <br/> |
|es  <br/> |Spanish  <br/> |
|et  <br/> |Estonian  <br/> |
|eu  <br/> |Basque  <br/> |
|fa  <br/> |Persian  <br/> |
|fi  <br/> |Finnish  <br/> |
|fil-PH  <br/> |Filipino (Philippines)  <br/> |
|fr  <br/> |French  <br/> |
|ga-IE  <br/> |Irish (Ireland)  <br/> |
|gl  <br/> |Galician  <br/> |
|gu  <br/> |Gujarati  <br/> |
|ha-Latn-NG  <br/> |Hausa (Latin, Nigeria)  <br/> |
|he  <br/> |Hebrew  <br/> |
|hi  <br/> |Hindi  <br/> |
|hr  <br/> |Croatian  <br/> |
|hu  <br/> |Hungarian  <br/> |
|hy  <br/> |Armenian  <br/> |
|id  <br/> |Indonesian  <br/> |
|ig-NG  <br/> |Igbo (Nigeria)  <br/> |
|is  <br/> |Icelandic  <br/> |
|it  <br/> |Italian  <br/> |
|iu-Latn-CA  <br/> |Inuktitut (Latin, Canada)  <br/> |
|ja  <br/> |Japanese  <br/> |
|ka  <br/> |Georgian  <br/> |
|kk  <br/> |Kazakh  <br/> |
|km-KH  <br/> |Khmer (Cambodia)  <br/> |
|kn  <br/> |Kannada  <br/> |
|ko  <br/> |Korean  <br/> |
|kok  <br/> |Konkani  <br/> |
|ky  <br/> |Kyrgyz  <br/> |
|lb-LU  <br/> |Luxembourgish (Luxembourg)  <br/> |
|lo-LA  <br/> |Lao (Lao People's Democratic Republic)  <br/> |
|lt  <br/> |Lithuanian  <br/> |
|lv  <br/> |Latvian  <br/> |
|mi-NZ  <br/> |Maori (New Zealand)  <br/> |
|mk  <br/> |Macedonian  <br/> |
|ml-IN  <br/> |Malayalam (India)  <br/> |
|mr  <br/> |Marathi  <br/> |
|ms  <br/> |Malay  <br/> |
|ms-BN  <br/> |Malay (Brunei Darussalam)  <br/> |
|mt-MT  <br/> |Maltese (Malta)  <br/> |
|ne-NP  <br/> |Nepali (Nepal)  <br/> |
|nl  <br/> |Dutch  <br/> |
|nn-NO  <br/> |Norwegian (Nynorsk)  <br/> |
|no  <br/> |Norwegian  <br/> |
|nso-ZA  <br/> |Sesotho sa Leboa (South Africa)  <br/> |
|or-IN  <br/> |Oriya (India)  <br/> |
|pa  <br/> |Punjabi  <br/> |
|pl  <br/> |Polish  <br/> |
|ps-AF  <br/> |Pashto (Afghanistan)  <br/> |
|pt  <br/> |Portuguese  <br/> |
|pt-PT  <br/> |Portuguese (Portugal)  <br/> |
|qut-GT  <br/> |K'iche (Guatemala)  <br/> |
|quz-PE  <br/> |Quechua (Peru)  <br/> |
|ro  <br/> |Romanian  <br/> |
|ru  <br/> |Russian  <br/> |
|rw-RW  <br/> |Kinyarwanda (Rwanda)  <br/> |
|si-LK  <br/> |Sinhala (Sri Lanka)  <br/> |
|sk  <br/> |Slovak  <br/> |
|sl  <br/> |Slovenian  <br/> |
|sq  <br/> |Albanian  <br/> |
|sr  <br/> |Serbian  <br/> |
|sr-Cyrl-CS  <br/> |Serbian (Cyrillic, Serbia)  <br/> |
|sv  <br/> |Swedish  <br/> |
|sw  <br/> |Kiswahili  <br/> |
|ta  <br/> |Tamil  <br/> |
|te  <br/> |Telugu  <br/> |
|th  <br/> |Thai  <br/> |
|tn-ZA  <br/> |Setswana (South Africa)  <br/> |
|tr  <br/> |Turkish  <br/> |
|tt  <br/> |Tatar  <br/> |
|uk  <br/> |Ukrainian  <br/> |
|ur  <br/> |Urdu  <br/> |
|uz  <br/> |Uzbek  <br/> |
|vi  <br/> |Vietnamese  <br/> |
|wo-SN  <br/> |Wolof (Senegal)  <br/> |
|xh-ZA  <br/> |isiXhosa (South Africa)  <br/> |
|yo-NG  <br/> |Yoruba (Nigeria)  <br/> |
|zh-Hans  <br/> |Chinese (Simplified)  <br/> |
|zh-Hant  <br/> |Chinese (Traditional)  <br/> |
|zh-HK  <br/> |Chinese (Hong Kong)  <br/> |
|zu-ZA  <br/> |isiZulu (South Africa)  <br/> |
   
To control the languages that are used in NDRs, you use these parameters on the **Set-TransportConfig** cmdlet: 
  
-  _ExternalDsnDefaultLanguage_ Specifies the default language to use on external NDRs. The default value is blank (  `$null`), which means the default Windows server language is used.
    
-  _InternalDsnDefaultLanguage_ Specifies the default language to use on internal NDRs. The default value is blank (  `$null`), which means the default Windows server language is used.
    
-  _ExternalDsnLanguageDetectionEnabled_
    
  -  `$true` Exchange tries to send an external NDR in the same language as the original message. This is the default value. 
    
  -  `$false` Language detection is disabled for external NDRs, The NDR language is determined by the  _ExternalDsnDefaultLanguage_ parameter. 
    
-  _InternalDsnLanguageDetectionEnabled_
    
  -  `$true` Exchange tries to send an internal NDR in the same language as the original message. This is the default value. 
    
  -  `$false` Language detection is disabled for internal NDRs, The NDR language is determined by the  _InternalDsnDefaultLanguage_ parameter. 
    
## HTML tags and special characters in NDRs
<a name="NDRTags"> </a>

The custom text that you include in an NDR can contain a maximum of 512 characters, which includes text and HTML tags. For example, you can include a detailed description of the problem, contact information for your help desk, and a link to your support department's web site.
  
To control whether Exchange uses HTML or plain text in NDRs, you use these parameters on the **Set-TransportConfig** cmdlet: 
  
-  _ExternalDsnSendHtml_
    
  -  `$true` Use HTML tags in NDRs for external senders. This is the default value. 
    
  -  `$false` Use plain text in NDRs for external senders. 
    
-  _InternalDsnSendHtml_
    
  -  `$true` Use HTML tags in NDRs for internal senders. This is the default value 
    
  -  `$false` Use plain text in NDRs for internal senders. 
    
This table describes the HTML tags that you can use in the NDR text.
  
****

|**Description**|**HTML tags**|
|:-----|:-----|
|Bold  <br/> | `<B>` and  `</B>` <br/> |
|Italic  <br/> | `<EM>` and  `</EM>` <br/> |
|Line break  <br/> | `<BR>` <br/> |
|Paragraph  <br/> | `<P>` and  `</P>` <br/> |
|Hyperlink  <br/> | `<A HREF="url">` and  `</A>` <br/> **Note**: Because this tag contains double quotation marks, you need to use single quotation marks (not double quotation marks) around the complete text string if you use this tag in your custom text. Otherwise, you'll receive an error.  <br/> |
   
Certain characters in an NDR require escape codes to identify them literally, and not by their function in the NDR. These characters are described in the following table:
  
****

|**Character**|**Escape code**|
|:-----|:-----|
|\<  <br/> | `&amp;lt;` <br/> |
|\>  <br/> | `&amp;gt;` <br/> |
|"  <br/> | `&amp;quot;` <br/> |
|&amp;  <br/> | `&amp;amp;` <br/> |
   
For example, if you want the NDR to display the text  `Please contact the Help Desk at <1234>.`, you need to the value  `"Please contact the Help Desk at &amp;lt;1234&amp;gt;."`
  
This is an example of a custom NDR text value that uses HTML tags and escape codes.
  
```
'You tried to send a message to a <B>disabled</B> mailbox. Please visit <A HREF="https://it.contoso.com">Internal Support</A> or contact &amp;quot;InfoSec&amp;quot; for more information.'
```


