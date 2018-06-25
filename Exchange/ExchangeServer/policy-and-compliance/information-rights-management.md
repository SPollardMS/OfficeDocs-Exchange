---
title: "Information Rights Management in Exchange 2016"
ms.author: chrisda
author: chrisda
manager: serdars
ms.date: 6/8/2018
ms.audience: ITPro
ms.topic: article
ms.prod: exchange-server-itpro
localization_priority: Normal
ms.assetid: 6ea3a695-3ddd-4d53-b3c6-90041f44ef64
description: "Summary: Learn how administrators can use Information Rights Management (IRM) in Exchange 2016 to help prevent the disclosure of sensitive information."
---

# Information Rights Management in Exchange 2016

 **Summary**: Learn how administrators can use Information Rights Management (IRM) in Exchange 2016 to help prevent the disclosure of sensitive information.
  
Every day, people use email to exchange sensitive information, such as confidential information or reports. Because email is accessible from just about anywhere, mailboxes have transformed into repositories that contain large amounts of potentially sensitive information. As a result, information leakage can be a serious threat to organizations. To help prevent information leakage, Exchange 2016 includes Information Rights Management (IRM) features, which provide persistent online and offline protection for email messages and attachments. These IRM features are basically unchanged from Exchange 2013.
  
## What is information leakage?

Information leakage is the disclosure of sensitive information to unauthorized users. Information leakage can be costly for an organization, and can have a wide-ranging impact on the organization's business, employees, customers, and partners. To avoid violating any applicable regulations, organizations need to protect themselves against accidental or intentional information leakage.
  
These are some consequences that can result from information leakage:
  
- **Financial damage**: The organization might incur a loss of business, fines, or adverse media coverage.
    
- **Damage to image and credibility**: Leaked email messages can potentially be a source of embarrassment for the sender and the organization.
    
- **Loss of competitive advantage**: This is one of the most serious consequences. The disclosure of strategic business or merger and acquisition plans can lead to losses in revenue or market capitalization for the organization. Other threats to competitive advantage include the loss of research information, analytical data, and other intellectual property.
    
## Traditional solutions to information leakage
<a name="traditional"> </a>

Although traditional solutions to information leakage may protect the initial access to data, they often don't provide constant protection. This table describes some traditional solutions to information leakage.
  
|**Solution**|**Description**|**Limitations**|
|:-----|:-----|:-----|
|Transport Layer Security (TLS)  <br/> |TLS is an Internet standard protocol that's used to encrypt network communications. In a messaging environment, TLS is used to encrypt server/server and client/server communications.  <br/> By default, Exchange uses TLS for all internal message transfers. Opportunistic TLS is also enabled by default for SMTP sessions with external hosts (TLS encryption is tried first, but if it isn't available, unencrypted communication is allowed). You can also configure domain security to enforce mutual TLS with external organizations.  <br/> |TLS only protects the SMTP session between two SMTP hosts. In other words, TLS protects information in motion, and it doesn't provide protection at the message-level or for information at rest. Unless the messages are encrypted using another method, messages in sender and recipient mailboxes remain unprotected.  <br/> For email sent outside the organization, you can require TLS only for the first hop. After a remote SMTP host receives the message, it can relay it to another SMTP host over an unencrypted session.  <br/>  Because TLS is a transport layer technology that's used in mail flow, it can't provide control over what the recipient does with the message.  <br/> |
|Message encryption  <br/> |Users can use technologies such as S/MIME to encrypt messages.  <br/> |Users decide whether a message gets encrypted.  <br/> There are additional costs of a public key infrastructure (PKI) deployment, with the accompanying overhead of certificate management for users and protection of private keys.  <br/>  After a message is decrypted, there's no control over what the recipient can do with the information. Decrypted information can be copied, printed, or forwarded. By default, saved attachments aren't protected.  <br/> Messaging servers can't open and inspect messages that are encrypted by S/MIME. Therefore, the messaging servers can't enforce messaging policies, scan messages for viruses, or take other actions that require access to the content in messages.  <br/> |
   
Finally, traditional solutions often lack enforcement tools that apply uniform messaging policies to prevent information leakage. For example, a user marks a message with **Company Confidential** and **Do Not Forward**. After the message is delivered to the recipient, the sender or the organization no longer has control over the message. The recipient can willfully or accidentally forward the message (using features such as automatic forwarding rules) to external email accounts, which subjects your organization to substantial information leakage risks.
  
## IRM in Exchange
<a name="irm"> </a>

IRM in Exchange helps prevent information leakage by offering these features:
  
- Prevent an authorized recipient of IRM-protected content from forwarding, modifying, printing, faxing, saving, or cutting and pasting the content.
    
- Protect supported attachment file formats with the same level of protection as the message.
    
- Support expiration of IRM-protected messages and attachments so they can no longer be viewed after the specified period.
    
- Prevent IRM-protected content from being copied using the Snipping Tool inWindows.
    
However, IRM in Exchange can't prevent the disclosure of information by using these methods:
  
- Third-party screen capture programs.
    
- Photographing IRM-protected content that's displayed on the screen.
    
- Users remembering or manually transcribing the information.
    
IRM uses Active Directory Rights Management Services (AD RMS), an information protection technology in Windows Server that uses extensible rights markup language (XrML)-based certificates and licenses to certify computers and users, and to protect content. When a document or message is protected using AD RMS, an XrML license containing the rights that authorized users have to the content is attached. To access IRM-protected content, AD RMS-enabled applications must procure a use license for the authorized user from the AD RMS server. Office applications, such as Word, Excel, PowerPoint and Outlook are RMS-enabled and can be used to create and consume protected content.
  
> [!NOTE]
> The Exchange Prelicense Agent attaches a use license to messages that are protected by the AD RMS server in your organization. For more information, see the [Prelicensing](#prelicensing.md) section later in this topic. 
  
To learn more about Active Directory Rights Management Services, see [Active Directory Rights Management Services](https://go.microsoft.com/fwlink/p/?linkId=129823).
  
### Active Directory Rights Management Services rights policy templates

AD RMS servers provide a Web service that's used to enumerate and acquire the XrML-based rights policy templates that you use to apply IRM protection to messages. By applying the appropriate rights policy template, you can control whether a recipient is allowed to reply to, reply to all, forward, extract information from, save, or print the message.
  
By default, Exchange ships with the **Do Not Forward** template. When this template is applied to a message, only the recipients addressed in the message can decrypt the message. The recipients can't forward the message, copy content from the message, or print the message. You can create additional RMS templates on the AD RMS servers in your organization to meet your requirements. 
  
For more information about rights policy templates, see [AD RMS Policy Template Considerations](https://go.microsoft.com/fwlink/p/?linkId=179455).
  
For more information about creating AD RMS rights policy templates, see [AD RMS Rights Policy Templates Deployment Step-by-Step Guide](https://go.microsoft.com/fwlink/p/?linkId=136593).
  
## Apply IRM protection to messages
<a name="applyingIRM"> </a>

By default, an Exchange organization is enabled for IRM, but to apply IRM protection to messages, you need to use one or more of these methods:
  
- **Manually by users in Outlook**: Users can IRM-protect messages in Outlook by using the AD RMS rights policy templates that are available to them. This process uses the IRM functionality in Outlook, not Exchange. For more information about using IRM in Outlook, see [Introduction to using IRM for email messages](https://go.microsoft.com/fwlink/p/?linkId=166897).
    
- **Manually by users in Outlook on the web**: When an administrator enables IRM in Outlook on the web (formerly known as Outlook Web App), users can IRM-protect messages that they send, and view IRM-protected messages that they receive. For more information about IRM in Outlook on the web, see [Understanding IRM in Outlook Web App](http://technet.microsoft.com/library/60a49dab-17ac-4d2c-9b41-7d87250d6c00.aspx).
    
- **Manually by users in Exchange ActiveSync**: When an administrator enables IRM in Exchange ActiveSync users can view, reply to, forward, and create IRM-protected messages on ActiveSync devices. For more information, see [Understanding Information Rights Management in Exchange ActiveSync](http://technet.microsoft.com/library/ebf04460-4d61-4b00-86b9-85ec1dbbd6a1.aspx).
    
- **Automatically in Outlook**: Administrators can create Outlook protection rules to automatically IRM-protect messages. Outlook protection rules are automatically deployed to Outlook clients, and IRM-protection is applied by Outlook when the user is composing a message. For more information, see [Understanding Outlook Protection Rules](http://technet.microsoft.com/library/bd7d0ad7-1f8e-46da-a74b-58c58f3eff93.aspx).
    
- **Automatically on Mailbox servers**: Administrators can create mail flow rules (also known as transport rules) to automatically IRM-protect messages that match specified conditions. For more information, see [Understanding Transport Protection Rules](http://technet.microsoft.com/library/9bd6d049-165e-4e51-a79f-3b8ff409da55.aspx).
    
    > [!NOTE]
    > IRM protection isn't applied again to messages that are already IRM-protected. For example, if a user IRM-protects a message in Outlook or Outlook on the web, a transport protection rule won't apply IRM protection to the same message. 
  
## Scenarios for IRM protection
<a name="scenarios"> </a>

This table describes the scenarios for sending messages, and whether IRM protection is available.
  
|**Scenario**|**Is sending IRM-Protected messages supported?**|**Requirements**|
|:-----|:-----|:-----|
|Sending messages within the same on-premises Exchange organization  <br/> |Yes  <br/> |For the requirements, see the [IRM requirements](#reqs.md) section later in this topic.  <br/> |
|Sending messages between different Active Directory forests in an on-premises organization.  <br/> |Yes  <br/> |For the requirements, see [Configuring AD RMS to Integrate with Exchange Server 2010 Across Multiple Forests](https://go.microsoft.com/fwlink/p/?linkId=199009).  <br/> |
|Sending messages between an on-premises Exchange organization and an Office 365 organization in a hybrid deployment.  <br/> |Yes  <br/> |For more information, see [IRM in Exchange 2013 Hybrid Deployments](http://technet.microsoft.com/library/ba6ec48b-8f79-4807-b74b-fd442bbbe82f.aspx).  <br/> |
|Sending messages to external recipients  <br/> |No  <br/> |Exchange doesn't include a solution for sending IRM-protected messages to external recipients in non-federated organizations. To create a federated trust between two Active Directory forests by using Active Directory Federation Services (AD FS), see [Understanding AD RMS Trust Policies](https://go.microsoft.com/fwlink/p/?linkId=182909).  <br/> |
   
## Decrypt IRM-protected messages to enforce messaging policies
<a name="decrypting"> </a>

To enforce messaging policies and for regulatory compliance, Exchange needs access to the content of encrypted messages. To meet eDiscovery requirements due to litigation, regulatory audits, or internal investigations, a designated auditor must also be able to search encrypted messages. To help with these tasks, Exchange includes the following decryption features:
  
- **Transport decryption**: Allows access to message content by the transport agents that are installed on Exchange servers. For more information, see [Understanding Transport Decryption](http://technet.microsoft.com/library/4267c46d-f488-404d-a5cb-51f9127461c0.aspx).
    
- **Journal report decryption**: Allows standard or premium journaling to save a clear-text copy of IRM-protected messages in journal reports. For more information, see [Enable journal report decryption](journaling/journaling-procedures.md#IRMDecryption).
    
- **IRM decryption for Exchange Search**: Allows Exchange Search to index content in IRM-protected messages. When a discovery manager performs an In-Place eDiscovery search, IRM-protected messages that have been indexed are returned in the search results. For more information, see [Configure IRM for Exchange Search and In-Place eDiscovery](http://technet.microsoft.com/library/d96790e9-93ad-4a56-b90f-2dbfa2f2073c.aspx).
    
To enable these decryption features, you need to add the Federation mailbox (a system mailbox that's created by Exchange), to the Super Users group on the AD RMS server. For instructions, see [Add Federated Delivery Mailbox to AD RMS Super Users](http://technet.microsoft.com/library/44618df9-54f0-4474-a450-dcba48a02901.aspx).
  
## Prelicensing
<a name="prelicensing"> </a>

To allow authorized users to view IRM-protected messages and attachments, Exchange automatically attaches a prelicense to protected messages. This prevents the client from making repeated trips to the AD RMS server to retrieve a use license, and enables offline viewing of IRM-protected messages. Prelicensing also allows users to view IRM-protected messages in Outlook on the web. When you enable IRM features, prelicensing is enabled by default.
  
## IRM agents
<a name="agents"> </a>

IRM features use the built-in transport agents that exist in the Transport service on Mailbox servers. Most of the built-in transport agents are invisible and unmanageable by the transport agent management cmdlets in the Exchange Management Shell (**\*-TransportAgent** ). 
  
The built-in transport agents that are associated with IRM are described in this table:
  
|**Agent name**|**Manageable?**|**SMTP or categorizer event**|**Description**|
|:-----|:-----|:-----|:-----|
|Journal Report Decryption Agent  <br/> |No  <br/> |**OnCategorizedMessage** <br/> |Provides a clear-text copy of the IRM-protected messages that are attached to journal reports.  <br/> |
|Prelicense Agent  <br/> |No  <br/> |**OnRoutedMessage** <br/> |Attaches a prelicense to IRM-protected messages.  <br/> |
|RMS Decryption Agent  <br/> |No  <br/> |**OnSubmittedMessage**,  <br/> |Decrypts IRM-protected messages to allow access to the message content by transport agents.  <br/> |
|RMS Encryption Agent  <br/> |No  <br/> |**OnRoutedMessage** <br/> |Applies IRM protection to messages flagged by the transport agent and re-encrypts transport decrypted messages.  <br/> |
|RMS Protocol Decryption Agent  <br/> |No  <br/> |**OnEndOfData** <br/> |Decrypts IRM-protected messages to allow access to the message content by transport agents.  <br/> |
|Transport Rule Agent  <br/> |Yes  <br/> |**OnRoutedMessage** <br/> |Flags messages that match the conditions in a transport protection rule to be IRM-protected by the RMS Encryption agent.  <br/> |
   
For more information about transport agents, see [Transport Agents](http://technet.microsoft.com/library/e7389d63-3172-40d5-bf53-0d7cd7e78340.aspx).
  
## IRM requirements
<a name="reqs"> </a>

By default, an Exchange organization is enabled for IRM. To actually implement IRM in your Exchange 2016 organization, your deployment must meet the requirements that are described in this table.
  
|**Server**|**Requirements**|
|:-----|:-----|
|AD RMS cluster  <br/> | *AD RMS cluster* is the term that's used for any AD RMS deployment, including a single AD RMS server. AD RMS is a Web service, so you don't need to set up a Windows Server failover cluster. For high availability and load-balancing, you can deploy multiple AD RMS servers in the cluster and use network load balancing (NLB).  <br/> **Service connection point**: AD RMS-aware applications like Exchange use the service connection point that's registered in Active Directory to discover an AD RMS cluster and URLs. There's only one service connection point for AD RMS in an Active Directory forest. You can register the service connection point during AD RMS Setup, or after setup is complete.  <br/> **Permissions**: Read and Execute permissions to the AD RMS server certification pipeline (the `ServerCertification.asmx` file at `\inetpub\wwwroot\_wmcs\certification\`) must be assigned to these security principals:  <br/> • The Exchange Servers group or individual Exchange servers.  <br/> • The AD RMS Service group on AD RMS servers.  <br/> For details, see [Set Permissions on the AD RMS Server Certification Pipeline](https://go.microsoft.com/fwlink/p/?linkId=186951).  <br/> **AD RMS super users**: To enable transport decryption, journal report decryption, IRM in Outlook on the web, and IRM decryption for Exchange Search, you need to add the Federation mailbox to the Super Users group on the AD RMS server. For details, see [Add Federated Delivery Mailbox to AD RMS Super Users](http://technet.microsoft.com/library/44618df9-54f0-4474-a450-dcba48a02901.aspx).  <br/> |
|Exchange  <br/> |Exchange 2010 or later is required.  <br/> In a production environment, installing AD RMS and Exchange on the same server isn't supported.  <br/> |
|Outlook  <br/> |AD RMS templates for protecting messages are available in Outlook 2007 or later.  <br/> Outlook protection rules in Exchange require Outlook 2010 or later,  <br/> |
|Exchange ActiveSync  <br/> |IRM is available on mobile applications and devices that support Exchange ActiveSync protocol version 14.1 or later, and the included **RightsManagementInformation** tag (both introduced in Exchange 2010 Service Pack 1). Users with supported devices can use ActiveSync to view, reply to, forward, and create IRM-protected messages without connecting to a computer to activate the device for IRM. For more information, see [Understanding Information Rights Management in Exchange ActiveSync](http://technet.microsoft.com/library/ebf04460-4d61-4b00-86b9-85ec1dbbd6a1.aspx).  <br/> |
   
Exchange IRM features support Office file formats. You can extend IRM protection to other file formats by deploying custom protectors. For more information about custom protectors, see Information Protection and Control Partners in [Microsoft partners](https://go.microsoft.com/fwlink/p/?linkId=210336).
  
## Configure and test IRM
<a name="configuring"> </a>

You use the Exchange Management Shell to configure IRM features in Exchange. For procedures, see [Managing Rights Protection](http://technet.microsoft.com/library/e5b3c7d1-31d6-481f-82e7-a3766da9a510.aspx).
  
After you install and configure a Mailbox server, you can use the **Test-IRMConfiguration** cmdlet to perform end-to-end tests of your IRM deployment. The cmdlet performs these tests: 
  
- Inspects IRM configuration for your Exchange organization.
    
- Checks the AD RMS server for version and hotfix information.
    
- Verifies whether an Exchange server can be activated for RMS by retrieving a Rights Account Certificate (RAC) and client licensor certificate.
    
- Acquires AD RMS rights policy templates from the AD RMS server.
    
- Verifies that the specified sender can send IRM-protected messages.
    
- Retrieves a Super User use license for the specified recipient.
    
- Acquires a prelicense for the specified recipient.
    
For more information, see [Test-IRMConfiguration](http://technet.microsoft.com/library/a730e7ff-a67f-4360-b5ff-70d171bb5e1d.aspx).
  
## Extend Rights Management with the Rights Management connector
<a name="extend"> </a>

The Azure Rights Management connector connector (RMS connector) is an optional application that enhances data protection for your Exchange server by employing the cloud-based Azure Rights Management (Azure RMS) service. Once you install the RMS connector, it provides continuous data protection during the lifetime of the information. And, because these services are customizable, you can define the level of protection that you need. For example, you can limit email message access to specific users, or set view-only rights for certain messages.
  
To learn more about the RMS connector and how to install it, see [Deploying the Azure Rights Management connector](https://go.microsoft.com/fwlink/p/?linkid=330432).
  

