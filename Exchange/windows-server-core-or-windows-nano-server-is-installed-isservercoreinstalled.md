---
title: Windows Server Core or Windows Nano Server is installed [IsServerCoreInstalled]
ms.prod: EXCHANGE
ms.assetid: 3d297c4f-7b5a-4faa-bf5e-320fe0529dfe
---


# Windows Server Core or Windows Nano Server is installed [IsServerCoreInstalled]

Microsoft Exchange Server 2016 Setup can't continue because it detected that the local computer is running Windows Server Core or Windows Nano Server. Exchange 2016 requires that **Windows Server with Desktop Experience** (Windows Server 2016) or **Windows Server with a GUI** (Windows Server 2012 and 2012R2) be installed on the local computer. Before you can install Exchange 2016, you need to do one of the following depending on the version of Windows Server you have installed:
  
    
    


- **Windows Server 2012 and Windows Server 2012 R2** Run the following command in Windows PowerShell
    
  ```
  
Install-WindowsFeature Server-Gui-Mgmt-Infra, Server-Gui-Shell -Restart
  ```

- **Windows Server 2016** Install Windows Server 2016 and choose the **Desktop Experience** installation option. If a computer is running Windows Server 2016 Core or Nano and you want to install Exchange 2016 on it, you'll need to reinstall the operating system and choose the **Desktop Experience** installation option.
    
  

For more information, see  [Exchange 2016 system requirements](exchange-2016-system-requirements.md).
  
    
    

Having problems? Ask for help in the Exchange forums. Visit the forums at:  [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612),  [Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or  [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351).Did you find what you're looking for? Please take a minute to  [send us feedback](mailto:ExchangeHelpFeedback@microsoft.com&amp;subject=Exchange%202016%20help%20feedback&amp;Body=Thanks%20for%20taking%20the%20time%20to%20send%20us%20feedback!%20We%20strive%20to%20respond%20to%20every%20message%20we%20receive,%20even%20though%20it%20might%20take%20us%20a%20while.%20Let%20us%20know%20what%20you%20think%20about%20Exchange%20content:%20What%20are%20we%20doing%20right%3F%20How%20can%20we%20make%20help%20better%3F%0APlease%20note%20that%20we're%20unable%20to%20respond%20to%20requests%20for%20support%20submitted%20via%20this%20email%20address.%20If%20you%20need%20help,%20please%20contact%20Exchange%20Server%20support%20at%20http://go.microsoft.com/fwlink/p/%3FLinkId=402506.%0AThanks!%0AThe%20Exchange%20Server%20Content%20Publishing%20team) about the information you were hoping to find.
