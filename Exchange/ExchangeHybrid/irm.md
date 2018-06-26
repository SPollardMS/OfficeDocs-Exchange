---
title: "IRM in Exchange hybrid deployments"
ms.author: dstrome
author: dstrome
manager: laurawi
ms.date: 12/9/2016
ms.audience: Developer
ms.topic: article
ms.prod: exchange-server-itpro
localization_priority: Normal
ms.collection: Ent_O365_Hybrid
ms.assetid: ba6ec48b-8f79-4807-b74b-fd442bbbe82f
description: "Summary: How IRM works in an Exchange hybrid environment, and how to configure IRM to work between Exchange Online and your on-premises Exchange servers."
---

# IRM in Exchange hybrid deployments

 **Summary**: How IRM works in an Exchange hybrid environment, and how to configure IRM to work between Exchange Online and your on-premises Exchange servers.
  
Information Rights Management (IRM) helps you to protect against leakage of sensitive information by providing persistent online and offline protection of email messages and attachments. Both your Exchange on-premises organization and Exchange Online, in Office 365 for enterprises, support IRM. However, there are differences between the two implementations, and you need to configure IRM in the Exchange Online organization before users in that organization can use it.
  
IRM uses Active Directory Rights Management Services (AD RMS), which is a component of Windows Server 2008 and later. AD RMS allows users to create rights-protected content, such as email messages and attachments, and then control how that content is used, and to whom it's distributed. Users can specify templates that determine how content can be used. For example, a user may specify that an email message can't be forwarded to other recipients or that information in the message can't be copied.
  
Learn more about IRM in Exchange 2010 at: [Understanding Information Rights Management](https://technet.microsoft.com/library/dd638140%28v=exchg.141%29.aspx).
  
Learn more about IRM in Exchange 2013 and Exchange 2016 at [Information Rights Management](http://technet.microsoft.com/library/6ea3a695-3ddd-4d53-b3c6-90041f44ef64.aspx).
  
Learn more about AD RMS at [Active Directory Rights Management Services Overview](https://go.microsoft.com/fwlink/p/?LinkId=215243).
  
## Differences between IRM in Exchange On-premises and Exchange Online

IRM functionality that's available in your on-premises Exchange organization may be different than the functionality available in your Exchange Online organization. The following table provides a summary of features and functionality available in each organization. (Learn more about these features at: [Understanding Information Rights Management](http://technet.microsoft.com/library/6ea3a695-3ddd-4d53-b3c6-90041f44ef64.aspx))
  
**Available IRM features**

|**Feature**|**Available in Exchange 2007 and earlier**|**Available in Exchange 2010**|**Available in Exchange Online and Exchange 2013 and later**|
|:-----|:-----|:-----|:-----|
|Manual protection of messages in Outlook  <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |
|Manual protection of messages in Outlook Web App  <br/> |No  <br/> |Yes  <br/> |Yes  <br/> |
|View IRM-protected messages in Outlook  <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |
|View IRM-protected messages in Outlook Web App  <br/> |No  <br/> |Yes  <br/> |Yes  <br/> |
|IRM Pre-licensing agent  <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |
|RMS policy templates  <br/> |No  <br/> |Yes  <br/> |Yes  <br/> |
|Transport decryption  <br/> |No  <br/> |Yes  <br/> |Yes  <br/> |
|Journal report decryption  <br/> |No  <br/> |Yes  <br/> |Yes  <br/> |
|Exchange Search and discovery decryption  <br/> |No  <br/> |Yes  <br/> |Yes  <br/> |
|Automatic Outlook protection rules  <br/> |No  <br/> |No  <br/> |Yes  <br/> |
|Automatic transport protection rules  <br/> |No  <br/> |Yes  <br/> |Yes  <br/> |
   
## IRM in hybrid deployments

Exchange uses AD RMS servers in the Active Directory forest in which the Exchange server is installed. For your on-premises Exchange servers, the on-premises AD RMS server is used. For your Exchange Online organization, AD RMS servers that are maintained within the Office 365 datacenters are used. The AD RMS configuration that each Exchange organization uses is independent of any other AD RMS deployment. 
  
AD RMS configuration, and therefore IRM configuration, isn't automatically replicated between your on-premises Exchange organization and the Exchange Online organization. Any AD RMS templates that you've defined aren't automatically copied to the Exchange Online organization. If you want the same AD RMS templates to be available in the Exchange Online organization, you must manually export the templates from your on-premises organization and apply them to the Office 365 organization. See [Configure IRM in hybrid deployments](irm.md#IRMConfig) later in this topic. 
  
### User experience

The IRM configuration that's applied to a user depends on the client the user uses and the location of the user's mailbox. The following table shows the AD RMS server a user will use.
  
**Active AD RMS server**

|**Client**|**On-premises mailbox**|**Exchange Online mailbox**|
|:-----|:-----|:-----|
|Outlook desktop clients  <br/> |On-premises AD RMS  <br/> |On-premises AD RMS  <br/> |
|Outlook on the web  <br/> |On-premises AD RMS  <br/> |Exchange Online AD RMS  <br/> |
|ActiveSync device  <br/> |On-premises AD RMS  <br/> |Exchange Online AD RMS  <br/> |
   
Depending on the AD RMS configuration you configure in your on-premises and Exchange Online organizations, it's possible that a user who uses Outlook 2007 and Outlook on the web may see different AD RMS templates. For this reason, we strongly recommend that you apply the same templates to both your on-premises and Exchange Online organizations.
  
There should be no difference in the IRM experience for Outlook client users, regardless of whether their mailbox is located in the on-premises or Exchange Online organization. 
  
An Outlook on the web user whose mailbox is located on an Exchange on-premises server can only open rights-protected messages after installing the Rights Management for Internet Explorer add-in. They can't reply to or create new rights-protected messages.
  
An Outlook on the web user whose mailbox is located in Exchange Online can open rights-protected messages without any additional software and can reply to, and create, new rights-protected messages.
  
### Server functionality

On-premises Exchange servers use the AD RMS pre-licensing agent to decrypt rights-protected messages so that users don't need to supply credentials when they open those messages. The on-premises Exchange server contacts the on-premises AD RMS server to check usage policies and rights, and to request authorization to decrypt the message. 
  
The Exchange Online organization provides several additional IRM-related features that make use of Exchange Online AD RMS. These features, such as journal report decryption, make the content of right-protected messages available to Exchange services for additional processing. For example, the decrypted contents of a journaled message can be saved, along with the original rights-protected message, to allow for easier discovery. Additionally, IRM templates can automatically be applied to messages using either Outlook protection rules or transport rules to ensure that messages adhere to organization policies regarding information protection.
  
## Configure IRM in hybrid deployments
<a name="IRMConfig"> </a>

IRM in Exchange relies on AD RMS being deployed in the Active Directory forest in which the Exchange server resides. AD RMS configuration isn't automatically synchronized between the on-premises and Exchange Online organizations. You must manually export the AD RMS configuration, known as a trusted publishing domain (TPD), from your on-premises AD RMS server, and import that configuration into the Exchange Online organization. The TPD contains the AD RMS configuration, including templates, which the Exchange Online organization needs to use IRM.
  
Learn more at [AD RMS Trusted Publishing Domain Considerations](https://go.microsoft.com/fwlink/p/?LinkId=215244).
  
In addition to applying your on-premises AD RMS configuration to the Exchange Online organization, you must ensure that your AD RMS servers can be contacted by Outlook and ActiveSync clients outside of your on-premises network. You must do this if you want these clients to access rights-protected messages outside of your on-premises network.
  
After you've configured your on-premises network and exported the TPD data, you need to configure the Exchange Online organization by importing the TPD data and enabling IRM.
  
> [!NOTE]
> Any time you modify your on-premises AD RMS configuration, you must manually apply the new configuration in the Exchange Online organization. To do so, export the TPD data from your on-premises AD RMS server and import it into the Exchange Online organization. 
  
## How to configure IRM in Exchange hybrid deployments
<a name="IRMConfig"> </a>

If you use IRM in your on-premises Exchange organization and you want your Exchange Online users to also use IRM, you need to do the following:
  
1. Configure your on-premises Active Directory Rights Management Services (AD RMS) server.
    
2. Enable IRM in your Exchange Online organization.
    
3. Distribute the imported AD RMS templates to users in the Exchange Online organization.
    
### How do I configure on-premises AD RMS servers?

To configure IRM in a hybrid deployment, you need to use Windows PowerShell to access your on-premises AD RMS server. Learn more at: [Using Windows PowerShell to Administer AD RMS](https://go.microsoft.com/fwlink/p/?LinkId=214938)
  
Do the following to export trusted publishing domain (TPD) data from your on-premises AD RMS server and then configure access to the AD RMS server for external clients.
  
1. Export TPD data from your on-premises organization. Learn more at: [Exporting a Trusted Publishing Domain](https://go.microsoft.com/fwlink/p/?LinkId=214942)
    
2. Configure access to AD RMS servers from external clients. Learn more at: [Adding an Extranet Cluster URL](https://go.microsoft.com/fwlink/p/?LinkId=214945)
    
### How do I enable IRM in the Exchange Online organization?

After you export the TPD data from your on-premises AD RMS servers, you need to import that data into the Exchange Online organization and then enable IRM.
  
1. In the Exchange Online organization, import the TPD data.
    
  ```
  Import-RMSTrustedPublishingDomain -FileData $( [Byte[]] (Get-Content -Encoding Byte -Path "<Path to exported TPD file>" -ReadCount 0))
  ```

2. Enable IRM in the Exchange Online organization.
    
  ```
  Set-IRMConfiguration -InternalLicensingEnabled $True
  ```

### How do I distribute AD RMS templates in the Exchange Online organization?

After you've enabled IRM in the Exchange Online organization, you must distribute the imported AD RMS templates. The following Exchange Online users and features use AD RMS templates: 
  
- Outlook on the web users
    
- Exchange ActiveSync users
    
- Transport rules
    
- Journal report decryption
    
- Outlook protection rules
    
1. In the Exchange Online organization, retrieve a list of AD RMS templates.
    
  ```
  Get-RMSTemplate -Type All
  ```

2. Distribute the AD RMS templates to users and features in the Exchange Online organization.
    
  ```
  Set-RMSTemplate <template name> -Type Distributed
  ```

    > [!NOTE]
    > You can't modify the "Do Not Forward" AD RMS template. 
  
3. Repeat step 2 for each AD RMS template you want to distribute.
    
### How do I know this worked?

Outlook on the web users should be able to apply AD RMS templates to new messages. Outlook on the web and Exchange ActiveSync users should be able to read messages that have AD RMS templates applied to them. In addition, all the AD RMS templates that were imported from your on-premises organization should be listed when you run the **Get-RMSTemplate** cmdlet. 
  
Run the following command in the Exchange Online organization.
  
```
Get-RMSTemplate 
```

Learn more at: [Understanding Information Rights Management in Outlook Web App](http://technet.microsoft.com/library/60a49dab-17ac-4d2c-9b41-7d87250d6c00.aspx)
  

