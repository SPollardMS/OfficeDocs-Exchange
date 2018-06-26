---
title: "Remote domains in Exchange Online"
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
ms.date: 1/9/2018
ms.audience: ITPro
ms.topic: article
ms.service: exchange-online
localization_priority: Normal
ms.assetid: f191e052-658d-4c74-bfe7-bcb1d525e4e3

---

# Remote domains in Exchange Online
There are many reasons why you might want to control the types and the format of messages that your users send to domains outside of your Exchange Online domain in Microsoft Office 365. Here are some of those reasons:
  
- You don't want to let your users forward messages to people on other domains.
    
- You work with an organization from whom you don't want to receive automatic messages, such as non-delivery reports and out-of-office replies.
    
- You have a business partner outside your organization, and you'd like that partner to receive the same out-of-office replies as those received by people inside your organization.
    
- Your users frequently send email to a company that supports limited email formats, and you'd like to make sure all emails sent to that organization are sent in a format that they can read.
    
To accomplish this, you use what's called a remote domain. The remote domain settings override settings that your users might configure in Outlook or Outlook on the web (formerly known as Outlook Web App), or that you configure in the Exchange admin center (EAC) or Exchange Online PowerShell. For example, users might have an out-of-office reply set up for people outside the organization, but if a sender from a remote domain sends mail to them, and the remote domain is not set to receive out-of-office replies, no out-of-office reply is sent. To change the settings, you can:
  
- Create a remote domain for a specific domain, and set unique properties for emails sent to that domain.
    
- Modify the settings for the default remote domain. If you have no other remote domains set up, changes to the default remote domain apply to all external domains. If you have other remote domains set up, changes to the default remote domain apply to all other external domains.
    
For instructions on how to create and configure remote domains, see [Manage remote domains in Exchange Online](manage-remote-domains.md).
  
## Reducing or increasing information flow to another company
<a name="RTT"> </a>

When a message comes from outside your organization, there are several types of replies that are automatically generated. Some types of replies are set up by users in Outlook or Outlook Web App, and others are set up by admins. Because the remote domain settings override settings configured by users, as well as mail user and mail contact settings configured by admins, you can choose which types of automatic replies are sent to everyone on a remote domain.
  
If a remote domain configuration blocks a specific type of reply, like a non-delivery report, from being sent to recipients in that domain, the reply is generated, but then it is deleted before it is sent. No error message is sent. For example, if you turn off automatic forwarding on the default remote domain, when users try to automatically forward email to another domain, they can change their settings or create the Inbox rule, but their messages won't be forwarded.
  
The following table shows the types of replies you can control in a remote domain and the settings that each remote domain setting overrides.
  
|**Type of reply**|**Description**|**Per-user settings that this remote domain setting overrides**|
|:-----|:-----|:-----|
|Out-of-office messages  <br/> |Specify whether an out-of-office message should be sent to people on the remote domain, and if so, which message to use. You can select either the reply that the user on your domain set up for people outside your organization, or the one for people inside your organization. The default is to send the out-of-office reply for people outside your organization.  <br/> |This setting overrides out-of-office reply settings specified by individual users in [Outlook](https://go.microsoft.com/fwlink/p/?LinkId=398992) or [Outlook on the web](https://go.microsoft.com/fwlink/p/?LinkId=398993).  <br/> |
|Automatic replies  <br/> |Allow or prevent automatic replies to senders on the remote domain. The default is to allow automatic replies.  <br/> |This setting overrides automatic replies set up by admins using the [Set-MailboxAutoReplyConfiguration](http://technet.microsoft.com/library/fda7b1fe-7f08-4711-aa91-9c270f62a8aa.aspx) cmdlet.  <br/> |
|Automatic forwards  <br/> |Allow or prevent automatically forwarded messages to be sent to people on the remote domain. The default is to allow automatic forwarding.  <br/> | When users configure automatic forwarding to recipients on a remote domain, the remote domain settings override users' automatic forwarding settings (messages are blocked if automatic forwards are disabled for the remote domain). Users can configure automatic forwarding by using these methods:  <br/>  Inbox rules in Outlook or Outlook on the web to forward messages. Learn more about Inbox rules in [Outlook ](https://go.microsoft.com/fwlink/p/?LinkId=398878) and [Outlook on the web](https://go.microsoft.com/fwlink/p/?LinkId=398877).  <br/>  Forwarding options in Outlook on the web. For more information, see [Forward email from Office 365 to another email account](https://go.microsoft.com/fwlink/p/?linkid=866249).  <br/> **Note**: When admins use other methods to configure automatic forwarding for users, the forwarded messages aren't affected by the remote domain settings (messages are forwarded to recipients on the remote domain even if automatic forwards are disabled for the remote domain). For example:  <br/>  Mail forwarding for a user. For more information, see [Configure email forwarding for a mailbox](../../recipients-in-exchange-online/manage-user-mailboxes/configure-email-forwarding.md).  <br/>  Mail flow rules (also known as transport rules) to forward messages. For more information, see [Mail flow rules (transport rules) in Exchange Online](../../security-and-compliance/mail-flow-rules/mail-flow-rules.md).  <br/> |
|Delivery reports  <br/> |Allow or prevent a delivery receipt to be sent to people on the remote domain. The default is to allow sending delivery reports.  <br/> |An email sender on the remote domain can request a delivery receipt on a message. This remote domain setting can override the sender's request for a delivery receipt and prevent the delivery receipt from being sent. For more information about requesting a delivery receipt, see [Add tracking to email messages](https://go.microsoft.com/fwlink/p/?LinkId=398873).  <br/> |
|Non-delivery report  <br/> |Allow or prevent non-delivery reports (also known a NDRs or bounce messages) to be sent to people on the remote domain. The default is to allow sending non-delivery reports.  <br/> |This remote domain setting is the only way to prevent non-delivery reports from being sent when a message can't be delivered.  <br/> |
|Meeting forward notifications  <br/> |Prevent or allow meeting forward notifications to be sent to people on the remote domain. The default is to prevent sending meeting forward notifications.  <br/> |Meeting forward notifications are automatically created and sent to the meeting organizer when a meeting participant forwards a meeting. Typically, they are sent to meeting organizers only on domains that are part of your Exchange Online organization. Admins can enable them to be sent to meeting organizers on the remote domain.  <br/> |
   
## Specifying message format
<a name="MessageFormat"> </a>

To make sure that email sent from your Exchange Online organization is compatible with the receiving messaging system in the remote domain, you can specify the message format and character set to use for all email messages sent to that remote domain. For example, if you know that the remote domain is not using Exchange, you can specify to never use Rich Text Format (RTF). The following table describes the message format settings.
  
|**Setting**|**Description**|**Settings that this overrides**|
|:-----|:-----|:-----|
|**Rich Text Format (RTF)** <br/> | Choose how to format messages:  <br/> **Always**: Use this value if the remote domain uses Exchange.  <br/> **Never**: If the remote domain does not use Exchange, use this value.  <br/> **Follow user settings**: Use message format settings defined by the user. Use this value if you don't know what email system the remote domain uses.  <br/>  The default is to follow the user's settings.  <br/> |Message format can be defined in several places: Outlook or Outlook on the web, and the admin can also use the [Set-MailContact](http://technet.microsoft.com/library/04c4e889-8546-4395-9d26-31af08264e45.aspx) or [Set-MailUser](http://technet.microsoft.com/library/087a55a2-ee8d-41a8-9c8f-d86e32ce8448.aspx) cmdlets to modify settings per recipient.  <br/> Remote domain settings override settings specified by a user or by the admin. For more information about the message formats and the order of precedence of message format settings, see [Message format and transmission in Exchange Online](../../mail-flow-best-practices/message-format-and-transmission.md).  <br/> |
|**MIME character set** and **Non-MIME character set** <br/> |
None:   Use the character set specified in the message. Select a character set from the list.   If the message does not have a character set, the selected character set is used. By default, no character sets are specified.  <br/> |These settings are used only if the message doesn't include a character set. For a complete list of supported character sets, see [Supported character sets for remote domains](supported-character-sets.md).  <br/> |
   
If you specify a particular message format for the remote domain, the format of the headers and message content sent to the domain are modified.
  
## Other settings
<a name="OtherSettings"> </a>

You can configure other message settings for remote domains by using Exchange Online PowerShell. For a complete list of settings, see [Set-RemoteDomain](http://technet.microsoft.com/library/4738bf25-39b8-4433-bd64-1d60252c2832.aspx).
  
## What else do I need to know?
<a name="OtherSettings"> </a>

- You can set up a remote domain only for an external domain. A domain is defined as external if it isn't listed on the **Office 365 admin center** \> **Domains** page. For example, if fabrikam.com is one of your domains, you can't create a remote domain for fabrikam.com. 
    
- You can't remove the default remote domain.
    
- You can specify all subdomains when you create a remote domain.
    
## See also
<a name="OtherSettings"> </a>

[Manage remote domains in Exchange Online](manage-remote-domains.md)

