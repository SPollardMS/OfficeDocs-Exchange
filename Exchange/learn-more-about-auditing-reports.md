---
title: Learn more about auditing reports
ms.prod: EXCHANGE
ms.assetid: a9aa9f58-63c9-43cd-89a8-13c22713e8c3
---


# Learn more about auditing reports

Use the **Auditing** page in the Exchange Administration Center (EAC) to troubleshoot configuration issues by tracking specific changes made by administrators and to help you meet regulatory, compliance, and litigation requirements. Microsoft Exchange provides two types of audit logging:
  
    
    


- Administrator audit logging records any action an administrator performs that is based on an Exchange Management Shell cmdlet. This can help you troubleshoot configuration issues or identify the cause of security-related or compliance-related problems. These actions are saved to the administrator audit log.
    
  
- Mailbox audit logging records when a mailbox is accessed by someone other than the person who owns the mailbox. This can help you determine who has accessed a mailbox and what they've done. These entries are saved to the mailbox audit log.
    
    > [!IMPORTANT]
      > You have to enable mailbox audit logging for each mailbox. If mailbox audit logging isn't enabled for a mailbox, entries for that mailbox won't be logged in the mailbox audit log. 

You can search for and export entries from the administrator and mailbox audit logs on the **Auditing** page. When you export your search results, Exchange saves them in an XML file and attaches it to an email message.
  
    
    

You can also run the following reports on the **Auditing** page. When you run a report, the results are displayed in the details pane.
- **Non-owner mailbox access report** Use this report to find mailboxes that have been accessed by someone other than the person who owns the mailbox. If you have a cloud-based Exchange organization, you can also use this report to determine if mailbox data in your cloud-based organization is being accessed by Microsoft datacenter personnel.
    
  
- **Administrator role group report** Use this report to search for changes made to administrator role groups.
    
  
- **In-place discovery and hold report** Use this report to find mailboxes that have been put on, or removed from, In-Place Hold.
    
  
- **Per-mailbox litigation hold report** Use this report to find mailboxes that have been put on, or removed from, litigation hold.
    
  

## For more information

 [Auditing Reports](http://technet.microsoft.com/library/2b3e1529-1677-4564-be0b-ce22757ddc0d.aspx)
  
    
    
 [Auditing Reports in EOP](http://technet.microsoft.com/library/003d7a74-3e16-4453-ae0c-9dbae51f66d1.aspx)
  
    
    
 [Run an Administrator Role Group Report in EOP](http://technet.microsoft.com/library/23b47b57-0eec-46a3-a03b-366ea014ab31.aspx)
  
    
    
 [View the Administrator Audit Log](http://technet.microsoft.com/library/5c62072a-556d-4fea-9973-d668c6b9fd57.aspx)
  
    
    

