---
title: Change the offline address book generation schedule in Exchange 2016
keywords: microsoft.exchange.management.snapin.esm.organizationconfiguration.mailbox.offlineaddressbookgeneralpage
f1_keywords:
- microsoft.exchange.management.snapin.esm.organizationconfiguration.mailbox.offlineaddressbookgeneralpage
ms.prod: EXCHANGE
ms.assetid: d2b4d527-311e-442d-9f1f-54fac8371b80
---


# Change the offline address book generation schedule in Exchange 2016
Learn how to configure the offline address book (OAB) update interval in Exchange 2016.
An offline address book (OAB) is a copy of an address book that's been downloaded so that an Outlook user can access the information it contains while disconnected from the server. By default, a new OAB is generated every 8 hours in Exchange Server 2016, but you can change the interval by using the Exchange Management Shell.
  
    
    

For additional management tasks related to OABs, see  [Procedures for offline address books in Exchange 2016](procedures-for-offline-address-books-in-exchange-2016.md).
## What do you need to know before you begin?


- Estimated time to complete each procedure: 5 minutes.
    
  
- You can only use PowerShell to perform this procedure. To learn how to open the Exchange Management Shell in your on-premises Exchange organization, see **Open the Exchange Management Shell**.
    
  
- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Offline address books" entry in the  [Email address and address book permissions](email-address-and-address-book-permissions.md) topic.
    
  
- For information about keyboard shortcuts that may apply to the procedures in this topic, see  [Keyboard shortcuts in the Exchange admin center](keyboard-shortcuts-in-the-exchange-admin-center.md).
    
  

> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at:  [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612),  [Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or  [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351). 
  
    
    


## Use the Exchange Management Shell to change the OAB generation schedule

Use the following syntax in the Exchange Management Shell.
  
    
    

```

New-SettingOverride -Name <UniqueOverrideName> -Component <Component> -Section OABGeneratorAssistant -Parameters @("WorkCycle=<Timespan>") -Reason <DescriptiveReason> [-Server <ServerName>]
```

 **Notes:**
  
    
    

- The value that's required for the  _Component_ parameter depends on your version Exchange 2016:
    
  - **Exchange 2016 CU3 or earlier** `MailboxAssistants`
    
  
  - **Exchange 2016 CU4 or later** `TimeBasedAssistants`
    
  
- To specify a  _<TimeSpan>_ value, use the syntax `d.hh:mm:ss`, where  _d_ = days, _hh_ = hours, _mm_ = minutes, and _ss_ = seconds.
    
  
- To configure the same settings on all Exchange 2016 servers in the Active Directory forest, don't use the  _Server_ parameter.
    
  
- To configure the settings on a specific Exchange 2016 server, use the  _Server_ parameter and the name of the server (don't use the fully qualified domain name or FQDN). This method is useful when you need to specify different settings on different Exchange servers.
    
  
These example specify that the offline address book is generated every two hours on all Exchange 2016 servers in the organization that are responsible for generating offline address books.
  
    
    

- **Setting override name** "OAB Generation Override" (must be unique)
    
  
- **WorkCycle** `02:00:00` (2 hours)
    
  
- **Override reason** Generate OAB every 2 hours
    
  
 **Exchange 2016 CU3 or earlier**:
  
    
    



```
New-SettingOverride -Name "OAB Generation Override" -Component MailboxAssistants -Section OABGeneratorAssistant -Parameters @("WorkCycle=02:00:00") -Reason "Generate OAB every 2 hours"
```

 **Exchange 2016 CU4 or later**:
  
    
    



```
New-SettingOverride -Name "OAB Generation Override" -Component TimeBasedAssistants -Section OABGeneratorAssistant -Parameters @("WorkCycle=02:00:00") -Reason "Generate OAB every 2 hours"
```

These examples specify the same offline address book generation schedule, but only on the server named Mailbox01.
  
    
    
 **Exchange 2016 CU3 or earlier**:
  
    
    



```
New-SettingOverride -Name "Mailbox01 OAB Generation Override" -Component MailboxAssistants -Section OABGeneratorAssistant -Parameters @("WorkCycle=02:00:00") -Reason "Generate OAB every 2 hours" -Server Mailbox01
```

 **Exchange 2016 CU4 or later**:
  
    
    



```
New-SettingOverride -Name "Mailbox01 OAB Generation Override" -Component TimeBasedAssistants -Section OABGeneratorAssistant -Parameters @("WorkCycle=02:00:00") -Reason "Generate OAB every 2 hours" -Server Mailbox01
```


## How do you know this worked?

To verify that you've configured the OAB generation schedule on an Exchange 2016 server, replace  _<ServerName>_ with the name of the server (not the FQDN), and run either of the following commands and verify the value of the **WorkCycle** property:
  
    
    

- **Exchange 2016 CU3 or earlier**:
    
  ```
  [xml]$diag=Get-ExchangeDiagnosticInfo -Server <ServerName> -Process Microsoft.Exchange.Directory.TopologyService -Component VariantConfiguration -Argument Config; $diag.Diagnostics.Components.VariantConfiguration.Configuration.MailboxAssistants.OABGeneratorAssistant
  ```

- **Exchange 2016 CU4 or later**:
    
  ```
  [xml]$diag=Get-ExchangeDiagnosticInfo -Server <ServerName> -Process MSExchangeMailboxAssistants -Component VariantConfiguration -Argument "Config,Component=TimeBasedAssistants"; $diag.Diagnostics.Components.VariantConfiguration.Configuration.TimeBasedAssistants.OABGeneratorAssistant
  ```


## See also


#### 


  
    
    
 [Procedures for offline address books in Exchange 2016](procedures-for-offline-address-books-in-exchange-2016.md)
