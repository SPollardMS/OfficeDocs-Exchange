---
title: Learn more about running a non-owner mailbox access report
ms.prod: EXCHANGE
ms.assetid: 18f52b7e-cd60-4a2f-b8a3-0c08747635bb
---


# Learn more about running a non-owner mailbox access report

The Non-Owner Mailbox Access Report in the Exchange Administration Center (EAC) lists the mailboxes that have been accessed by someone other than the person who owns the mailbox. When a mailbox is accessed by a non-owner, Microsoft Exchange logs information about this action in a mailbox audit log that is stored as an email message in a hidden folder in the mailbox being audited. Entries in the mailbox audit log are retained for 90 days by default. Entries from this log are displayed as search results and include a list of mailboxes accessed by a non-owner, who accessed the mailbox and when, the actions performed by the non-owner, and whether the action was successful. You have to enable mailbox audit logging for each mailbox that you want to run a non-owner mailbox access report for. If mailbox audit logging isn't enabled, you won't get any results when you run a report. By default, Exchange runs the report for non-owner access to any mailboxes in the organization in the past two weeks.
  
    
    

Why would you need to know about non-owner mailbox access?
- You want to enforce compliance and privacy regulations by monitoring actions performed on mailbox data by non-owners.
    
  
- You need to be prepared to provide information relevant to legal cases, such as showing the state of mailbox data at a given time, who sent email from a mailbox, and if a particular person viewed mailbox data.
    
  
- You need to identify unauthorized access to mailbox data by users inside and outside your organization.
    
  
- Cloud-based organizations want to ensure that their mailbox data isn't being accessed by Microsoft datacenter personnel or delegated administrators.
    
  
What are the types of non-owner access? When you enable mailbox audit logging for a mailbox, Exchange logs specific actions by non-owners, including both administrators and delegated users who have been assigned permissions to a mailbox. You can also narrow the search to users inside or outside your organization.
## For more information

 [Run a non-owner mailbox access report](run-a-non-owner-mailbox-access-report.md)
  
    
    
 [Export Mailbox Audit Logs](http://technet.microsoft.com/library/b458a95a-3321-4647-8884-cf97f8e7186a.aspx)
  
    
    

