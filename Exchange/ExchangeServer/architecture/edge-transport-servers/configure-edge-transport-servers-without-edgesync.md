---
title: "Configure Internet mail flow through Edge Transport servers without using EdgeSync"
ms.author: chrisda
author: chrisda
manager: serdars
ms.date: 4/19/2018
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 6bb98d10-6f12-4b08-a58e-36375f605d65
description: "Learn how you can configure mail flow between your Exchange organization and an Edge Transport server without using an Edge Subscription."
---

# Configure Internet mail flow through Edge Transport servers without using EdgeSync

Learn how you can configure mail flow between your Exchange organization and an Edge Transport server without using an Edge Subscription.
  
We recommend that you use the Edge Subscription process to establish mail flow between your Exchange organization and an Edge Transport server as described in [Edge Subscriptions](edge-subscriptions.md). However, certain situations may prevent you from subscribing the Edge Transport server to your Exchange organization. To manually establish mail flow between your Exchange organization and an Edge Transport server, you need to create the Send connectors and Receive connectors as described in this topic.
  
For more information about Send connectors, see [Send connectors](../../mail-flow/connectors/send-connectors.md). For more information about Receive connectors, see [Receive connectors](../../mail-flow/connectors/receive-connectors.md).
  
## Before you begin

- Estimated time to complete this task: 30 minutes.
    
- On Edge Transport servers, you can only use the Exchange Management Shell to create Send connectors and Receive connectors. On Mailbox servers, you can use the Exchange admin center (EAC) or the Exchange Management Shell to create Send connectors. For information about opening and using the EAC, see [Exchange admin center in Exchange 2016](../../architecture/client-access-services/eac.md). To learn how to open the Exchange Management Shell in your on-premises Exchange organization, see **Open the Exchange Management Shell**.
    
- This procedure uses Basic authentication over TLS to provide encryption and authentication. When you use Basic authentication over TLS, the receiving server must have an X.509 (SSL) server certificate that matches the fully qualified domain name (FQDN) on the Receive connector (by default, the FQDN of the server that contains the Receive connector).
    
    You can use Externally Secured authentication instead, but communication between the Edge Transport server and Mailbox server isn't authenticated or encrypted by Exchange. We only recommend Externally Secured authentication when you're using an additional encryption method (for example, IPsec or a VPN).
    
    > [!NOTE]
    > Secure Sockets Layer (SSL) is being replaced by Transport Layer Security (TLS) as the protocol that's used to encrypt data sent between computer systems. They're so closely related that the terms "SSL" and "TLS" (without versions) are often used interchangeably. Because of this similarity, references to "SSL" in Exchange topics, the Exchange admin center, and the Exchange Management Shell have often been used to encompass both the SSL and TLS protocols. Typically, "SSL" refers to the actual SSL protocol only when a version is also provided (for example, SSL 3.0). To find out why you should disable the SSL protocol and switch to TLS, check out [Protecting you against the SSL 3.0 vulnerability](https://blogs.office.com/2014/10/29/protecting-ssl-3-0-vulnerability/). 
  
- An Edge Transport server is typically multihomed (has network adapters connected to multiple network segments that each have unique IP configurations): 
    
  - The network adapter that's connected to the external (public) network segment should be configured to use a public DNS server for name resolution. This enables the server to resolve SMTP domain names to MX resource records and route mail to the Internet.
    
  - The network adapter that's connected to the internal (private) network segment should be configured to use a DNS server in the perimeter network, or should have a Hosts file available to resolve internal host names.
    
- Some of the procedures require user accounts:
    
  - An Active Directory account that belongs to the Exchange Servers universal security group. This account is used by the Send connector on the Edge Transport server for smart host authentication to the destination Mailbox servers in the Exchange organization.
    
    **Note**: This account is granted permissions associated with Exchange servers. Make sure you safeguard the account credentials to prevent misuse of the account. You can configure the account to allow logon to specific computers only.
    
  - A local account on the Edge Transport server. This account is used by the Send connector on the Mailbox server for smart host authentication to the destination Edge Transport server.
    
- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Send connectors" entry, the "Send connectors - Edge Transport" entry, and the "Receive connectors - Edge Transport" entry in the [Mail flow permissions](../../permissions/feature-permissions/mail-flow-permissions.md) topic. 
    
- For information about keyboard shortcuts that may apply to the procedures in this topic, see [Keyboard shortcuts in the Exchange admin center](../../about-documentation/keyboard-shortcuts-in-eac.md).
    
> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at: [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351). 
  
## Edge Transport Server Procedures

The following connectors are required on the Edge Transport server:
  
1. Create a Send connector to only send messages to the Internet
    
2. Create a Send connector to only send messages to Mailbox servers in the Exchange organization
    
3. Create a Receive connector to only receive messages from Mailbox servers in the Exchange organization
    
4. Modify the default Receive connector to only accept messages only from the Internet.
    
    By default, a single Receive connector named Default internal receive connector  _\<ServerName\>_ is created during the installation of the Edge Transport server role. This connector can be used for both incoming Internet messages and incoming messages from internal Mailbox servers. 
    
The following sections walk you through all the configuration steps required to prepare your Edge Transport server to communicate with your Exchange organization.
  
### Step 1: Create a Send connector to only send messages to the Internet

This Send connector requires the following configuration:
  
- **Name** To Internet (or any descriptive name) 
    
- **Usage type** Internet 
    
- **Address spaces** "\*" (all domains) 
    
- **Network settings** Use DNS MX records to route mail automatically. Depending on your network configuration, you can also route mail through a smart host. The smart host then routes mail to the Internet. 
    
To create a Send connector that's configured to send messages to the Internet, run this command:
  
```
New-SendConnector -Name "To Internet" -AddressSpaces * -Usage Internet -DNSRoutingEnabled $true
```

For detailed syntax and parameter information, see [New-SendConnector](http://technet.microsoft.com/library/7b315ab0-8778-4835-a252-fb94129d7a8e.aspx).
  
### Step 2: Create a Send connector to only send messages to the Exchange organization

This Send connector requires the following configuration:
  
- **Name** To Internal Org (or any descriptive name) 
    
- **Usage type** Internal 
    
- **Address spaces** `--` (indicates all accepted domains for the Exchange organization) 
    
- DNS routing disabled (smart host routing enabled)
    
- **Smart hosts** FQDN of one or more Mailbox servers as smart hosts. For example, mbxserver01.contoso.com and mbxserver02.contoso.com. 
    
- **Smart host authentication methods** Basic authentication over TLS 
    
- **Smart host authentication credentials** Credentials for the user account in the internal domain that's a member of the Exchange Servers universal security group. You need to use the **Get-Credential** cmdlet to store the credentials. Use the format  _\<Domain\>_\ _\<UserName\>_ or the user principal name (UPN)(chris@contoso.com) to enter the username. 
    
To create a Send connector configured to send messages to the Exchange organization, replace the smart host values with the Mailbox servers in your organization, and run this command:
  
```
New-SendConnector -Name "To Internal Org" -Usage Internal -AddressSpaces "--" -DNSRoutingEnabled $false -SmartHosts mbxserver01.contoso.com,mbxserver02.contoso.com -SmartHostAuthMechanism BasicAuthRequireTLS -AuthenticationCredential (Get-Credential)
```

For detailed syntax and parameter information, see [New-SendConnector](http://technet.microsoft.com/library/7b315ab0-8778-4835-a252-fb94129d7a8e.aspx).
  
### Step 3: Modify the default Receive connector to only accept messages from the Internet

You should make the following configuration changes to the default Receive connector:
  
- Modify the name to indicate that the connector will be used solely to receive email from the Internet (the default name is Default internal receive connector  _\<ServerName\>_).
    
- Change the network bindings to accept messages only from the network adapter that is accessible from the Internet (for example, 10.1.1.1 and the standard SMTP TCP port value of 25).
    
To modify the default Receive connector to only accept messages from the Internet, replace < _ServerName\>_ and bindings ith the name of your Edge Transport server and external network adapter configuration, and run this command: 
  
```
Set-ReceiveConnector -Identity "Default internal Receive connector ServerName>" -Name "From Internet" -Bindings 10.1.1.1:25
```

For detailed syntax and parameter information, see [Set-ReceiveConnector](http://technet.microsoft.com/library/eb7f8960-e772-4312-9d3f-47dd27d9545c.aspx).
  
### Step 4: Create a Receive connector configured to only accept messages from the Exchange organization

This Receive connector requires the following configuration:
  
- **Name** From Internal Org (or any descriptive name) 
    
- **Usage type** Internal 
    
- **Local network bindings** Internal network-facing network adapter (for example, 10.1.1.2 and the standard SMTP TCP port value of 25). 
    
- **Remote network settings** IP address of one or more Mailbox servers in the Exchange organization. For example, 192.168.5.10 and 192.168.5.20. 
    
- **Authentication methods** TLS, Basic authentication, Basic authentication over TLS, and Exchange Server authentication. 
    
To create a Receive connector configured to only accept messages from the Exchange organization, replace the bindings and remote IP ranges with your values, and run this command.
  
```
New-ReceiveConnector -Name "From Internal Org" -Usage Internal -AuthMechanism TLS,BasicAuth,BasicAuthRequireTLS,ExchangeServer -Bindings 10.1.1.2:25 -RemoteIPRanges 192.168.5.10,192.168.5.20
```

For detailed syntax and parameter information, see [New-ReceiveConnector](http://technet.microsoft.com/library/eb527447-ed68-4a55-943b-aad8c8a94d01.aspx).
  
### How do you know this worked?

To verify that you have successfully configured the required Send connectors and Receive connectors on the Edge Transport server, run this command on the Edge Transport server and verify the property values:
  
```
Get-SendConnector | Format-List Name,Usage,AddressSpaces,SourceTransportServers,DSNRoutingEnabled,SmartHosts,SmartHostAuthMechanism; Get-ReceiveConnector | Format-List Name,Usage,AuthMechanism,Bindings,RemoteIPRanges
```

## Mailbox server procedures

You need to create a Send connector in your Exchange organization to send outgoing messages to the Edge Transport server for relay to the Internet. You source the Send connector on one or more Mailbox servers.
  
You don't need to modify the default Receive connectors on Mailbox servers. The default Receive connector named Default Frontend  _\<MailboxServerName\>_ in the Front End Transport service on Mailbox servers is already configured to accept messages from an Edge Transport server. For more information about default Receive connectors on Mailbox servers, see [Default Receive connectors created during setup](../../mail-flow/connectors/receive-connectors.md#DefaultConnectors).
  
### Step 5: Create a Send connector to send outgoing messages to the Edge Transport server

This Send connector requires the following configuration:
  
- **Name** To Edge (or any descriptive name) 
    
- **Usage type** Internal 
    
- **Address spaces** "\*" (all external domains) 
    
- DNS routing disabled (smart host routing enabled)
    
- **Smart hosts** IP address or FQDN of the Edge Transport server. For example, edge01.contoso.net. 
    
- **Source servers** FQDN of one or more Mailbox servers. For example, mbxserver01.contoso.com and mbxserver02.contoso.com. 
    
- **Smart host authentication methods** Basic authentication over TLS. 
    
- **Smart host authentication credentials** Credentials for the user account on the Edge Transport server. 
    
#### Use the EAC to create a Send connector to send outgoing messages to the Edge Transport server

1. In the EAC, go to **Mail flow** > **Send connectors**, and then click **Add**![Add icon](../../media/ITPro_EAC_AddIcon.png). This starts the **New Send connector** wizard. 
    
2. On the first page, configure these settings:
    
  - **Name** Enter To Edge.
    
  - **Type** Select **Internal**.
    
    Click **Next**.
    
3. On the next page, select **Route mail through smart hosts**, and then click **Add**![Add icon](../../media/ITPro_EAC_AddIcon.png). In the **Add smart host** dialog box that appears, identify the Edge Transport by using one of these values: 
    
  - **IP address** For example, 10.1.1.2. 
    
  - **Fully qualified domain name (FQDN)** For example, edge01.contoso.net. Note that the source Mailbox servers for the Send connector must be able to resolve the Edge Transport server in DNS by using this FQDN. If they can't, use the IP address instead. 
    
    Click **Save**.
    
4. On the next page, in the **Smart host authentication** section, select **Basic authentication**, and then configure these additional settings:
    
  - Select **Offer basic authentication only after starting TLS**
    
  - In the **User name** and **Password** fields, enter the credentials for the local user account on the Edge Transport server. 
    
    Click **Next**.
    
5. On the next page, in the **Address space** section, click **Add**![Add icon](../../media/ITPro_EAC_AddIcon.png). In the **Add domain** dialog box that appears, enter the following information: 
    
  - **Type** Verify SMTP is selected. 
    
  - **Fully Qualified Domain Name (FQDN)** Enter an asterisk ( \*) to indicate the Send connector is used for all external domains.
    
  - **Cost** Verify 1 is entered. A lower value indicates a more preferred route. 
    
    Click **Save**.
    
6. Back on the previous page, the **Scoped send connector** setting is important if your organization has Exchange servers installed in multiple Active Directory sites: 
    
  - If you don't select **Scoped send connector**, the connector is usable by all transport servers (Exchange 2016 Mailbox servers, Exchange 2013 Mailbox servers, and Exchange 2010 Hub Transport servers) in the entire Active Directory forest. This is the default value.
    
  -  If you select **Scoped send connector**, the connector is only usable by other transport servers in the same Active Directory site.
    
    Click **Next**.
    
7. On the next page, in the **Source server** section, click **Add**![Add icon](../../media/ITPro_EAC_AddIcon.png). In the **Select a Server** dialog box that appears, select one or more Mailbox servers that you want to use to send outgoing mail through the Edge Transport server. Select a Mailbox server and click **Add -\>** (repeat as many times a necessary), click **OK**, and then click **Finish**.
    
#### Use the Exchange Management Shell to create a Send connector to send outgoing messages to the Edge Transport server

To create a Send connector to send outgoing messages to the Edge Transport server, replace the smart hosts and source Mailbox servers with your values, and run this command:
  
```
New-SendConnector -Name "To Edge" -Usage Internal -AddressSpaces * -DNSRoutingEnabled $false -SmartHosts edge01.contoso.com -SourceTransportServers mbxserver01.contoso.com,mbxserver02.contoso.com -SmartHostAuthMechanism BasicAuthRequireTLS -AuthenticationCredential (Get-Credential)
```

For detailed syntax and parameter information, see [New-SendConnector](http://technet.microsoft.com/library/7b315ab0-8778-4835-a252-fb94129d7a8e.aspx).
  
#### How do you know this worked?

To verify that you've successfully created a Send connector to send outgoing messages to the Edge Transport server, use either of these steps:
  
- In the EAC, go to **Mail flow** > **Send connectors**, select the Send connector named To Edge > click **Edit**![Edit icon](../../media/ITPro_EAC_EditIcon.png), and verify the property values.
    
- In the Exchange Management Shell, run this command on a Mailbox server to verify the property values:
    
  ```
  Get-SendConnector -Identity "To Edge" | Format-List Usage,AddressSpaces,DSNRoutingEnabled,SmartHosts,SourceTransportServers,SmartHostAuthMechanism
  ```


