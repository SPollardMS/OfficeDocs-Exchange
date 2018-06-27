---
title: "Manage accepted domains in Exchange Online"
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
ms.date: 6/23/2018
ms.audience: ITPro
ms.topic: article
ms.service: exchange-online
localization_priority: Normal
ms.assetid: 0fc0ecc0-e133-48fa-9d72-cb4793a73960
description: "When you add your domain to Office 365, it's called an accepted domain. This means that users in this domain can send and receive mail. For more information on how to add your domain to Office 365 using the Office 365 admin center, see Add a domain to Office 365."
---

# Manage accepted domains in Exchange Online

When you add your domain to Office 365, it's called an accepted domain. This means that users in this domain can send and receive mail. For more information on how to add your domain to Office 365 using the Office 365 admin center, see [Add a domain to Office 365](https://support.office.com/en-us/article/Add-a-domain-to-Office-365-6383f56d-3d09-4dcb-9b41-b5f5a5efd611).
  
After you add your domain using the Office 365 admin center, you can use the Exchange admin center (EAC) to view your accepted domains and configure the domain type.
  
There are two types of accepted domains, Authoritative and Internal Relay, which can be defined as follows:
  
- **Authoritative** - Selecting this option means that email is delivered to email addresses that are listed for recipients in Office 365 for this domain. Emails for unknown recipients are rejected. 
    
  - If you just added your domain to Office 365 and you select this option, it's critical that you add your recipients to Office 365 before setting up mail to flow through the service.
    
  - This option is typically used when all the email recipients in your domain are using Office 365. You can also use it if some recipients exist on your own email servers. However, if recipients exist on your own email servers, you must add your recipients to this Office 365 domain in order to make sure that mail is delivered as expected. For more information about how to manage your recipients, see these topics:
    
  - **Exchange Online**: [Manage mail users](../../recipients-in-exchange-online/manage-mail-users.md)
    
  - **Exchange Online Protection**: [Manage Mail Users in EOP](http://technet.microsoft.com/library/4bfaf2ab-e633-4227-8bde-effefb41a3db.aspx)
    
  - Setting this option enables Directory Based Edge Blocking (DBEB). For more information about DBEB, see [Use Directory Based Edge Blocking to reject messages sent to invalid recipients](../../mail-flow-best-practices/use-directory-based-edge-blocking.md).
    
- **Internal relay** - Selecting this option means that recipients for this domain can be in Office 365 or your own email servers. Email is delivered to known recipients in Office 365 or is relayed to your own email server if the recipients aren't known to Office 365. 
    
  - **You should not select this option if all of the recipients for this domain are in Office 365.**
    
  - If you select this option, you must create a connector for mail flow from Office 365 to your on-premises email server; otherwise recipients on the domain who are not hosted in Office 365 won't be able to receive mail on your own email servers. For more information about setting up connectors, see [Set up connectors to route mail between Office 365 and your own email servers](../../mail-flow-best-practices/use-connectors-to-configure-mail-flow/set-up-connectors-to-route-mail.md).
    
  - This option is required if you enable the subdomain routing option on a domain in order to let email pass through the service and be delivered to any subdomains of your accepted domains. For more information, see [Enable mail flow for subdomains in Exchange Online](enable-mail-flow-for-subdomains.md).
    
## What do you need to know before you begin?

- Estimated time to complete: 10 minutes.
    
- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Domains" entry in the [Mail flow permissions](http://technet.microsoft.com/library/f49f4fb5-af75-43cb-900f-c5f7b8cfa143.aspx) topic. 
    
- To learn how to use Windows PowerShell to connect to Exchange Online, see [Connect to Exchange Online PowerShell](https://go.microsoft.com/fwlink/p/?linkid=396554).
    
- For information about keyboard shortcuts that may apply to the procedures in this topic, see **Keyboard shortcuts in the Exchange admin center**.
    
> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612),[Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351). 
  
## What do you want to do?

### View accepted domains

#### Use the Exchange admin center (EAC) to view accepted domains

1. In the EAC, navigate to **Mail flow** \> **Accepted domains**.
    
2. Click the **Name**, **Accepted Domain**, or **Domain Type** column heading to sort alphabetically in ascending or descending order. By default, accepted domains are sorted alphabetically by name in ascending order. 
    
#### Use the Exchange Management Shell to view accepted domains

To view summary information about all accepted domains, run the following command.
  
```
Get-AcceptedDomain
```

To view details about a specific accepted domain, use the following syntax.
  
```
Get-AcceptedDomain <Name> | Format-List
```

This example shows details about the accepted domain named contso.com.
  
```
Get-AcceptedDomain contoso.com | Format-List
```

### Configure the domain type

After you add a domain to your Exchange Online organization in the Office 365 admin center, you can configure the domain type.
  
#### Use the EAC to change the domain type

1. In the EAC, navigate to **Mail flow** \> **Accepted domains**.
    
2. Select the domain and click **Edit**![Edit icon](../../media/ITPro_EAC_EditIcon.gif).
    
3. In the **Accepted Domain** window, in the **This accepted domain is** section, select the domain type. The possible values are **Authoritative** and **Internal relay**.
    
  - If you select **Authoritative**, you must confirm that you want to enable Directory Based Edge Blocking.
    
  - If you select **Internal Relay**, you can enable match subdomains to enable mail flow to all subdomains. For more information, see [Enable mail flow for subdomains in Exchange Online](enable-mail-flow-for-subdomains.md).
    
4. When you are finished, click **Save**.
    
#### Use the Exchange Management Shell to change the domain type

To configure the domain type, use the following syntax.
  
```
Set-AcceptedDomain <Name> -DomainType <Authoritative | InternalRelay>
```

This example configures the accepted domain named contoso.com as an internal relay domain.
  
```
Set-AcceptedDomain contoso.com -DomainType InternalRelay
```

#### How do you know this worked?

To verify that you have successfully configured the domain type, do either of the following:
  
- In the EAC at **Mail flow** \> **Accepted domains**, click **Refresh**![Refresh Icon](../../media/ITPro_EAC_RefreshIcon.gif). In the list of accepted domains, verify the domain type value of the accepted domain is configured correctly.
    
- In the Exchange Management Shell, run the command **Get-AcceptedDomain**. In the list of accepted domains, verify the domain type value of the accepted domain is configured correctly. 
    

