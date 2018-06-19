---
title: "Configure mail flow and client access"
ms.author: dstrome
author: dstrome
manager: serdars
ms.date: 6/8/2018
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.collection: Strat_EX_Admin
ms.assetid: 4acc7f2a-93ce-468c-9ace-d5f7eecbd8d4
description: "Summary: How to set up mail flow and client access in Exchange 2016."
---

# Configure mail flow and client access

 **Summary**: How to set up mail flow and client access in Exchange 2016.
  
After you've installed Microsoft Exchange Server 2016 in your organization, you need to configure it for mail flow and client access. Without these additional steps, you won't be able to send mail to the Internet and external clients such as Microsoft Office Outlook, and Exchange ActiveSync devices won't be able to connect to your Exchange organization.
  
The steps in this topic assume a basic Exchange deployment with a single Active Directory site and a single simple mail transport protocol (SMTP) namespace.
  
> [!IMPORTANT]
> This topic uses example values such as Ex2016MBX, contoso.com, mail.contoso.com, and 172.16.10.11. Replace the example values with the server names, FQDNs, and IP addresses for your organization. 
  
For additional management tasks related to mail flow and clients and devices, see [Mail flow and the transport pipeline](../../mail-flow/mail-flow.md) and [Clients and mobile](../../clients/clients.md).
  
## What do you need to know before you begin?

- Estimated time to complete this task: 50 minutes
    
- Procedures in this topic require specific permissions. See each procedure for its permissions information.
    
- You might receive certificate warnings when you connect to the Exchange admin center (EAC) website until you configure a secure sockets layer (SSL) certificate on the Mailbox server. You'll be shown how to do this later in this topic.
    
- For information about keyboard shortcuts that may apply to the procedures in this topic, see [Keyboard shortcuts in the Exchange admin center](../../about-documentation/exchange-admin-center-keyboard-shortcuts.md).
    
> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at: [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351). 
  
## Step 1: Create a Send connector
<a name="CreateConnector"> </a>

You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Send connectors" entry in the [Mail flow permissions](../../permissions/feature-permissions/mail-flow-permissions.md) topic. 
  
Before you can send mail to the Internet, you need to create a Send connector on the Mailbox server. Do the following.
  
1. Open the EAC by browsing to the URL of your Mailbox server. For example, https://Ex2016MBX/ECP.
    
2. Enter your user name and password in **Domain\user name** and **Password** and then click **Sign in**.
    
3. Go to **Mail flow** \> **Send connectors**. On the **Send connectors** page, click **New**![Add icon](../../media/ITPro_EAC_AddIcon.png).
    
4. In the **New send connector** wizard, specify a name for the Send connector and then select **Internet**. Click **Next**.
    
5. Verify that **MX record associated with recipient domain** is selected. Click **Next**.
    
6. Under **Address space**, click **Add**![Add icon](../../media/ITPro_EAC_AddIcon.png). In the **Add domain** window, make sure **SMTP** is selected in the **Type** field. In the **Fully Qualified Domain Name (FQDN)** field, enter \*. Click **Save**.
    
7. Make sure **Scoped send connector** isn't selected and then click **Next**.
    
8. Under **Source server**, click **Add**![Add icon](../../media/ITPro_EAC_AddIcon.png). In the **Select a Server** window, select a Mailbox server. After you've selected the server, click **Add** and then click **OK**.
    
9. Click **Finish**.
    
> [!NOTE]
> A default inbound Receive connector is created when Exchange 2016 is installed. This Receive connector accepts anonymous SMTP connections from external servers. You don't need to do any additional configuration if this is the functionality you want. If you want to restrict inbound connections from external servers, modify the **Default Frontend \<Mailbox server\>** Receive connector on the Mailbox server. 
  
### How do you know this step worked?

To verify that you have successfully created an outbound Send connector, do the following:
  
1. In the EAC, verify the new Send connector appears in **Mail flow** \> **Send connectors**.
    
2. Open Outlook Web App and send an email message to an external recipient. If the recipient receives the message, you've successfully configured the Send connector.
    
## Step 2: Add additional accepted domains
<a name="AddAcceptedDomain"> </a>

You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Accepted domains" entry in the [Mail flow permissions](../../permissions/feature-permissions/mail-flow-permissions.md) topic. 
  
By default, when you deploy a new Exchange 2016 organization in an Active Directory forest, Exchange uses the domain name of the Active Directory domain where Setup /PrepareAD was run. If you want recipients to receive and send messages to and from another domain, you must add the domain as an accepted domain. This domain is also added as the primary SMTP address on the default email address policy in the next step.
  
> [!IMPORTANT]
> A public Domain Name System (DNS) MX resource record is required for each SMTP domain for which you accept email from the Internet. Each MX record should resolve to the Internet-facing server that receives email for your organization. 
  
1. Open the EAC by browsing to the URL of your Mailbox server. For example, https://Ex2016MBX/ECP.
    
2. Enter your user name and password in **Domain\user name** and **Password** and then click **Sign in**.
    
3. Go to **Mail flow** \> **Accepted domains**. On the **Accepted domains** page, click **New**![Add icon](../../media/ITPro_EAC_AddIcon.png).
    
4. In the **New accepted domain** wizard, specify a name for the accepted domain. 
    
5. In the **Accepted domain** field, specify the SMTP recipient domain you want to add. For example, contoso.com. 
    
6. Select **Authoritative domain** and then click **Save**.
    
### How do you know this step worked?

To verify that you have successfully created an accepted domain, do the following:
  
- In the EAC, verify the new accepted domain appears in **Mail flow** \> **Accepted domains**.
    
## Step 3: Configure the default email address policy
<a name="ConfigEAP"> </a>

You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Email address policies" entry in the [Email address and address book permissions](../../permissions/feature-permissions/address-book-permissions.md) topic. 
  
If you added an accepted domain in the previous step and you want that domain to be added to every recipient in the organization, you need to update the default email address policy.
  
1. Open the EAC by browsing to the URL of your Mailbox server. For example, https://Ex2016MBX/ECP.
    
2. Enter your user name and password in **Domain\user name** and **Password** and then click **Sign in**.
    
3. Go to **Mail flow** \> **Email address policies**. On the **Email address policies** page, select **Default Policy** and then click **Edit**![Edit icon](../../media/ITPro_EAC_EditIcon.png).
    
4. On the **Default Policy Email Address Policy** page, click **Email Address Format**.
    
5. Under **Email address format**, click the SMTP address you want to change and then click **Edit**![Edit icon](../../media/ITPro_EAC_EditIcon.png).
    
6. On the **Email address format** page in the **Email address parameters** field, specify the SMTP recipient domain you want to apply to all recipients in the Exchange organization. This domain must match the accepted domain you added in the previous step. For example, @contoso.com. Click **Save**.
    
7. Click **Save**
    
8. In the **Default Policy** details pane, click **Apply**.
    
> [!NOTE]
> We recommend that you configure a user principal name (UPN) that matches the primary email address of each user. If you don't provide a UPN that matches the email address of a user, the user will be required to manually provide their domain\user name or UPN in addition to their email address. If their UPN matches their email address, Outlook Web App, ActiveSync, and Outlook will automatically match their email address to their UPN. 
  
### How do you know this step worked?

To verify that you have successfully configured the default email address policy, do the following:
  
1. In the EAC, go to **Recipients** \> **Mailboxes**.
    
2. Select a mailbox and then, in the recipient details pane, verify that the **User mailbox** field has been set to  _\<alias\>_@ _\<new accepted domain\>_. For example, david@contoso.com.
    
3. Optionally, create a new mailbox and verify the mailbox is given an email address with the new accepted domain by doing the following:
    
1. Go to **Recipients** \> **Mailboxes**, click **New**![Add icon](../../media/ITPro_EAC_AddIcon.png) and then select **User mailbox**.
    
2. On the new user mailbox page, provide the information required to create a new mailbox. Click **Save**.
    
3. Select the new mailbox and then, in the recipient details pane, verify that the **User mailbox** field has been set to  _\<alias\>_@ _\<new accepted domain\>_. For example, david@contoso.com.
    
## Step 4: Configure external URLs
<a name="ConfigExternalURL"> </a>

You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the " _\<Service\>_ virtual directory settings" entry in the [Clients and mobile devices permissions](../../permissions/feature-permissions/client-and-mobile-device-permissions.md) topic. 
  
Before clients can connect to your new server from the Internet, you need to configure the external domains, or URLs, on the Mailbox server's virtual directories and then configure your public domain name service (DNS) records. The steps below configure the same external domain on the external URL of each virtual directory. If you want to configure different external domains on one or more virtual directory external URLs, you need to configure the external URLs manually. For more information, see [Virtual Directory Management](http://technet.microsoft.com/library/1af30fd5-621c-4acb-b6df-d8fa64d719ba.aspx).
  
1. Open the EAC by browsing to the URL of your Mailbox server. For example, https://Ex2016MBX/ECP.
    
2. Enter your user name and password in **Domain\user name** and **Password** and then click **Sign in**.
    
3. Go to **Servers** \> **Servers**, select the name of the Internet-facing Mailbox and then click **Edit**![Edit icon](../../media/ITPro_EAC_EditIcon.png).
    
4. Click **Outlook Anywhere**.
    
5. In the **Specify the external hostname** field, specify the externally accessible FQDN of the Mailbox server. For example, mail.contoso.com. 
    
6. While you're here, let's also set the internally accessible FQDN of the Mailbox server. In the **Specify the internal hostname** field, insert the FQDN you used in the previous step. For example, mail.contoso.com. 
    
7. Click **Save**.
    
8. Go to **Servers** \> **Virtual directories** and then click **Configure external access domain**![Configure icon](../../media/ITPro_EAC_ConfigureIcon.png).
    
9. Under **Select the Mailbox servers to use with the external URL**, click **Add**![Add icon](../../media/ITPro_EAC_AddIcon.png)
  
10. Select the Mailbox servers you want to configure and then click **Add**. After you've added all of the Mailbox servers you want to configure, click **OK**.
    
11. In **Enter the domain name you will use with your external Mailbox servers**, type the external domain you want to apply. For example, mail.contoso.com. Click **Save**.
    
    **Note**: Some organizations make the Outlook Web App FQDN unique to protect users against changes to underlying server FQDN changes. Many organizations use owa.contoso.com for their Outlook Web App FQDN instead of mail.contoso.com. If you want to configure a unique Outlook Web App FQDN, do the following after you completed the previous step. This checklist assumes you have configured a unique Outlook Web App FQDN.
    
1. Select **owa (Default Web Site)** and click **Edit**![Edit icon](../../media/ITPro_EAC_EditIcon.png).
    
2. In **External URL**, type https://, then the unique Outlook Web App FQDN you want to use, and then append /owa. For example, https://owa.contoso.com/owa.
    
3. Click **Save**.
    
4. Select **ecp (Default Web Site)** and click **Edit**![Edit icon](../../media/ITPro_EAC_EditIcon.png).
    
5. In **External URL**, type https://, then the same Outlook Web App FQDN that you specified in the previous step, and then append /ecp. For example, https://owa.contoso.com/ecp.
    
6. Click **Save**.
    
After you've configured the external URL on the Mailbox server virtual directories, you need to configure your public DNS records for Autodiscover, Outlook Web App, and mail flow. The public DNS records should point to the external IP address or FQDN of your Internet-facing Mailbox server and use the externally accessible FQDNs that you've configured on your Mailbox server. The following are examples of recommended DNS records that you should create to enable mail flow and external client connectivity.
  
|**FQDN**|**DNS record type**|**Value**|
|:-----|:-----|:-----|
|Contoso.com  <br/> |MX  <br/> |Mail.contoso.com  <br/> |
|Mail.contoso.com  <br/> |A  <br/> |172.16.10.11  <br/> |
|Owa.contoso.com  <br/> |CNAME  <br/> |Mail.contoso.com  <br/> |
|Autodiscover.contoso.com  <br/> |CNAME  <br/> |Mail.contoso.com  <br/> |
   
### How do you know this step worked?

To verify that you have successfully configured the external URL on the Mailbox server virtual directories, do the following:
  
1. In the EAC, go to **Servers** \> **Virtual directories**.
    
2. In the **Select server** field, select the Internet-facing Mailbox server. 
    
3. Select a virtual directory and then, in the virtual directory details pane, verify that the **External URL** field is populated with the correct FQDN and service as shown below: 
    
|**Virtual directory**|**External URL value**|
|:-----|:-----|
|**Autodiscover** <br/> |No external URL displayed  <br/> |
|**ECP** <br/> |https://owa.contoso.com/ecp  <br/> |
|**EWS** <br/> |https://mail.contoso.com/EWS/Exchange.asmx  <br/> |
|**Microsoft-Server-ActiveSync** <br/> |https://mail.contoso.com/Microsoft-Server-ActiveSync  <br/> |
|**OAB** <br/> |https://mail.contoso.com/OAB  <br/> |
|**OWA** <br/> |https://owa.contoso.com/owa  <br/> |
|**PowerShell** <br/> |http://mail.contoso.com/PowerShell  <br/> |
   
To verify that you have successfully configured your public DNS records, do the following:
  
1. Open a command prompt and run  `nslookup.exe`.
    
2. Change to a DNS server that can query your public DNS zone.
    
3. In  `nslookup`, look up the record of each FQDN you created. Verify that the value that's returned for each FQDN is correct.
    
4. In  `nslookup`, type  `set type=mx` and then look up the accepted domain you added in Step 1. Verify that the value returned matches the FQDN of the Mailbox server. 
    
## Step 5: Configure internal URLs
<a name="ConfigInternalURL"> </a>

You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the " _\<Service\>_ virtual directory settings" entry in the [Clients and mobile devices permissions](../../permissions/feature-permissions/client-and-mobile-device-permissions.md) topic. 
  
Before clients can connect to your new server from your intranet, you need to configure the internal domains, or URLs, on the Mailbox server's virtual directories and then configure your private domain name service (DNS) records.
  
The procedure below lets you choose whether you want users to use the same URL on your intranet and on the Internet to access your Exchange server or whether they should use a different URL. What you choose depends on the addressing scheme you have in place already or that you want to implement. If you're implementing a new addressing scheme, we recommend that you use the same URL for both internal and external URLs. Using the same URL makes it easier for users to access your Exchange server because they only have to remember one address. Regardless of the choice you make, you need to make sure you configure a private DNS zone for the address space you configure. For more information about administering DNS zones, see [Administering DNS Server](https://go.microsoft.com/fwlink/p/?LinkID=190631).
  
For more information about internal and external URLs on virtual directories, see [Virtual Directory Management](http://technet.microsoft.com/library/1af30fd5-621c-4acb-b6df-d8fa64d719ba.aspx).
  
### Configure internal and external URLs to be the same

1. Open the Exchange Management Shell on your Mailbox server.
    
2. Store the host name of your Mailbox server in a variable that will be used in the next step. For example, Ex2016MBX.
    
  ```
  $HostName = "Ex2016MBX"
  ```

3. Run each of the following commands in the Exchange Management Shell to configure each internal URL to match the virtual directory's external URL.
    
  ```
  Set-EcpVirtualDirectory "$HostName\ECP (Default Web Site)" -InternalUrl ((Get-EcpVirtualDirectory "$HostName\ECP (Default Web Site)").ExternalUrl)
  ```

  ```
  Set-WebServicesVirtualDirectory "$HostName\EWS (Default Web Site)" -InternalUrl ((get-WebServicesVirtualDirectory "$HostName\EWS (Default Web Site)").ExternalUrl)
  ```

  ```
  Set-ActiveSyncVirtualDirectory "$HostName\Microsoft-Server-ActiveSync (Default Web Site)" -InternalUrl ((Get-ActiveSyncVirtualDirectory "$HostName\Microsoft-Server-ActiveSync (Default Web Site)").ExternalUrl)
  ```

  ```
  Set-OabVirtualDirectory "$HostName\OAB (Default Web Site)" -InternalUrl ((Get-OabVirtualDirectory "$HostName\OAB (Default Web Site)").ExternalUrl)
  ```

  ```
  Set-OwaVirtualDirectory "$HostName\OWA (Default Web Site)" -InternalUrl ((Get-OwaVirtualDirectory "$HostName\OWA (Default Web Site)").ExternalUrl)
  ```

  ```
  Set-PowerShellVirtualDirectory "$HostName\PowerShell (Default Web Site)" -InternalUrl ((Get-PowerShellVirtualDirectory "$HostName\PowerShell (Default Web Site)").ExternalUrl)
  ```

After you've configured the internal URL on the Mailbox server virtual directories, you need to configure your private DNS records for Outlook Web App, and other connectivity. Depending on your configuration, you'll need to configure your private DNS records to point to the internal or external IP address or fully qualified domain name (FQDN) of your Mailbox server. The following are examples of recommended DNS records that you should create to enable internal client connectivity.
  
|**FQDN**|**DNS record type**|**Value**|
|:-----|:-----|:-----|
|Mail.contoso.com  <br/> |CNAME  <br/> |Ex2016MBX.corp.contoso.com  <br/> |
|Owa.contoso.com  <br/> |CNAME  <br/> |Ex2016MBX.corp.contoso.com  <br/> |
   
#### How do you know this step worked?

To verify that you have successfully configured the internal URL on the Mailbox server virtual directories, do the following:
  
1. In the EAC, go to **Servers** \> **Virtual directories**.
    
2. In the **Select server** field, select the Internet-facing Mailbox server. 
    
3. Select a virtual directory and then click **Edit**![Edit icon](../../media/ITPro_EAC_EditIcon.png).
    
4. Verify that the **Internal URL** field is populated with the correct FQDN and service as shown below: 
    
|**Virtual directory**|**Internal URL value**|
|:-----|:-----|
|**Autodiscover** <br/> |No internal URL displayed  <br/> |
|**ECP** <br/> |https://owa.contoso.com/ecp  <br/> |
|**EWS** <br/> |https://mail.contoso.com/EWS/Exchange.asmx  <br/> |
|**Microsoft-Server-ActiveSync** <br/> |https://mail.contoso.com/Microsoft-Server-ActiveSync  <br/> |
|**OAB** <br/> |https://mail.contoso.com/OAB  <br/> |
|**OWA** <br/> |https://owa.contoso.com/owa  <br/> |
|**PowerShell** <br/> |http://mail.contoso.com/PowerShell  <br/> |
   
To verify that you have successfully configured your private DNS records, do the following:
  
1. Open a command prompt and run  `nslookup.exe`.
    
2. Change to a DNS server that can query your private DNS zone.
    
3. In  `nslookup`, look up the record of each FQDN you created. Verify that the value that's returned for each FQDN is correct.
    
### Configure different internal and external URLs

1. Open the EAC by browsing to the URL of your Mailbox server. For example, https://Ex2016MBX/ECP.
    
2. Go to **Servers** \> **Virtual directories**.
    
3. In the **Select server** field, select the Internet-facing Mailbox server. 
    
4. Select the virtual directory you want to change and click **Edit**![Edit icon](../../media/ITPro_EAC_EditIcon.png).
    
5. In **Internal URL**, replace the host name between **https://** and the first forward slash ( **/** ) with the new FQDN you want to use. For example, if you want to change the EWS virtual directory FQDN from Ex2016MBX.corp.contoso.com to internal.contoso.com, change the internal URL from https://Ex2016MBX.corp.contoso.com/ews/exchange.asmx to https://internal.contoso.com/ews/exchange.asmx. 
    
6. Click **Save**.
    
7. Repeat steps 5 and 6 for each virtual directory you want to change.
    
    > [!NOTE]
    > The ECP and OWA virtual directory internal URLs must be the same. You can't set an internal URL on the Autodiscover virtual directory. 
  
After you've configured the internal URL on the Mailbox server virtual directories, you need to configure your private DNS records for Outlook Web App, and other connectivity. Depending on your configuration, you'll need to configure your private DNS records to point to the internal or external IP address or FQDN of your Mailbox server. The following is an example of recommended DNS record that you should create to enable internal client connectivity if you've configured your virtual directory internal URLs to use internal.contoso.com.
  
|**FQDN**|**DNS record type**|**Value**|
|:-----|:-----|:-----|
|internal.contoso.com  <br/> |CNAME  <br/> |Ex2016MBX.corp.contoso.com  <br/> |
   
#### How do you know this step worked?

To verify that you have successfully configured the internal URL on the Mailbox server virtual directories, do the following:
  
1. In the EAC, go to **Servers** \> **Virtual directories**.
    
2. In the **Select server** field, select the Internet-facing Mailbox server. 
    
3. Select a virtual directory and then click **Edit**![Edit icon](../../media/ITPro_EAC_EditIcon.png).
    
4. Verify that the **Internal URL** field is populated with the correct FQDN. For example, you may have set the internal URLs to use internal.contoso.com. 
    
|**Virtual directory**|**Internal URL value**|
|:-----|:-----|
|**Autodiscover** <br/> |No internal URL displayed  <br/> |
|**ECP** <br/> |https://internal.contoso.com/ecp  <br/> |
|**EWS** <br/> |https://internal.contoso.com/EWS/Exchange.asmx  <br/> |
|**Microsoft-Server-ActiveSync** <br/> |https://internal.contoso.com/Microsoft-Server-ActiveSync  <br/> |
|**OAB** <br/> |https://internal.contoso.com/OAB  <br/> |
|**OWA** <br/> |https://internal.contoso.com/owa  <br/> |
|**PowerShell** <br/> |http://internal.contoso.com/PowerShell  <br/> |
   
To verify that you have successfully configured your private DNS records, do the following:
  
1. Open a command prompt and run  `nslookup.exe`.
    
2. Change to a DNS server that can query your private DNS zone.
    
3. In  `nslookup`, look up the record of each FQDN you created. Verify that the value that's returned for each FQDN is correct.
    
## Step 6: Configure an SSL certificate
<a name="ConfigCert"> </a>

You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Certificate management" entry in the [Mail flow permissions](../../permissions/feature-permissions/mail-flow-permissions.md) topic. 
  
Some services, such as Outlook Anywhere and Exchange ActiveSync, require certificates to be configured on your Exchange 2016 server. The following steps show you how to configure an SSL certificate from a third-party certificate authority (CA):
  
1. Open the EAC by browsing to the URL of your Mailbox server. For example, https://Ex2016MBX/ECP.
    
2. Enter your user name and password in **Domain\user name** and **Password** and then click **Sign in**.
    
3. Go to **Servers** \> **Certificates**. On the **Certificates** page, make sure your Mailbox server is selected in the **Select server** field, and then click **New**![Add icon](../../media/ITPro_EAC_AddIcon.png).
    
4. In the **New Exchange certificate** wizard, select **Create a request for a certificate from a certification authority** and then click **Next**.
    
5. Specify a name for this certificate and then click **Next**.
    
6. If you want to request a wildcard certificate, select **Request a wild-card certificate** and then specify the root domain of all subdomains in the **Root domain** field. If you don't want to request a wildcard certificate and instead want to specify each domain you want to add to the certificate, leave this page blank. Click **Next**.
    
7. Click **Browse** and specify an Exchange server to store the certificate on. The server you select should be the Internet-facing Mailbox server. Click **Next**.
    
8. For each service in the list shown, verify that the external or internal server names that users will use to connect to the Exchange server are correct. For example:
    
  - If you configured your internal and external URLs to be the same, **Outlook Web App (when accessed from the Internet)** and **Outlook Web App (when accessed from the Intranet)** should show owa.contoso.com. **OAB (when accessed from the Internet)** and **OAB (when accessed from the Intranet)** should show mail.contoso.com. 
    
  - If you configured the internal URLs to be internal.contoso.com, **Outlook Web App (when accessed from the Internet)** should show owa.contoso.com and **Outlook Web App (when accessed from the Intranet)** should show internal.contoso.com. 
    
    These domains will be used to create the SSL certificate request. Click **Next**.
    
9. Add any additional domains you want included on the SSL certificate.
    
10. Select the domain that you want to be the common name for the certificate, and then click **Set as common name**. For example, contoso.com. Click **Next**.
    
11. Provide information about your organization. This information will be included with the SSL certificate. Click **Next**.
    
12. Specify the network location where you want this certificate request to be saved. Click **Finish**.
    
After you've saved the certificate request, submit the request to your certificate authority (CA). This can be an internal CA or a third-party CA, depending on your organization. Clients that connect to the Mailbox server must trust the CA that you use. After you receive the certificate from the CA, complete the following steps:
  
1. On the **Server** \> **Certificates** page in the EAC, select the certificate request you created in the previous steps. 
    
2. In the certificate request details pane, click **Complete** under **Status**.
    
3. On the complete pending request page, specify the path to the SSL certificate file and then click **OK**.
    
4. Select the new certificate you just added, and then click **Edit**![Edit icon](../../media/ITPro_EAC_EditIcon.png).
    
5. On the certificate page, click **Services**.
    
6. Select the services you want to assign to this certificate. At minimum, you should select **SMTP** and **IIS**. Click **Save**.
    
7. If you receive the warning **Overwrite the existing default SMTP certificate?**, click **Yes**.
    
### How do you know this step worked?

To verify that you have successfully added a new certificate, do the following:
  
1. In the EAC, go to **Servers** \> **Certificates**.
    
2. Select the new certificate and then, in the certificate details pane, verify that the following are true:
    
  - **Status** shows **Valid**
    
  - **Assigned to services** shows, at minimum, **IIS** and **SMTP**.
    
## How do you know this task worked?
<a name="ConfigCert"> </a>

To verify that you have configured mail flow and external client access, do the following:
  
1. In Outlook, on an Exchange ActiveSync device, or on both, create a new profile. Verify that Outlook or the mobile device successfully creates the new profile.
    
2. In Outlook, or on the mobile device, send a new message to an external recipient. Verify the external recipient receives the message.
    
3. In the external recipient's mailbox, reply to the message you just sent from the Exchange mailbox. Verify the Exchange mailbox receives the message.
    
4. Go to https://owa.contoso.com/owa and verify that there are no certificate warnings.
    

