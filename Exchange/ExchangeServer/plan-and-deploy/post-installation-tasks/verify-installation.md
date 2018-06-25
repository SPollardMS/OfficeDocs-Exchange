---
title: "Verify an Exchange 2016 installation"
ms.author: dstrome
author: dstrome
manager: serdars
ms.date: 6/8/2018
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: exchange-server-itpro
localization_priority: Normal
ms.collection: Strat_EX_Admin
ms.assetid: fdd20a2a-c8c1-4d17-b813-3c05d88a4411
description: "Summary: Learn how to verify your Exchange 2016 installation and make troubleshooting easier."
---

# Verify an Exchange 2016 installation

 **Summary**: Learn how to verify your Exchange 2016 installation and make troubleshooting easier.
  
After you install Microsoft Exchange Server 2016, we recommend that you verify the installation by running the **Get-ExchangeServer** cmdlet and by reviewing the setup log file. If the setup process fails or errors occur during installation, you can use the setup log file to track down the source of the problem. 
  
Having problems? Ask for help in the Exchange forums. Visit the forums at: [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351).
  
Did you find what you're looking for? Please take a minute to [send us feedback](mailto:ExchangeHelpFeedback@microsoft.com&subject=Exchange%202016%20help%20feedback&Body=Thanks%20for%20taking%20the%20time%20to%20send%20us%20feedback!%20We%20strive%20to%20respond%20to%20every%20message%20we%20receive,%20even%20though%20it%20might%20take%20us%20a%20while.%20Let%20us%20know%20what%20you%20think%20about%20Exchange%20content:%20What%20are%20we%20doing%20right%3F%20How%20can%20we%20make%20help%20better%3F%0APlease%20note%20that%20we're%20unable%20to%20respond%20to%20requests%20for%20support%20submitted%20via%20this%20email%20address.%20If%20you%20need%20help,%20please%20contact%20Exchange%20Server%20support%20at%20http://go.microsoft.com/fwlink/p/%3FLinkId=402506.%0AThanks!%0AThe%20Exchange%20Server%20Content%20Publishing%20team) about the information you were hoping to find. 
  
## Run Get-ExchangeServer

To verify that Exchange 2016 installed successfully, run the **Get-ExchangeServer** cmdlet in the Exchange Management Shell. A list is displayed of all Exchange 2016 server roles that are installed on the specified server when this cmdlet is run. 
  
For detailed syntax and parameter information, see [Get-ExchangeServer](http://technet.microsoft.com/library/96543903-10fa-46fe-9ea0-90570ca0ad2e.aspx).
  
## Review the setup log file

You can also learn more about the installation and configuration of Exchange 2016 by reviewing the setup log file created during the setup process.
  
During installation, Exchange Setup logs events in the **Application** log of **Event Viewer** on computers that are running Windows Server 2012 and Windows Server 2012 R2. Review the **Application** log, and make sure there are no warning or error messages related to Exchange setup. These log files contain a history of each action that the system takes during Exchange 2016 setup and any errors that may have occurred. By default, the logging method is set to `Verbose`. Information is available for each installed server role.
  
You can find the setup log file at _\<system drive\>_\ExchangeSetupLogs\ExchangeSetup.log. The _\<system drive\>_ variable represents the root directory of the drive where the operating system is installed. 
  
The setup log file tracks the progress of every task that is performed during the Exchange 2016 installation and configuration. The file contains information about the status of the prerequisite and system readiness checks that are performed before installation starts, the application installation progress, and the configuration changes that are made to the system. Check this log file to verify that the server roles were installed as expected.
  
We recommend that you start your review of the setup log file by searching for any errors. If you find an entry that indicates that an error occurred, read the associated text to determine the cause of the error.
  

