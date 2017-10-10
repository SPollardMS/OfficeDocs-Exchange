---
title: Exchange 2016 Setup - Server Role Selection
ms.prod: EXCHANGE
ms.assetid: 324bea51-6d43-4569-be87-af14a1468744
---


# Exchange 2016 Setup - Server Role Selection

On the **Server Role Selection** page you can choose which Microsoft Exchange Server 2016 server roles you want to install on this computer.
  
    
    

Exchange includes the Mailbox and Edge Transport server roles. The Edge Transport server role must be installed on its own computer. You can't install the Mailbox server role on the same computer as the Edge Transport server role.
You can select **Automatically install Windows Server roles and features that are required to install Exchange Server** to have the Setup wizard install required Windows prerequisites. You may need to restart the computer to complete the installation of some Windows features. If you don't select this option, you must install the Windows features manually.
  
    
    


> [!NOTE]
> This option installs only the Windows features required by Exchange. You must install other prerequisites manually. For more information, see  [Exchange 2016 prerequisites](exchange-2016-prerequisites.md). 
  
    
    

The **Management Tools** option is selected automatically if any server role is selected. If you want to administer Exchange from a client computer, you can install the management tools separately from the Mailbox and Edge Transport server roles.
> [!NOTE]
> You can only administer the Edge Transport server role using the Exchange Management Shell. 
  
    
    

For more information about deploying Exchange 2016, see  [Planning and deployment](planning-and-deployment.md).For more information about Exchange server roles, see  [Exchange 2016 Architecture](http://technet.microsoft.com/library/0dac9f83-efd2-4a2d-940a-c03310bf9c6a.aspx).Having problems? Ask for help in the Exchange forums. Visit the forums at:  [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612),  [Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or  [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351).Did you find what you're looking for? Please take a minute to  [send us feedback](mailto:ExchangeHelpFeedback@microsoft.com&amp;subject=Exchange%202016%20help%20feedback&amp;Body=Thanks%20for%20taking%20the%20time%20to%20send%20us%20feedback!%20We%20strive%20to%20respond%20to%20every%20message%20we%20receive,%20even%20though%20it%20might%20take%20us%20a%20while.%20Let%20us%20know%20what%20you%20think%20about%20Exchange%20content:%20What%20are%20we%20doing%20right%3F%20How%20can%20we%20make%20help%20better%3F%0APlease%20note%20that%20we're%20unable%20to%20respond%20to%20requests%20for%20support%20submitted%20via%20this%20email%20address.%20If%20you%20need%20help,%20please%20contact%20Exchange%20Server%20support%20at%20http://go.microsoft.com/fwlink/p/%3FLinkId=402506.%0AThanks!%0AThe%20Exchange%20Server%20Content%20Publishing%20team) about the information you were hoping to find.
