---
title: "Journaling in Exchange Online"
ms.author: markjjo
author: markjjo
manager: scotv
ms.date: 6/23/2018
ms.audience: End User
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 1e7df155-02a3-4daf-94f9-8ea46f041a3a
description: "Find information about journaling in Exchange Online. Learn the difference between journaling and data archiving, how journaling helps with compliance, and more."
---

# Journaling in Exchange Online

Find information about journaling in Exchange Online. Learn the difference between journaling and data archiving, how journaling helps with compliance, and more.
  
Journaling can help your organization respond to legal, regulatory, and organizational compliance requirements by recording inbound and outbound email communications. When planning for messaging retention and compliance, it's important to understand journaling, how it fits in your organization's compliance policies, and how Exchange Online helps you secure journaled messages.
  
## Why journaling is important
<a name="why"> </a>

First, it's important to understand the difference between journaling and a data archiving strategy:
  
- Journaling is the ability to record all communications, including email communications, in an organization for use in the organization's email retention or archival strategy. To meet an increasing number of regulatory and compliance requirements, many organizations must maintain records of communications that occur when employees perform daily business tasks. 
    
- Data archiving refers to backing up the data, removing it from its native environment, and storing it elsewhere, therefore reducing the strain of data storage. You can use Exchange journaling as a tool in your email retention or archival strategy. 
    
Although journaling may not be required by a specific regulation, compliance may be achieved through journaling under certain regulations. For example, corporate officers in some financial sectors may be held liable for the claims made by their employees to their customers. To verify that the claims are accurate, a corporate officer may set up a system where managers review some part of employee-to-client communications regularly. Every quarter, the managers verify compliance and approve their employees' conduct. After all managers report approval to the corporate officer, the corporate officer reports compliance, on behalf of the company, to the regulating body. In this example, email messages might be one type of the employee-to-client communications that managers must review; therefore, journaling can be used to collect all email messages sent by client-facing employees. Other client communication mechanisms may include faxes and telephone conversations, which may also be subject to regulation. The ability to journal all classes of data in an enterprise is a valuable functionality of the IT architecture.
  
The following list shows some of the more well-known U.S. and international regulations where journaling may help form part of your compliance strategies:
  
- Sarbanes-Oxley Act of 2002 (SOX)
    
- Security Exchange Commission Rule 17a-4 (SEC Rule 17 A-4)
    
- National Association of Securities Dealers 3010 &amp; 3110 (NASD 3010 &amp; 3110)
    
- Gramm-Leach-Bliley Act (Financial Modernization Act)
    
- Financial Institution Privacy Protection Act of 2001
    
- Financial Institution Privacy Protection Act of 2003
    
- Health Insurance Portability and Accountability Act of 1996 (HIPAA)
    
- Uniting and Strengthening America by Providing Appropriate Tools Required to Intercept and Obstruct Terrorism Act of 2001 (Patriot Act)
    
- European Union Data Protection Directive (EUDPD)
    
- Japan's Personal Information Protection Act
    
## Journal rules
<a name="rules"> </a>

The following are key aspects of journal rules:
  
- **Journal rule scope** Defines which messages are journaled by the Journaling agent. 
    
- **Journal recipient** Specifies the SMTP address of the recipient you want to journal. 
    
- **Journaling mailbox** Specifies one or more mailboxes used for collecting journal reports. 
    
> [!NOTE]
> In Office 365, the maximum number of journal rules you can create is 10. 
  
### Journal rule scope
<a name="scope"> </a>

You can use a journal rule to journal only internal messages, only external messages, or both. The following list describes these scopes:
  
- **Internal messages only** Journal rules with the scope set to journal internal messages sent between the recipients inside your Exchange organization. 
    
- **External messages only** Journal rules with the scope set to journal external messages sent to recipients or received from senders outside your Exchange organization. 
    
- **All messages** Journal rules with the scope set to journal all messages that pass through your organization regardless of origin or destination. These include messages that may have already been processed by journal rules in the Internal and External scopes. 
    
### Journal recipient
<a name="recip"> </a>

You can implement targeted journaling rules by specifying the SMTP address of the recipient you want to journal. The recipient can be an Exchange mailbox, distribution group, mail user, or contact. These recipients may be subject to regulatory requirements, or they may be involved in legal proceedings where email messages or other communications are collected as evidence. By targeting specific recipients or groups of recipients, you can easily configure a journaling environment that matches your organization's processes and meets regulatory and legal requirements. Targeting only the specific recipients that need to be journaled also minimizes storage and other costs associated with retention of large amounts of data.
  
All messages sent to or from the journaling recipients you specify in a journaling rule are journaled. If you specify a distribution group as the journaling recipient, all messages sent to or from members of the distribution group are journaled. If you don't specify a journaling recipient, all messages sent to or from recipients that match the journal rule scope are journaled.
  
 **Unified Messaging-enabled journal recipients**
  
Many organizations that implement journaling may also use Unified Messaging (UM) to consolidate their email, voice mail, and fax infrastructure. However, you may not want the journaling process to generate journal reports for messages generated by Unified Messaging. In these cases, you can decide whether to journal voice mail messages and missed call notification messages handled by an Exchange server running the Unified Messaging service or to skip such messages. If your organization doesn't require journaling of such messages, you can reduce the amount of hard disk storage space required to store journal reports by skipping these messages.
  
> [!NOTE]
> Messages that contain faxes generated by a the Unified Messaging service are always journaled, even if you disable the journaling of Unified Messaging voice mail and missed call notification messages. 
  
For more information about how to enable or disable voice mail and missed call notification messages, see **Disable or enable journaling of voice mail and missed call notifications**.
  
### Journaling mailbox
<a name="mailbox"> </a>

The journaling mailbox is used to collect journal reports. How you configure the journaling mailbox depends on your organization's policies, regulatory requirements, and legal requirements. You can specify one journaling mailbox to collect messages for all the journal rules configured in the organization, or you can use different journaling mailboxes for different journal rules or sets of journal rules. 
  
> [!IMPORTANT]
> In Office 365, you can't designate an Exchange Online mailbox as a journaling mailbox. You can deliver journal reports to an on-premises archiving system or a third-party archiving service. If you're running an Exchange hybrid deployment with your mailboxes split between on-premises servers and Office 365, you can designate an on-premises mailbox as the journaling mailbox for your Exchange Online and on-premises mailboxes. 
  
Journaling mailboxes contain very sensitive information. You must secure journaling mailboxes because they collect messages that are sent to and from recipients in your organization. These messages may be part of legal proceedings or may be subject to regulatory requirements. Various laws require that messages remain tamper-free before they're submitted to an investigatory authority. We recommend that you create policies that govern who can access the journaling mailboxes in your organization, limiting access to only those individuals who have a direct need to access them. Speak with your legal representatives to make sure that your journaling solution complies with all the laws and regulations that apply to your organization.
  
> [!IMPORTANT]
> If you've configured a journaling rule to send the journal reports to a journaling mailbox that doesn't exist or is an invalid destination, the journal report remains in the transport queue on Microsoft datacenter servers. If this happens, Microsoft datacenter personnel will attempt to contact your organization and ask you to fix the problem so that the journal reports can be successfully delivered to a journaling mailbox. If you haven't resolved the issue after two days of being contacted, Microsoft will disable the problematic journaling rule. 
  
#### Alternate journaling mailbox

When the journaling mailbox is unavailable, you may not want the undeliverable journal reports to collect in mail queues on Mailbox servers. Instead, you can configure an alternate journaling mailbox to store those journal reports. The alternate journaling mailbox receives the journal reports as attachments in the non-delivery reports (NDRs) generated when the journaling mailbox or the server on which it's located refuses delivery of the journal report or becomes unavailable.
  
When the journaling mailbox becomes available again, you can use the **Send Again** feature of OfficeOutlook to submit journal reports for delivery to the journaling mailbox. 
  
When you configure an alternate journaling mailbox, all the journal reports that are rejected or can't be delivered across your entire Exchange organization are delivered to the alternate journaling mailbox. Therefore, it's important to make sure that the alternate journaling mailbox and the Mailbox server where it's located can support many journal reports.
  
> [!CAUTION]
> If you configure an alternate journaling mailbox, you must monitor the mailbox to make sure that it doesn't become unavailable at the same time as the journal mailboxes. If the alternate journaling mailbox also becomes unavailable or rejects journal reports at the same time, the rejected journal reports are lost and can't be retrieved. 
  
Because the alternate journaling mailbox collects all the rejected journal reports for the entire Exchange organization, you must make sure that this doesn't violate any laws or regulations that apply to your organization. If laws or regulations prohibit your organization from allowing journal reports sent to different journaling mailboxes from being stored in the same alternate journaling mailbox, you may be unable to configure an alternate journaling mailbox. Discuss this with your legal representatives to determine whether you can use an alternate journaling mailbox.
  
When you configure an alternate journaling mailbox, you should use the same criteria that you used when you configured the journaling mailbox.
  
> [!IMPORTANT]
> The alternate journaling mailbox should be treated as a special dedicated mailbox. Any messages addressed directly to the alternate journaling mailbox aren't journaled. 
  
## Journal reports
<a name="report"> </a>

A journal report is the message that the Journaling agent generates when a message matches a journal rule and is to be submitted to the journaling mailbox. The original message that matches the journal rule is included unaltered as an attachment to the journal report. The body of a journal report contains information from the original message such as the sender email address, message subject, message-ID, and recipient email addresses. This is also referred to as envelope journaling, and is the only journaling method supported by Office 365. 
  
### Journal reports and IRM-protected messages

When implementing journaling, you must consider journaling reports and IRM-protected messages. IRM-protected messages will affect the search and discovery capabilities of third-party archiving systems that don't have RMS support built-in. In Office 365, you can configure Journal Report Decryption to save a clear-text copy of the message in a journal report. 
  
## Troubleshooting
<a name="trouble"> </a>

Having problems? Ask for help in the Exchange forums. Visit the forums at [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612),[Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351).. If you're having trouble with the **JournalingReportDNRTo** mailbox, see [Transport and Mailbox Rules in Exchange Online don't work as expected](https://go.microsoft.com/fwlink/p/?LinkId=331674).
  

