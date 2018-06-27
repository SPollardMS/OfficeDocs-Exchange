---
title: "Clients and mobile devices permissions"
ms.author: dmaguire
author: msdmaguire
manager: serdars
ms.date: 6/7/2018
ms.audience: ITPro
ms.topic: reference
ms.prod: exchange-server-itpro
localization_priority: Normal
ms.assetid: 57eca42a-5a7f-4c65-89f0-7a84f2dbea19
description: "Summary: Learn about permissions that are required to perform tasks for clients and mobile devices in Exchange Server 2016."
---

# Clients and mobile devices permissions

 **Summary**: Learn about permissions that are required to perform tasks for clients and mobile devices in Exchange Server 2016.
  
The permissions required to perform tasks for clients and mobile devices vary depending on the procedure being performed or the cmdlet you want to run. For more information about client and mobile device features, see [Clients and mobile](../../clients/clients.md).
  
To find out what permissions you need to perform the procedure or run the cmdlet, do the following:
  
1. In the table below, find the feature that is most related to the procedure you want to perform or the cmdlet you want to run.
    
2. Next, look at the permissions required for the feature. You must be assigned one of those role groups, an equivalent custom role group, or an equivalent management role. You can also click on a role group to see its management roles. If a feature lists more than one role group, you only need to be assigned one of the role groups to use the feature. For more information about role groups and management roles, see **Understanding Role Based Access Control**.
    
3. Now, run the **Get-ManagementRoleAssignment** cmdlet to look at the role groups or management roles assigned to you to see if you have the permissions that are necessary to manage the feature.
    
    > [!NOTE]
    > You must be assigned the Role Management management role to run the **Get-ManagementRoleAssignment** cmdlet. If you don't have permissions to run the **Get-ManagementRoleAssignment** cmdlet, ask your Exchange administrator to retrieve the role groups or management roles assigned to you.
  
If you want to delegate the ability to manage a feature to another user, see **Delegate a Management Role**.
  
> [!NOTE]
> Some features may require that you have local administrator permissions on the server you want to manage. To manage these features, you must be a member of the Local Administrators group on that server.
  
## Client Access service permissions
<a name="ClientAccessServer"> </a>

You can configure any of the following features for the Client Access service.
  
Users who are assigned the View-Only Management role group can view the configuration of the features in the following table. For more information, see **View Only Organization Management**.
  
|**Feature**|**Permissions required**|
|:-----|:-----|
|Client Access service array settings  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> [Server Management](http://technet.microsoft.com/library/30cbc4de-adb3-42e8-922f-7661095bdb8c.aspx) <br/> |
|Client Access service settings  <br/> |[Server Management](http://technet.microsoft.com/library/30cbc4de-adb3-42e8-922f-7661095bdb8c.aspx) <br/> |
|Client Access service email channel settings  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> [Server Management](http://technet.microsoft.com/library/30cbc4de-adb3-42e8-922f-7661095bdb8c.aspx) <br/> |
|Client Access user settings  <br/> |[Server Management](http://technet.microsoft.com/library/30cbc4de-adb3-42e8-922f-7661095bdb8c.aspx) <br/> |
|Client Access virtual directory settings  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> [Server Management](http://technet.microsoft.com/library/30cbc4de-adb3-42e8-922f-7661095bdb8c.aspx) <br/> |
|RPC Client Access settings  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> [Server Management](http://technet.microsoft.com/library/30cbc4de-adb3-42e8-922f-7661095bdb8c.aspx) <br/> [View-Only Organization Management](http://technet.microsoft.com/library/c514c6d0-0157-4c52-9ec6-441d9a30f3df.aspx) <br/> |
|Push notification proxy settings  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> [Recipient Management](http://technet.microsoft.com/library/669d602e-68e3-41f9-a455-b942d212d130.aspx) <br/> |
|OAuth authentication redirection settings  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> |
   
## Exchange ActiveSync permissions
<a name="ExchangeActiveSync"> </a>

You can configure any of the following for Exchange ActiveSync.
  
Users who are assigned the View-Only Management role group can view the configuration of the features in the following table. For more information, see **View Only Organization Management**.
  
|**Feature**|**Permissions required**|
|:-----|:-----|
|Exchange ActiveSync Autoblock settings  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> |
|Exchange ActiveSync mailbox policy settings  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> [Server Management](http://technet.microsoft.com/library/30cbc4de-adb3-42e8-922f-7661095bdb8c.aspx) <br/> |
|Exchange ActiveSync server settings  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> [Server Management](http://technet.microsoft.com/library/30cbc4de-adb3-42e8-922f-7661095bdb8c.aspx) <br/> |
|Exchange ActiveSync settings  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> [Server Management](http://technet.microsoft.com/library/30cbc4de-adb3-42e8-922f-7661095bdb8c.aspx) <br/> |
|Exchange ActiveSync user settings  <br/> |[Recipient Management](http://technet.microsoft.com/library/669d602e-68e3-41f9-a455-b942d212d130.aspx) <br/> |
|Exchange ActiveSync virtual directory settings  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> [Server Management](http://technet.microsoft.com/library/30cbc4de-adb3-42e8-922f-7661095bdb8c.aspx) <br/> |
|Mobile device mailbox policy settings  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> [Server Management](http://technet.microsoft.com/library/30cbc4de-adb3-42e8-922f-7661095bdb8c.aspx) <br/> |
|Mobile device user settings  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> [Server Management](http://technet.microsoft.com/library/30cbc4de-adb3-42e8-922f-7661095bdb8c.aspx) <br/> [Recipient Management](http://technet.microsoft.com/library/669d602e-68e3-41f9-a455-b942d212d130.aspx) <br/> |
   
## Autodiscover permissions
<a name="Autodiscover"> </a>

You can configure the following for the Autodiscover service.
  
Users who are assigned the View-Only Management role group can view the configuration of the features in the following table. For more information, see **View Only Organization Management**.
  
|**Feature**|**Permissions required**|
|:-----|:-----|
|Autodiscover service configuration settings  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> [Server Management](http://technet.microsoft.com/library/30cbc4de-adb3-42e8-922f-7661095bdb8c.aspx) <br/> [View-Only Organization Management](http://technet.microsoft.com/library/c514c6d0-0157-4c52-9ec6-441d9a30f3df.aspx) <br/> [Delegated Setup](http://technet.microsoft.com/library/49362059-e53f-4135-ad2b-9edfbfff9a1e.aspx) <br/> [Hygiene Management](http://technet.microsoft.com/library/fc0a9ec2-9c3d-42f6-8442-8603fb29d464.aspx) <br/> |
|Autodiscover virtual directory settings  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> [Server Management](http://technet.microsoft.com/library/30cbc4de-adb3-42e8-922f-7661095bdb8c.aspx) <br/> |
   
## Availability service permissions
<a name="AvailabilityService"> </a>

You can configure the following for the Availability service.
  
Users who are assigned the View-Only Management role group can view the configuration of the features in the following table. For more information, see **View Only Organization Management**.
  
|**Feature**|**Permissions required**|
|:-----|:-----|
|Availability service address space settings  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> [View-Only Organization Management](http://technet.microsoft.com/library/c514c6d0-0157-4c52-9ec6-441d9a30f3df.aspx) <br/> |
|Availability service configuration settings  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> [Server Management](http://technet.microsoft.com/library/30cbc4de-adb3-42e8-922f-7661095bdb8c.aspx) <br/> [View-Only Organization Management](http://technet.microsoft.com/library/c514c6d0-0157-4c52-9ec6-441d9a30f3df.aspx) <br/> |
   
## Client throttling permissions
<a name="ClientThrottling"> </a>

You can configure the following for client throttling.
  
Users who are assigned the View-Only Management role group can view the configuration of the features in the following table. For more information, see **View Only Organization Management**.
  
|**Feature**|**Permissions required**|
|:-----|:-----|
|Client throttling settings  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> [View-Only Organization Management](http://technet.microsoft.com/library/c514c6d0-0157-4c52-9ec6-441d9a30f3df.aspx) <br/> |
   
## Exchange Web Services permissions
<a name="ClientThrottling"> </a>

You can configure the following for Web Services virtual directories.
  
Users who are assigned the View-Only Management role group can view the configuration of the features in the following table. For more information, see **View Only Organization Management**.
  
|**Feature**|**Permissions required**|
|:-----|:-----|
|Exchange Web Services virtual directory settings  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> [Server Management](http://technet.microsoft.com/library/30cbc4de-adb3-42e8-922f-7661095bdb8c.aspx) <br/> |
|Test Exchange Web Services  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> [Server Management](http://technet.microsoft.com/library/30cbc4de-adb3-42e8-922f-7661095bdb8c.aspx) <br/> |
|Test Outlook Web Services  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> |
   
## Outlook Anywhere permissions
<a name="OutlookAnywhere"> </a>

You can configure and manage the following settings for Outlook Anywhere.
  
Users who are assigned the View-Only Management role group can view the configuration of the features in the following table. For more information, see **View Only Organization Management**.
  
|**Feature**|**Permissions required**|
|:-----|:-----|
|Outlook Anywhere configuration (enable, disable, change, view)  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> [Server Management](http://technet.microsoft.com/library/30cbc4de-adb3-42e8-922f-7661095bdb8c.aspx) <br/> [View-Only Organization Management](http://technet.microsoft.com/library/c514c6d0-0157-4c52-9ec6-441d9a30f3df.aspx) <br/> [Delegated Setup](http://technet.microsoft.com/library/49362059-e53f-4135-ad2b-9edfbfff9a1e.aspx) <br/> [Hygiene Management](http://technet.microsoft.com/library/fc0a9ec2-9c3d-42f6-8442-8603fb29d464.aspx) <br/> |
|RPC over HTTP Proxy component  <br/> |Local Server Administrator  <br/> |
|Test Outlook Anywhere connectivity  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> [View-Only Organization Management](http://technet.microsoft.com/library/c514c6d0-0157-4c52-9ec6-441d9a30f3df.aspx) <br/> [Server Management](http://technet.microsoft.com/library/30cbc4de-adb3-42e8-922f-7661095bdb8c.aspx) <br/> |
   
## Outlook on the web permissions
<a name="OutlookWebApp"> </a>

You can use the following features to view Outlook on the web settings, control security and user access to Outlook on the web, and test Outlook on the web connectivity.
  
Users who are assigned the View-Only Management role group can view the configuration of the features in the following table. For more information, see **View Only Organization Management**.
  
|**Feature**|**Permissions required**|
|:-----|:-----|
|Graphics editor  <br/> |Local Server Administrator  <br/> |
|IIS Manager  <br/> |Local Server Administrator  <br/> |
|ISA Server 2006  <br/> |ISA Server Enterprise Administrator  <br/> |
|Outlook on the web mailbox policies  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> [Recipient Management](http://technet.microsoft.com/library/669d602e-68e3-41f9-a455-b942d212d130.aspx) <br/> |
|Outlook on the web virtual directories  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> [Server Management](http://technet.microsoft.com/library/30cbc4de-adb3-42e8-922f-7661095bdb8c.aspx) <br/> |
|Registry Editor  <br/> |Local Server Administrator  <br/> |
|S/MIME configuration  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> |
|Text editor  <br/> |Local Server Administrator  <br/> |
|View Outlook on the web mailbox policies  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> [Recipient Management](http://technet.microsoft.com/library/669d602e-68e3-41f9-a455-b942d212d130.aspx) <br/> [View-Only Organization Management](http://technet.microsoft.com/library/c514c6d0-0157-4c52-9ec6-441d9a30f3df.aspx) <br/> [Delegated Setup](http://technet.microsoft.com/library/49362059-e53f-4135-ad2b-9edfbfff9a1e.aspx) <br/> [Hygiene Management](http://technet.microsoft.com/library/fc0a9ec2-9c3d-42f6-8442-8603fb29d464.aspx) <br/> |
   
## POP3 and IMAP4 permissions
<a name="POP3andIMAP4"> </a>

You can configure the following for POP3 and IMAP4.
  
Users who are assigned the View-Only Management role group can view the configuration of the features in the following table. For more information, see **View Only Organization Management**.
  
|**Feature**|**Permissions required**|
|:-----|:-----|
|IMAP4 settings  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> [Server Management](http://technet.microsoft.com/library/30cbc4de-adb3-42e8-922f-7661095bdb8c.aspx) <br/> [View-Only Organization Management](http://technet.microsoft.com/library/c514c6d0-0157-4c52-9ec6-441d9a30f3df.aspx) <br/> |
|POP3 settings  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> [Server Management](http://technet.microsoft.com/library/30cbc4de-adb3-42e8-922f-7661095bdb8c.aspx) <br/> [View-Only Organization Management](http://technet.microsoft.com/library/c514c6d0-0157-4c52-9ec6-441d9a30f3df.aspx) <br/> |
|Test IMAP4 settings  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> [Server Management](http://technet.microsoft.com/library/30cbc4de-adb3-42e8-922f-7661095bdb8c.aspx) <br/> [View-Only Organization Management](http://technet.microsoft.com/library/c514c6d0-0157-4c52-9ec6-441d9a30f3df.aspx) <br/> |
|Test POP3 settings  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> [Server Management](http://technet.microsoft.com/library/30cbc4de-adb3-42e8-922f-7661095bdb8c.aspx) <br/> [View-Only Organization Management](http://technet.microsoft.com/library/c514c6d0-0157-4c52-9ec6-441d9a30f3df.aspx) <br/> |
   
## Windows PowerShell virtual directory permissions
<a name="PowerShell"> </a>

You can configure the following for Windows PowerShell.
  
Users who are assigned the View-Only Management role group can view the configuration of the features in the following table. For more information, see **View Only Organization Management**.
  
|**Feature**|**Permissions required**|
|:-----|:-----|
|Test Windows PowerShell  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> |
|Windows PowerShell settings  <br/> |[Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> |
   
## Text Messaging permissions
<a name="TextMessaging"> </a>

You can configure the following for text messaging.
  
Users who are assigned the View-Only Management role group can view the configuration of the features in the following table. For more information, see **View Only Organization Management**.
  
|**Feature**|**Permissions required**|
|:-----|:-----|
|Text messaging notification settings  <br/> |[Recipient Management](http://technet.microsoft.com/library/669d602e-68e3-41f9-a455-b942d212d130.aspx) <br/> |
|Text messaging settings  <br/> |[Recipient Management](http://technet.microsoft.com/library/669d602e-68e3-41f9-a455-b942d212d130.aspx) <br/> |
|Text messaging user settings  <br/> |[Recipient Management](http://technet.microsoft.com/library/669d602e-68e3-41f9-a455-b942d212d130.aspx) <br/> |
   

