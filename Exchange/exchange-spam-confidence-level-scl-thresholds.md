---
title: Exchange spam confidence level (SCL) thresholds
ms.prod: EXCHANGE
ms.assetid: 0009b4af-be6d-41d2-98bc-b5487272c74a
---


# Exchange spam confidence level (SCL) thresholds
Learn how to minimize spam in Exchange 2016 by configuring and adjusting the spam confidence level (SCL) thresholds.
> [!NOTE]
> On November 1, 2016, Microsoft stopped producing spam definition updates for the SmartScreen filters in Exchange and Outlook. The existing SmartScreen spam definitions will be left in place, but their effectiveness will likely degrade over time. For more information, see  [Deprecating support for SmartScreen in Outlook and Exchange](https://go.microsoft.com/fwlink/p/?linkid=835894). 
  
    
    

In Exchange Server 2016, you can define specific actions for messages according to spam confidence level (SCL) thresholds. For example, you can define different thresholds for rejecting, deleting, or quarantining messages on an Exchange server that's running the Content Filter agent. These SCL thresholds and actions are basically unchanged from Exchange Server 2010
The Content Filter agent assigns an SCL rating to messages late in the antispam cycle, after the other antispam agents have processed inbound messages. Many of the other antispam agents that process inbound messages before the Content Filter agent are absolute in how they act on a message. For example, the Connection Filtering agent on an Edge Transport server rejects messages from IP addresses based on a real-time block list. Similarly, the Sender Filter agent blocks messages based on a list of blocked senders, and the Recipient Filter agent blocks messages based on a list of blocked recipients. By processing messages first, the other antispam agents greatly reduce the number of messages (in most cases, blatantly unwanted messages) that need to be processed by the Content Filter agent. For more information about the order that antispam agents process messages in, see  [Antispam protection in Exchange 2016](antispam-protection-in-exchange-2016.md).
  
    
    

Because content filtering isn't an exact science, it's important to be able to adjust the actions of the Content Filter agent based on different SCL values. By carefully monitoring and adjusting the SCL thresholds, you can minimize the following conditions:
- The number of messages in and the size of the spam quarantine mailbox.
    
  
- The number of legitimate email messages that are mistakenly quarantined or placed in the user's Junk Email folder (false positives).
    
  
- The number of offensive spam email messages that reach the user's mailbox (messages shouldn't even reach the Junk Email folder).
    
  
- The number of spam email messages that reach the user's Inbox.
    
  
The combination of this SCL thresholds in the Content Filter agent and the SCL Junk Email folder threshold on the user's mailbox helps you implement a more comprehensive and precise antispam strategy, which can help you reduce the overall cost of deploying and maintaining an antispam solution across your Exchange organization.
## SCL threshold actions

By adjusting SCL threshold actions, you can escalate the content filtering action taken on messages that have a greater probability of being spam. To understand this functionality, it's helpful to understand the different SCL threshold actions and how they're implemented:
  
    
    

- **SCL delete threshold** When the message's SCL value is greater than or equal to the SCL delete threshold, the Content Filter agent silently deletes the message. There's no protocol-level communication that tells the source messaging server or sender that the message was deleted. If the message's SCL value is lower than the SCL delete threshold, the Content Filter agent compares the SCL value to the SCL reject threshold.
    
  
- **SCL reject threshold** When the message's SCL value is greater than or equal to the SCL reject threshold, but less than the SCL delete threshold, the Content Filter agent rejects the message and sends a rejection response to the sending system. You can customize the rejection response. In some cases, a non-delivery report (also known as an NDR, delivery status notification, DSN, or bounce message) is sent to the original sender of the message. If the message's SCL value is lower than the SCL reject threshold, the Content Filter agent compares the SCL value to the SCL quarantine threshold.
    
  
- **SCL quarantine threshold** When the message's SCL value is greater than or equal to the SCL quarantine threshold, but less than the SCL reject threshold, the Content Filter agent sends the message to the spam quarantine mailbox. For more information about the configuring the spam quarantine mailbox, see [Configure a spam quarantine mailbox](configure-a-spam-quarantine-mailbox.md).
    
    Administrators need periodically review the spam quarantine mailbox to verify that too much obvious spam isn't unnecessarily quarantined (the SCL quarantine threshold is too high), and that too much legitimate email isn't quarantined (the SCL quarantine threshold is too low). To view the results of antispam tests on quarantined messages, see  [View antispam stamps in Outlook](view-antispam-stamps-in-outlook.md).
    
    If the message's SCL value is lower than the SCL quarantine threshold, the message is delivered to the appropriate Mailbox server, where the organization's or mailbox's SCL Junk Email folder threshold is evaluated.
    
  
- **SCL Junk Email folder threshold** If the message's SCL value is greater than the SCL Junk Email folder threshold that's configured for the organization or on the mailbox, the message is delivered to the Junk Email folder. If the message's SCL value is equal to or lower than the Junk Email folder threshold, the message is delivered to the Inbox.
    
    Unlike the other SCL thresholds that are controlled by the Content Filter agent, the SCL Junk Email folder threshold is controlled by the junk email rule (a hidden Inbox rule named Junk E-mail Rule) that's enabled by default in every mailbox. The Content Filter agent assigns the SCL value to a message, but the Junk E-mail Rule is responsible for delivering the message to the Junk Email folder. For more information, see  [Use the Exchange Management Shell to enable or disable the junk email rule in a mailbox](configure-exchange-antispam-settings-on-mailboxes.md#EnableOrDisableJunkEmailRule).
    
  
The Content Filter agent and the Junk Email folder process the SCL threshold value differently. The Content Filter agent uses greater than or equal to for the SCL threshold value, but the Junk Email folder uses greater than. For example, if you configure the Content Filter agent with an SCL delete threshold of 8, all messages with an SCL of 8 or higher are silently deleted. However, if you configure the Junk Email folder with an SCL threshold of 4, all messages with an SCL of 5 or higher are moved to the Junk Email folder, while messages with an SCL of 4 or lower are delivered to the Inbox.
  
    
    

## Scope of SCL thresholds

You can configure the SCL thresholds in the following locations:
  
    
    

- **Server configuration** The SCL delete, reject, and quarantine thresholds on the Content Filter agent.
    
  
- **Organization configuration** The SCL Junk Email folder threshold value on the Exchange organization.
    
  
- **Mailbox configuration** The SCL thresholds on specific mailboxes.
    
  

### SCL thresholds on the Content Filter agent

You use the **Set-ContentFilterConfig** cmdlet to configure the SCL delete, reject, and quarantine thresholds on an Edge Transport server or Mailbox server where you're running the Content Filter agent. Over time, as you analyze the spam functionality and metrics provided by the antispam logging and reporting features, you can make additional adjustments to these SCL thresholds as needed.
  
    
    
The SCL threshold parameters that are available on the **Set-ContentFilterConfig** cmdlet are described in the following table.
  
    
    


|**Parameter**|**Description**|
|:-----|:-----|
| _SCLDeleteEnabled_ <br/> |Enables and disables the SCL delete threshold. Valid values are  `$true` or `$false`. The default value is  `$false`, which means the SCL delete threshold isn't enabled by default.  <br/> You set the SCL delete threshold value with the  _SCLDeleteThreshold_ parameter. <br/> |
| _SCLDeleteThreshold_ <br/> |The SCL value that's used when the SCL delete threshold is enabled. A message with an SCL value that's greater than or equal to this value is silently deleted. The maximum value is 9, which is also the default value.  <br/> When you enable the SCL delete threshold, this value should be greater than all other SCL thresholds.  <br/> |
| _SCLRejectEnabled_ <br/> |Enables and disables the SCL reject threshold. Valid values are  `$true` or `$false`. The default value is  `$true`, which means the SCL reject threshold is enabled by default.  <br/> You set the SCL reject threshold value with the  _SCLRejectThreshold_ parameter. <br/> |
| _SCLRejectThreshold_ <br/> |The SCL value that's used when the SCL reject threshold is enabled. A message with an SCL value that's greater than or equal to this value is rejected, and an NDR is sent to the sender. The maximum value is 9, and the default value is 7.  <br/> When you enable the SCL reject threshold, this value should be less than the SCL delete threshold, but greater than the SCL quarantine and Junk Email folder thresholds.  <br/> |
| _SCLQuarantineEnabled_ <br/> |Enables and disables the SCL quarantine threshold. Valid values are  `$true` or `$false`. The default value is  `$false`, which means the SCL quarantine threshold isn't enabled by default.  <br/> You set the SCL quarantine threshold value with the  _SCLQuarantineThreshold_ parameter. <br/> For more information about the configuring the spam quarantine mailbox that's required to quarantine messages, see  [Configure a spam quarantine mailbox](configure-a-spam-quarantine-mailbox.md).  <br/> |
| _SCLQuarantineThreshold_ <br/> |The SCL value that's used when the SCL quarantine threshold is enabled. A message with an SCL value that's greater than or equal to this value is redirected to the spam quarantine mailbox. The maximum value is 9, which is also the default value.  <br/> When you enable the SCL quarantine threshold, this value should be less than the SCL reject threshold, but greater than the SCL Junk Email folder threshold (the  _SCLJunkThreshold_ parameter on the **Set-OrganizationConfig** or **Set-Mailbox** cmdlets). <br/> |
   
For examples of configuring the SCL thresholds on the Content Filter agent, see  [Use the Exchange Management Shell to configure SCL thresholds for content filtering](content-filtering-procedures.md#ShellSCL).
  
    
    

### SCL thresholds on the organization

You use the  _SCLJunkThreshold_ parameter **Set-OrganizationConfig** cmdlet to set the SCL Junk Email folder threshold value for all mailboxes in the organization. This is the only SCL threshold that you can configure at the organization level. The SCL value is typically assigned to messages by the Content Filter agent.
  
    
    
The  _SCLJunkThreshold_ parameter on the **Set-OrganizationConfig** cmdlet is described in the following table.
  
    
    


|**Parameter**|**Description**|
|:-----|:-----|
| _SCLJunkThreshold_ <br/> |The SCL value that's used when the junk email rule is enabled in the mailbox, and an SCL Junk Email folder threshold isn't configured on the mailbox.  <br/> A message with an SCL value that's greater than this value is moved to the Junk Email folder by the junk email rule. The maximum value is 9, and the default value is 4, which means that messages with an SCL value of 5 or higher are moved to the Junk Email folder, and messages with an SCL value of 4 or lower are delivered to the Inbox.  <br/> |
   
 **Notes**:
  
    
    

- The SCL Junk Email folder threshold is enabled by default, because the junk email rule is enabled by default in all mailboxes. If the junk email rule is disabled in the mailbox, the SCL Junk Email folder threshold (for the organization or the mailbox) is disabled for the mailbox.
    
  
- You can disable the junk email rule in a mailbox by using the  _Enabled_ parameter on the **Set-MailboxJunkEmailConfiguration** cmdlet, but only after the mailbox has been opened in Outlook (in Cached Exchange mode) or Outlook on the web.
    
  
- You can control the availability of the junk email settings in Outlook on the web, which prevents users from enabling or disabling the junk email rule in their own mailbox.
    
  
For more information, see the  [Configure Exchange antispam settings on mailboxes](configure-exchange-antispam-settings-on-mailboxes.md) topic.
  
    
    

### SCL thresholds on a mailbox

You can use the **Set-Mailbox** cmdlet to configure all SCL thresholds on a mailbox. The same SCL parameters that are available on the **Set-ContentFilterConfig** cmdlet are also available on the **Set-Mailbox** cmdlet:
  
    
    

-  _SCLDeleteEnabled_
    
  
-  _SCLDeleteThreshold_
    
  
-  _SCLRejectEnabled_
    
  
-  _SCLRejectThreshold_
    
  
-  _SCLQuarantineEnabled_
    
  
-  _SCLQuarantineThreshold_
    
  
Unlike the SCL threshold parameters on **Set-ContentFilterConfig**, the parameters on the **Set-Mailbox** cmdlet also accept the value `$null` (the value is blank), which is the default value for all SCL thresholds on the mailbox. This blank default value indicates that no SCL thresholds are configured on the mailbox, so the Content Filter agent uses its SCL threshold settings for messages that are sent to the mailbox.
  
    
    
If you configure an SCL threshold on a mailbox (the value isn't blank), the setting override the corresponding SCL threshold on the Content Filter agent for messages that are sent to the mailbox. The SCL thresholds that you configure on the mailbox are stored in Active Directory, and are replicated to subscribed Edge Transport servers by the Microsoft Exchange EdgeSync service.
  
    
    
The results are similar for the  _SCLJunkThreshold_ parameter that's available on **Set-OrganizationConfig** and **Set-Mailbox**: the SCL Junk Email folder threshold value that you configure on the mailbox (the value isn't blank) overrides the SCL value on the organization for messages that are sent to the mailbox.
  
    
    

> [!NOTE]
> SCL thresholds on a mailbox are not enforced for messages that are received from distribution groups. 
  
    
    

The SCL threshold setting that's unique to a mailbox is the ability to enable or disable the SCL Junk Email folder threshold. The  _SCLJunkEnabled_ parameter is only available on the **Set-Mailbox** cmdlet, and is described in the following table.
  
    
    


|**Parameter**|**Description**|
|:-----|:-----|
| _SCLJunkEnabled_ <br/> |Enables and disables the SCL Junk Email folder threshold on the mailbox. Valid values are  `$true`,  `$false`, or  `$null` (blank). The default value is blank ( `$null`), which means the SCL Junk Email folder threshold isn't configured on the mailbox, and is controlled by whether the junk email rule is enabled or disabled in the mailbox.  <br/> The default SCL Junk Email folder threshold value is set by the  _SCLJunkThreshold_ parameter on the **Set-OrganizationConfig** cmdlet. You can override this value for the mailbox by using the _SCLJunkThreshold_ parameter on the **Set-Mailbox** cmdlet. <br/> |
   
 **Notes**:
  
    
    

- You can disable the SCL Junk Email folder threshold on a mailbox by disabling the junk email rule in the mailbox. However, disabling the rule also prevents the rule from using the mailbox's safelist collection (Safe Senders list, Safe Recipients list, Blocked Senders list) to move messages to the Junk Email folder, or keep messages out of the Junk Email folder.
    
  
- Even if the junk email rule is disabled in the mailbox, and the SCL Junk Email folder threshold is disabled on the mailbox, the client-side Outlook Junk Email Filter can still move messages to the Junk Email folder.
    
  
For more information, see the  [Configure Exchange antispam settings on mailboxes](configure-exchange-antispam-settings-on-mailboxes.md) topic.
  
    
    

## Monitoring the SCL thresholds

You can use several built-in scripts that are located in the  `%ExchangeInstallPath%Scripts` folder, such as **get-AntispamSCLHistogram.ps1**, for gathering filtering result data. If the data indicates that you need to make immediate adjustments, reconfigure the SCL thresholds. Otherwise, collect data and analyze the spam reporting to determine whether adjustments are required.
  
    
    

