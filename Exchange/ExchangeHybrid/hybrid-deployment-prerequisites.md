---
title: "Hybrid deployment prerequisites"
ms.author: dstrome
author: dstrome
manager: laurawi
ms.date: 7/25/2017
ms.audience: Developer
ms.topic: article
ms.prod: exchange-server-itpro
localization_priority: Normal
ms.collection:
- Ent_O365_Hybrid
- Strat_EX_EXOBlocker
- Hybrid
ms.assetid: e7454db0-fed4-4662-8890-9501126b1ba2
description: "Summary: What your Exchange environment needs before you can set up a hybrid deployment."
---

# Hybrid deployment prerequisites

 **Summary**: What your Exchange environment needs before you can set up a hybrid deployment.
  
Before you create and configure a hybrid deployment using the Hybrid Configuration wizard, your existing on-premises Exchange organization needs to meet certain requirements. If you don't meet these requirements, you won't be able to complete the steps within the Hybrid Configuration wizard and you won't be able to configure a hybrid deployment between your on-premises Exchange organization and Exchange Online.
  
## Prerequisites for hybrid deployment

The following prerequisites are required for configuring a hybrid deployment:
  
- **On-premises Exchange organization** Hybrid deployments can be configured for on-premises Exchange 2007-based organizations or later. 
    
    The version of Exchange you have installed in your on-premises organization determines the hybrid deployment version you can install. You should typically configure the newest hybrid deployment version that's supported in your organization. For example, if your on-premises organization is running Exchange 2007, you need to configure an Exchange 2013-based hybrid deployment. For a complete listing of Exchange Server and Office 365 for enterprises hybrid deployment compatibility, see following table.
    
|**On-premises environment**|**Exchange 2016-based hybrid deployment**|**Exchange 2013-based hybrid deployment**|**Exchange 2010-based hybrid deployment**|
|:-----|:-----|:-----|:-----|
|Exchange 2016  <br/> |Supported  <br/> |Not supported  <br/> |Not supported  <br/> |
|Exchange 2013  <br/> |Supported  <br/> |Supported  <br/> |Not supported  <br/> |
|Exchange 2010  <br/> |Supported  <br/> |Supported  <br/> |Supported  <br/> |
|Exchange 2007  <br/> |Not supported  <br/> |Supported  <br/> |Supported  <br/> |
   
- **On-premises Exchange releases** Hybrid deployments require the latest cumulative update or update rollup available for the version of Exchange you have installed in your on-premises organization. If you can't install the latest cumulative update or update rollup, the immediately previous release is also supported. Older cumulative updates or update rollups aren't supported. 
    
    For example, assume you've installed Exchange 2013 Cumulative Update 8 in your on-premises organization, and the latest available release of Exchange 2013 is Cumulative Update 10. To remain in a supported hybrid configuration, you need to upgrade your Exchange 2013 servers to at least Cumulative Update 9. However, we'd strongly recommend you upgrade to Cumulative Update 10. 
    
    Cumulative updates and update rollups are released on a quarterly cadence so keeping your servers on the latest cumulative update or update rollup gives you some additional flexibility if you periodically need extra time to complete upgrades. 
    
- **On-premises server roles** The server roles you need to install in your on-premises organization depend on the version of Exchange you have installed. 
    
  - **Exchange 2010** At least one server with the Mailbox, Hub Transport, and Client Access server roles installed. While it's possible to install the Mailbox, Hub Transport, and Client Access roles on separate servers, we strongly recommend that you install all of the roles on each server to provide additional reliability and improved performance. 
    
  - **Exchange 2013** At least one server with the Mailbox and Client Access server roles installed. While it's possible to install the Mailbox and Client Access roles on separate servers, we strongly recommend that you install both roles on each server to provide additional reliability and improved performance. 
    
  - **Exchange 2016 and newer** At least one server that has the Mailbox server role installed. 
    
    Hybrid deployments also support Exchange servers running the Edge Transport server role. Edge Transport servers also need to be updated to the latest cumulative update or update rollup available for the version of Exchange you've installed. We strongly recommend that you deploy Edge Transport servers in a perimeter network. Mailbox and Client Access servers can't be deployed in a perimeter network.
    
- **Office 365** Hybrid deployments are supported in all Office 365 plans that support Azure Active Directory synchronization. All Office 365 Enterprise, Government, Academic and Midsize plans support hybrid deployments. Office 365 Business and Home plans don't support hybrid deployments. 
    
    Learn more at [Sign up for Office 365](https://go.microsoft.com/fwlink/p/?linkId=203981).
    
- **Custom domains** Register any custom domains you want to use in your hybrid deployment with Office 365. You can do this by using the Office 365 Administrative portal, or by optionally configuring Active Directory Federation Services (AD FS) in your on-premises organization. 
    
    Learn more at [Add your domain to Office 365](https://go.microsoft.com/fwlink/p/?linkid=229238).
    
- **Active Directory synchronization** Deploy the Azure Active Directory Connect tool to enable Active Directory synchronization with your on-premises organization. 
    
    Learn more at [Azure AD Connect User Sign-on options](http://go.microsoft.com/fwlink/p/?LinkId=723514).
    
- **Autodiscover DNS records** Configure the Autodiscover public DNS records for your existing SMTP domains to point to an on-premises Exchange 2013 Client Access server. 
    
- **Office 365 organization in the Exchange admin center (EAC)** The Office 365 organization node is included by default in the on-premises EAC, but you must connect the EAC to your Office 365 organization using your Office 365 administrator credentials before you can use the Hybrid Configuration wizard. This also allows you to manage both the on-premises and Exchange Online organizations from a single management console. 
    
    Learn more at [Hybrid management in Exchange hybrid deployments](hybrid-management.md).
    
- **Certificates** Install and assign Exchange services to a valid digital certificate purchased from a trusted public certificate authority (CA). Although self-signed certificates should be used for the on-premises federation trust with the Microsoft Federation Gateway, self-signed certificates can't be used for Exchange services in a hybrid deployment. The Internet Information Services (IIS) instance on the Exchange servers configured in the hybrid deployment must have a valid digital certificate purchased from a trusted CA. Additionally, the EWS external URL and the Autodiscover endpoint specified in your public DNS must be listed in Subject Alternative Name (SAN) of the certificate. The certificate installed on the Exchange servers used for mail transport in the hybrid deployment must all use the same certificate (that is, they are issued by the same CA and have the same subject). 
    
    Learn more at [Certificate requirements for hybrid deployments](certificate-requirements.md).
    
- **EdgeSync** If you've deployed Edge Transport servers in your on-premises organization and want to configure the Edge Transport servers for hybrid secure mail transport, you must configure EdgeSync prior to using the Hybrid Configuration wizard. You also need to run EdgeSync each time you apply a new cumulative update or update rollup to an Edge Transport server. 
    
    > [!IMPORTANT]
    > Although EdgeSync is a requirement in deployments with Edge Transport servers, additional manual transport configuration settings will be required when you configure Edge Transport servers for hybrid secure mail transport. 
  
    Learn more at [Edge Transport servers with hybrid deployments](edge-transport-servers.md).
    
- **Unified Messaging-enabled (UM) mailboxes** If you have UM-enabled mailboxes and you want to move them to Office 365, you need the following in addition to an Exchange hybrid deployment. These requirements need to be met **before** you move any UM-enabled mailboxes to Office 365. 
    
  - Lync Server 2010, Lync Server 2013, or Skype for Business Server 2015 or later integrated with your on-premises telephony system **or**
    
  - Skype for Business Online integrated with your on-premises telephony system **or**
    
  - A traditional on-premises PBX or IP-PBX solution.
    
  - UM mailbox policies created in Exchange Online that mirror the names of the UM mailbox policies in your on-premises organization. 
    
    > [!NOTE]
    > You can map multiple on-premises UM mailbox policies to one UM mailbox policy in Exchange Online. If you want to do this, you'll need to use the Exchange Management Shell to manually map each on-premises UM mailbox policy to an Exchange Online policy. 
  
    For more information, check out [Telephone System Integration with UM](http://technet.microsoft.com/library/b8790117-b040-4c84-9d34-005c75088e76.aspx), [Telephony Advisor for Exchange 2013](http://technet.microsoft.com/library/e9f760f2-5901-4ed2-95a5-724555cc700e.aspx), and [Set up Cloud PBX voicemail](https://go.microsoft.com/fwlink/p/?linkid=826207).
    
## Hybrid deployment protocols, ports, and endpoints

Hybrid deployment features and components require certain incoming protocols, ports and connection endpoints to be accessible to Office 365 in order to work correctly. Before configuring your hybrid deployment, verify that your on-premises network and security configuration can support the features and components in the table below. In addition to allowing specific inbound protocols, ports, and endpoints, computers on your network also need to be able to access the IP addresses, ports, and URLs listed in [Office 365 URLs and IP address ranges](https://go.microsoft.com/fwlink/?LinkId=823100). 
  
|**Transport Protocol**|**Upper Level Protocol**|**Feature/Component**|**On-premises Endpoint**|**On-premises Path**|**Authentication Provider**|**Authorization Method**|**Pre-Auth Supported?**|
|:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
|TCP 25 (SMTP)  <br/> |SMTP/TLS  <br/> |Mail flow between Office 365 and on-premises  <br/> |Exchange 2016 Mailbox/Edge  <br/> Exchange 2013 CAS/Edge  <br/> Exchange 2010 HUB/Edge  <br/> |N/A  <br/> |N/A  <br/> |Certificate-based  <br/> |No  <br/> |
|TCP 443 (HTTPS)  <br/> |Autodiscover  <br/> |Autodiscover  <br/> |Exchange 2016 Mailbox  <br/> Exchange 2013/2010 CAS  <br/> |/autodiscover/autodiscover.svc/wssecurity  <br/> /autodiscover/autodiscover.svc  <br/> |Azure AD authentication system  <br/> |WS-Security Authentication  <br/> |No  <br/> |
|TCP 443 (HTTPS)  <br/> |EWS  <br/> |Free/busy, MailTips, Message Tracking  <br/> |Exchange 2016 Mailbox  <br/> Exchange 2013/2010 CAS  <br/> |/ews/exchange.asmx/wssecurity  <br/> |Azure AD authentication system  <br/> |WS-Security Authentication  <br/> |No  <br/> |
|TCP 443 (HTTPS)  <br/> |EWS  <br/> |Multi-mailbox search  <br/> |Exchange 2016 Mailbox  <br/> Exchange 2013/2010 CAS  <br/> |/ews/exchange.asmx/wssecurity  <br/> /autodiscover/autodiscover.svc/wssecurity  <br/> /autodiscover/autodiscover.svc  <br/> |Auth Server  <br/> |WS-Security Authentication  <br/> |No  <br/> |
|TCP 443 (HTTPS)  <br/> |EWS  <br/> |Mailbox migrations  <br/> |Exchange 2016 Mailbox  <br/> Exchange 2013/2010 CAS  <br/> |/ews/mrsproxy.svc  <br/> |NTLM  <br/> |Basic  <br/> |Yes  <br/> |
|TCP 443 (HTTPS)  <br/> |Autodiscover  <br/> EWS  <br/> |OAuth  <br/> |Exchange 2016 Mailbox  <br/> Exchange 2013/2010 CAS  <br/> |/ews/exchange.asmx/wssecurity  <br/> /autodiscover/autodiscover.svc/wssecurity  <br/> /autodiscover/autodiscover.svc  <br/> |Auth Server  <br/> |WS-Security Authentication  <br/> |No  <br/> |
|TCP 443 (HTTPS)  <br/> |N/A  <br/> |AD FS (included with Windows)  <br/> |Windows 2008/2012 Server  <br/> |/adfs/\*  <br/> |Azure AD authentication system  <br/> |Varies per config.  <br/> |2-factor  <br/> |
|TCP 443 (HTTPS)  <br/> |N/A  <br/> |Azure Active Directory Connect with AD FS  <br/> |Windows 2012 R2 Server  <br/> |/adfs/\*  <br/> |Azure AD authentication system  <br/> |Varies per config.  <br/> |2-factor  <br/> |
   
## Recommended tools and services

In addition to the required prerequisites described earlier, other tools and services are beneficial when you're configuring hybrid deployments with the Hybrid Configuration wizard:
  
- **Exchange Server Deployment Assistant** Exchange Server Deployment Assistant is a free web-based tool that helps you deploy Exchange in your on-premises organization, configure a hybrid deployment between your on-premises organization and Office 365, or migrate completely to Office 365. The tool asks you a small set of simple questions and then, based on your answers, creates a customized checklist with instructions to deploy or configure Exchange Server. The Deployment Assistant gives you exactly the right information you need to configure your hybrid deployment. 
    
    Learn more at [Exchange Server Deployment Assistant](https://technet.microsoft.com/exdeploy2013).
    
- **Remote Connectivity Analyzer tool** The Microsoft Remote Connectivity Analyzer tool checks the external connectivity of your on-premises Exchange organization and makes sure that you're ready to configure your hybrid deployment. We strongly recommend that you check your on-premises organization with the Remote Connectivity Analyzer tool prior to configuring your hybrid deployment with the Hybrid Configuration wizard. 
    
    Learn more at [Microsoft Remote Connectivity Analyzer](https://testconnectivity.microsoft.com/).
    
- **Single sign-on** Single sign-on enables users to access both the on-premises and Exchange Online organizations with a single user name and password. It provides users with a familiar sign-on experience and allows administrators to easily control account policies for Exchange Online organization mailboxes by using on-premises Active Directory management tools. 
    
    You have a couple of options when deploying single sign-on: password synchronization and Active Directory Federation Services. Both options are provided by Azure Active Directory Connect. Password synchronization enables almost any organization, no matter the size, to easily implement single sign-on. For this reason, and because the user experience in a hybrid deployment is significantly better with single sign-on enabled, we strongly recommend implement it. For very large organizations, such as those with multiple Active Directory forests that need to join the hybrid deployment, Active Directory Federation Services is required.
    
    Learn more at [Single sign-on with hybrid deployments](single-sign-on.md).
    

