---
title: "Recover an Exchange Server"
ms.author: dmaguire
author: msdmaguire
manager: serdars
ms.date: 4/20/2018
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.collection: Strat_EX_Admin
ms.assetid: 46e9a1cf-b64c-43c3-a898-6171176da761
description: "Summary: Step-by-step guidance for recovering a lost Exchange 2016 Server."
---

# Recover an Exchange Server

 **Summary**: Step-by-step guidance for recovering a lost Exchange 2016 Server.
  
You can recover a lost server by using the **Setup /m:RecoverServer** switch in Microsoft Exchange Server 2016. Most of the settings for a computer running Exchange 2016 are stored in Active Directory. The  _/m:RecoverServer_ switch rebuilds an Exchange server with the same name by using the settings and other information stored in Active Directory. 
  
Recovering a lost Exchange server is often accomplished by using new hardware. However, you can also use an existing server.
  
This topic shows you how to recover a lost Exchange 2016 server that isn't a member of a database availability group (DAG). For detailed steps about how to recover a server that was a member of a DAG, see [Recover a database availability group member server](recover-dag-member-server.md).
  
> [!NOTE]
>  If Exchange is installed in a location other than the default location, you must use the  _/TargetDir_ switch to specify the location of the Exchange binary files. If you don't use the  _/TargetDir_ switch, the Exchange files are installed in the default location (%programfiles%\Microsoft\Exchange Server\V15). >  To determine the install location, follow these steps: >  Open ADSIEDIT.MSC or LDP.EXE. >  Navigate to the following location: **CN=ExServerName,CN=Servers,CN=First Administrative Group,CN=Administrative Groups,CN=ExOrg Name,CN=Microsoft Exchange,CN=Services,CN=Configuration,DC=DomainName,CN=Com**>  Right-click the Exchange server object, and then click **Properties**. >  Locate the **msExchInstallPath** attribute. This attribute stores the current installation path. 
  
Looking for other management tasks related to backing up and restoring data? Check out [Backup, Restore, and Disaster Recovery](http://technet.microsoft.com/library/394fc4ed-fa02-41fa-9159-cc2754ff8875.aspx).
  
## What do you need to know before you begin?

- Estimated time to complete: 20 minutes
    
- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Exchange infrastructure permissions" section in the [Exchange infrastructure and PowerShell permissions](../../permissions/feature-permissions/exchange-infrastructure-and-powershell-permissions.md) topic. 
    
- You must recover the server to the same Cumulative Update version as it was at the time of failure. It is not possible to recover a server and update it at the same time.
    
- The server on which recovery is being performed must be running the same operating system as the lost server. For example, you can't recover a server that was running Exchange 2013 and Windows Server 2008 R2 on a server running Windows Server 2012, or vice versa. Likewise, you can't recover a server that was running Exchange 2013 and Windows Server 2012 on a server running Windows Server 2012 R2, or vice versa.
    
- The same disk drive letters on the failed server for mounted databases must exist on the server on which you're running recovery.
    
- The server on which recovery is being performed should have the same performance characteristics and hardware configuration as the lost server.
    
- For information about keyboard shortcuts that may apply to the procedures in this topic, see [Keyboard shortcuts in the Exchange admin center](../../about-documentation/keyboard-shortcuts-in-eac.md).
    
> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at: [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351).. 
  
## Recover a Lost Exchange Server

1. Reset the computer account for the lost server. For detailed steps, see [Reset a Computer Account](https://go.microsoft.com/fwlink/p/?linkId=165388).
    
2. Install the proper operating system and name the new server with the same name as the lost server. Recovery won't succeed if the server on which recovery is being performed doesn't have the same name as the lost server.
    
3. Join the server to the same domain as the lost server.
    
4. Install the necessary prerequisites and operating system components. For details, see [Exchange 2016 system requirements](../../plan-and-deploy/system-requirements.md) and [Exchange 2016 prerequisites](../../plan-and-deploy/prerequisites.md).
    
5. Log on to the server being recovered and open a command prompt.
    
6. Navigate to the Exchange 2016 installation files, and run the following command.
    
  ```
  Setup /m:RecoverServer /IAcceptExchangeServerLicenseTerms
  ```

7. After Setup has completed, but before the recovered server is put into production, reconfigure any custom settings that were previously present on the server, and then restart the server.
    
## How do you know this worked?

The successful completion of Setup will be the primary indicator that the recovery was successful. To further verify that you've successfully recovered a lost server, do the following:
  
- Open the Windows Services tool (services.msc) and verify that the Microsoft Exchange services have been installed and are running.
    

