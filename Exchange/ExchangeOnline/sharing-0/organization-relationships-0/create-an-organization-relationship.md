---
title: "Create an organization relationship in Exchange Online"
ms.author: dstrome
author: dstrome
manager: scotv
ms.date: 4/29/2016
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 8b9a1782-f6be-46bc-bec9-49633be0dc1f
description: "Set up an organization relationship to share calendar information with an external business partner. Office 365 admins can set up an organization relationship with another Office 365 organization or with an Exchange on-premises organization."
---

# Create an organization relationship in Exchange Online

Set up an organization relationship to share calendar information with an external business partner. Office 365 admins can set up an organization relationship with another Office 365 organization or with an Exchange on-premises organization. 
  
## What do you need to know before you begin?

- Estimated time to complete: 15 minutes.
    
- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the [Permissions in Exchange Online](../../permissions/permissions.md) topic. 
    
- If you want to share calendars with an on-premises Exchange organization, the on-premises Exchange administrator has to set up an authentication relationship with the cloud (also known as "federation") and must meet minimum software requirements.
    
## What do you want to do?

### Use the Exchange admin center to create an organization relationship
<a name="BKMK_EAC"> </a>

1. From the Office 365 admin center dashboard, go to **Admin** \> **Exchange**.
    
2. Go to **organization** \> **sharing**.
    
3. Under **Organization Sharing**, click **New**![Add Icon](../../media/ITPro_EAC_AddIcon.gif).
    
4. In **new organization relationship**, in the **Relationship name** box, type a friendly name for the organization relationship. 
    
5. In the **Domains to share with** box, type the domain for the external Office 365 or Exchange on-premises organization you want to let see your calendars. If you need to enter more than one domain, separate the domain names with a comma. For example, contoso.com, service.contoso.com.
    
6. Select the **Enable calendar free/busy information sharing** check box to turn on calendar sharing with the domains you listed. Set the sharing level for calendar free/busy information and set which users can share calendar free/busy information. 
    
    To set the free/busy access level, select one of the following:
    
  - **Calendar free/busy information with time only**
    
  - **Calendar free/busy with time, subject, and location**
    
    To set which users will share calendar free/busy information, select one of the following:
    
  - **Everyone in your organization**
    
  - **A specified security group**
    
    Click **browse** to pick the security group from a list, then click **ok**.
    
7. Click **save** to create the organization relationship. 
    
### Use the Exchange Management Shell to create an organization relationship
<a name="BKMK_Shell"> </a>

This example creates an organization relationship with Contoso, Ltd with the following conditions:
  
- An organization relationship is set up with contoso.com, northamerica.contoso.com, and europe.contoso.com.
    
- Free/busy access is enabled.
    
- Contoso.com and the subdomains get free/busy time, subject, and location information from your organization.
    
```
New-OrganizationRelationship -Name "Contoso" -DomainNames "contoso.com","northamerica.contoso.com","europe.contoso.com" -FreeBusyAccessEnabled $true -FreeBusyAccessLevel LimitedDetails

```

If you're not sure which domains Contoso has set up for cloud-based authentication, you can run this command to automatically find the configuration information. The **Get-FederationInformation** cmdlet is used to find the right information, which is then passed to the **New-OrganizationRelationship** cmdlet. 
  
```
Get-FederationInformation -DomainName Contoso.com | New-OrganizationRelationship -Name "Contoso" -FreeBusyAccessEnabled $true -FreeBusyAccessLevel LimitedDetails

```

For detailed syntax and parameter information, see [Get-FederationInformation](http://technet.microsoft.com/library/e7e948c8-453d-49e2-97da-45fd2a7853ba.aspx) and [New-OrganizationRelationship](http://technet.microsoft.com/library/ec35c7ed-6f91-435e-8c9f-9dbc53c993fe.aspx).
  
If you're setting up an organization relationship with an on-premises Exchange organization, you may want to provide the connection settings. This example creates an organization relationship with Fourth Coffee and specifies the connection settings to use. The following conditions apply:
  
- The organization relationship is established with the domain fourthcoffee.com.
    
- The Exchange Web Services application URL is mail.fourthcoffee.com.
    
- The Autodiscover URL is https://mail.fourthcoffee.com/autodiscover/autodiscover.svc/wssecurity.
    
- Free/busy access is enabled.
    
- Fourth Coffee sees free/busy information with the time.
    
```
New-OrganizationRelationship -Name "Fourth Coffee" -DomainNames "fourthcoffee.com" -FreeBusyAccessEnabled $true -FreeBusyAccessLevel -AvailabilityOnly -TargetAutodiscoverEpr "https://mail.fourthcoffee.com/autodiscover/autodiscover.svc/wssecurity" -TargetApplicationUri "mail.fourthcoffee.com"

```

For detailed syntax and parameter information, see [New-OrganizationRelationship](http://technet.microsoft.com/library/ec35c7ed-6f91-435e-8c9f-9dbc53c993fe.aspx).
  
## How do you know this worked?

The successful completion of the **New organization relationship** wizard indicates that the organization relationship was created. 
  
You can also run the following Exchange Management Shell command to verify the organization relationship information:
  
```
Get-OrganizationRelationship | format-list
```

> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612),[Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351). 
  

