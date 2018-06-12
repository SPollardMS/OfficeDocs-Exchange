---
title: "Organization-wide disclaimers, signatures, footers, or headers in Exchange 2016"
ms.author: chrisda
author: chrisda
manager: serdars
ms.date: 6/8/2018
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: e45e33c9-e53b-427c-ada5-70901bc399b8
description: "Summary: Learn about using mail flow rules (transport rules) to add disclaimers to email messages in Exchange 2016."
---

# Organization-wide disclaimers, signatures, footers, or headers in Exchange 2016

 **Summary**: Learn about using mail flow rules (transport rules) to add disclaimers to email messages in Exchange 2016.
  
You can add an email disclaimer, legal disclaimer, disclosure statement, signature, or other information to the top or bottom of email messages that enter or leave your organization. You might be required to do this for legal, business, or regulatory requirements, to identify potentially unsafe email messages, or for other reasons that are unique to your organization.
  
To create a disclaimer, you create a mail flow rule (also known as transport rule) with an action that adds the specified text to email messages. You can configure the rule to apply the disclaimer to all messages (no conditions), or you can define conditions that determine when the disclaimer is added (for example, when the sender is a member of a specific group, when the message includes specific words or text patterns, or outgoing messages only). You can also define exceptions that prevent the disclaimer from being added to messages (for example, messages from specific senders, messages sent to specific recipients, or messages that already contain the disclaimer). To apply multiple disclaimers to the same message, you need to use multiple rules. For more information about mail flow rules, see [Mail flow rules in Exchange 2016](mail-flow-rules.md).
  
Looking for procedures? See [Configure a Disclaimer or Other Email Header or Footer](http://technet.microsoft.com/library/29ac61c2-77f1-4071-b14e-8cc64e3e76ba.aspx).
  
## Examples
<a name="Examples"> </a>

 **Note**: The examples in this topic are not intended for use as-is. Modify them for your needs.
  
|**Type**|**Sample text added**|
|:-----|:-----|
|Legal - outgoing messages  <br/> |This email and any files transmitted with it are confidential and intended solely for the use of the individual or entity to whom they are addressed. If you have received this email in error, please notify the system manager.  <br/> |
|Legal - incoming messages  <br/> |Employees are expressly required not to make defamatory statements and not to infringe or authorize any infringement of copyright or any other legal right by email communications. Employees who receive such an email must notify their supervisor immediately.  <br/> |
|Notice that message was sent to an alias  <br/> |This message was sent to the Sales discussion group.  <br/> |
|Signature - uses unique data for each employee  <br/> |Kathleen Mayer  <br/> Sales Department  <br/> Contoso  <br/> www.contoso.com  <br/> kathleen@contoso.com  <br/> cell: 111-222-1234  <br/> |
|Advertisement  <br/> |Click here for March specials  <br/> |
   
## Location for your disclaimer
<a name="Examples"> </a>

You can choose whether to insert the disclaimer at the beginning of the message (prepend), or at the end of the message (append).
  
In the EAC, you select the action **Append the disclaimer** or **Apply a disclaimer to the message** \> **prepend a disclaimer**.
  
In the Exchange Management Shell, you use the  _ApplyHtmlDisclaimerTextLocation_ parameter with the value  `Append` (default) or  `Prepend`.
  
## Format your disclaimer
<a name="FormatDisclaimer"> </a>

Here's the formatting that you can use in your disclaimer text.
  
|**Type of information**|**Description**|
|:-----|:-----|
|Plain text  <br/> |The maximum length is 5,000 characters, including any HTML tags and inline Cascading Style Sheets (CSS).  <br/> |
|HTML and inline CSS  <br/> |You can use HTML and inline CSS styles to format the text. For example, use the  `<HR>` tag to add a line before the disclaimer.  <br/> HTML is ignored if the disclaimer is added to a plain text message.  <br/> |
|Images  <br/> |Use the  `<IMG>` tag to point to an image available on the Internet. For example,  `<IMG src="http://contoso.com/images/companylogo.gif" alt="Contoso logo">`.  <br/> By default, Outlook and Outlook on the web (formerly known as Outlook Web App) block external web content, including images. Users need to acknowledge and download the blocked external content. We recommend that you test disclaimers that have  `IMG` tags to verify they display the way you want.  <br/> |
|User information for personalized signatures  <br/> |You can use tokens to add unique attributes from each user's Active Directory account, such as  `DisplayName`,  `FirstName`,  `LastName`,  `PhoneNumber`,  `Email`,  `FaxNumber`, and  `Department`. The syntax is to enclose the attribute name in two percent signs (for example,  `%%DisplayName%%`).  <br/> For a complete list of attributes that can be used in disclaimers and personalized signatures, see the description for the  `ADAttribute` property in [Mail flow rule conditions and exceptions (predicates) in Exchange 2016](conditions-and-exceptions.md).  <br/> |
   
Here's an example of an HTML disclaimer that includes a signature, an  `IMG` tag, and embedded CSS. 
  
```
<div style="font-size:9pt;  font-family: 'Calibri',sans-serif;">
%%displayname%%</br>
%%title%%</br>
%%company%%</br>
%%street%%</br>
%%city%%, %%state%% %%zipcode%%</div>
&amp;nbsp;</br>
<div style="background-color:#D5EAFF; border:1px dotted #003333; padding:.8em; ">
<div><img alt="Fabrikam"  src="http://fabrikam.com/images/fabrikamlogo.png"></div>
<span style="font-size:12pt;  font-family: 'Cambria','times new roman','garamond',serif; color:#ff0000;">HTML Disclaimer Title</span></br>
<p style="font-size:8pt; line-height:10pt; font-family: 'Cambria','times roman',serif;">This message contains confidential information and is intended only for the individual(s) addressed in the message. If you are not the named addressee, you should not disseminate, distribute, or copy this e-mail. If you are not the intended recipient, you are notified that disclosing, distributing, or copying this e-mail is strictly prohibited.  </p>
<span style="padding-top:10px; font-weight:bold; color:#CC0000; font-size:10pt; font-family: 'Calibri',Arial,sans-serif; "><a href="http://www.fabrikam.com">Fabrikam, Inc. </a></span></br></br>
</div>
```

## Fallback options for disclaimer rules
<a name="FallbackOptions"> </a>

Exchange can't modify the content of some messages (for example, encrypted messages). For rules that add disclaimers to messages, you need to specify what to do if the disclaimer can't be added. This is known as the  *fallback option*  for the disclaimer rule. The available fallback options are: 
  
- **Wrap**: The original message is wrapped in a new message envelope, and the disclaimer text is inserted into the new message. This is the default value.
    
  - Subsequent mail flow rules are applied to the new message envelope, not to the original message. Therefore, configure these rules with a lower priority than other rules.
    
  - If the original message can't be wrapped in a new message envelope, the original message isn't delivered. The message is returned to the sender in an non-delivery report (also known as an NDR or bounce message).
    
- **Ignore**: The rule is ignored and the message is delivered without the disclaimer
    
- **Reject**: The message is returned to the sender in an NDR.
    
In the EAC, you select the fallback option in the rule action. In the Exchange Management Shell, you use the  _ApplyHtmlDisclaimerFallbackAction_ parameter. 
  
## Scope your disclaimer
<a name="Scoping"> </a>

As you work on your disclaimers, consider which messages they should apply to. For example, you might want different disclaimers for internal and external messages, or for messages sent by users in specific departments. To make sure only the first message in a conversation gets a disclaimer, add an exception that prevents the disclaimer text from being applied to the same messages over and over again.
  
Here are some examples of the conditions and exceptions you can use.
  
|**Description**|**Conditions and exceptions in EAC**|**Conditions and exceptions in the Exchange Management Shell for the New-TransportRule or Set-TransportRule cmdlets**|
|:-----|:-----|:-----|
|The recipient is located outside your Exchange organization. An exception is configured so messages that already contain the disclaimer text "CONTOSO LEGAL NOTICE" don't have the disclaimer applied again.  <br/> |Condition: **The recipient is located** \> **Outside the organization** <br/> Exception: **The subject or body** \> **Subject or body matches these text patterns** \> CONTOSO LEGAL NOTICE <br/> | `-FromScope NotInOrganization -ExceptIf -SubjectOrBodyMatches "CONTOSO LEGAL NOTICE"` <br/> |
|Incoming messages with executable attachments  <br/> |Condition 1: **The sender is located** \> **Outside the organization** <br/> Condition 2: **Any attachment** \> **has executable content** <br/> | `-FromScope NotInOrganization -AttachmentHasExecutableContent` <br/> |
|Sender is in the marketing department  <br/> |Condition: **The sender** \> **is a member of this group** \>  _group name_ <br/> | `-FromMemberOf "Marketing Team"` <br/> |
|Every message that comes from an external sender to the sales discussion group  <br/> |Condition 1: **The sender is located** \> **Outside the organization** <br/> Condition 2: **The message** \> **To or Cc box contains this person** \>  _group name_ <br/> | `-FromScope NotInOrganization -SentTo "Sales Discussion Group"` <br/> |
|Prepend an advertisement to outgoing messages for one month  <br/> |Condition 1: **The recipient is located** \> **Outside the organization** <br/> Enter the dates in the **Activate this rule on the following date** and **Deactivate this rule on the following date** fields.  <br/> | `-ApplyHtmlDisclaimerLocation Prepend -SentToScope NotInOrganization -ActivationDate '03/1/2016' -ExpiryDate '03/31/2016'` <br/> |
   
For a complete list of conditions and exceptions that you can use to target the disclaimer, see [Mail flow rule conditions and exceptions (predicates) in Exchange 2016](conditions-and-exceptions.md).
  
## For more information
<a name="MoreInfo"> </a>

[Configure a Disclaimer or Other Email Header or Footer](http://technet.microsoft.com/library/29ac61c2-77f1-4071-b14e-8cc64e3e76ba.aspx)
  
[Mail flow rules in Exchange 2016](mail-flow-rules.md) (Exchange 2016) 
  
[Transport Rules](http://technet.microsoft.com/library/743bd525-0ca2-426d-b76c-b4a052bc8886.aspx) (Exchange Online) 
  
[Transport Rules](http://technet.microsoft.com/library/9c2cf227-eff7-48ef-87fb-487186e47363.aspx) (Exchange Online Protection) 
  

