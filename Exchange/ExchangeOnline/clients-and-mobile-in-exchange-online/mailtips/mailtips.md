---
title: "MailTips"
ms.author: dmaguire
author: msdmaguire
manager: laurawi
ms.date: 4/28/2017
ms.audience: Developer
ms.topic: overview
ms.service: exchange-online
localization_priority: Normal
ms.assetid: 9c989167-cc0c-40a6-82ba-383f573bd2d5

description: "MailTips are informative messages displayed to users while they're composing a message. Microsoft Exchange Server 2013 analyzes the message, including the list of recipients to which it's addressed, and if it detects a potential problem, it notifies the user with MailTips prior to sending the message. With the help of the information provided by MailTips, senders can adjust the message they're composing to avoid undesirable situations or non-delivery reports (NDRs)."
---

# MailTips

MailTips are informative messages displayed to users while they're composing a message. Microsoft Exchange Server 2013 analyzes the message, including the list of recipients to which it's addressed, and if it detects a potential problem, it notifies the user with MailTips prior to sending the message. With the help of the information provided by MailTips, senders can adjust the message they're composing to avoid undesirable situations or non-delivery reports (NDRs).
  
## How MailTips work

MailTips are implemented as a web service in Exchange 2013. When a sender is composing a message, the client software makes an Exchange web service call to the Client Access server to get the list of MailTips. The server responds with the list of MailTips that apply to that message, and the client software displays the MailTips to the sender.
  
The following unproductive messaging scenarios are common in any messaging environment:
  
- NDRs resulting from messages that violate restrictions configured in an organization such as message size restrictions or maximum number of recipients per message.
    
- NDRs resulting from messages sent to recipients that don't exist, recipients that are restricted, or users whose mailboxes are full.
    
- Sending messages to users with Automatic Replies configured.
    
All of these scenarios involve the user sending a message, expecting it to be delivered, and instead receiving a response stating that the message isn't delivered. Even in the best-case scenario, like the automatic reply, these events result in lost productivity. In the case of an NDR, this scenario could result in a costly call to the Help desk.
  
There are also several scenarios where sending a message won't result in an error, but can have undesirable, even embarrassing consequences:
  
- Messages sent to extremely large distribution groups.
    
- Messages sent to inappropriate distribution groups.
    
- Messages inadvertently sent to recipients outside your organization.
    
- Selecting **Reply to All** to a message that was received as a Bcc recipient. 
    
All of these problematic scenarios can be mitigated by informing users of the possible outcome of sending the message as they're composing the message. For example, if senders know that the size of the message they're trying to send exceeds the corporate policy, they won't attempt to send the message. Similarly, if senders are notified that the message they're sending will be delivered to people outside the organization, they're more likely to ensure that the content and the tone of the message are appropriate.
  
The following messaging clients support MailTips:
  
- Outlook Web App
    
- Microsoft Outlook 2010 or later
    
## MailTips in Exchange

The following table lists the available MailTips in Exchange 2013.
  
|**MailTip**|**Availability**|**Scenario**|
|:-----|:-----|:-----|
|Invalid Internal Recipient  <br/> |Outlook  <br/> |The Invalid Internal Recipient MailTip is displayed if the sender adds a recipient that appears to be internal to the organization but doesn't exist.  <br/> This could happen if the sender addresses a message to a user who is no longer with the company but whose address resolves due to name resolution cache or an entry in the sender's Contacts folder. It can also happen if the sender types an SMTP address with a domain for which Exchange is authoritative and the address doesn't resolve to an existing recipient.  <br/> The MailTip indicates the invalid recipient and gives the sender the option to remove the recipient from the message.  <br/> |
|Mailbox Full  <br/> |Outlook  <br/> Outlook Web App  <br/> |The Mailbox Full MailTip is displayed if the sender adds a recipient whose mailbox is full and your organization has implemented a Prohibit Receive restriction for mailboxes over a specified size.  <br/> The MailTip indicates the recipient whose mailbox is full and gives the sender the option to remove the recipient from the message.  <br/> The MailTip is accurate at the time of display. If the message isn't immediately sent, the MailTip is updated every two hours. This also applies to messages that were saved in the Drafts folder and reopened after two hours.  <br/> |
|Automatic Replies  <br/> |Outlook  <br/> Outlook Web App  <br/> |The Automatic Replies MailTip is displayed if the sender adds a recipient who has turned on Automatic Replies.  <br/> The MailTip indicates the recipient has Automatic Replies turned on and also displays the first 175 characters of the automatic reply configured by the recipient.  <br/> The MailTip is accurate at the time of display. If the message isn't immediately sent, the MailTip is updated every two hours. This also applies to messages that were saved in the Drafts folder and reopened after two hours.  <br/> If part of your user mailboxes are hosted on Exchange Online and you're in a coexistence with Exchange Online scenario, the setting on the remote domain object that represents the remote part of your organization has a direct effect on how this MailTip is processed.  <br/> In Exchange 2013, users can configure different Automatic Replies for internal and external senders. If the remote domain is configured as an internal domain (by setting the  _IsInternal_ parameter on the remote domain object to  `$true`), the internal automatic reply is returned to all users in the organization regardless of where their mailbox resides. However, if the remote domain isn't configured as an internal domain, the internal automatic reply is returned to all users whose mailboxes are in the local domain and the external automatic reply is returned to users whose mailboxes are in the remote domain.  <br/> |
|Custom  <br/> |Outlook  <br/> Outlook Web App  <br/> |A custom MailTip is displayed if the sender adds a recipient for whom a customized MailTip is configured.  <br/> A custom MailTip can be useful for providing specific information about a recipient. For example, you can create a custom MailTip for a distribution group explaining its purpose to reduce its misuse. For more information, see [Configure custom MailTips for recipients](configure-custom-mailtips.md).  <br/> By default, custom MailTips aren't displayed if the sender isn't allowed to send to that recipient. In that case, the Restricted Recipient MailTip is displayed. However, you can change this configuration and have the custom MailTip also display.  <br/> |
|Restricted Recipient  <br/> |Outlook  <br/> Outlook Web App  <br/> | The Restricted Recipient MailTip is displayed if the sender adds a recipient for which delivery restrictions are configured prohibiting this sender from sending messages.  <br/>  The MailTip indicates the recipient to which the sender isn't allowed to send messages and gives the sender the option to remove the recipient from the message. It also clearly informs the sender that the message won't be delivered if sent.  <br/>  If the restricted recipient is an external recipient, or if it's a distribution group that contains external recipients, this information is also provided to the sender. However, the following MailTips, if applicable, are suppressed:  <br/>  Automatic Replies  <br/>  Mailbox Full  <br/>  Custom MailTip  <br/>  Moderated Recipient  <br/>  Oversize Message  <br/> |
|External Recipients  <br/> |Outlook  <br/> Outlook Web App  <br/> |The External Recipients MailTip is displayed if the sender adds a recipient that's external, or adds a distribution group that contains external recipients.  <br/> This MailTip informs senders if a message they're composing will leave the organization, helping them make the correct decisions about wording, tone, and content.  <br/> By default, this MailTip is turned off. You can turn it on using the **Set-OrganizationConfig** cmdlet. For details, see [MailTips over organization relationships](mailtips-over-organization-relationships.md).  <br/> If part of your user mailboxes are hosted on Exchange Online and you're in coexistence with an Exchange Online scenario, the setting on the remote domain object that represents the remote part of your organization has a direct effect on how this MailTip is processed.  <br/> If the remote domain is configured as an internal domain (by setting the  _IsInternal_ parameter on the remote domain object to  `$true`), any recipients in this remote domain will be treated as internal and therefore the External Recipients MailTip won't be displayed. However, if the remote domain isn't configured as an internal domain, the recipients in that domain will be considered external and this MailTip will be displayed when a message is being composed to those recipients.  <br/> > [!NOTE]> This MailTip isn't evaluated when composing a message to a distribution group in the remote domain.           |
|Large Audience  <br/> |Outlook  <br/> Outlook Web App  <br/> |The Large Audience MailTip is displayed if the sender adds a distribution group that has more than the large audience size configured in your organization. By default, Exchange displays this MailTip for messages to distribution groups that have more than 25 members. For details, see [Configure the large audience size for your organization](configure-large-audience-size.md).  <br/> The size of distribution groups isn't calculated each time. Instead, the distribution group information is read from the group metrics data.  <br/> |
|Moderated Recipient  <br/> |Outlook  <br/> Outlook Web App  <br/> |The Moderated Recipient MailTip is displayed if the sender adds a recipient that's moderated.  <br/> The MailTip indicates which recipient is moderated and informs the sender that this may result in delay of the delivery.  <br/> If the sender is also the moderator, this MailTip isn't displayed. It's also not displayed if the sender has been explicitly allowed to send messages to the recipient (by adding the sender's name to the Accept Messages Only From list for the recipient).  <br/> For instructions on how to configure moderated recipients in Exchange 2013, see [Common message approval scenarios](../../security-and-compliance/mail-flow-rules/common-message-approval-scenarios.md).  <br/> For instructions on how to configure moderated recipients in Exchange Online, see [Configure a moderated recipient in Exchange Online](../../recipients-in-exchange-online/configure-a-moderated-recipient.md).  <br/> |
|Reply-All on Bcc  <br/> |Outlook Web App  <br/> |The Reply-All on Bcc MailTip is displayed if the sender receives a Bcc copy of a message and selects **Reply to All**.  <br/> When a user selects **Reply to All** to such a message, the fact that the user received a Bcc of that message is revealed to the rest of the audience to which the message was sent. In almost all cases, this is an undesirable situation, and this MailTip informs the user of this condition.  <br/> |
|Oversize Message  <br/> |Outlook  <br/> | The Oversize Message MailTip is displayed if the message the sender is composing is larger than configured message size limits in your organization.  <br/>  The MailTip is displayed if the message size violates one of the following size restrictions:  <br/>  Maximum send size setting on the sender's mailbox  <br/>  Maximum receive size setting on the recipient's mailbox  <br/>  Maximum message size restriction for the organization  <br/> > [!NOTE]>  Due to the complexity of the implementation, the message size limits on the connectors in your organization aren't taken into account.           |
   
## MailTip restrictions

MailTips are subject to the following restrictions:
  
- MailTips aren't supported when working in offline mode in Outlook.
    
- When a message is addressed to a distribution group, the MailTips for individual recipients that are members of that distribution group aren't evaluated. However, if any of the members is an external recipient, the External Recipients MailTip is displayed, which shows the sender the number of external recipients in the distribution group.
    
- If the message is addressed to more than 200 recipients, individual mailbox MailTips aren't evaluated due to performance reasons.
    
- Custom MailTips are limited to 175 characters.
    
- While Exchange 2010 would populate MailTips in their entirety, Exchange 2013 will only display up to 1000 characters.
    
- If the sender starts composing a message and leaves it open for an extended period of time, the Automatic Replies and Mailbox Full MailTips are evaluated every two hours.
    

