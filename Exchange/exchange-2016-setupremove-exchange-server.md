---
title: Exchange 2016 Setup - Remove Exchange Server
ms.prod: EXCHANGE
ms.assetid: 73bb4bb0-0c1f-4ac6-9e53-1c9801acb8a0
---


# Exchange 2016 Setup - Remove Exchange Server

On the **Remove Exchange Server** page, you can remove Exchange from the computer.
  
    
    

When you remove Exchange from the computer, the following are removed:
- All server roles.
    
  
- All installation files.
    
  
- The Exchange server object and all its child objects from Active Directory.
    
    > [!IMPORTANT]
      > If you used  `Setup.exe /NewProvisionedServer` to provision the server, you must use `Setup.exe /RemoveProvisionedServer` after Exchange has been removed from the computer to remove the Exchange server object and all its child objects from Active Directory.
Removing Exchange from a computer doesn't remove any Exchange-related databases or log files. You must remove those files manually.Having problems? Ask for help in the Exchange forums. Visit the forums at:  [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612),  [Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or  [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351).Did you find what you're looking for? Please take a minute to  [send us feedback](mailto:ExchangeHelpFeedback@microsoft.com&amp;subject=Exchange%202016%20help%20feedback&amp;Body=Thanks%20for%20taking%20the%20time%20to%20send%20us%20feedback!%20We%20strive%20to%20respond%20to%20every%20message%20we%20receive,%20even%20though%20it%20might%20take%20us%20a%20while.%20Let%20us%20know%20what%20you%20think%20about%20Exchange%20content:%20What%20are%20we%20doing%20right%3F%20How%20can%20we%20make%20help%20better%3F%0APlease%20note%20that%20we're%20unable%20to%20respond%20to%20requests%20for%20support%20submitted%20via%20this%20email%20address.%20If%20you%20need%20help,%20please%20contact%20Exchange%20Server%20support%20at%20http://go.microsoft.com/fwlink/p/%3FLinkId=402506.%0AThanks!%0AThe%20Exchange%20Server%20Content%20Publishing%20team) about the information you were hoping to find.
