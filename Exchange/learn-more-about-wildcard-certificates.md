---
title: Learn more about wildcard certificates
ms.prod: EXCHANGE
ms.assetid: 63a840b9-f126-487d-b267-03ee15e4ddf2
---


# Learn more about wildcard certificates

A wildcard certificate's **Subject** field contains the common name as the wildcard character (*) plus a single domain or subdomain. For example, *.contoso.com or *.eu.contoso.com. The *.contoso.com certificate can be used for any hosts in the contoso.com domain. Likewise, the *.eu.contoso.com certificate can be used for any hosts in the eu.contoso.com subdomain.
  
    
    

The key limitations of wildcard certificates are:
- You can't use wildcard certificates with other top-level domains (TLDs). For example, you can't use the *.contoso.com certificate for contoso.net hosts.
    
  
- You can only use wildcard certificates for host names at the level of the wildcard. For example, you can't use the *.contoso.com certificate for www.eu.contoso.com. Or, you can't use the *.eu.contoso.com certificate for www.uk.eu.contoso.com.
    
  
- Older clients, devices, applications, or services might not support wildcard certificates.
    
  
In terms of interoperability with Exchange, a wildcard certificate and a subject alternative name (SAN) certificate are functionally equivalent. The decision on whether to use a SAN certificate vs a wildcard certificate is more about the key capabilities or limitations (real or perceived) for each type of certificate.For example, if all of your common names will be in the same level of contoso.com, it doesn't matter if you use a SAN certificate or a wildcard certificate. But, if need to use the certificate for autodiscover.contoso.com, autodiscover.fabrikam.com, and autodiscover.northamerica.contoso.com, you need to use a SAN certificate.For more information about wildcard certificates and SAN certificates, see  [Digital certificates overview](digital-certificates-and-encryption-in-exchange-2016.md#Overview).
