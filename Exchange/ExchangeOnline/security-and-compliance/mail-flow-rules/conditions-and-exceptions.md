---
title: "Mail flow rule conditions and exceptions (predicates) in Exchange Online"
ms.author: stephow
author: stephow
manager: scotv
ms.date: 6/23/2018
ms.audience: ITPro
ms.topic: article
ms.service: exchange-online
localization_priority: Normal
ms.assetid: 7235e5ed-f7f4-41b1-b1a0-47bb96223a2f

---

# Mail flow rule conditions and exceptions (predicates) in Exchange Online
Conditions and exceptions in mail flow rules (also known as transport rules) identify the messages that the rule is applied to or not applied to. For example, if the rule adds a disclaimer to messages, you can configure the rule to only apply to messages that contain specific words, messages sent by specific users, or to all messages except those sent by the members of a specific group. Collectively, the conditions and exceptions in mail flow rules are also known as predicates, because for every condition, there's a corresponding exception that uses the exact same settings and syntax. The only difference is conditions specify messages to include, while exceptions specify messages to exclude.
  
Most conditions and exceptions have one property that requires one or more values. For example, the **The sender is** condition requires the sender of the message. Some conditions have two properties. For example, the **A message header includes any of these words** condition requires one property to specify the message header field, and a second property to specify the text to look for in the header field. Some conditions or exceptions don't have any properties. For example, the **Any attachment has executable content** condition simply looks for attachments in messages that have executable content. 
  
For more information about mail flow rules in Exchange Online, see [Mail flow rules (transport rules) in Exchange Online](mail-flow-rules.md).
  
For more information about conditions and exceptions in mail flow rules in Exchange Online Protection or Exchange 2013, see [Mail flow rule conditions and exceptions (predicates) in Exchange Online Protection](http://technet.microsoft.com/library/04edeaba-afd4-4207-b2cb-51bcc44e483c.aspx) or [Mail flow rule conditions and exceptions (predicates) in Exchange 2013](http://technet.microsoft.com/library/c918ea00-1e68-4b8b-8d51-6966b4432e2d.aspx).
  
## Conditions and exceptions for mail flow rules in Exchange Online
<a name="MBConditions"> </a>

The tables in the following sections describe the conditions and exceptions that are available in mail flow rules in Exchange Online. The property types are described in the **Property types** section. 
  
[Senders](conditions-and-exceptions.md#Senders)
  
[Recipients](conditions-and-exceptions.md#Recipients)
  
[Message subject or body](conditions-and-exceptions.md#MessageSubjectOrBody)
  
[Attachments](conditions-and-exceptions.md#Attachments)
  
[Any recipients](conditions-and-exceptions.md#AnyRecipients)
  
[Message sensitive information types, To and Cc values, size, and character sets](conditions-and-exceptions.md#Message)
  
[Sender and recipient](conditions-and-exceptions.md#SenderAndRecipient)
  
[Message properties](conditions-and-exceptions.md#MessageProperties)
  
[Message headers](conditions-and-exceptions.md#MessageHeaders)
  
 **Notes**:
  
- After you select a condition or exception in the Exchange admin center (EAC), the value that's ultimately shown in the **Apply this rule if** or **Except if** field is often different (shorter) than the click path value you selected. Also, when you create new rules based on a template (a filtered list of scenarios), you can often select a short condition name instead of following the complete click path. The short names and full click path values are shown in the EAC column in the tables. 
    
- If you select **[Apply to all messages]** in the EAC, you can't specify any other conditions. The equivalent in Exchange Online PowerShell is to create a rule without specifying any condition parameters. 
    
- The settings and properties are the same in conditions and exceptions, so the output of the **Get-TransportRulePredicate** cmdlet doesn't list exceptions separately. Also, the names of some of the predicates that are returned by this cmdlet are different than the corresponding parameter names, and a predicate might require multiple parameters. 
    
### Senders
<a name="Senders"> </a>

For conditions and exceptions that examine the sender's address, you can specify where rule looks for the sender's address.
  
In the EAC, in the **Properties of this rule** section, click **Match sender address in message**. Note that you might need to click **More options** to see this setting. In Exchange Online PowerShell, the parameter is  _SenderAddressLocation_. The available values are:
  
- **Header** Only examine senders in the message headers (for example, the **From**, **Sender**, or **Reply-To** fields). This is the default value. 
    
- **Envelope** Only examine senders from the message envelope (the **MAIL FROM** value that was used in the SMTP transmission, which is typically stored in the **Return-Path** field). Note that message envelope searching is only available for the following conditions (and the corresponding exceptions): 
    
  - **The sender is** (  _From_)
    
  - **The sender is a member of** (  _FromMemberOf_)
    
  - **The sender address includes** (  _FromAddressContainsWords_)
    
  - **The sender address matches** (  _FromAddressMatchesPatterns_)
    
  - **The sender's domain is** (  _SenderDomainIs_)
    
- **Header or envelope** (  `HeaderOrEnvelope`) Examine senders in the message header and the message envelope.
    
|**Condition or exception in the EAC**|**Condition and exception parameters in Exchange Online PowerShell**|**Property type**|**Description**|
|:-----|:-----|:-----|:-----|
|**The sender is** <br/> **The sender** \> **is this person** <br/> | _From_ <br/>  _ExceptIfFrom_ <br/> | `Addresses` <br/> |Messages that are sent by the specified mailboxes, mail users, or mail contacts in the organization.  <br/> |
|**The sender is located** <br/> **The sender** \> **is external/internal** <br/> | _FromScope_ <br/>  _ExceptIfFromScope_ <br/> | `UserScopeFrom` <br/> |Messages that are sent by either internal senders or external senders.  <br/> |
|**The sender is a member of** <br/> **The sender** \> **is a member of this group** <br/> | _FromMemberOf_ <br/>  _ExceptIfFromMemberOf_ <br/> | `Addresses` <br/> |Messages that are sent by a member of the specified group.  <br/> |
|**The sender address includes** <br/> **The sender** \> **address includes any of these words** <br/> | _FromAddressContainsWords_ <br/>  _ExceptIfFromAddressContainsWords_ <br/> | `Words` <br/> |Messages that contain the specified words in the sender's email address.  <br/> |
|**The sender address matches** <br/> **The sender** \> **address matches any of these text patterns** <br/> | _FromAddressMatchesPatterns_ <br/>  _ExceptIfFromAddressMatchesPatterns_ <br/> | `Patterns` <br/> |Messages where the sender's email address contains text patterns that match the specified regular expressions.  <br/> |
|**The sender is on a recipient's list** <br/> **The sender** \> **is on a recipient's supervision list** <br/> | _SenderInRecipientList_ <br/>  _ExceptIfSenderInRecipientList_ <br/> | `SupervisionList` <br/> |Messages where the sender is on the recipient's Allow list or Block list.  <br/> |
|**The sender's specified properties include any of these words** <br/> **The sender** \> **has specific properties including any of these words** <br/> | _SenderADAttributeContainsWords_ <br/>  _ExceptIfSenderADAttributeContainsWords_ <br/> |First property:  `ADAttribute` <br/> Second property:  `Words` <br/> |Messages where the specified Active Directory attribute of the sender contains any of the specified words.  <br/> Note that the **Country** attribute requires the two-letter country code value (for example, DE for Germany).  <br/> |
|**The sender's specified properties match these text patterns** <br/> **The sender** \> **has specific properties matching these text patterns** <br/> | _SenderADAttributeMatchesPatterns_ <br/>  _ExceptIfSenderADAttributeMatchesPatterns_ <br/> |First property:  `ADAttribute` <br/> Second property:  `Patterns` <br/> |Messages where the specified Active Directory attribute of the sender contains text patterns that match the specified regular expressions.  <br/> |
|**The sender has overridden the Policy Tip** <br/> **The sender** \> **has overridden the Policy Tip** <br/> | _HasSenderOverride_ <br/>  _ExceptIfHasSenderOverride_ <br/> |n/a  <br/> |Messages where the sender has chosen to override a data loss prevention (DLP) policy. For more information about DLP policies, see [Data loss prevention](../../security-and-compliance/data-loss-prevention/data-loss-prevention.md).  <br/> |
|**Sender's IP address is in the range** <br/> **The sender** \> **IP address is in any of these ranges or exactly matches** <br/> | _SenderIPRanges_ <br/>  _ExceptIfSenderIPRanges_ <br/> | `IPAddressRanges` <br/> |Messages where the sender's IP address matches the specified IP address, or falls within the specified IP address range.  <br/> |
|**The sender's domain is** <br/> **The sender** \> **domain is** <br/> | _SenderDomainIs_ <br/>  _ExceptIfSenderDomainIs_ <br/> | `DomainName` <br/> |Messages where the domain of the sender's email address matches the specified value.  <br/> If you need to find sender domains that  *contain*  the specified domain (for example, any subdomain of a domain), use **The sender address matches** (  _FromAddressMatchesPatterns_) condition and specify the domain by using the syntax:  `'@domain\.com$'`.  <br/> |
   
[Return to top](conditions-and-exceptions.md#RTT)
  
### Recipients
<a name="Recipients"> </a>

|**Condition or exception in the EAC**|**Condition and exception parameters in Exchange Online PowerShell**|**Property type**|**Description**|
|:-----|:-----|:-----|:-----|
|**The recipient is** <br/> **The recipient** \> **is this person** <br/> | _SentTo_ <br/>  _ExceptIfSentTo_ <br/> | `Addresses` <br/> |Messages where one of the recipients is the specified mailbox, mail user, or mail contact in the organization. The recipients can be in the **To**, **Cc**, or **Bcc** fields of the message.  <br/> **Note**: You can't specify distribution groups or mail-enabled security groups. If you need to take action on messages that are sent to a group, use the **To box contains** (  _AnyOfToHeader_) condition instead.  <br/> |
|**The recipient is located** <br/> **The recipient** \> **is external/external** <br/> | _SentToScope_ <br/>  _ExceptIfSentToScope_ <br/> | `UserScopeTo` <br/> |Messages that are sent to internal or external recipients.  <br/> |
|**The recipient is a member of** <br/> **The recipient** \> **is a member of this group** <br/> | _SentToMemberOf_ <br/>  _ExceptIfSentToMemberOf_ <br/> | `Addresses` <br/> |Messages that contain recipients who are members of the specified group. The group can be in the **To**, **Cc**, or **Bcc** fields of the message.  <br/> |
|**The recipient address includes** <br/> **The recipient** \> **address includes any of these words** <br/> | _RecipientAddressContainsWords_ <br/>  _ExceptIfRecipientAddressContainsWords_ <br/> | `Words` <br/> |Messages that contain the specified words in the recipient's email address.  <br/> **Note**: This condition doesn't consider messages that are sent to recipient proxy addresses. It only matches messages that are sent to the recipient's primary email address.  <br/> |
|**The recipient address matches** <br/> **The recipient** \> **address matches any of these text patterns** <br/> | _RecipientAddressMatchesPatterns_ <br/>  _ExceptIfRecipientAddressMatchesPatterns_ <br/> | `Patterns` <br/> |Messages where a recipient's email address contains text patterns that match the specified regular expressions.  <br/> **Note**: This condition doesn't consider messages that are sent to recipient proxy addresses. It only matches messages that are sent to the recipient's primary email address.  <br/> |
|**The recipient is on the sender's list** <br/> **The recipient** \> **is on the sender's supervision list** <br/> | _RecipientInSenderList_ <br/>  _ExceptIfRecipientInSenderList_ <br/> | `SupervisionList` <br/> |Messages where the recipient is on the sender's Allow list or Block list.  <br/> |
|**The recipient's specified properties include any of these words** <br/> **The recipient** \> **has specific properties including any of these words** <br/> | _RecipientADAttributeContainsWords_ <br/>  _ExceptIfRecipientADAttributeContainsWords_ <br/> |First property:  `ADAttribute` <br/> Second property:  `Words` <br/> |Messages where the specified Active Directory attribute of a recipient contains any of the specified words.  <br/> Note that the **Country** attribute requires the two-letter country code value (for example, DE for Germany).  <br/> |
|**The recipient's specified properties match these text patterns** <br/> **The recipient** \> **has specific properties matching these text patterns** <br/> | _RecipientADAttributeMatchesPatterns_ <br/>  _ExceptIfRecipientADAttributeMatchesPatterns_ <br/> |First property:  `ADAttribute` <br/> Second property:  `Patterns` <br/> |Messages where the specified Active Directory attribute of a recipient contains text patterns that match the specified regular expressions.  <br/> |
|**A recipient's domain is** <br/> **The recipient** \> **domain is** <br/> | _RecipientDomainIs_ <br/>  _ExceptIfRecipientDomainIs_ <br/> | `DomainName` <br/> |Messages where the domain of a recipient's email address matches the specified value.  <br/> If you need to find recipient domains that  *contain*  the specified domain (for example, any subdomain of a domain), use **The recipient address matches** (  _RecipientAddressMatchesPatterns_) condition, and specify the domain by using the syntax  `'@domain\.com$'`.  <br/> |
   
[Return to top](conditions-and-exceptions.md#RTT)
  
### Message subject or body
<a name="MessageSubjectOrBody"> </a>

> [!NOTE]
> The search for words or text patterns in the subject or other header fields in the message occurs  *after*  the message has been decoded from the MIME content transfer encoding method that was used to transmit the binary message between SMTP servers in ASCII text. You can't use conditions or exceptions to search for the raw (typically, Base64) encoded values of the subject or other header fields in messages. 
  
|**Condition or exception in the EAC**|**Condition and exception parameters in Exchange Online PowerShell**|**Property type**|**Description**|
|:-----|:-----|:-----|:-----|
|**The subject or body includes** <br/> **The subject or body** \> **subject or body includes any of these words** <br/> | _SubjectOrBodyContainsWords_ <br/>  _ExceptIfSubjectOrBodyContainsWords_ <br/> | `Words` <br/> |Messages that have the specified words in the **Subject** field or message body.  <br/> |
|**The subject or body matches** <br/> **The subject or body** \> **subject or body matches these text patterns** <br/> | _SubjectOrBodyMatchesPatterns_ <br/>  _ExceptIfSubjectOrBodyMatchesPatterns_ <br/> | `Patterns` <br/> |Messages where the **Subject** field or message body contain text patterns that match the specified regular expressions.  <br/> |
|**The subject includes** <br/> **The subject or body** \> **subject includes any of these words** <br/> | _SubjectContainsWords_ <br/>  _ExceptIfSubjectContainsWords_ <br/> | `Words` <br/> |Messages that have the specified words in the **Subject** field.  <br/> |
|**The subject matches** <br/> **The subject or body** \> **subject matches these text patterns** <br/> | _SubjectMatchesPatterns_ <br/>  _ExceptIfSubjectMatchesPatterns_ <br/> | `Patterns` <br/> |Messages where the **Subject** field contains text patterns that match the specified regular expressions.  <br/> |
   
[Return to top](conditions-and-exceptions.md#RTT)
  
### Attachments
<a name="Attachments"> </a>

For more information about how mail flow rules inspect message attachments, see [Use mail flow rules to inspect message attachments in Office 365](inspect-message-attachments.md).
  
|**Condition or exception in the EAC**|**Condition and exception parameters in Exchange Online PowerShell**|**Property type**|**Description**|
|:-----|:-----|:-----|:-----|
|**Any attachment's content includes** <br/> **Any attachment** \> **content includes any of these words** <br/> | _AttachmentContainsWords_ <br/>  _ExceptIfAttachmentContainsWords_ <br/> | `Words` <br/> |Messages where an attachment contains the specified words.  <br/> |
|**Any attachments content matches** <br/> **Any attachment** \> **content matches these text patterns** <br/> | _AttachmentMatchesPatterns_ <br/>  _ExceptIfAttachmentMatchesPatterns_ <br/> | `Patterns` <br/> |Messages where an attachment contains text patterns that match the specified regular expressions.  <br/> **Note**: Only the first 150 kilobytes (KB) of the attachments are scanned.  <br/> |
|**Any attachment's content can't be inspected** <br/> **Any attachment** \> **content can't be inspected** <br/> | _AttachmentIsUnsupported_ <br/>  _ExceptIfAttachmentIsUnsupported_ <br/> |n/a  <br/> |Messages where an attachment isn't natively recognized by Exchange Online.  <br/> |
|**Any attachment's file name matches** <br/> **Any attachment** \> **file name matches these text patterns** <br/> | _AttachmentNameMatchesPatterns_ <br/>  _ExceptIfAttachmentNameMatchesPatterns_ <br/> | `Patterns` <br/> |Messages where an attachment's file name contains text patterns that match the specified regular expressions.  <br/> |
|**Any attachment's file extension matches** <br/> **Any attachment** \> **file extension includes these words** <br/> | _AttachmentExtensionMatchesWords_ <br/>  _ExceptIfAttachmentExtensionMatchesWords_ <br/> | `Words` <br/> |Messages where an attachment's file extension matches any of the specified words.  <br/> |
|**Any attachment is greater than or equal to** <br/> **Any attachment** \> **size is greater than or equal to** <br/> | _AttachmentSizeOver_ <br/>  _ExceptIfAttachmentSizeOver_ <br/> | `Size` <br/> |Messages where any attachment is greater than or equal to the specified value.  <br/> In the EAC, you can only specify the size in kilobytes (KB).  <br/> |
|**The message didn't complete scanning** <br/> **Any attachment** \> **didn't complete scanning** <br/> | _AttachmentProcessingLimitExceeded_ <br/>  _ExceptIfAttachmentProcessingLimitExceeded_ <br/> |n/a  <br/> |Messages where the rules engine couldn't complete the scanning of the attachments. You can use this condition to create rules that work together to identify and process messages where the content couldn't be fully scanned.  <br/> |
|**Any attachment has executable content** <br/> **Any attachment** \> **has executable content** <br/> | _AttachmentHasExecutableContent_ <br/>  _ExceptIfAttachmentHasExecutableContent_ <br/> |n/a  <br/> |Messages where an attachment is an executable file. The system inspects the file's properties rather than relying on the file's extension.  <br/> |
|**Any attachment is password protected** <br/> **Any attachment** \> **is password protected** <br/> | _AttachmentIsPasswordProtected_ <br/>  _ExceptIfAttachmentIsPasswordProtected_ <br/> |n/a  <br/> |Messages where an attachment is password protected (and therefore can't be scanned). Password detection only works for Office documents and .zip files.  <br/> |
|**has these properties, including any of these words** <br/> **Any attachment** \> **has these properties, including any of these words** <br/> | _AttachmentPropertyContainsWords_ <br/>  _ExceptIfAttachmentPropertyContainsWords_ <br/> |First property:  `DocumentProperties` <br/> Second property:  `Words` <br/> |Messages where the specified property of an attached Office document contains the specified words. This condition helps you integrate mail flow rules with SharePoint, UNRESOLVED_TOKEN_VAL(exFCI) (FCI) in UNRESOLVED_TOKEN_VAL(exWinSvr2012R2) or later, or a third-party classification system.  <br/> You can select from a list of built-in properties, or specify a custom property.  <br/> |
   
[Return to top](conditions-and-exceptions.md#RTT)
  
### Any recipients
<a name="AnyRecipients"> </a>

The conditions and exceptions in this section provide a unique capability that affects  *all*  recipients when the message contains at least one of the specified recipients. For example, let's say you have a rule that rejects messages. If you use a recipient condition from the [Recipients](conditions-and-exceptions.md#Recipients) section, the message is only rejected for those specified recipients. For example, if the rule finds the specified recipient in a message, but the message contains five other recipients. The message is rejected for that one recipient, and is delivered to the five other recipients. 
  
If you add a recipient condition from this section, that same message is rejected for the detected recipient and the five other recipients.
  
Conversely, a recipient exception from this section  *prevents*  the rule action from being applied to  *all*  recipients of the message, not just for the detected recipients. 
  
 **Note**: This condition doesn't consider messages that are sent to recipient proxy addresses. It only matches messages that are sent to the recipient's primary email address.
  
|**Condition or exception in the EAC**|**Condition and exception parameters in Exchange Online PowerShell**|**Property type**|**Description**|
|:-----|:-----|:-----|:-----|
|**Any recipient address includes** <br/> **Any recipient** \> **address includes any of these words** <br/> | _AnyOfRecipientAddressContainsWords_ <br/>  _ExceptIfAnyOfRecipientAddressContainsWords_ <br/> | `Words` <br/> |Messages that contain the specified words in the **To**, **Cc**, or **Bcc** fields of the message.  <br/> |
|**Any recipient address matches** <br/> **Any recipient** \> **address matches any of these text patterns** <br/> | _AnyOfRecipientAddressMatchesPatterns_ <br/>  _ExceptIfAnyOfRecipientAddressMatchesPatterns_ <br/> | `Patterns` <br/> |Messages where the **To**, **Cc**, or **Bcc** fields contain text patterns that match the specified regular expressions.  <br/> |
   
[Return to top](conditions-and-exceptions.md#RTT)
  
### Message sensitive information types, To and Cc values, size, and character sets
<a name="Message"> </a>

The conditions in this section that look for values in the **To** and **Cc** fields behave like the conditions in the [Any recipients](conditions-and-exceptions.md#AnyRecipients) section (  *all*  recipients of the message are affected by the rule, not just the detected recipients). 
  
 **Note**: This condition doesn't consider messages that are sent to recipient proxy addresses. It only matches messages that are sent to the recipient's primary email address.
  
|**Condition or exception in the EAC**|**Condition and exception parameters in Exchange Online PowerShell**|**Property type**|**Description**|
|:-----|:-----|:-----|:-----|
|**The message contains sensitive information** <br/> **The message** \> **contains any of these types of sensitive information** <br/> | _MessageContainsDataClassifications_ <br/>  _ExceptIfMessageContainsDataClassifications_ <br/> | `SensitiveInformationTypes` <br/> |Messages that contain sensitive information as defined by data loss prevention (DLP) policies.  <br/> This condition is required for rules that use the **Notify the sender with a Policy Tip** (  _NotifySender_) action.  <br/> |
|**The To box contains** <br/> **The message** \> **To box contains this person** <br/> | _AnyOfToHeader_ <br/>  _ExceptIfAnyOfToHeader_ <br/> | `Addresses` <br/> |Messages where the **To** field includes any of the specified recipients.  <br/> |
|**The To box contains a member of** <br/> **The message** \> **To box contains a member of this group** <br/> | _AnyOfToHeaderMemberOf_ <br/>  _ExceptIfAnyOfToHeaderMemberOf_ <br/> | `Addresses` <br/> |Messages where the **To** field contains a recipient who is a member of the specified group.  <br/> |
|**The Cc box contains** <br/> **The message** \> **Cc box contains this person** <br/> | _AnyOfCcHeader_ <br/>  _ExceptIfAnyOfCcHeader_ <br/> | `Addresses` <br/> |Messages where the **Cc** field includes any of the specified recipients.  <br/> |
|**The Cc box contains a member of** <br/> **The message** \> **contains a member of this group** <br/> | _AnyOfCcHeaderMemberOf_ <br/>  _ExceptIfAnyOfCcHeaderMemberOf_ <br/> | `Addresses` <br/> |Messages where the **Cc** field contains a recipient who is a member of the specified group.  <br/> |
|**The To or Cc box contains** <br/> **The message** \> **To or Cc box contains this person** <br/> | _AnyOfToCcHeader_ <br/>  _ExceptIfAnyOfToCcHeader_ <br/> | `Addresses` <br/> |Messages where the **To** or **Cc** fields contain any of the specified recipients.  <br/> |
|**The To or Cc box contains a member of** <br/> **The message** \> **To or Cc box contains a member of this group** <br/> | _AnyOfToCcHeaderMemberOf_ <br/>  _ExceptIfAnyOfToCcHeaderMemberOf_ <br/> | `Addresses` <br/> |Messages where the **To** or **Cc** fields contain a recipient who is a member of the specified group.  <br/> |
|**The message size is greater than or equal to** <br/> **The message** \> **size is greater than or equal to** <br/> | _MessageSizeOver_ <br/>  _ExceptIfMessageSizeOver_ <br/> | `Size` <br/> |Messages where the total size (message plus attachments) is greater than or equal to the specified value.  <br/> In the EAC, you can only specify the size in kilobytes (KB).  <br/> **Note**: Message size limits on mailboxes are evaluated before mail flow rules. A message that's too large for a mailbox will be rejected before a rule with this condition is able to act on the message.  <br/> |
|**The message character set name includes any of these words** <br/> **The message** \> **character set name includes any of these words** <br/> | _ContentCharacterSetContainsWords_ <br/>  _ExceptIfContentCharacterSetContainsWords_ <br/> | `CharacterSets` <br/> |Messages that have any of the specified character set names.  <br/> |
   
[Return to top](conditions-and-exceptions.md#RTT)
  
### Sender and recipient
<a name="SenderAndRecipient"> </a>

|**Condition or exception in the EAC**|**Condition and exception parameters in Exchange Online PowerShell**|**Property type**|**Description**|
|:-----|:-----|:-----|:-----|
|**The sender is one of the recipient's** <br/> **The sender and the recipient** \> **the sender's relationship to a recipient is** <br/> | _SenderManagementRelationship_ <br/>  _ExceptIfSenderManagementRelationship_ <br/> | `ManagementRelationship` <br/> |Messages where the either sender is the manager of a recipient, or the sender is managed by a recipient.  <br/> |
|**The message is between members of these groups** <br/> **The sender and the recipient** \> **the message is between members of these groups** <br/> | _BetweenMemberOf1_ and  _BetweenMemberOf2_ <br/>  _ExceptIfBetweenMemberOf1_ and  _ExceptIfBetweenMemberOf2_ <br/> | `Addresses` <br/> |Messages that are sent between members of the specified groups.  <br/> |
|**The manager of the sender or recipient is** <br/> **The sender and the recipient** \> **the manager of the sender or recipient is this person** <br/> | _ManagerForEvaluatedUser_ and  _ManagerAddress_ <br/>  _ExceptIfManagerForEvaluatedUser_ and  _ExceptIfManagerAddress_ <br/> |First property:  `EvaluatedUser` <br/> Second property:  `Addresses` <br/> |Messages where either a specified user is the manager of the sender, or a specified user is the manager of a recipient.  <br/> |
|**The sender's and any recipient's property compares as** <br/> **The sender and the recipient** \> **the sender and recipient property compares as** <br/> | _ADAttributeComparisonAttribute_ and  _ADComparisonOperator_ <br/>  _ExceptIfADAttributeComparisonAttribute_ and  _ExceptIfADComparisonOperator_ <br/> |First property:  `ADAttribute` <br/> Second property:  `Evaluation` <br/> |Messages where the specified Active Directory attribute for the sender and recipient either match or don't match.  <br/> |
   
[Return to top](conditions-and-exceptions.md#RTT)
  
### Message properties
<a name="MessageProperties"> </a>

|**Condition or exception in the EAC**|**Condition and exception parameters in Exchange Online PowerShell**|**Property type**|**Description**|
|:-----|:-----|:-----|:-----|
|**The message type is** <br/> **The message properties** \> **include the message type** <br/> | _MessageTypeMatches_ <br/>  _ExceptIfMessageTypeMatches_ <br/> | `MessageType` <br/> |Messages of the specified type.  <br/> > [!NOTE]> When Outlook or Outlook Web App is configured to forward a message, the **ForwardingSmtpAddress** property is added to the message. The message type isn't changed to  `AutoForward`.           |
|**The message is classified as** <br/> **The message properties** \> **include this classification** <br/> | _HasClassification_ <br/>  _ExceptIfHasClassification_ <br/> | `MessageClassification` <br/> |Messages that have the specified message classification. This is a custom message classification that you can create in your organization by using the **New-MessageClassification** cmdlet.  <br/> |
|**The message isn't marked with any classifications** <br/> **The message properties** \> **don't include any classification** <br/> | _HasNoClassification_ <br/>  _ExceptIfHasNoClassification_ <br/> |n/a  <br/> |Messages that don't have a message classification.  <br/> |
|**The message has an SCL greater than or equal to** <br/> **The message properties** \> **include an SCL greater than or equal to** <br/> | _SCLOver_ <br/>  _ExceptIfSCLOver_ <br/> | `SCLValue` <br/> |Messages that are assigned a spam confidence level (SCL) that's greater than or equal to the specified value.  <br/> |
|**The message importance is set to** <br/> **The message properties** \> **include the importance level** <br/> | _WithImportance_ <br/>  _ExceptIfWithImportance_ <br/> | `Importance` <br/> |Messages that are marked with the specified Importance level.  <br/> |
   
[Return to top](conditions-and-exceptions.md#RTT)
  
### Message headers
<a name="MessageHeaders"> </a>

> [!NOTE]
> The search for words or text patterns in the subject or other header fields in the message occurs  *after*  the message has been decoded from the MIME content transfer encoding method that was used to transmit the binary message between SMTP servers in ASCII text. You can't use conditions or exceptions to search for the raw (typically, Base64) encoded values of the subject or other header fields in messages. 
  
|**Condition or exception in the EAC**|**Condition and exception parameters in Exchange Online PowerShell**|**Property type**|**Description**|
|:-----|:-----|:-----|:-----|
|**A message header includes** <br/> **A message header** \> **includes any of these words** <br/> | _HeaderContainsMessageHeader_ and  _HeaderContainsWords_ <br/>  _ExceptIfHeaderContainsMessageHeader_ and  _ExceptIfHeaderContainsWords_ <br/> |First property:  `MessageHeaderField` <br/> Second property:  `Words` <br/> |Messages that contain the specified header field, and the value of that header field contains the specified words.  <br/> The name of the header field and the value of the header field are always used together.  <br/> |
|**A message header matches** <br/> **A message header** \> **matches these text patterns** <br/> | _HeaderMatchesMessageHeader_ and  _HeaderMatchesPatterns_ <br/>  _ExceptIfHeaderMatchesMessageHeader_ and  _ExceptIfHeaderMatchesPatterns_ <br/> |First property:  `MessageHeaderField` <br/> Second property:  `Patterns` <br/> |Messages that contain the specified header field, and the value of that header field contains the specified regular expressions.  <br/> The name of the header field and the value of the header field are always used together.  <br/> |
   
[Return to top](http://technet.microsoft.com/library/c918ea00-1e68-4b8b-8d51-6966b4432e2d.aspx#RTT)
  
## Property types
<a name="PropertyTypes"> </a>

The property types that are used in conditions and exceptions are described in the following table.
  
> [!NOTE]
> If the property is a string, trailing spaces are not allowed. 
  
|**Property type**|**Valid values**|**Description**|
|:-----|:-----|:-----|
| `ADAttribute`|Select from a predefined list of Active Directory attributes|UNRESOLVED_TOKENBLOCK_VAL(PD_Transport_Rules_ADAttributes_Snippet)In the EAC, to specify multiple words or text patterns for the same attribute, separate the values with commas. For example, the value San Francisco,Palo Alto for the **City** attribute looks for "City equals San Francisco" or City equals Palo Alto". In Exchange Online PowerShell, use the syntax  `"AttributeName1:Value1,Value 2 with spaces,Value3...","AttributeName2:Word4,Value 5 with spaces,Value6..."`, where  `Value` is the word or text pattern that you want to match. For example,  `"City:San Francisco,Palo Alto"` or  `"City:San Francisco,Palo Alto"`, `"Department:Sales,Finance"`.When you specify multiple attributes, or multiple values for the same attribute, the **or** operator is used. Don't use values with leading or trailing spaces. Note that the **Country** attribute requires the two-letter ISO 3166-1 country code value (for example, DE for Germany). To search for values, see [https://go.microsoft.com/fwlink/p/?LinkId=331680](https://go.microsoft.com/fwlink/p/?LinkId=331680).|
| `Addresses`|Exchange Online recipients|Depending on the nature of the condition or exception, you might be able to specify any mail-enabled object in the organization (for example, recipient-related conditions), or you might be limited to a specific object type (for example, groups for group membership conditions). And, the condition or exception might require one value, or allow multiple values.In Exchange Online PowerShell, separate multiple values by commas. **Note**: This condition doesn't consider messages that are sent to recipient proxy addresses. It only matches messages that are sent to the recipient's primary email address.|
| `CharacterSets`|Array of character set names| One or more content character sets that exist in a message. For example:  `Arabic/iso-8859-6` `Chinese/big5` `Chinese/euc-cn` `Chinese/euc-tw` `Chinese/gb2312` `Chinese/iso-2022-cn` `Cyrillic/iso-8859-5` `Cyrillic/koi8-r` `Cyrillic/windows-1251` `Greek/iso-8859-7` `Hebrew/iso-8859-8` `Japanese/euc-jp` `Japanese/iso-022-jp` `Japanese/shift-jis` `Korean/euc-kr` `Korean/johab` `Korean/ks_c_5601-1987` `Turkish/windows-1254` `Turkish/iso-8859-9` `Vietnamese/tcvn`|
| `DomainName`|Array of SMTP domains|For example,  `contoso.com` or  `eu.contoso.com`.In Exchange Online PowerShell, you can specify multiple domains separated by commas.|
| `EvaluatedUser`|Single value of **Sender** or **Recipient**|Specifies whether the rule is looking for the manager of the sender or the manager of the recipient.|
| `Evaluation`|Single value of **Equal** or **Not equal** (  `NotEqual`)|When comparing the Active Directory attribute of the sender and recipients, this specifies whether the values should match, or not match.|
| `Importance`|Single value of **Low**, **Normal**, or **High**|The Importance level that was assigned to the message by the sender in Outlook or Outlook Web App.|
| `IPAddressRanges`|Array of IP addresses or address ranges| You enter the IPv4 addresses using the following syntax: **Single IP address** For example,  `192.168.1.1`. **IP address range** For example,  `192.168.0.1-192.168.0.254`. **Classless InterDomain Routing (CIDR) IP address range** For example,  `192.168.0.1/25`.  In Exchange Online PowerShell, you can specify multiple IP addresses or ranges separated by commas. |
| `ManagementRelationship`|Single value of **Manager** or **Direct report**( `DirectReport`)|Specifies the relationship between the sender and any of the recipients. The rule checks the **Manager** attribute in Active Directory to see if the sender is the manager of a recipient, or if the sender is managed by a recipient. |
| `MessageClassification`|Single message classification|In the EAC, you select from the list of message classifications that you've created.In Exchange Online PowerShell, you use the **Get-MessageClassification** cmdlet to identify the message classification. For example, use the following command to search for messages with the  `Company Internal` classification and prepend the message subject with the value  `CompanyInternal`. `New-TransportRule "Rule Name" -HasClassification @(Get-MessageClassification "Company Internal").Identity -PrependSubject "CompanyInternal"`|
| `MessageHeaderField`|Single string|Specifies the name of the header field. The name of the header field is always paired with the value in the header field (word or text pattern match).The message header is a collection of required and optional header fields in the message. Examples of header fields are **To**, **From**, **Received**, and **Content-Type**. Official header fields are defined in RFC 5322. Unofficial header fields start with **X-** and are known as X-headers.|
| `MessageType`|Single message type value| Specifies one of the following message types: **Automatic reply** (  `OOF`) **Auto-forward** (  `AutoForward`) **Encrypted** **Calendaring** **Permission controlled** (  `PermissionControlled`) **Voicemail** **Signed** **Approval request** (  `ApprovalRequest`) **Read receipt** (  `ReadReceipt`) > [!NOTE]>  When Outlook or Outlook Web App is configured to forward a message, the **ForwardingSmtpAddress** property is added to the message. The message type isn't changed to  `AutoForward`.           |
| `Patterns`|Array of regular expressions|Specifies one or more regular expressions that are used to identify text patterns in values. For more information, see [Regular Expression Syntax](https://go.microsoft.com/fwlink/p/?LinkID=180327).In Exchange Online PowerShell, you specify multiple regular expressions separated by commas, and you enclose each regular expression in quotation marks (").|
| `SCLValue`| One of the following values: **Bypass spam filtering** (  `-1`)  Integers 0 through 9 |Specifies the spam confidence level (SCL) that's assigned to a message. A higher SCL value indicates that a message is more likely to be spam.|
| `SensitiveInformationTypes`|Array of sensitive information types|Specifies one or more sensitive information types that are defined in your organization. For a list of built-in sensitive information types, see [What the sensitive information types in Exchange look for](http://technet.microsoft.com/library/98b81f9c-87bb-4905-8e53-04621c3ae74d.aspx).In Exchange Online PowerShell, use the syntax  `@{<SensitiveInformationType1>},@{<SensitiveInformationType2>},...`. For example, to look for content that contains at least two credit card numbers, and at least one ABA routing number, use the value  `@{Name="Credit Card Number"; minCount="2"},@{Name="ABA Routing Number"; minCount="1"}`.|
| `Size`|Single size value| Specifies the size of an attachment or the whole message.  In the EAC, you can only specify the size in kilobytes (KB).  In Exchange Online PowerShell, when you enter a value, qualify the value with one of the following units:  `B` (bytes)  `KB` (kilobytes)  `MB` (megabytes)  `GB` (gigabytes)  For example,  `20MB` Unqualified values are typically treated as bytes, but small values may be rounded up to the nearest kilobyte. |
| `SupervisonList`|Single value of **Allow** or **Block**|Supervision policies were a feature in Live@edu that allowed you to control who could send mail to and receive mail from users in your organization (for example, the closed campus and anti-bullying policies). In Office 365, you can't configure supervision list entries on mailboxes.|
| `UserScopeFrom`|Single value of **Inside the organization** (  `InOrganization`) or **Outside the organization** (  `NotInOrganization`)| A sender is considered to be inside the organization if either of the following conditions is true:  The sender is a mailbox, mail user, group, or mail-enabled public folder that exists in the organization's Active Directory.  The sender's email address is in an accepted domain that's configured as an authoritative domain or an internal relay domain, **and** the message was sent or received over an authenticated connection. For more information about accepted domains, see [Accepted Domains](http://technet.microsoft.com/library/c1839a5b-49f9-4c53-b247-f4e5d78efc45.aspx).  A sender is considered to be outside the organization if either of the following conditions is true:  The sender's email address isn't in an accepted domain.  The sender's email address is in an accepted domain that's configured as an external relay domain. > [!NOTE]>  To determine whether mail contacts are considered to be inside or outside the organization, the sender's address is compared with the organization's accepted domains.           |
| `UserScopeTo`| One of the following values: **Inside the organization** (  `InOrganization`) **Outside the organization** (  `NotInOrganization`) | A recipient is considered to be inside the organization if either of the following conditions is true:  The recipient is a mailbox, mail user, group, or mail-enabled public folder that exists in the organization's Active Directory.  The recipient's email address is in an accepted domain that's configured as an authoritative domain or an internal relay domain, **and** the message was sent or received over an authenticated connection.  A recipient is considered to be outside the organization if either of the following conditions is true:  The recipient's email address isn't in an accepted domain.  The recipient's email address is in an accepted domain that's configured as an external relay domain. |
| `Words`|Array of strings| Specifies one or more words to look for. The words aren't case-sensitive, and can be surrounded by spaces and punctuation marks. Wildcards and partial matches aren't supported.  For example, "contoso" matches " Contoso.". However, if the text is surrounded by other characters, it isn't considered a match. For example, "contoso" doesn't match the following values:  Acontoso  Contosoa  Acontosob  The asterisk (\*) is treated as a literal character, and isn't used as a wildcard character. |
   
[Return to top](http://technet.microsoft.com/library/c918ea00-1e68-4b8b-8d51-6966b4432e2d.aspx#RTT)
  
## For more information
<a name="PropertyTypes"> </a>

[Mail flow rules (transport rules) in Exchange Online](mail-flow-rules.md)
  
[Mail flow rule actions in Exchange Online](mail-flow-rule-actions.md)
  
[Mail flow rule procedures in Exchange Online](mail-flow-rule-procedures.md)
  
[Transport Rule Conditions (Predicates)](http://technet.microsoft.com/library/c918ea00-1e68-4b8b-8d51-6966b4432e2d.aspx) for Exchange 2013 
  
[Transport Rule Conditions (Predicates)](http://technet.microsoft.com/library/04edeaba-afd4-4207-b2cb-51bcc44e483c.aspx) for Exchange Online Protection 
  
[New-TransportRule](http://technet.microsoft.com/library/eb3546bf-ca37-474e-9c22-962fe95af276.aspx)
  

