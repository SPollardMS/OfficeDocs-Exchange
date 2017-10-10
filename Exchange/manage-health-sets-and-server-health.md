---
title: Manage health sets and server health
ms.prod: EXCHANGE
ms.assetid: a4f84312-6cfa-4f17-9707-676aadab1143
---


# Manage health sets and server health
 **Summary**: Powershell cmdlets that can help you monitor the health of your Exchange 2016 organization.
You can use the built-in health reporting cmdlets to perform a variety of tasks related to managed availability, such as:
  
    
    


- Viewing the health of a server or group of servers
    
  
- Viewing a list of health sets
    
  
- Viewing a list of probes, monitors, and responders associated with a particular health set
    
  
- View a list of monitors and their current health
    
  

## What do you need to know before you begin?


- Estimated time to complete each procedure: 2 minutes
    
  
- For information about keyboard shortcuts that may apply to the procedures in this topic, see  [Keyboard shortcuts in the Exchange admin center](keyboard-shortcuts-in-the-exchange-admin-center.md).
    
  

> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at:  [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612),  [Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or  [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351). 
  
    
    


## What do you want to do?


### View Server Health

You can use the Shell to get a summary of the health of a server running Exchange 2016.
  
    
    

#### Use the Shell to View Server Health

Run either of the following commands to view the health sets and health information on a server running Exchange 2016.
  
    
    

```

Get-HealthReport -Identity <ServerName>
```


```
Get-ServerHealth -Identity <ServerName> | Format-Table Server,CurrentHealthSetState,Name,HealthSetName,AlertValue,HealthGroupName -Auto
```

Run any of the following commands to view the health sets on a server or database availability group running Exchange 2016.
  
    
    



```
Get-ExchangeServer | Get-HealthReport -RollupGroup
```




```
Get-ExchangeServer | Get-HealthReport -RollupGroup -HealthSetName <HealthSet>
```




```
(Get-DatabaseAvailabiltyGroup <DAGName>).Servers | Get-HealthReport -RollupGroup
```


### View a List of Health Sets

A health set is a group of monitors, probes and responders for a component that determine whether the component is healthy or unhealthy. You can use the Shell to view the list of health sets on a server running Exchange 2016.
  
    
    

#### Use the Shell to View a List of Health Sets

Run the following command to view the health sets on a server running Exchange 2016.
  
    
    

```
Get-HealthReport -Server <ServerName>
```


### View the Probes, Monitors and Responders for a Health Set

A health set is a group of monitors, probes and responders for a component that determine whether the component is healthy or unhealthy. You can use the Shell to view the list of probes, monitors, and responders associated with a health set on a server running Exchange 2016.
  
    
    

#### Use the Shell to View the Probes, Monitors and Responders for a Health Set

Run the following command to view the probes, monitors and responders associated with a health set on a server running Exchange 2016.
  
    
    

```
Get-MonitoringItemIdentity -Server <ServerName> -Identity <HealthSetName> | Format-Table Identity,ItemType,Name -Auto
```


### View a List of Monitors and Their Current Health

The health of a monitor is reported by using the "worst of" monitors in the health set. You can view the details of a health set to see which monitors are healthy and which ones are unhealthy.
  
    
    

#### Use the Shell to View a List of Monitors and Their Current Health

Run the following command to view a list of the monitors and their current health on a server running Exchange 2016.
  
    
    

```
Get-ServerHealth -HealthSet <HealthSetName> -Server <ServerName> | Format-Table Name, AlertValue -Auto
```


