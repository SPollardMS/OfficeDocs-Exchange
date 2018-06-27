---
title: "Certificate procedures in Exchange 2016"
ms.author: chrisda
author: chrisda
manager: serdars
ms.date: 6/7/2018
ms.audience: ITPro
ms.topic: overview
ms.prod: exchange-server-itpro
localization_priority: Normal
ms.assetid: 8975848d-07f0-4643-9eac-20aece69945f

description: "Summary: A list certificate management tasks in Exchange 2016."
---

# Certificate procedures in Exchange 2016

 **Summary**: A list certificate management tasks in Exchange 2016.
  
Ensuring that certificates are installed and configured correctly is key to delivering a secure messaging infrastructure for the enterprise. In Exchange Server 2016, you can manage certificates in the Exchange admin center (EAC), and in the Exchange Management Shell. Certificate management in the EAC has been improved over certificate management in the Exchange Management Console in Exchange Server 2010. Specifically, certificate management in the EAC can help administrators by:
  
- Minimizing the number of certificates that are required.
    
- Minimizing the interaction that's required for certificates.
    
- Allowing the centralized installation and management of certificates on all Exchange servers in the organization.
    
For more information about certificates in Exchange 2016, see [Digital certificates and encryption in Exchange 2016](certificates.md).
  
The tasks that are associated with certificate management in Exchange are described in the following table.
  
|**Task**|**EAC**|**Exchange Management Shell**|**Topic**|**Comments**|
|:-----|:-----|:-----|:-----|:-----|
|Create a new self-signed certificate on an Exchange server.  <br/> |**Servers** \> **Certificates** \> select the server \> **Add** ![Add icon](../../media/ITPro_EAC_AddIcon.png) \> **Create a self-signed certificate** <br/> |**New-ExchangeCertificate** <br/> |[Create a new Exchange 2016 self-signed certificate](create-self-signed-certificates.md) <br/> |You can create new self-signed certificates and configure the certificates for Exchange services in one step.  <br/> |
|Create a new certificate request (also known as a certificate signing request or CSR) for a certification authority (CA).  <br/> |**Servers** \> **Certificates** \> select the server \> **Add** ![Add icon](../../media/ITPro_EAC_AddIcon.png) \> **Create a request for a certificate from a certification authority** <br/> |**New-ExchangeCertificate** with the _GenerateRequest_ switch.  <br/> |[Create an Exchange 2016 certificate request for a certification authority](create-ca-certificate-requests.md) <br/> |The procedures are the same for an internal CA (for example, Active Directory Certificate Services) or a commercial CA.  <br/> |
|Complete a pending certificate request on an Exchange server.  <br/> |**Servers** \> **Certificates** \> select the server \> select the certificate request \> click the **Complete** link in the details pane.  <br/> |**Import-ExchangeCertificate** <br/> |[Complete a pending Exchange 2016 certificate request](complete-pending-certificate-requests.md) <br/> |After you receive the certificate file or files from the CA, you install them on the Exchange server.  <br/> |
|Assign a certificate to Exchange services.  <br/> |**Servers** \> **Certificates** \> select the server \> select the certificate \> **Edit** ![Edit icon](../../media/ITPro_EAC_EditIcon.png) \> **Services** tab.  <br/> |**Enable-ExchangeCertificate** <br/> |[Assign certificates to Exchange 2016 services](assign-certificates-to-services.md) <br/> |The procedures are the same for self-signed certificates, or certificates that were issued by a CA.  <br/> For certificates issued by a CA, you can only assign the certificates to Exchange services after you complete the pending certificate request (install the certificate on the Exchange server).  <br/> |
|Delete an existing certificate or certificate request from an Exchange server.  <br/> |**Servers** \> **Certificates** \> select the server \> select the certificate \> **Delete** ![Delete icon](../../media/ITPro_EAC_DeleteIcon.png)           <br/> |**Remove-ExchangeCertificate** <br/> |n/a  <br/> |The procedures are the same for self-signed certificates, certificate requests, or certificates issued by a CA.  <br/> |
|Renew an existing certificate on an Exchange server.  <br/> |**Servers** \> **Certificates** \> select the server \> select the certificate \> click **Renew** in the details pane.  <br/> |**Get-ExchangeCertificate** and **New-ExchangeCertificate** <br/> |[Renew an Exchange 2016 certificate](renew-certificates.md) <br/> |For self-signed certificates, you renew the certificate in one step.  <br/> For certificates that were issued by a CA, you create a request to renew the certificate, and send the request to the CA.  <br/> The notification viewer in the EAC displays a warning when a certificate on any Exchange server in your organization is about to expire.  <br/> |
|Export an existing certificate or certificate request from an Exchange server.  <br/> |**Servers** \> **Certificates** \> select the server \> select the certificate \> **More options** ![More Options icon](../../media/ITPro_EAC_MoreOptionsIcon.png) \> **Export Exchange Certificate** <br/> |**Export-ExchangeCertificate** <br/> |[Export a certificate from an Exchange server](export-certificates.md) <br/> |You can only export valid (unexpired) certificates where the **PrivateKeyExportable** property has the value `True`.  <br/> You can only export pending certificate requests in the Exchange Management Shell. You can't import an exported pending certificate request.  <br/> |
|Import (install) a certificate on an Exchange server.  <br/> |**Servers** \> **Certificates** \> select the server \> **More options** ![More Options icon](../../media/ITPro_EAC_MoreOptionsIcon.png) \> **Import Exchange Certificate** <br/> |**Import-ExchangeCertificate** <br/> |[Import or install a certificate on an Exchange 2016 server](import-certificates.md) <br/> |Import a certificate that was exported from another server.  <br/> |
|View existing certificates or certificate requests on an Exchange server, or view the details for a specific certificate or certificate request.  <br/> |**Servers** \> **Certificates** \> select the server  <br/> For details on a specific certificate or certificate request, select the item from the list, and then click **Edit** ![Edit icon](../../media/ITPro_EAC_EditIcon.png).  <br/> |**Get-ExchangeCertificate** <br/> |n/a  <br/> |Some certificate properties are visible in the details pane in the EAC when you select the certificate or certificate request from the list.  <br/> Some certificate properties aren't visible in the standard view in the Exchange Management Shell. To see them, you need to specify the property name (exact name or wildcard match) with the **Format-Table** or **Format-List** cmdlets. For more information, see [Get-ExchangeCertificate](http://technet.microsoft.com/library/e368589a-6510-4209-9f10-171d1990cd7d.aspx).  <br/> |
   

