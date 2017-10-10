---
title: Learn more about including domains in a certificate
ms.prod: EXCHANGE
ms.assetid: c7bb64c0-0a86-4cd0-bd4c-2356943a5426
---


# Learn more about including domains in a certificate

Your new Exchange certificate request can contain one or more domain names. 
  
    
    

This page lists the host names that will be included in the certificate request for a subject alternative name (SAN) certificate, or a certificate for a single host name. The host name that's used in the certificate's **Subject** field is bold, which can be hard to see if that host name is selected. You can verify the host name entries that are required in the certificate based on the selections that you made on the previous page. Or, you can ignore the values from the last page and add, edit, or remove host name values.
- If you want a SAN certificate, the **Subject** field still requires one common name (CN) value. To select the host name for the certificate's **Subject** field, select the value and click **Set as common name** (check mark). The value should now appear bold.
    
  
- If you want a certificate for a single host name, select the other values one at a time and click **Remove** (
  
    
    
![Remove icon](images/ITPro_EAC_RemoveIcon.png)
  
    
    
).
    
  
For more information about SAN certificates and single host name certificates, see  [Digital certificates overview](digital-certificates-and-encryption-in-exchange-2016.md#Overview).
