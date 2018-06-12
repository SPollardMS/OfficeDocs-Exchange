---
title: "Release notes for Exchange 2016"
ms.author: dstrome
author: dstrome
manager: serdars
ms.date: 6/8/2018
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 1879fd5e-3d63-4264-9cc2-9c050c6ab3c5
description: "Welcome to Microsoft Exchange Server 2016! This topic contains important information that you need to know to successfully deploy Exchange 2016. Please read this topic completely before beginning your deployment."
---

# Release notes for Exchange 2016

> [!TIP]
> Coming from the Exchange Deployment Assistant? Click [Release notes for Exchange 2013](https://technet.microsoft.com/library/jj150489%28v=exchg.150%29.aspx). 
  
Welcome to Microsoft Exchange Server 2016! This topic contains important information that you need to know to successfully deploy Exchange 2016. Please read this topic completely before beginning your deployment.
  
## Setup
<a name="Setup"> </a>

- **Installing Exchange using Delegate Admin permissions causes Setup to fail**: When a user who's a member of only the Delegated Setup role group attempts to install Exchange on a pre-provisioned server, Setup will fail. This happens because the Delegated Setup group lacks the permissions required to create and configure certain objects in Active Directory.
    
    To work around this issue, do one of the following:
    
  - Add the user installing Exchange to the Domain Admins Active Directory security group.
    
  - Install Exchange using a user that's a member of the Organization Management role group.
    
## Mailbox
<a name="Mailbox"> </a>

- **Moving mailboxes from earlier versions of Exchange to Exchange 2016 CU5 or later can fail**: When you attempt to move a mailbox from an earlier version of Exchange to Exchange CU5 or later using a migration batch request, the move might fail. This can happen if the migration system mailbox isn't located on an Exchange 2016 server with CU5 or later installed.
    
    Before you can move mailboxes to Exchange 2016 CU5 or later using a migration batch request, you need to move the migration mailbox to an Exchange server running CU5 or later using the following steps.
    
1. Open the Exchange Management Shell on your Exchange 2016 Mailbox server.
    
2. Run the following command to get a list of mailbox databases that are located on your Exchange 2016 servers. Copy the name of the mailbox database where you want to move the migration mailbox to the clipboard.
    
  ```
  Get-MailboxDatabase | Where {$_.AdminDisplayVersion -Like "*15.1*"} | Format-Table Name, ServerName
  ```

3. Run the following command to move the migration mailbox to your Exchange 2016 server. Paste the mailbox database name you copied in the previous step after  _TargetDatabase_.
    
  ```
  New-MoveRequest "Migration.8f3e7716-2011-43e4-96b1-aba62d229136" -TargetDatabase "<mailbox database name>"
  ```

- **Mailbox servers running different versions of Exchange can be added to the same database availability group**: The **Add-DatabaseAvailabilityGroupServer** cmdlet and the Exchange admin center incorrectly allow an Exchange 2013 server to be added to an Exchange 2016-based database availability group (DAG), and vice versa. Exchange supports adding only Mailbox servers running the same version (Exchange 2013 versus Exchange 2016, for example) to a DAG. Additionally, the Exchange admin center displays both Exchange 2013 and Exchange 2016 servers in the list of servers available to add to a DAG. This could allow an administrator to inadvertently add a server running an incompatible version of Exchange to a DAG (for example, adding an Exchange 2013 server to an Exchange 2016-based DAG). 
    
    There is currently no workaround for this issue. Administrators must be diligent when adding a Mailbox server to a DAG. Add only Exchange 2013 servers to Exchange 2013-based DAGs, and only Exchange 2016 servers to Exchange 2016-based DAGs. You can differentiate each version of Exchange by looking at the **Version** column in the list of servers in the Exchange admin center. The following are the server versions for Exchange 2013 and Exchange 2016: 
    
  - **Exchange 2013** 15.0 (Build xxx.xx) 
    
  - **Exchange 2016** 15.1 (Build xxx.xx) 
    
- **Can't connect to archive mailbox when using MAPI over HTTP**: In Exchange 2016, MAPI over HTTP can be enabled per-mailbox. An issue exists that prevents users from accessing their archive mailbox, if one is configured, when the following are true:
    
  - MAPI over HTTP is enabled on the user's mailbox.
    
  - MAPI over HTTP is disabled at the organization level.
    
    When these conditions are true, the user won't be able to open their archive mailbox and they'll get the error **The set of folders cannot be opened. The attempt to log on to Microsoft Exchange has failed.**
    
    To work around the issue, do one of the following
    
  - Open the archive mailbox using Outlook on the web.
    
  - Disable MAPI over HTTP on the mailbox by running the following command.
    
  ```
  Set-CasMailbox <email address> -MapiHttpEnabled $False
  ```

- **Notifications Broker service stops after 30 seconds** When you start your Exchange server, you might notice the **Notifications Broker** service start and then stop after approximately 30 seconds. If you attempt to start the service manually, it will successfully start and then stop, again after approximately 30 seconds. No errors or warnings are included in the Event log. 
    
    This behavior is expected in on-premises deployments of Exchange 2016. The **Notifications Broker** service performs a configuration check on each time the server starts. If there is nothing for the **Notifications Broker** service to do, it stops automatically until the next time the server is restarted. 
    
## Mail flow
<a name="MailFlow"> </a>

- **Edge Transport servers can reject mail sent to valid recipients** Exchange 2016 Edge Transport servers may reject messages sent to valid internal recipients when the following are true: 
    
  - Exchange 2016 Cumulative Update 1 (CU1) is installed on the server.
    
  - Recipient validation is enabled on the server.
    
    When an Edge Transport rejects a message because of this issue, the sender will receive a non-delivery report (NDR) with the status code **5.1.10**, and the error **Recipient not found by SMTP address lookup**. The recipient won't receive the message.
    
    To work around the issue, do **one** of the following: 
    
  - Disable recipient validation on the affected Edge Transport server(s) by running the following command.
    
  ```
  Set-RecipientFilterConfig -RecipientValidationEnabled $False
  ```

  - Disable the recipient validation cache on the affected Edge Transport server(s) by running the following command.
    
  ```
  Get-TransportService | Set-TransportService -RecipientValidationCacheEnabled $False
  ```

    > [!CAUTION]
    > Disabling the recipient validation cache causes Exchange to verify that recipients on inbound messages are valid by querying the local instance of Active Directory Lightweight Directory Services. This can significantly increase the resources Exchange needs to process messages. Before you disable the recipient validation cache, verify that your server has sufficient capacity to handle the additional demand. 
  
  - Configure your firewall or external mail exchanger (MX) DNS record to send mail to an Edge Transport server that doesn't have Exchange 2016 Cumulative Update 1 installed. You might need to configure your firewall to allow TCP port 25 to connect to the new Internet-facing server.
    
  - Configure your firewall or external MX DNS record to send mail to an Exchange 2016 Mailbox server. You might need to configure your firewall to allow TCP port 25 to connect to the new Internet-facing server.
    

