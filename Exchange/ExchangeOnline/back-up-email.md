---
title: "Backing up email in Exchange Online"
ms.author: kwekua
author: kwekua
manager: scotv
ms.date: 6/25/2018
ms.audience: ITPro
ms.topic: article
ms.service: exchange-online
localization_priority: Normal
ms.assetid: 94d2f62e-5d43-4200-b7ce-33b1f41f1d59
description: "One of the questions we often hear isHow does Exchange Online back up my data?You may be asking this because you're concerned about how to recover your data if there is a failure. Or you may be wondering how to recover your data if it gets accidentally deleted. This topic answers these questions."
---

# Backing up email in Exchange Online

One of the questions we often hear is "How does Exchange Online back up my data?" You may be asking this because you're concerned about how to recover your data if there is a failure. Or you may be wondering how to recover your data if it gets accidentally deleted. This topic answers these questions.
  
## Backing up data in Exchange Online

Lots of things can disrupt service availability, such as hardware failure, natural disasters, or human error. To ensure that your data is always available and that services continue, even when unexpected events occur, Exchange Online uses the same technologies found in Exchange 2013. For example, Exchange Online uses the Exchange 2013 feature known as Database Availability Groups to replicate Exchange Online mailboxes to multiple databases in separate Microsoft datacenters. As a result, you can readily access up-to-date mailbox data in the event of a failure that affects one of the database copies. In addition to having multiple copies of each mailbox database, the different datacenters back up data for one another. If one fails, the affected data are transferred to another datacenter with limited service interruption and users experience seamless connectivity.
  
> [!NOTE]
> You can obtain the most current information related to a service interrupting event by logging into the Service Health Dashboard. For more information, see [View the status of your services](https://go.microsoft.com/fwlink/?LinkId=786661). 
  
### What happens if users accidently delete data from their mailboxes?

Exchange Online service provides several options for Deleted item recovery, which include manual recovery from Deleted Items, recovery from Recoverable Items, Single Items recovery, and retention policies and tags. Archiving and litigation hold are also available within the appropriate licensing to complement the needs of preserving data.
  
- **Deleted item retention** Users can restore email items that have been deleted from any email folder. When a user deletes an item, it is kept in the Deletions subfolder of the Recoverable Items folder. Items remain in this folder until the user manually removes them, or until they are automatically removed by retention policies. For more information about recoverable items, see [Recoverable Items folder](http://technet.microsoft.com/library/efc48fb4-2ed8-4d05-93af-f3505fbc389d.aspx)
    
- **Single item recovery** Email recovery has improved in Exchange Online to allow users to recover single items without having to restore mailbox databases. When the Managed Folder Assistant processes the Recoverable Items folder for a mailbox that has single item recovery enabled, any item in the Purges subfolder isn't purged if the deleted item retention period hasn't elapsed for that item. 
    
- **Retention tags and retention policies** These settings specify how long a message remains in a mailbox and the action to be taken when the message reaches the specified retention age. When a message reaches its retention age, it's moved to the user's In-Place Archive or deleted. For more information about Retention tags and policies, see [Retention tags and retention policies](security-and-compliance/messaging-records-management/retention-tags-and-policies.md).
    
> [!IMPORTANT]
>  With all the previously mentioned options for Deleted item recovery, note that point in time restoration of mailbox items is out of the scope of the Exchange service. However, Exchange Online offers extensive retention and recovery support for an organization's email infrastructure, and your mailbox data is available when you need it, no matter what happens. >  You can find more details about additional options in the following topics: > [High Availability and Business Continuity](http://technet.microsoft.com/library/7b03465e-3b9c-4500-8956-a83377f4c2c3.aspx)> [Exchange Online Service Description](http://technet.microsoft.com/library/7a83da3c-3b6d-4f86-ad4d-6104707cd0ec.aspx)> [Create or remove an In-Place Hold](security-and-compliance/create-or-remove-in-place-holds.md)> [Place a mailbox on Litigation Hold](http://technet.microsoft.com/library/adee4621-3626-4aec-aa53-00b35ff0d0b0.aspx)> [Manage inactive mailboxes in Exchange Online](http://technet.microsoft.com/library/c60e9ae7-dd02-4c5f-9f5d-7626a9101094.aspx)
  
## How do users backup Outlook data?

Users can export their Outlook data to Outlook on another computer or back up that data by following the steps in the [Export or backup email, contacts, and calendar to an Outlook .pst file](https://go.microsoft.com/fwlink/p/?LinkId=325560) topic. Unfortunately, Outlook Web App users cannot back up their data themselves. 
  
To learn how to restore deleted items in Outlook, see [Recover deleted items in Outlook](https://support.office.com/en-us/article/Recover-deleted-items-in-Outlook-for-Windows-49e81f3c-c8f4-4426-a0b9-c0fd751d48ce?CorrelationId=a8a3b0dd-599f-44de-bbf8-70ae117aab62&amp;ui=en-US&amp;rs=en-US&amp;ad=US).
  
To learn how to restore deleted items in Outlook Web App, see [Recover deleted items or email in Outlook Web App](https://support.office.com/en-us/article/Recover-deleted-items-or-email-in-Outlook-Web-App-c3d8fc15-eeef-4f1c-81df-e27964b7edd4?ui=en-US&amp;rs=en-US&amp;ad=US).
  
## Backing up Exchange 2016 on-premises

Read [Using Windows Server Backup to back up and restore Exchange data](https://go.microsoft.com/fwlink/?LinkId=816871) for more info about backing up Exchange Server 2016. 
  
## Offboard a user from Office 365

For more info what to do when a user in your organization leaves, check out [Offboard a user from Office 365](https://go.microsoft.com/fwlink/?LinkId=816871). This topic discusses the steps you should take and how to secure your data after an employee leaves your organization.
  

