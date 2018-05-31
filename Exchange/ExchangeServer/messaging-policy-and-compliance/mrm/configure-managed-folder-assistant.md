---
title: "Configure and run the Managed Folder Assistant in Exchange 2016"
ms.author: serdars
author: SerdarSoysal
manager: serdars
ms.date: 1/5/2018
ms.audience: End User
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 9fcfb9b6-bd24-4218-a163-bc599cd5476a
description: "Summary: Learn how to configure the Managed Folder Assistant in Exchange 2016."
---

# Configure and run the Managed Folder Assistant in Exchange 2016

 **Summary**: Learn how to configure the Managed Folder Assistant in Exchange 2016.
  
The Managed Folder Assistant (MFA) is an Exchange Mailbox Assistant that applies and processes the message retention settings that are configured in retention policies. 
  
As in Exchange 2013, the Managed Folder Assistant in Exchange 2016 is a throttle-based assistant that's always running. The MFA doesn't need to be scheduled, and the system resources that are consumed by the MFA can be throttled. You can configure the Managed Folder Assistant to process all mailboxes on a Mailbox server within a certain time period that's known as a work cycle. By default, the work cycle for the MFA is one day (all mailboxes on the server are processed by the MFA every day).
  
You can also force the MFA to immediately process a specified mailbox.
  
## What do you need to know before you begin?

- You can only use PowerShell to perform this procedure. To learn how to open the Exchange Management Shell in your on-premises Exchange organization, see **Open the Exchange Management Shell**.
    
- Although the  _ManagedFolderAssistantSchedule_ parameter is available in Exchange 2016, it doesn't work on Exchange 2016 servers. It's only used for coexistence with previous versions of Exchange. 
    
- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Messaging records management" entry in the [Messaging policy and compliance permissions in Exchange 2016](../../permissions/feature-permissions/messaging-policy-and-compliance-permissions.md) topic. 
    
## Configure the Managed Folder Assistant

Configuring the interval for when the MFA processes mailboxes is a two-step process:
  
1. Configure the work cycle for the MFA.
    
2. Apply the new work cycle value for the MFA.
    
### Step 1: Use the Exchange Management Shell to configure the work cycle for the Managed Folder Assistant

To configure the work cycle for the MFA, use this syntax:
  
```
New-SettingOverride -Name "<UniqueOverrideName>" -Component TimeBasedAssistants -Section ELCAssistant -Parameters @("WorkCycle=<Timespan>") -Reason "<DescriptiveReason>" [-Server <ServerName>]
```

 **Notes:**
  
- To specify a  _\<TimeSpan\>_ value, use the syntax  `d.hh:mm:ss`, where  _d_ = days,  _hh_ = hours,  _mm_ = minutes, and  _ss_ = seconds. 
    
- To configure the same work cycle for the MFA on all Exchange 2016 Mailbox servers in the Active Directory forest, don't use the  _Server_ parameter. 
    
- To configure the work cycle for the MFA on a specific Exchange 2016 Mailbox server, use the  _Server_ parameter and the name (not the fully qualified domain name or FQDN) of the server. This method is useful when you need to specify different work cycle values for the MFA on different Exchange servers. 
    
This example configures the work cycle for the MFA to two days (the MFA processes mailboxes every two days). Because we aren't using the  _Server_ parameter, the setting is applied to all Exchange 2016 Mailbox servers in the organization. 
  
- **Setting override name** "MFA WorkCycle Override" (must be unique) 
    
- **WorkCycle** `2.00:00:00` (2 days; note the value  `2`also works)
    
- **Override reason** Process mailboxes every 2 days 
    
```
New-SettingOverride -Name "MFA WorkCycle Override" -Component TimeBasedAssistants -Section ELCAssistant -Parameters @("WorkCycle=2.00:00:00") -Reason "Process mailboxes every 2 days"
```

This example specifies the same 2 day work cycle for the MFA, but only on the server named Mailbox01.
  
```
New-SettingOverride -Name "Mailbox01 MFA WorkCycle Override" -Component TimeBasedAssistants -Section ELCAssistant -Parameters @("WorkCycle=2.00:00:00") -Reason "Process mailboxes every 2 days" -Server Mailbox01
```

### Step 2: Use the Exchange Management Shell to apply the new the work cycle value for the Managed Folder Assistant

To apply the new the work cycle value for the MFA, use this syntax:
  
```
Get-ExchangeDiagnosticInfo -Process Microsoft.Exchange.Directory.TopologyService -Component VariantConfiguration -Argument Refresh [-Server <ServerName>]
```

 **Notes:**
  
- If you didn't use the  _Server_ parameter in Step 1, don't use it here. If you used the  _Server_ parameter in Step 1, use the same server name here. 
    
- If you delete the custom work cycle value for the MFA by using the **Remove-SettingOverride** cmdlet, you still need to run this command to change the work cycle back to the default value of one day. 
    
This example applies the new work cycle value for the MFA on all Exchange 2016 Mailbox servers in the organization.
  
```
Get-ExchangeDiagnosticInfo -Process Microsoft.Exchange.Directory.TopologyService -Component VariantConfiguration -Argument Refresh
```

This example applies the new work cycle value for the MFA on the server named Mailbox01.
  
```
Get-ExchangeDiagnosticInfo -Process Microsoft.Exchange.Directory.TopologyService -Component VariantConfiguration -Argument Refresh -Server Mailbox01
```

### How do you know this worked?

To verify that you've successfully configured the work cycle for the Managed Folder Assistant on one or more servers, replace  _\<ServerName\>_ with the name of the server (not the FQDN), and run the following command to verify the value of the **WorkCycle** property: 
  
```
[xml]$diag=Get-ExchangeDiagnosticInfo -Server <ServerName> -Process MSExchangeMailboxAssistants -Component VariantConfiguration -Argument "Config,Component=TimeBasedAssistants"; $diag.Diagnostics.Components.VariantConfiguration.Configuration.TimeBasedAssistants.ElcAssistant
```

## Use the Exchange Management Shell to start the Managed Folder Assistant on a specific mailbox

To trigger the MFA to immediately process a mailbox, use this syntax:
  
```
Start-ManagedFolderAssistant -Identity <MailboxIdentity>
```

This example triggers the Managed Folder Assistant to immediately process Morris Cornejo's mailbox.
  
```
Start-ManagedFolderAssistant -Identity morris.cornejo@contoso.com
```

For detailed syntax and parameter information, see [Start-ManagedFolderAssistant](http://technet.microsoft.com/library/75d840ea-5abc-44bb-b361-e81561fa1b04.aspx).
  

