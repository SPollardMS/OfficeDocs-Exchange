---
title: What's discontinued in Exchange 2016
ms.prod: EXCHANGE
ms.assetid: 0ac0001c-b314-4108-b895-d9c0e271b489
---



# What's discontinued in Exchange 2016

This topic discusses the components, features, or functionality that have been removed, discontinued, or replaced in Exchange 2016.
  
    
    


## Discontinued features from Exchange 2013 to Exchange 2016

This section lists the Exchange 2013 features that are no longer available in Exchange 2016.
  
    
    

### Architecture



|**Feature**|**Comments and mitigation**|
|:-----|:-----|
|Client Access server role  <br/> |The Client Access server role has been replaced by Client Access services that run on the Mailbox server role. The Mailbox server role now performs all functionality that was previously included with the Client Access server role. For more information about the new Mailbox server role, see  [Exchange 2016 architecture](exchange-2016-architecture.md).  <br/> |
|MAPI/CDO library  <br/> |The MAPI/CDO library has been replaced by Exchange Web Services (EWS), Exchange ActiveSync (EAS), and Representational State Transfer (REST)* APIs. If an application uses the MAPI/CDO library, it needs to move to EWS, EAS, or the REST APIs to communicate with Exchange 2016. <br/> |
   
* REST APIs will be included in a future release of Exchange 2016.
  
    
    

## De-emphasized features in Exchange 2016

The following features are being de-emphasized in Exchange 2016 and may not be included in future versions of Exchange.
  
    
    

- Third-party replication APIs
    
  
- RPC over HTTP
    
  
- Database Availability Group support for failover cluster administrative access points
    
  

## Discontinued features from Exchange 2010 to Exchange 2016

This section lists the Exchange 2010 features that are no longer available in Exchange 2016.
  
    
    

### Architecture



|**Feature**|**Comments and mitigation**|
|:-----|:-----|
|Hub Transport server role  <br/> |The Hub Transport server role has been replaced by Transport services which run on the Mailbox server role. The Mailbox server role includes the Microsoft Exchange Transport, Microsoft Exchange Mailbox Transport Delivery, the Microsoft Exchange Mailbox Transport Submission, and the Microsoft Exchange Frontend Transport service. For more information, see  [Mail flow and the transport pipeline](mail-flow-and-the-transport-pipeline.md).  <br/> |
|Unified Messaging server role  <br/> |The Unified Messaging server role has been replaced by Unified Messaging services which run on the Mailbox and Client Access server roles. The Mailbox server role includes the Microsoft Exchange Unified Messaging service and the Client Access server role includes the Microsoft Exchange Unified Messaging Call Router service. For more information, see  [Voice Architecture Changes](http://technet.microsoft.com/library/55d5ca4a-b0cd-45f1-9f47-e745ef208698.aspx).  <br/> |
|MAPI/CDO library  <br/> |The MAPI/CDO library has been replaced by Exchange Web Services (EWS), Exchange ActiveSync (EAS), and Representational State Transfer (REST)* APIs. If an application uses the MAPI/CDO library, it needs to move to EWS, EAS, or the REST APIs to communicate with Exchange 2016. <br/> |
   
* REST APIs will be included in a future release of Exchange 2016.
  
    
    

### Management interfaces



|**Feature**|**Comments and mitigation**|
|:-----|:-----|
|Exchange Management Console and Exchange Control Panel  <br/> |The Exchange Management Console and the Exchange Control Panel have been replaced by the Exchange admin center (EAC). EAC uses the same virtual directory (/ecp) as the Exchange Control Panel. For more information, see  [Exchange admin center in Exchange 2016](exchange-admin-center-in-exchange-2016.md).  <br/> |
   

### Client access



|**Feature**|**Comments and mitigation**|
|:-----|:-----|
|Outlook 2003 is not supported  <br/> |To connect Microsoft Outlook to Exchange 2016, the use of the Autodiscover service is required. However, Microsoft Outlook 2003 doesn't support the use of the Autodiscover service.  <br/> |
|RPC/TCP access for Outlook clients  <br/> |In Exchange 2016, Microsoft Outlook clients can connect using Outlook Anywhere (RPC/HTTP) or MAPI over HTTP Outlook 2013 Service Pack 1 and later. If you have Outlook clients in your organization, using Outlook Anywhere and/or MAPI over HTTP is required. For more information, see  [Outlook Anywhere](http://technet.microsoft.com/library/9026d461-ec6a-4ef5-ba9d-de33030858f3.aspx) and [MAPI over HTTP in Exchange 2016](mapi-over-http-in-exchange-2016.md).  <br/> |
   

### Outlook Web App and Outlook



|**Feature**|**Comments and mitigation**|
|:-----|:-----|
|Spell check  <br/> |Outlook Web App no longer has built-in spell check services. Instead, it uses the spell check features in your Web browsers.  <br/> |
|Customizable filters  <br/> |Outlook Web App no longer has customizable filtered views and no longer supports saving filtered views to Favorites. Customizable filters have been replaced by fixed filters that can be used to view all messages, unread messages, messages sent to the user, or flagged messages.  <br/> |
|Message flags  <br/> |The ability to set a custom date on a message flag isn't available in Outlook Web App. You can use Outlook to set custom dates.  <br/> |
|Chat contact list  <br/> |The chat contact list that appeared in the folder list in Outlook Web App for Exchange 2010 is no longer available.  <br/> |
|Search folders  <br/> |The ability for users to use Search folders isn't currently available in Outlook Web App.  <br/> |
   

### Mail flow



|**Feature**|**Comments and mitigation**|
|:-----|:-----|
|Linked connectors  <br/> |The ability to link a Send connector to a Receive connector has been removed. Specifically, the  _LinkedReceiveConnector_ parameter has been removed from [New-SendConnector](http://technet.microsoft.com/library/7b315ab0-8778-4835-a252-fb94129d7a8e.aspx) and [Set-SendConnector](http://technet.microsoft.com/library/5b9cf002-848a-4f35-b51f-e1ede131b136.aspx).  <br/> |
   

### Antispam and antimalware



|**Feature**|**Comments and mitigation**|
|:-----|:-----|
|Anti-spam agent management in the EMC  <br/> |In Exchange 2010, when you enabled the anti-spam agents on a Hub Transport server, you could manage the anti-spam agents in the Exchange Management Console (EMC). In Exchange 2016, when you enable the anti-spam agents on a Mailbox server, you can't manage the agents using the EAC. You can only use the Exchange Management Shell. For information about how to enable the anti-spam agents on a Mailbox server, see  [Enable antispam functionality on Mailbox servers](enable-antispam-functionality-on-mailbox-servers.md).  <br/> |
|Connection Filtering agent on Hub Transport servers  <br/> |In Exchange 2010, when you enabled the anti-spam agents on a Hub Transport server, the Attachment Filter agent was the only anti-spam agent that wasn't available. In Exchange 2016, when you enable the anti-spam agents on a Mailbox server, the Attachment Filter agent and the Connection Filtering agent aren't available. The Connection Filtering agent provides IP Allow List and IP Block List capabilities. For information about how to enable the anti-spam agents on a Mailbox server, see  [Enable antispam functionality on Mailbox servers](enable-antispam-functionality-on-mailbox-servers.md).  <br/> > [!NOTE]> The only way to enable the Connection Filtering agent is to install an Edge Transport server in the perimeter network. For more information, see  [Edge Transport servers](edge-transport-servers.md).           |
   

### Messaging policy and compliance



|**Feature**|**Comments and mitigation**|
|:-----|:-----|
|Managed Folders  <br/> |In Exchange 2010, you use managed folders for messaging retention management (MRM). In Exchange 2016, managed folders aren't supported. You must use retention policies for MRM.  <br/> > [!NOTE]> Cmdlets related to managed folders are still available. You can create managed folders, managed content settings and managed folder mailbox policies, and apply a managed folder mailbox policy to a user, but the MRM assistant skips processing of mailboxes that have a managed folder mailbox policy applied.           |
|Port Managed Folder wizard  <br/> |In Exchange 2010, you use the Port Managed Folder wizard to create retention tags based on managed folder and managed content settings. In Exchange 2016, the Exchange admin center doesn't include this functionality. You can use the **New-RetentionPolicyTag** cmdlet with the _ManagedFolderToUpgrade_ parameter to create a retention tag based on a managed folder. <br/> |
   

### Unified Messaging and voice mail



|**Feature**|**Comments and mitigation**|
|:-----|:-----|
|Directory lookups using Automatic Speech Recognition (ASR)  <br/> |In Exchange 2010, Outlook Voice Access users can use speech inputs using Automatic Speech Recognition (ASR) to search for users listed in the directory. Speech inputs could be also used in Outlook Voice Access to navigate menus, messages, and other options. However, even if an Outlook Voice Access user is able to use speech inputs, they have to use the telephone key pad to enter their PIN, and navigate personal options.  <br/> In Exchange 2016, authenticated and non-authenticated Outlook Voice Access users can't search for users in the directory using speech inputs or ASR in any language. However, callers that call into an auto attendant can use speech inputs in multiple languages to navigate auto attendant menus and search for users in the directory.  <br/> |
   

### Mailbox database copies



|**Feature**|**Comments and mitigation**|
|:-----|:-----|
| Update-MailboxDatabaseCopy <br/>  Update Mailbox Database Copy wizard <br/> |Content index catalog seeding is no longer possible over the replication network; it can only be done over a MAPI network. This is true even when you use the  `-Network` parameter in the Update-MailboxDatabaseCopy cmdlet. <br/> |
   
