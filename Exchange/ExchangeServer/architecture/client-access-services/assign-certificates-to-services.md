---
title: "Assign certificates to Exchange 2016 services"
ms.author: chrisda
author: chrisda
manager: serdars
ms.date: 4/19/2018
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.collection: Strat_EX_Admin
ms.assetid: f4c170cd-76d3-499d-a34e-8a2bc8724c52
description: "Learn how to assign certificates to Exchange services in Exchange 2016."
---

# Assign certificates to Exchange 2016 services

Learn how to assign certificates to Exchange services in Exchange 2016.
  
After you install a certificate on an Exchange Server 2016 server, you need to assign the certificate to one or more Exchange services before the Exchange server is able to use the certificate for encryption. You can assign certificates to services in the Exchange admin center (EAC) or in the Exchange Management Shell. Once you assign a certificate to a service, you can't remove the assignment. If you no longer want to use a certificate for a specific service, you need to assign another certificate to the service, and then remove the certificate that you don't want to use.
  
The available Exchange services are described in the following table.
  
****

|**Service**|**Uses**|
|:-----|:-----|
|IIS  <br/> | TLS encryption for internal and external client connections that use HTTP. This includes:  <br/>  Autodiscover  <br/>  Exchange ActiveSync  <br/>  Exchange admin center  <br/>  Exchange Web Services  <br/>  Offline address book (OAB) distribution  <br/>  Outlook Anywhere (RPC over HTTP)  <br/>  Outlook MAPI over HTTP  <br/>  Outlook on the web  <br/> |
|IMAP  <br/> |TLS encryption for IMAP4 client connections.  <br/> Don't assign a wildcard certificate to the IMAP4 service. Instead, use the **Set-ImapSettings** cmdlet to configure the fully qualified domain name (FQDN) that clients use to connect to the IMAP4 service.  <br/> |
|POP  <br/> |TLS encryption for POP3 client connections.  <br/> Don't assign a wildcard certificate to the POP3 service. Instead, use the **Set-PopSettings** cmdlet to configure the FQDN that clients use to connect to the POP3 service.  <br/> |
|SMTP  <br/> |TLS encryption for external SMTP client and server connections.  <br/> Mutual TLS authentication between Exchange and other messaging servers.  <br/> When you assign a certificate to SMTP, you are prompted to replace the default Exchange self-signed certificate that's used to encrypt SMTP communication between internal Exchange servers. Typically, you don't need to replace the default SMTP certificate.  <br/> |
| Unified Messaging (  `UM`)  <br/> |TLS encryption for client connections to the backend UM service on Mailbox servers.  <br/> You can only assign a certificate to the UM service when the UM startup mode property of the service is set to TLS or Dual. If the UM startup mode is set to the default value TCP, you can't assign the certificate to the UM service. For more information, see [Configure the Startup Mode on a Mailbox Server](http://technet.microsoft.com/library/4457d6a0-52bd-4269-8cb5-d34d7fe9bfc3.aspx).  <br/> |
|Unified Messaging Call Router ( `UMCallRouter`)  <br/> |TLS encryption for client connections to the UM Call Router service in the Client Access services on Mailbox servers.  <br/> You can only assign a certificate to the UM Call Router service when the UM startup mode property of the service is set to TLS or Dual. If the UM startup mode is set to the default value TCP, you can't assign the certificate to the UM Call Router service. For more information, see [Configure the Startup Mode on a Client Access Server](http://technet.microsoft.com/library/71cc9061-9e3c-4b4a-8dbe-f590ca5bcee8.aspx).  <br/> |
   
## What do you need to know before you begin?

- Estimated time to complete: 5 minutes.
    
- After you do the procedures in this topic, you might need to restart Internet Information Services (IIS). In some scenarios, Exchange might continue to use the previous certificate for encrypting and decrypting the cookie that's used for Outlook on the web (formerly known as Outlook Web App) authentication. We recommend restarting IIS in environments that use Layer 4 load balancing.
    
- If you renew or replace a certificate that was issued by a CA on a subscribed Edge Transport server, you need to remove the old certificate, and then delete and recreate the Edge Subscription. For more information, see [Edge Subscription process](../../architecture/edge-transport-servers/edge-subscriptions.md#Process).
    
- To learn how to open the Exchange Management Shell in your on-premises Exchange organization, see **Open the Exchange Management Shell**.
    
- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Client Access services security" entry in the [Clients and mobile devices permissions](../../permissions/feature-permissions/clients-and-mobile-devices.md) topic. 
    
- For information about keyboard shortcuts that may apply to the procedures in this topic, see [Keyboard shortcuts in the Exchange admin center](../../about-documentation/keyboard-shortcuts-in-eac.md).
    
> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at: [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351). 
  
## Use the EAC to assign a certificate to Exchange services

1. Open the EAC, and navigate to **Servers** > **Certificates**.
    
2. In the **Select server** list, select the Exchange server that holds the certificate. 
    
3. Select the certificate that you want to configure, and then click **Edit**![Edit icon](../../media/ITPro_EAC_EditIcon.png). The certificate needs to have the **Status** value **Valid**.
    
4. On the **Services** tab, in the **Specify the services you want to assign this certificate to** section, select the services. Remember, you can add services, but you can't remove them. When you are finished, click **Save**.
    
## Use the Exchange Management Shell to assign a certificate to Exchange services

To assign a certificate to Exchange services, use the following syntax:
  
```
Enable-ExchangeCertificate -Thumbprint <Thumbprint> -Services <Service1>,<Service2>... [-Server <ServerIdentity>]
```

This example assigns the certificate that has the thumbprint value  `434AC224C8459924B26521298CE8834C514856AB` to the POP, IMAP, IIS, and SMTP services. 
  
```
Enable-ExchangeCertificate -Thumbprint 434AC224C8459924B26521298CE8834C514856AB -Services POP,IMAP,IIS,SMTP
```

You can find the certificate thumbprint value by using the **Get-ExchangeCertificate** cmdlet. 
  
## How do you know this worked?

To verify that you have successfully assigned a certificate to one or more Exchange services, use either of the following procedures:
  
- In the EAC at **Servers** > **Certificates**, verify the server where you installed the certificate is selected. Select the certificate, and in the details pane, verify that the **Assigned to services property** contains the services that you selected. 
    
- In the Exchange Management Shell on the server where you installed the certificate, run the following command to verify the Exchange services for the certificate:
    
  ```
  Get-ExchangeCertificate | Format-List FriendlyName,Subject,CertificateDomains,Thumbprint,Services
  ```


