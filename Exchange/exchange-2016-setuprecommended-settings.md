---
title: Exchange 2016 Setup - Recommended Settings
ms.prod: EXCHANGE
ms.assetid: 1cc13946-8318-4951-b4c1-59cd0c207bb4
---


# Exchange 2016 Setup - Recommended Settings

On the **Recommended Settings** page, you can choose whether Microsoft Exchange Server 2016 automatically configures Error Reporting and Customer Experience Information Program (CEIP) settings for you or if you want to configure these options manually.
  
    
    

If you select **Use recommended settings**, Setup will do the following:
- **Enable Error Reporting** Exchange will automatically send error reports to Microsoft. If an error occurs, the server uses an HTTPS (TCP Port 443) connection to send information to Microsoft over an encrypted channel. This information is stored in facilities with controlled access and is used only to improve Microsoft products. Exchange Error Reporting doesn't intentionally collect any personal information such as email addresses. However individual error reports may inadvertently contain personal information. Although such information could potentially be used to determine the identity of Exchange Server users, if present, it will not be used.
    
    When the Exchange Error Reporting feature is enabled and the issue has a known solution, the server will receive feedback from Microsoft. This feedback will contain a link to a web page that may help you resolve the problem.
    
    For more information about Error Reporting, see  [Privacy Statement for the Microsoft Error Reporting Service](https://go.microsoft.com/fwlink/p/?LinkId=260761).
    
  
- **Enable CEIP collection** CEIP collects information about computer hardware and how you use Exchange, without interrupting you. This helps Microsoft understand which Exchange features to improve. We won't use the information to identify or contact you.
    
    If you join the program, all Exchange servers in your organization will be included. You can exclude specific servers at any time by using the **Set-ExchangeServer** cmdlet in the Exchange Management Shell. If you don't join the program, none of your servers will be included.
    
    For more information about CEIP, see  [Microsoft Customer Experience Information Program](https://go.microsoft.com/fwlink/?LinkID=128530).
    
  
If you choose **Don't use recommended settings**, the Error Reporting and CEIP settings remain disabled. You can enable them yourself at any time.Having problems? Ask for help in the Exchange forums. Visit the forums at:  [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612),  [Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or  [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351).Did you find what you're looking for? Please take a minute to  [send us feedback](mailto:ExchangeHelpFeedback@microsoft.com&amp;subject=Exchange%202016%20help%20feedback&amp;Body=Thanks%20for%20taking%20the%20time%20to%20send%20us%20feedback!%20We%20strive%20to%20respond%20to%20every%20message%20we%20receive,%20even%20though%20it%20might%20take%20us%20a%20while.%20Let%20us%20know%20what%20you%20think%20about%20Exchange%20content:%20What%20are%20we%20doing%20right%3F%20How%20can%20we%20make%20help%20better%3F%0APlease%20note%20that%20we're%20unable%20to%20respond%20to%20requests%20for%20support%20submitted%20via%20this%20email%20address.%20If%20you%20need%20help,%20please%20contact%20Exchange%20Server%20support%20at%20http://go.microsoft.com/fwlink/p/%3FLinkId=402506.%0AThanks!%0AThe%20Exchange%20Server%20Content%20Publishing%20team) about the information you were hoping to find.
