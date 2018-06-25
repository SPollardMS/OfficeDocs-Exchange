---
title: "Digital certificates and encryption in Exchange 2016"
ms.author: chrisda
author: chrisda
manager: serdars
ms.date: 6/12/2018
ms.audience: ITPro
ms.topic: overview
ms.prod: exchange-server-itpro
localization_priority: Normal
ms.assetid: a9e2e08c-d46a-4135-a387-eb653212b676
description: "Summary: Learn about SSL, TLS, encryption, and digital certificates in Exchange 2016."
---

# Digital certificates and encryption in Exchange 2016

 **Summary**: Learn about SSL, TLS, encryption, and digital certificates in Exchange 2016.
  
Encryption and digital certificates are important considerations in any organization. By default, Exchange Server 2016 is configured to use Transport Layer Security (TLS) to encrypt communication between internal Exchange servers, and between Exchange services on the local server. But, Exchange administrators need to consider their encryption requirements for communication with internal and external clients (computers and mobile devices), and external messaging servers.
  
> [!NOTE]
> Secure Sockets Layer (SSL) is being replaced by Transport Layer Security (TLS) as the protocol that's used to encrypt data sent between computer systems. They're so closely related that the terms "SSL" and "TLS" (without versions) are often used interchangeably. Because of this similarity, references to "SSL" in Exchange topics, the Exchange admin center, and the Exchange Management Shell have often been used to encompass both the SSL and TLS protocols. Typically, "SSL" refers to the actual SSL protocol only when a version is also provided (for example, SSL 3.0). To find out why you should disable the SSL protocol and switch to TLS, check out [Protecting you against the SSL 3.0 vulnerability](https://blogs.office.com/2014/10/29/protecting-ssl-3-0-vulnerability/). 
  
This topic describes the different types of certificates that are available, the default configuration for certificates in Exchange, and recommendations for additional certificates that you'll need to use with Exchange.
  
For the procedures that are required for certificates in Exchange 2016, see [Certificate procedures in Exchange 2016](certificate-procedures.md).
  
## Digital certificates overview
<a name="Overview"> </a>

Digital certificates are electronic files that work like an online password to verify the identity of a user or a computer. They're used to create the encrypted channel that's used for client communications. A certificate is a digital statement that's issued by a certification authority (CA) that vouches for the identity of the certificate holder and enables the parties to communicate in a secure manner by using encryption.
  
Digital certificates provide the following services:
  
- **Encryption**: They help protect the data that's exchanged from theft or tampering.
    
- **Authentication**: They verify that their holders—people, web sites, and even network devices such as routers—are truly who or what they claim to be. Typically, the authentication is one-way, where the source verifies the identity of the target, but mutual TLS authentication is also possible.
    
Certificates can be issued for several uses. For example: web user authentication, web server authentication, Secure/Multipurpose Internet Mail Extensions (S/MIME), Internet Protocol security (IPsec), and code signing.
  
A certificate contains a public key and attaches that public key to the identity of a person, computer, or service that holds the corresponding private key. The public and private keys are used by the client and the server to encrypt data before it's transmitted. For Windows users, computers, and services, trust in the CA is established when the root certificate is defined in the trusted root certificate store, and the certificate contains a valid certification path. A certificate is considered valid if it hasn't been revoked (it isn't in the CA's certificate revocation list or CRL), or hasn't expired.
  
The three primary types of digital certificates are described in the following table.
  
|**Type**|**Description**|**Advantages**|**Disadvantages**|
|:-----|:-----|:-----|:-----|
|Self-signed certificate  <br/> |The certificate is signed by the application that created it.  <br/> |Cost (free).  <br/> |The certificate isn't automatically trusted by client computers and mobile devices. The certificate needs to be manually added to the trusted root certificate store on all client computers and devices, but not all mobile devices allow changes to the trusted root certificate store.  <br/> Not all services work with self-signed certificates.  <br/> Difficult to establish an infrastructure for certificate lifecycle management. For example, self-signed certificates can't be revoked.  <br/> |
|Certificate issued by an internal CA  <br/> |The certificate is issued by a public key infrastructure (PKI) in your organization. An example is Active Directory Certificate Services (AD CS). For more information, see [Active Directory Certificate Services Overview](https://go.microsoft.com/fwlink/p/?LinkID=392697).  <br/> |Allows organizations to issue their own certificates.  <br/> Less expensive than certificates from a commercial CA.  <br/> |Increased complexity to deploy and maintain the PKI.  <br/> The certificate isn't automatically trusted by client computers and mobile devices. The certificate needs to be manually added to the trusted root certificate store on all client computers and devices, but not all mobile devices allow changes to the trusted root certificate store.  <br/> |
|Certificate issued by a commercial CA  <br/> |The certificate is purchased from a trusted commercial CA.  <br/> |Simplified certificate deployment, because all clients, devices, and servers automatically trust the certificates.  <br/> |Cost. You need to plan ahead to minimize the number of certificates that are required.  <br/> |
   
To prove that a certificate holder is who they claim to be, the certificate must accurately identify the certificate holder to other clients, devices, or servers. The three basic methods to do this are described in the following table.
  
|**Method**|**Description**|**Advantages**|**Disadvantages**|
|:-----|:-----|:-----|:-----|
|Certificate subject match  <br/> |The certificate's **Subject** field contains the common name (CN) of the host. For example, the certificate that's issued to www.contoso.com can be used for the web site https://www.contoso.com.  <br/> |Compatible with all clients, devices, and services.  <br/> Compartmentalization. Revoking the certificate for a host doesn't affect other hosts.  <br/> |Number of certificates required. You can only use the certificate for the specified host. For example, you can't use the www.contoso.com certificate for ftp.contoso.com, even when the services are installed on the same server.  <br/> Complexity. On a web server, each certificate requires its own IP address binding.  <br/> |
|Certificate subject alternative name (SAN) match  <br/> |In addition to the **Subject** field, the certificate's **Subject Alternative Name** field contains a list of multiple host names. For example:  <br/> • www.contoso.com  <br/> • ftp.contoso.com  <br/> • ftp.eu.fabirkam.net  <br/> |Convenience. You can use the same certificate for multiple hosts in multiple, separate domains.  <br/> Most clients, devices, and services support SAN certificates.  <br/> Auditing and security. You know exactly which hosts are capable of using the SAN certificate.  <br/> |More planning required. You need to provide the list of hosts when you create the certificate.  <br/> Lack of compartmentalization. You can't selectively revoke certificates for some of the specified hosts without affecting all of the hosts in the certificate.  <br/> |
|Wildcard certificate match  <br/> |The certificate's **Subject** field contains the common name as the wildcard character (\*) plus a single domain or subdomain. For example, \*.contoso.com or \*.eu.contoso.com. The \*.contoso.com wildcard certificate can be used for:  <br/> • www.contoso.com  <br/> • ftp.contoso.com  <br/> • mail.contoso.com  <br/> |Flexibility. You don't need to provide a list of hosts when you request the certificate, and you can use the certificate on any number of hosts that you may need in the future.  <br/> |You can't use wildcard certificates with other top-level domains (TLDs). For example, you can't use the \*.contoso.com wildcard certificate for \*.contoso.net hosts.  <br/> You can only use wildcard certificates for host names at the level of the wildcard. For example, you can't use the \*.contoso.com certificate for www.eu.contoso.com. Or, you can't use the \*.eu.contoso.com certificate for www.uk.eu.contoso.com.  <br/> Older clients, devices, applications, or services might not support wildcard certificates.  <br/> Wildcards aren't available with Extended Validation (EV) certificates.  <br/> Careful auditing and control is required. If the wildcard certificate is compromised, it affects every host in the specified domain.  <br/> |
   
## Certificates in Exchange
<a name="ExchangeCerts"> </a>

When you install Exchange 2016 on a server, two self-signed certificates are created and installed by Exchange. A third self-signed certificate is created and installed by Microsoft Windows for the Web Management service in Internet Information Services (IIS). These three certificates are visible in the Exchange admin center (EAC) and the Exchange Management Shell, and are described in the following table:
  
****

|**Name**|**Comments**|
|:-----|:-----|
|Microsoft Exchange  <br/> |This Exchange self-signed certificate has the following capabilities:  <br/> • The certificate is automatically trusted by all other Exchange servers in the organization. This includes any Edge Transport server subscribed to the Exchange organization.  <br/> • The certificate is automatically enabled for all Exchange services except Unified Messaging, and is used to encrypt internal communication between Exchange servers, Exchange services on the same computer, and client connections that are proxied from the Client Access services to the backend services on Mailbox servers.  <br/> • The certificate is automatically enabled for inbound connections from external SMTP messaging servers, and outbound connections to external SMTP messaging servers. This default configuration allows Exchange to provide *opportunistic TLS* on all inbound and outbound SMTP connections. Exchange attempts to encrypt the SMTP session with an external messaging server, but if the external server doesn't support TLS encryption, the session is unencrypted.  <br/> • The certificate doesn't provide encrypted communication with internal or external clients. Clients and servers don't trust the Exchange self-signed certificate, because the certificate isn't defined in their trusted root certification stores.  <br/> |
|Microsoft Exchange Server Auth Certificate  <br/> |This Exchange self-signed certificate is used for server-to-server authentication and integration by using OAuth. For more information, see [Plan Exchange 2016 integration with SharePoint and Skype for Business](../../plan-and-deploy/integration-with-sharepoint-and-skype/integration-with-sharepoint-and-skype.md).  <br/> |
|WMSVC  <br/> |This Windows self-signed certificate is used by the Web Management service in IIS to enable remote management of the web server and its associated web sites and applications.  <br/> If you remove this certificate, the Web Management service will fail to start if no valid certificate is selected. Having the service in this state can prevent you from installing Exchange updates, or uninstalling Exchange from the server. For instructions on how to correct this issue, see [Event ID 1007 — IIS Web Management Service Authentication](https://go.microsoft.com/fwlink/p/?LinkId=746383) <br/> |
   
The properties of these self-signed certificates are described in the [Properties of the default self-signed certificates](certificates.md#DefaultCertificateProperties) section. 
  
These are the key issues that you need to consider when it comes to certificates in Exchange:
  
- You don't need to replace the Microsoft Exchange self-signed certificate to encrypt network traffic between Exchange servers and services in your organization.
    
- You need additional certificates to encrypt connections to Exchange servers by internal and external clients.
    
- You need additional certificates to force the encryption of SMTP connections between Exchange servers and external messaging servers.
    
The following elements of planning and deployment for Exchange 2016 are important drivers for your certificate requirements:
  
- **Load balancing**: Do you plan to terminate the encrypted channel at load balancer or reverse proxy server, use Layer 4 or Layer 7 load balancers, and use session affinity or no session affinity? For more information, see [Load Balancing in Exchange 2016](https://blogs.technet.com/b/exchange/archive/2015/10/08/load-balancing-in-exchange-2016.aspx).
    
- **Namespace planning**: What versions of Exchange are present, are you using the bound or unbound namespace model, and are you using *split-brain DNS* (configuring different IP addresses for the same host based on internal vs. external access)? For more information, see [Namespace Planning in Exchange 2016](https://blogs.technet.com/b/exchange/archive/2015/10/06/namespace-planning-in-exchange-2016.aspx).
    
- **Client connectivity**: What services will your clients use (web-based services, POP, IMAP, etc.) and what versions of Exchange are involved? For more information, see the following topics:
    
  - [Client Connectivity in an Exchange 2016 Coexistence Environment with Exchange 2013](https://blogs.technet.com/b/exchange/archive/2015/10/28/client-connectivity-in-an-exchange-2016-coexistence-environment-with-exchange-2013.aspx)
    
  - [Client Connectivity in an Exchange 2016 Coexistence Environment with Exchange 2010](https://blogs.technet.com/b/exchange/archive/2015/10/26/client-connectivity-in-an-exchange-2016-coexistence-environment-with-exchange-2010.aspx)
    
  - [Client Connectivity in an Exchange 2016 Coexistence Environment with Mixed Exchange Versions](https://blogs.technet.com/b/exchange/archive/2015/10/30/client-connectivity-in-an-exchange-2016-coexistence-environment-with-mixed-exchange-versions.aspx)
    
## Certificate requirements for Exchange services
<a name="CertRequirements"> </a>

The Exchange services that certificates can be assigned to are described in the following table.
  
****

|**Service**|**Description**|
|:-----|:-----|
|IIS (HTTP)  <br/> |By default, the following services are offered under the default website in the Client Access (frontend) services on a Mailbox server, and are used by clients to connect to Exchange:  <br/> • Autodiscover  <br/> • Exchange ActiveSync  <br/> • Exchange admin center  <br/> • Exchange Web Services  <br/> • Offline address book (OAB) distribution  <br/> • Outlook Anywhere (RPC over HTTP)  <br/> • Outlook MAPI over HTTP  <br/> • Outlook on the web  <br/> • Remote PowerShell<sup>\*</sup> <br/> Because you can only associate a single certificate with a website, all the DNS names that clients use to connect to these services need to be included in the certificate. You can accomplish this by using a SAN certificate or a wildcard certificate.  <br/> |
|POP or IMAP  <br/> |The certificates that are used for POP or IMAP can be different from the certificate that's used for IIS. However, to simplify administration, we recommend that you also include the host names that are used for POP or IMAP in your IIS certificate, and use the same certificate for all of these services.  <br/> |
|SMTP  <br/> |SMTP connections from clients or messaging servers are accepted by one or more Receive connectors that are configured in the Front End Transport service on the Exchange server. For more information, see [Receive connectors](../../mail-flow/connectors/receive-connectors.md).  <br/> To require TLS encryption for SMTP connections, you can use a separate certificate for each Receive connector. The certificate must include the DNS name that's used by the SMTP clients or servers to connect to the Receive connector. To simplify certificate management, consider including all DNS names for which you have to support TLS traffic in a single certificate.  <br/> To require *mutual TLS authentication*, where the SMTP connections between the source and destination servers are both encrypted and authenticated, see [Domain Security](http://technet.microsoft.com/library/bce3dbca-30a3-4343-924e-4ccf9e3fe0e1.aspx).  <br/> |
|Unified Messaging (UM)  <br/> |For more information, see [Deploying Certificates for UM](http://technet.microsoft.com/library/95658f6f-eac2-4674-90e7-f2d3f25c5242.aspx).  <br/> |
|Hybrid deployment with Microsoft Office 365  <br/> |For more information, see [Certificate Requirements for Hybrid Deployments](http://technet.microsoft.com/library/48d532cc-29f9-4009-9d2d-f19a9c13c320.aspx).  <br/> |
|Secure/Multipurpose Internet Mail Extensions (S/MIME)  <br/> |For more information, see [S/MIME for message signing and encryption](../../policy-and-compliance/smime.md).  <br/> |
   
<sup>\*</sup> Kerberos authentication and Kerberos encryption are used for remote PowerShell access, from both the Exchange admin center and the Exchange Management Shell. Therefore, you don't need to configure your certificates for use with remote PowerShell, as long as you connect directly to an Exchange server (not to a load balanced namespace). To use remote PowerShell to connect to an Exchange server from a computer that isn't a member of the domain, or to connect from the Internet, you need to configure your certificates for use with remote PowerShell. 
  
## Best practices for Exchange certificates
<a name="BestPractices"> </a>

Although the configuration of your organization's digital certificates will vary based on its specific needs, information about best practices has been included to help you choose the digital certificate configuration that's right for you.
  
- **Use as few certificates as possible**: Very likely, this means using SAN certificates or wildcard certificates. In terms of interoperability with Exchange, both are functionally equivalent. The decision on whether to use a SAN certificate vs a wildcard certificate is more about the key capabilities or limitations (real or perceived) for each type of certificate as described in the [Digital certificates overview](certificates.md#Overview).
    
    For example, if all of your common names will be in the same level of contoso.com, it doesn't matter if you use a SAN certificate or a wildcard certificate. But, if need to use the certificate for autodiscover.contoso.com, autodiscover.fabrikam.com, and autodiscover.northamerica.contoso.com, you need to use a SAN certificate.
    
- **Use certificates from a commercial CA for client and external server connections**: Although you can configure most clients to trust any certificate or certificate issuer, it's much easier to use a certificate from a commercial CA for client connections to your Exchange servers. No configuration is required on the client to trust a certificate that's issued by a commercial CA. Many commercial CAs offer certificates that are configured specifically for Exchange. You can use the EAC or the Exchange Management Shell to generate certificate requests that work with most commercial CAs.
    
- **Choose the right commercial CA**: Compare certificate prices and features between CAs. For example:
    
  - Choose a CA that says it supports "Unified Communications" (UC) certificates for use with Exchange. For more information, see [Unified Communications certificate partners](https://go.microsoft.com/fwlink/p/?LinkID=282625).
    
  - Verify that the CA is trusted by the clients (operating systems, browsers, and mobile devices) that connect to your Exchange servers.
    
  - Verify that the CA supports the kind of certificate that you need. For example, not all CAs support SAN certificates, the CA might limit the number of common names that you can use in a SAN certificate, or the CA may charge extra based on the number of common names in a SAN certificate.
    
  - See if the CA offers a grace period during which you can add additional common names to SAN certificates after they're issued without being charged.
    
  - Verify that the certificate's license allows you to use the certificate on the required number of servers. Some CAs only allow you to use the certificate on one server.
    
- **Use the Exchange certificate wizard**: A common error when you create certificates is to forget one or more common names that are required for the services that you want to use. The certificate wizard in the Exchange admin center helps you include the correct list of common names in the certificate request. The wizard lets you specify the services that will use the certificate, and includes the common names that you need to have in the certificate for those services. Run the certificate wizard when you've deployed your initial set of Exchange 2016 servers and determined which host names to use for the different services for your deployment.
    
- **Use as few host names as possible**: Minimizing the number of host names in SAN certificates reduces the complexity that's involved in certificate management. Don't feel obligated to include the host names of individual Exchange servers in SAN certificates if the intended use for the certificate doesn't require it. Typically, you only need to include the DNS names that are presented to the internal clients, external clients, or external servers that use the certificate to connect to Exchange.
    
    For a simple Exchange 2016 organization named Contoso, this is a hypothetical example of the minimum host names that would be required:
    
  - **mail.contoso.com**: This host name covers most connections to Exchange, including Outlook, Outlook on the web, OAB distribution, Exchange Web Services, POP3, IMAP4, SMTP, Exchange admin center, and Exchange ActiveSync.
    
  - **autodiscover.contoso.com**: This specific host name is required by clients that support Autodiscover, including Outlook, Exchange ActiveSync, and Exchange Web Services clients. For more information, see [Autodiscover service](autodiscover.md).
    
  - **legacy.contoso.com**: This host name is required in a coexistence scenario with Exchange 2010. If you'll have clients with mailboxes on Exchange 2010 servers, configuring a legacy host name prevents your users from having to learn a second URL during the upgrade process.
    
## Properties of the default self-signed certificates
<a name="DefaultCertificateProperties"> </a>

Some of the more interesting properties of the default self-signed certificates that are visible in the Exchange admin center and/or the Exchange Management Shell on an Exchange server are described in the following table.
  
****

|**Name** (`FriendlyName`)  <br/> |**Microsoft Exchange** <br/> |**Microsoft Exchange Server Auth Certificate** <br/> |**WMSVC** <br/> |
|:-----|:-----|:-----|:-----|
|**Subject** <br/> | `CN=<ServerName>`: For example, `CN=Mailbox01`.  <br/> | `CN=Microsoft Exchange Server Auth Certificate` <br/> | `CN=WMSvc-<ServerName>`: For example, `CN=WMSvc-Mailbox01`.  <br/> |
|**Subject Alternative Names** (`CertificateDomains`)  <br/> | _\<ServerName\>_: For example, Mailbox01.  <br/> _\<ServerFQDN\>_: For example, Mailbox01.contoso.com.  <br/> |none  <br/> |WMSvc- _\<ServerName\>_: For example, WMSvc-Mailbox01.  <br/> |
|**Has private key** (`HasPrivateKey`)  <br/> |**Yes** (True)  <br/> |**Yes** (True)  <br/> |**Yes** (True)  <br/> |
| `PrivateKeyExportable`\* <br/> |False  <br/> |True  <br/> |True  <br/> |
| `EnhancedKeyUsageList`\* <br/> |Server Authentication (1.3.6.1.5.5.7.3.1)  <br/> |Server Authentication (1.3.6.1.5.5.7.3.1)  <br/> |Server Authentication (1.3.6.1.5.5.7.3.1)  <br/> |
| `IISServices`\* <br/> | `IIS://<ServerName>/W3SVC/1, IIS://<ServerName>/W3SVC/2`: For example, `IIS://Mailbox01/W3SVC/1, IIS://Mailbox01/W3SVC/2`.  <br/> |none  <br/> |none  <br/> |
| `IsSelfSigned` <br/> |True  <br/> |True  <br/> |True  <br/> |
|**Issuer** <br/> | `CN=<ServerName>`: For example, `CN=Mailbox01`.  <br/> | `CN=Microsoft Exchange Server Auth Certificate` <br/> | `CN=WMSvc-<ServerName>`: For example, `CN=WMSvc-Mailbox01`.  <br/> |
| `NotBefore` <br/> |The date/time that Exchange was installed.  <br/> |The date/time that Exchange was installed.  <br/> |The date/time that the IIS Web Manager service was installed.  <br/> |
|**Expires on** (`NotAfter`)  <br/> |5 years after `NotBefore`.  <br/> |5 years after `NotBefore`.  <br/> |10 years after `NotBefore`.  <br/> |
|**Public key size** (`PublicKeySize`)  <br/> |2048  <br/> |2048  <br/> |2048  <br/> |
| `RootCAType` <br/> |Registry  <br/> |None  <br/> |Registry  <br/> |
|**Services** <br/> |IMAP, POP, IIS, SMTP  <br/> |SMTP  <br/> |None  <br/> |
   
\* These properties aren't visible in the standard view in the Exchange Management Shell. To see them, you need to specify the property name (exact name or wildcard match) with the **Format-Table** or **Format-List** cmdlets. For example: 
  
- `Get-ExchangeCertificate -Thumbprint <Thumbprint> | Format-List *`
    
- `Get-ExchangeCertificate -Thumbprint <Thumbprint> | Format-Table -Auto FriendlyName,*PrivateKey*`
    
For more information, see [get-ExchangeCertificate](http://technet.microsoft.com/library/e368589a-6510-4209-9f10-171d1990cd7d.aspx).
  
Further details about the default self-signed certificates that are visible in Windows Certificate Manger are described in the following table.
  
****

|**Friendly name** <br/> |**Microsoft Exchange** <br/> |**Microsoft Exchange Server Auth Certificate** <br/> |**WMSVC** <br/> |
|:-----|:-----|:-----|:-----|
|**Signature algorithm** <br/> |sha1RSA  <br/> |sha1RSA  <br/> |sha1RSA  <br/> |
|**Signature hash algorithm** <br/> |sha1  <br/> |sha1  <br/> |sha1  <br/> |
|**Key usage** <br/> |Digital Signature, Key Encipherment (a0)  <br/> |Digital Signature, Key Encipherment (a0)  <br/> |Digital Signature, Key Encipherment (a0), Data Encipherment (b0 00 00 00)  <br/> |
|**Basic constraints** <br/> | `Subject Type=End Entity`.  <br/> `Path Length Constraint=None`.  <br/> | `Subject Type=End Entity`.  <br/> `Path Length Constraint=None`.  <br/> |n/a  <br/> |
|**Thumbprint algorithm** <br/> |sha1  <br/> |sha1  <br/> |sha1  <br/> |
   
Typically, you don't use Windows Certificate Manger to manage Exchange certificates (use the Exchange admin center or the Exchange Management Shell). Note that the WMSVC certificate isn't an Exchange certificate.
  

