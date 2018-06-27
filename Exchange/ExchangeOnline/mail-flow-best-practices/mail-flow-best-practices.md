---
title: "Mail flow best practices for Exchange Online and Office 365 (overview)"
ms.author: chrisda
author: chrisda
manager: serdars
ms.date: 6/23/2018
ms.audience: ITPro
ms.topic: article
ms.service: exchange-online
localization_priority: Normal
ms.assetid: 0e6cd9d5-ad3e-418a-8ea9-3bf33332c491
description: "Use Microsoft Exchange Online and Office 365 to manage mail flow. Find out how, and get tips and best practices for setting up and managing your email."
---

# Mail flow best practices for Exchange Online and Office 365 (overview)

Use Microsoft Exchange Online and Office 365 to manage mail flow. Find out how, and get tips and best practices for setting up and managing your email.
  
 **This article is intended for IT Pros. Want something else?**
  
 **Try [Set up Office 365 for business](https://go.microsoft.com/fwlink/p/?LinkID=522378) or [Deploy Office 365 Enterprise for your organization](https://go.microsoft.com/fwlink/p/?LinkID=703951)**. 
  
Office 365 gives you flexibility in determining the best arrangement for how email is delivered to your organization's mailboxes. The path email takes from the Internet to a mailbox and vice versa is called mail flow. Most organizations want Office 365 to manage all their mailboxes and filtering, and some organizations need more complex mail flow setups to make sure that they comply with specific regulatory or business needs. If you're part of a small business or simply an organization that wants Office 365 to manage all your mailboxes and mail flow, we recommend following the steps in [Set up Office 365 for business](https://go.microsoft.com/fwlink/p/?LinkID=522378). That article provides a complete checklist for setting up Office 365 services and programs, including how to set up your mail flow and email clients.
  
For information about how your email is protected with EOP, see [Exchange Online Protection Overview](http://technet.microsoft.com/library/1270a65f-ddc3-4430-b500-4d3a481efb1e.aspx).
  
> [!TIP]
> Are you new to Office 365 mail flow? Check out the [Introduction to the basics of Office 365 mail flow](http://technet.microsoft.com/library/840fd26f-5409-4325-8543-7cdaa2f8bb25.aspx) topic. We especially recommend reading the part about SPF records because customers often list the wrong values in their SPF record, which can cause mail flow problems. 
  
Office 365 mail flow covers the following scenarios:
  
|**Mail flow setup**|**Your organization's scenario**|**Complexity**|
|:-----|:-----|:-----|
|[Manage all mailboxes and mail flow using Office 365](manage-mailboxes-with-office-365.md) <br/> |**[Manage all mailboxes and mail flow using Office 365 (recommended).](manage-mailboxes-with-office-365.md#BKMK_HostedMailFlow)** <br/> I'm a new Office 365 customer, and all my users' mailboxes are in Office 365. I want to use all filtering solutions offered by Office 365.  <br/> **[Manage all mailboxes and mail flow using Office 365 (recommended).](manage-mailboxes-with-office-365.md#BKMK_HostedMailFlow)** <br/> I'm a new Office 365 customer. I have an existing email service but plan to move all the existing users' mailboxes to the cloud at once. I want to use all filtering solutions offered by Office 365.  <br/> |Simple  <br/> |
|[Manage mail flow using a third-party cloud service with Office 365](manage-mail-flow-using-third-party-cloud.md) <br/> |**[Scenario 1 - MX record points to third-party spam filtering](manage-mail-flow-using-third-party-cloud.md#Scenario1)** <br/>  I plan to have Office 365 host all of my organization's mailboxes. My organization uses (or plans to use) a third-party (mail services) cloud solution for filtering spam and malware. All email sent from the Internet must be filtered by this third-party cloud service.  <br/> **[Scenario 2 (unsupported) - MX record points to third-party solution without spam filtering](manage-mail-flow-using-third-party-cloud.md#Scenario2)** <br/>  I plan to have Office 365 host all my organization's mailboxes. My organization needs to send all email to a third-party service, such as archiving or auditing. However, the third-party service doesn't provide a spam filtering solution.  <br/> |Complex  <br/> |
|[Manage mail flow with mailboxes in multiple locations (Office 365 and on-prem)](manage-mail-flow-for-multiple-locations.md) <br/> **Important**: In the near future, Office 365 will reject email from unknown senders that are relayed from on-premises servers. This means that if the sender or recipient domain of a message doesn't belong to your organization, Office 365 will reject the message unless you have created a connector to allow this behavior. This change will help prevent unauthorized parties from using your organization to send spam or malware through Office 365.  <br/> This change potentially affects your mail flow if you use any scenario in this section. Each scenario has best practices to ensure that your mail flow continues uninterrupted.  <br/> |**[Scenario 1: MX record points to Office 365 and Office 365 filters all messages](manage-mail-flow-for-multiple-locations.md#scenario1)** <br/>  I'm migrating my mailboxes to Office 365, and I want to keep some mailboxes on my organization's mail server (on-premises server). I want to use Office 365 as my spam filtering solution and would like to send my messages from my on-premises server to the Internet via Office 365. Office 365 sends and receives all messages.  <br/> **[Scenario 2: MX record points to Office 365 and mail is filtered on-premises](manage-mail-flow-for-multiple-locations.md#scenario2)** <br/>  I'm migrating my mailboxes to Office 365, and I want to keep some mailboxes on my organization's mail server (on-premises server). I want to use the filtering and compliance solutions that are already in my on-premises environment. And all messages coming from the Internet to my cloud mailboxes or messages sent to the Internet from my cloud mailboxes need to route through my on-premises servers.  <br/> **[Scenario 3: MX record points to my on-premises servers](manage-mail-flow-for-multiple-locations.md#scenario3)** <br/>  I'm migrating my mailboxes to Office 365, and I want to keep some mailboxes on my organization's mail server (on-premises server). I want to use the filtering and compliance solutions that are already in my on-premises email environment. All messages coming from the Internet to my cloud mailboxes or messages sent to the Internet from cloud mailboxes must route through my on-premises servers. And I need to point my domain's MX record to my on-premises server.  <br/> **[Scenario 4: MX record points to my on-premises server, which filters and provides compliance solutions for your messages. Your on-premises server needs to relay messages to the internet through Office 365.](manage-mail-flow-for-multiple-locations.md#scenario4)** <br/> I'm migrating my mailboxes to Office 365, and I want to keep some mailboxes on my organization's mail server (on-premises server). I want to use the filtering and compliance solutions that are already in my on-premises email environment. All messages sent from my on-premises servers must relay through Office 365 to the Internet. And I need to point my domain's MX record to my on-premises server.  <br/> |Very complex  <br/> |
|[Manage mail flow using a third-party cloud service with mailboxes on Office 365 and on-prem](manage-mail-flow-on-office-365-and-on-prem.md) <br/> |**Scenario** <br/> I'm migrating my mailboxes to Office 365, and I want to keep some mailboxes on my organization's mail server (on-premises server). I want to use a third-party cloud service to filter spam from the Internet. My messages to the Internet need to route through Office 365 to protect my on-premises servers' IP addresses from being added to external block lists.  <br/> |Most complex  <br/> |
|Send emails from a multifunction printer/scanner/fax/application through Office 365  <br/> For details about this scenario, see [How to set up a multifunction device or application to send email using Office 365](http://technet.microsoft.com/library/2c0012a9-7e71-40cd-a516-1b26117bf491.aspx).  <br/> |**Scenario** <br/> All my organization's mailboxes are hosted in Office 365, but I have a multifunction printer, scanner, fax machine, or an application that needs to send email.  <br/> |Complex  <br/> |
|Using Exchange Online Protection (EOP) standalone  <br/> For details about this scenario, see [Mail Flow in EOP](http://technet.microsoft.com/library/e109077e-cc85-4c19-ae40-d218ac7d0548.aspx) and [How do Office 365 connectors work with my own email servers (also called "on-premises servers")?](use-connectors-to-configure-mail-flow/set-up-connectors-to-route-mail.md#HowdoconnectorsinEOP) <br/> |**Scenario** <br/> I have my own email servers (on-premises servers), and I subscribe to EOP for email protection services only.  <br/> |Simple  <br/> |
   
For information about migrating your email to Microsoft Exchange Online, see [Ways to migrate multiple email accounts to Office 365](https://go.microsoft.com/fwlink/p/?LinkID=524030). 
  
## Introduction to the basics of Office 365 mail flow
<a name="BKMK_IntroductionToMailFlow"> </a>

Office 365 uses domains, like contoso.com, to route email messages. When you set up email in Office 365, you typically switch from the default domain that you got when you first signed up for Office 365 (the domain ending with .onmicrosoft.com) to your organization's domain. Domain names, like contoso.com, are managed by using a worldwide system of domain registrars (for example, GoDaddy, HostGator, or Moniker) and databases called the Domain Name System (DNS). DNS provides a mapping between human-readable computer hostnames and the IP addresses used by networking equipment. If you're new to DNS, we recommend that you read [DNS basics](http://go.microsoft.com/fwlink/p/?LinkID=528444). The following video provides you with a quick overview of some of the most important concepts about what DNS is and how it works.
  
> [!VIDEO https://www.microsoft.com/videoplayer/embed/c005f2a4-90ad-46fe-b1ab-90f41f2a9d53?autoplay=false]
  
### Understanding how DNS records control mail flow

In Office 365 mail flow, two DNS records are particularly important: MX records and SPF records.
  
 **MX (mail exchanger) records** provide an easy way for mail servers to know where to send email. You can think of the MX record as a type of postal address. If you want Office 365 to receive all email addressed to anyone@contoso.com, the MX record for contoso.com should point to Office 365, and it will look like the following example: 
  
```
Hostname: contoso-com.mail.protection.outlook.com
Priority: 0
TTL: 1 hour

```

 **SPF (sender policy framework) records** are a specially formatted TXT record in DNS. SPF records make sure that only the organization that owns a domain is actually sending email from that domain. SPF is basically a security measure to make sure someone doesn't impersonate another organization. (This impersonation is often called spoofing.) As a domain owner, you can use an SPF record to publish a list of IP addresses or subnets that are authorized to send email on your organization's behalf. This can be helpful if you want to send email from multiple servers or services with different IP addresses. The SPF record for an organization's domain that uses Office 365 to send all their mail should look like the following example:
  
```
v=spf1 include:spf.protection.outlook.com -all
```

> [!IMPORTANT]
> You can only have one SPF record per domain. Having multiple SPF records will invalidate all SPF records and cause mail flow problems. 
  
The SPF record configuration in the previous example tells the recipient email servers that email sent from Office 365's IP addresses are authorized for the domain. Because most modern email servers look up a domain's SPF record before they accept any email from it, it's important to set up a valid SPF record in DNS when you first set up mail flow.
  
### How MX records affect spam filtering

For the best mail flow experience-especially for spam filtering—we recommend pointing the MX record for your organization's domain to Office 365. Spam scanning is the initial connection point to the Office 365 service. Who is sending the message, the IP address of the server that originally sent the message, and the behavior of the connecting mail server, all help determine whether a message is legitimate or spam. If your domain's MX record doesn't point to Office 365, the spam filters won't be as effective. If your MX record doesn't point to Office 365, there will be some valid messages that the service misclassifies as spam and some spam messages that the service misclassifies as legitimate email.
  
With that said, there are legitimate business scenarios that require your domain's MX record to point to somewhere other than Office 365. For example, email destined for your organization might need to initially arrive at another destination (such as a third-party archiving solution), then route through Office 365, and then be delivered to mailboxes on your organization's mail server. This setup might provide the best solution to meet your business requirements.
  
Whatever your needs, this guide will help you understand how your MX records, SPF records, and, potentially, connectors need to be set up.
  
## For more information
<a name="BKMK_IntroductionToMailFlow"> </a>

The following are additional topics related to mail flow in Exchange Online:
  
[Test mail flow by validating your Office 365 connectors](test-mail-flow.md)
  
[Troubleshoot Office 365 mail flow](troubleshoot-mail-flow.md)
  
[Use Directory Based Edge Blocking to reject messages sent to invalid recipients](use-directory-based-edge-blocking.md)
  
[Manage accepted domains in Exchange Online](manage-accepted-domains/manage-accepted-domains.md)
  
[Remote domains in Exchange Online](remote-domains/remote-domains.md)
  
[Message format and transmission in Exchange Online](message-format-and-transmission.md)
  
[Configure the external postmaster address in Exchange Online](configure-external-postmaster-address.md)
  
[How to set up a multifunction device or application to send email using Office 365](http://technet.microsoft.com/library/2c0012a9-7e71-40cd-a516-1b26117bf491.aspx)
  

