---
title: "Configure MAPI over HTTP"
ms.author: dmaguire
author: msdmaguire
manager: serdars
ms.date: 6/8/2018
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 2c07b1e6-8d07-4e73-8800-b306e2266c7d
description: "Summary: How to enable or disable MAPI over HTTP in your Exchange 2016 organization."
---

# Configure MAPI over HTTP

 **Summary**: How to enable or disable MAPI over HTTP in your Exchange 2016 organization.
  
In Exchange 2016, MAPI over HTTP can be set at the organization level or at the individual mailbox level. Mailbox-level settings always take precedence over organization-wide settings. At the organization level, MAPI over HTTP is enabled by default in new Exchange 2016 topologies, in topologies where all servers have been upgraded from Exchange 2010 to Exchange 2016, and in mixed topologies consisting of both Exchange 2010 and Exchange 2016 servers.
  
> [!NOTE]
> When MAPI over HTTP is enabled at the organization level, the  `MapiHttpEnabled` parameter of the  `Get-OrganizationConfig` cmdlet is set to **True**. 
  
This article describes how to configure and then enable MAPI over HTTP for Exchange 2016 organizations that contain Exchange 2013 servers, or for any topology where MAPI over HTTP has been previously disabled. You can also use the procedures in this article to disable MAPI over HTTP at the organization level.
  
 This article also describes how to enable or disable MAPI over HTTP for an individual mailbox. At the mailbox level, you have the ability to allow or block MAPI over HTTP connections internally, externally, or both. In all cases, when MAPI over HTTP is disabled, connections will be made with Outlook Anywhere. 
  
## Configure MAPI over HTTP

Complete the following steps to configure MAPI over HTTP for your organization. These steps assume you have already configured the prerequisites described in [MAPI over HTTP in Exchange 2016](mapi-over-http.md). Once configured (steps 1-3), use step 4 to enable or disable specific permission scenarios at the organization level, at the mailbox level, or both.
  
1. **Virtual directory configuration**: By default, Exchange 2016 creates a virtual directory for MAPI over HTTP. You use the **Set-MapiVirtualDirectory** cmdlet to configure the virtual directory. You must configure an internal URL, an external URL, or both. For more information see, [Set-MapiVirtualDirectory](http://technet.microsoft.com/library/c9308fe6-3b61-4d99-a5f2-ef47abbc7656.aspx).
    
    For example, to configure the default MAPI virtual directory on the local Exchange server by setting the internal URL value to https://contoso.com/mapi, and the authentication method to  `Negotiate`, run the following command:
    
  ```
  Set-MapiVirtualDirectory -Identity "Contoso\mapi (Default Web Site)" -InternalUrl https://Contoso.com/mapi -IISAuthenticationMethods Negotiate
  ```

2. **Certificate configuration**: The digital certificate used by your Exchange environment must include the same  _InternalURL_ and  _ExternalURL_ values that are defined on the MAPI virtual directory. For more information on Exchange 2016 certificate management, see [Digital certificates and encryption in Exchange 2016](../../architecture/client-access/certificates.md). Make sure the Exchange certificate is trusted on the Outlook client workstation and that there are no certificate errors, especially when you access the URLs configured on the MAPI virtual directory.
    
3. **Update server rules**: Verify that your load balancers, reverse proxies, and firewalls are configured to allow access to the MAPI over HTTP virtual directory.
    
4. Use the following steps to enable MAPI over HTTP in your entire Exchange organization, or enable MAPI over HTTP for one or more individual mailboxes.
    
    > [!NOTE]
    > After running the commands below, Outlook clients with MAPI over HTTP enabled will see a message to restart Outlook to use MAPI over HTTP. 
  
    **Enable MAPI over HTTP in your Exchange organization**
    
    In Exchange 2016, MAPI over HTTP connections are set with the  `MapiHttpEnabled` parameter on the  `set-OrganizationConfig` cmdlet. **True** indicates MAPI over HTTP connections are allowed for all mailboxes in the organization. **False** will prevent MAPI over HTTP connections for all mailboxes. 
    
    Note that connection settings made at the mailbox level take precedence over any organization-wide settings.
    
    The following example enables MAPI over HTTP connections for the entire organization:
    
  ```
  Set-OrganizationConfig -MapiHttpEnabled $true
  ```

    For more information see [get-OrganizationConfig](http://technet.microsoft.com/library/3e07e5cc-5066-40e7-8642-845ad080f9a9.aspx).
    
    **Enable MAPI over HTTP for an individual mailbox**
    
    To enable or disable MAPI over HTTP at the mailbox level, use the  `set-Casmailbox` cmdlet with the  `MapiHttpEnabled` parameter. The default value is **Null**, which means the mailbox will follow organization-level settings. The other options are **True** to enable MAPI over HTTP and **False** to disable. In either case, the setting would override any organization-level settings. 
    
    If MAPI over HTTP is enabled at the organization level but disabled for a mailbox, that mailbox will use Outlook Anywhere connections.
    
    The following example enables MAPI over HTTP connections for a single mailbox:
    
  ```
  Set-CasMailbox <user or mailbox ID> -MapiHttpEnabled $true
  ```

    For more information, see [Set-CASMailbox](http://technet.microsoft.com/library/ff7d4dc5-755e-4005-a0a3-631eed3f9b3b.aspx).
    
### Test MAPI over HTTP connections

You can test the end-to-end MAPI over HTTP connection by using the **Test-OutlookConnectivity** cmdlet. To use the **Test-OutlookConnectivity** cmdlet, the Microsoft Exchange Health Manager (MSExchangeHM) service must be started. 
  
The following example tests the MAPI over HTTP connection from the Exchange server named ContosoMail.
  
```
Test-OutlookConnectivity -RunFromServerId ContosoMail -ProbeIdentity OutlookMapiHttpSelfTestProbe
```

A successful test returns output that's similar to the following example:
  
```
MonitorIdentity                                          StartTime              EndTime                Result      Error     Exception
---------------                                          ---------              -------                ------      -----     ---------
OutlookMapiHttp.Protocol\OutlookMapiHttpSelfTestProbe    2/14/2016 7:15:00 AM   2/14/2016 7:15:10 AM   Succeeded
```

For more information, see [Test-OutlookConnectivity](http://technet.microsoft.com/library/09d810f1-0550-4cd3-8feb-f524018a5d6b.aspx).
  
Logs for MAPI over HTTP activity are at the following locations:
  
- %ExchangeInstallPath%Logging\MAPI Address Book Service\
    
- %ExchangeInstallPath%Logging\MAPI Client Access\
    
- %ExchangeInstallPath%Logging\HttpProxy\Mapi\
    
## Combining MAPI over HTTP configurations and internal or external connections

The following table summarizes the different setting combinations allowable at the organization level, in combination with different connection settings on individual mailboxes. As described previously in this article, the organization settings are made with  `Set-Organization -MapiHttpEnabled <parameter>` and mailbox settings are made with  `Set-Casmailbox <user ID or mailbox ID> -MapiHttpEnabled <parameter>`.
  
In addition, you can use the  `MapiBlockOutlookExternalConnectivity` parameter with  `Set-Casmailbox` to allow or deny external connections to a mailbox through Outlook Anywhere or MAPI over HTTP. **True** will allow only internal connections to the mailbox. **False** is the default setting. 
  
|**Organization setting (MapiHttpEnabled value)**|**User or mailbox setting (MapiHttpEnabled value)**|**User or mailbox setting (MapiBlockOutlookExternalConnectivity setting)**|**AutoDiscover result**|
|:-----|:-----|:-----|:-----|
|$true  <br/> |$null  <br/> |$false  <br/> |MAPI over HTTP, internal and external  <br/> |
|$true  <br/> |$null  <br/> |$true  <br/> |MAPI over HTTP, internal only  <br/> |
|$true  <br/> |$true  <br/> |$false  <br/> |MAPI over HTTP, internal and external  <br/> |
|$true  <br/> |$true  <br/> |$true  <br/> |MAPI over HTTP, internal only  <br/> |
|$true  <br/> |$false  <br/> |$false  <br/> |Outlook Anywhere, internal and external  <br/> |
|$true  <br/> |$false  <br/> |$true  <br/> |Outlook Anywhere, internal only  <br/> |
|$false  <br/> |$null  <br/> |$false  <br/> |Outlook Anywhere, internal and external  <br/> |
|$false  <br/> |$null  <br/> |$true  <br/> |Outlook Anywhere, internal only  <br/> |
|$false  <br/> |$true  <br/> |$false  <br/> |MAPI over HTTP, internal and external  <br/> |
|$false  <br/> |$true  <br/> |$true  <br/> |MAPI over HTTP, internal only  <br/> |
|$false  <br/> |$false  <br/> |$false  <br/> |Outlook Anywhere, internal and external  <br/> |
|$false  <br/> |$false  <br/> |$true  <br/> |Outlook Anywhere, internal only  <br/> |
   
## Manage MAPI over HTTP

You can manage the configuration of MAPI over HTTP by using the following cmdlets:
  
- [Set-MapiVirtualDirectory](http://technet.microsoft.com/library/c9308fe6-3b61-4d99-a5f2-ef47abbc7656.aspx)
    
- [Get-MapiVirtualDirectory](http://technet.microsoft.com/library/6837cb55-6734-4a28-9062-7227f57dafb2.aspx)
    
- [New-MapiVirtualDirectory](http://technet.microsoft.com/library/acb5be3d-f42b-4685-ba2a-680731281edf.aspx)
    
- [Remove-MapiVirtualDirectory](http://technet.microsoft.com/library/eff7df8c-3c92-4004-89dd-0a06511e8668.aspx)
    

