---
title: "Enable mail flow for subdomains in Exchange Online"
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
ms.date: 6/23/2018
ms.audience: End User
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 4033a30a-f506-481c-8ef0-fd9a0508ae38
description: "If you have a hybrid environment, with mailboxes hosted both in Exchange Online and on-premises, and you have subdomains of the accepted domains that only exist in your on-premises environment, you can enable email flow to and from these on-premises subdomains. For example, if you have an accepted domain called Contoso.com, and you enable match subdomains, users can send email to, or receive email from all subdomains of Contoso.com that exist in your on-premises environment, such as marketing.contoso.com and nwregion.contoso.com. In Microsoft Forefront Online Protection for Exchange (FOPE), this feature was called catch-all domains."
---

# Enable mail flow for subdomains in Exchange Online

If you have a hybrid environment, with mailboxes hosted both in Exchange Online and on-premises, and you have subdomains of the accepted domains that only exist in your on-premises environment, you can enable email flow to and from these on-premises subdomains. For example, if you have an accepted domain called Contoso.com, and you enable match subdomains, users can send email to, or receive email from all subdomains of Contoso.com that exist in your on-premises environment, such as marketing.contoso.com and nwregion.contoso.com. In Microsoft Forefront Online Protection for Exchange (FOPE), this feature was called catch-all domains.
  
> [!IMPORTANT]
> If you have a limited number of subdomains, and know all the subdomain names, we recommend setting up each subdomain as an accepted domain by using the Office 365 admin center, rather than using the procedures in this topic. By setting up each subdomain separately, you can have finer control over mail flow, and include unique transport rules for each subdomain. For more information about adding a domain in the Office 365 admin center, see [Add your domain to Office 365](https://go.microsoft.com/fwlink/p/?LinkId=282303). > > In order to enable match subdomains, an accepted domain must be set up as an internal relay. For information about setting the domain type to internal relay, see [Manage accepted domains in Exchange Online](manage-accepted-domains.md). > > After you enable match subdomains, in order for the service to deliver mail for all subdomains to your organization's email server (outside Office 365), you must also change the outbound connector. For instructions, see [Use the EAC to add the domain to your outbound connector](enable-mail-flow-for-subdomains.md#outboundconnector). 
  
## What do you need to know before you begin?

- Estimated time to complete: 5 minutes
    
- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Domains" entry in the [Feature permissions in Exchange Online](../../permissions/feature-permissions.md) topic. 
    
- For information about keyboard shortcuts that may apply to the procedures in this topic, see **Keyboard shortcuts in the Exchange admin center**.
    
> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612),[Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351). 
  
## What Do You Want to Do

### Use the EAC to set up match subdomains on a domain

1. In the EAC, go to **Mail Flow** \> **Accepted domains**, and select the domain. 
    
2. Verify that **Internal Relay** is selected. 
    
3. Select **Match subdomains for this domain for sending and receiving emails**.
    
### Use the EAC to add the domain to your outbound connector
<a name="outboundconnector"> </a>

1. In the EAC, go to **Mail Flow** \> **Connectors**. 
    
2. Under **Outbound Connectors**, select the connector for your organization's email server, and then select **Edit**![Edit icon](../../media/ITPro_EAC_EditIcon.gif). 
    
3. Select **Scope**, and then select one of the following:
    
  - Select **Route all accepted domains through this connector**.
    
  - In the **Recipient domains** section, select **New**![Add Icon](../../media/ITPro_EAC_AddIcon.gif). In the **Add domain** box, enter a wildcard domain entry for the domain for which you enabled match subdomains. For example, if you enabled match subdomains for contoso.com, enter \*.contonso.com as a recipient domain. 
    
> [!NOTE]
> If you don't yet have an outbound connector, see [Configure mail flow using connectors in Office 365](../../mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow.md). 
  
### Use the Exchange Management Shell to set up match subdomains on a domain
<a name="outboundconnector"> </a>

To add match subdomains to a domain that is set up as an internal relay, use this syntax
  
```
Set-AcceptedDomain -Identity <Domain Name> -MatchSubdomains $true 
```

This example sets up match subdomains for the contoso.com domain.
  
```
Set-AcceptedDomain -Identity contoso.com -MatchSubdomains $true 
```

For more information about using the Exchange Management Shell, see [set-AcceptedDomain](http://technet.microsoft.com/library/2ef9a20b-0974-45d0-9dae-23bab22d736e.aspx) and [PowerShell in Exchange Online Protection](http://technet.microsoft.com/library/f7918a88-774a-405e-945b-bc2f5ee9f748.aspx).
  
#### How do you know this worked?

To verify that you successfully added match subdomains to a domain using the Exchange Management Shell, do the following:
  
1. Run the command  `Get-RemoteDomain <Domain Name> | Format-List` to verify the  _MatchSubdomains_ setting. 
    

