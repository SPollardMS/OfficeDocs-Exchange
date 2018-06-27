---
title: "Troubleshoot Office 365 mail flow"
ms.author: tirich
author: tirich
manager: scotv
ms.date: 12/9/2016
ms.audience: ITPro
ms.topic: article
ms.service: exchange-online
localization_priority: Normal
ms.assetid: ccb62ce1-a822-4859-a0db-3d546c5c1f50
description: "Can't send or receive email? Office 365 for business has several ways that can troubleshoot the issue as an admin. We recommend using the automated solutions because they are typically easier and faster than manual troubleshooting."
---

# Troubleshoot Office 365 mail flow

Can't send or receive email? Office 365 for business has several ways that can troubleshoot the issue as an admin. We recommend using the automated solutions because they are typically easier and faster than manual troubleshooting.
  
## The automated mail flow troubleshooter can help in these scenarios

Problems with mail delivery can be a very frustrating for both the user and the administrator. Whether your mailboxes are hosted on-premises, in Office 365, or a combination of both, mail flow issues can occur from time to time. Luckily, the [mail flow troubleshooter](https://aka.ms/fixemail) (requires global admin sign-in) can help you troubleshoot some of these issues if they happened in the past 7 days. For example, if you have problems sending and receiving mail or if mail is delayed in the following scenarios: 
  
- The sender's mailbox is hosted on Office 365, and the recipient's mailbox is outside your organization.
    
- The sender's mailbox is outside your organization, and the recipient's mailbox is hosted in Office 365.
    
- The sender's and recipient's mailboxes are both located in Office 365.
    
- The sender's mailbox is hosted in Office 365, and the recipient's mailbox is located on an on-premise Exchange server, and both mailboxes are in the same organization.
    
- The sender's mailbox is hosted on an on-premise Exchange Server server and the recipient's mailbox is hosted in Office 365, and both mailboxes are in the same organization.
    
For instructions about using the mail flow troubleshooter and other troubleshooting options, see [Find and fix email delivery issues as an Office 365 for business admin](https://support.office.com/en-us/article/Find-and-fix-email-delivery-issues-as-an-Office-365-for-business-admin-e7758b99-1896-41db-bf39-51e2dba21de6).
  
The following video demonstrates several of the [automated mail flow troubleshooting options for Office 365 admins](https://support.office.com/en-us/article/Find-and-fix-email-delivery-issues-as-an-Office-365-for-business-admin-e7758b99-1896-41db-bf39-51e2dba21de6).
  
> [!VIDEO https://www.microsoft.com/videoplayer/embed/8b10af9a-455c-410a-8c17-24d5e5be098a?autoplay=false]
  
## Troubleshoot mail flow caused by connectors

To validate and troubleshoot mail flow from Office 365 to your organization's email server (also called on-premises server), validate your connectors. You can set up and validate connectors on the **connectors** page in the Exchange admin center (EAC). The built-in validation tests that your mail flow from Office 365 reaches: 
  
- Your organization's email server
    
- A partner organization.
    
For more information, see [Validate connectors in Office 365](use-connectors-to-configure-mail-flow/validate-connectors.md).
  
## Troubleshoot mail flow issues caused by incorrect SPF records or MX records

[Troubleshooting: Best practices for SPF in Office 365](http://technet.microsoft.com/library/3aff33c5-1416-4867-a23b-e0c0c5b4d2be.aspx#SPFTroubleshoot) gives tips on how to fix several SPF record errors. The beginning of that article also provides an explanation of what SPF records are and how Office 365 uses them to prevent spoofing. 
  
Mail flow issues can also happen when your MX record is not setup correctly. To verify your MX record, see [Find and fix issues after adding your domain or DNS records in Office 365](https://go.microsoft.com/fwlink/?LinkId=624017).
  
## For more information

[Mail flow best practices for Exchange Online and Office 365 (overview)](mail-flow-best-practices.md)
  
[Mail Flow in EOP](http://technet.microsoft.com/library/e109077e-cc85-4c19-ae40-d218ac7d0548.aspx)
  

