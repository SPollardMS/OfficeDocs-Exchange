---
title: Learn more about types of new Exchange certificates
ms.prod: EXCHANGE
ms.assetid: eac77d2f-052a-4f7e-851d-3aa56596d01e
---


# Learn more about types of new Exchange certificates

When you create a certificate for use with Exchange, you have two choices. These choices are described in the following sections.
  
    
    


## Create a certificate request for a certification authority

You create a certificate request (also known as a certificate signing request or CSR) that you send to the certification authority (CA). The CA creates the certificate based on the information in the request, and sends the certificate to you. After you receive the certificate, you complete the request by installing the certificate file or files on the Exchange server.
  
    
    
For more information, see the following topics:
  
    
    

-  [Create an Exchange 2016 certificate request for a certification authority](create-an-exchange-2016-certificate-request-for-a-certification-authority.md)
    
  
-  [Complete a pending Exchange 2016 certificate request](complete-a-pending-exchange-2016-certificate-request.md)
    
  
There are two basic types of CAs:
  
    
    

- **An internal CA** The certificate is issued by a public key infrastructure (PKI) in your organization, for example, Active Directory Certificate Services (AD CS). Although it's easy and convenient to issue a certificate from an internal CA (after you install and configure the PKI), the certificate isn't automatically trusted by client computers and mobile devices. You need to manually add the certificate to the trusted root certificate store on all client computers and devices, but not all mobile devices allow changes to the trusted root certificate store.
    
  
- **A commercial CA** You purchase the certificate from a trusted commercial CA. Although you need to plan ahead to minimize the cost and number of certificates that are required, all clients, devices, and servers automatically trust the certificate.
    
  
Typically, you'll want to use certificates from a commercial CA for client connections and external server connections to Exchange. Although you can configure most clients to trust any certificate or certificate issuer, it's much easier to use a certificate from a commercial CA. No configuration is required on the client to trust these certificates, and many commercial CAs offer certificates that are configured specifically for Exchange.
  
    
    
For more information, see the following topics:
  
    
    

-  [Digital certificates and encryption in Exchange 2016](digital-certificates-and-encryption-in-exchange-2016.md)
    
  
-  [Unified Communications certificate partners](https://go.microsoft.com/fwlink/p/?LinkID=282625)
    
  

## Create a self-signed certificate

A self-signed certificate is a certificate that's signed by the application that created it. In this case, the certificate is created and signed by Exchange. A self-signed certificates is very easy to create, but like a certificate that's issued by an internal CA, the certificate isn't automatically trusted by client computers and mobile devices. And, some services don't work with self-signed certificates (for example, Outlook Anywhere).
  
    
    
For more information about creating a self-signed certificate, see  [Create a new Exchange 2016 self-signed certificate](create-a-new-exchange-2016-self-signed-certificate.md).
  
    
    
Exchange automatically installs a self-signed certificate named Microsoft Exchange that's used to encrypt network traffic between Exchange servers and services in your organization. Typically, you don't need to replace the Microsoft Exchange certificate for this purpose. You do need additional certificates (likely, purchased from a commercial CA) to encrypt connections to Exchange servers by internal and external clients, and to force the encryption of SMTP connections between Exchange servers and external messaging servers.
  
    
    

