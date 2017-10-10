---
title: Exchange 2016 Setup - Enter Credentials
ms.prod: EXCHANGE
ms.assetid: aacff641-11d3-40a6-bb6e-2afcd039ebf2
---


# Exchange 2016 Setup - Enter Credentials

On the **Enter Credentials** page, provide the user name and password of an administrator account in the Office 365 organization that's part of a hybrid deployment with your on-premises organization.
  
    
    

The user that you provide must be a member of the Organization Management role group in Exchange Online. (Exchange Online is a service that's part of your Office 365 organization.) The user must be in the Office 365 organization that's already configured in a hybrid deployment with your on-premises organization. If you provide a user that's a part of another Office 365 organization, you'll receive an error.
> [!CAUTION]
> Global Administrators in your Office 365 organization are automatically members of the Organization Management role group in the Exchange Online service. 
  
    
    

After you provide the user name and password, Setup will verify that your on-premises organization and your Office 365 tenant are ready for a hybrid deployment. Setup performs these checks by connecting to the Office 365 organization using remote Windows PowerShell. This connection requires that the computer has access to the Internet and can connect to https://ps.outlook.com/powershell.For more information about hybrid deployments, see  [Exchange Server 2016 Preview Hybrid Deployments](http://technet.microsoft.com/library/59e32000-4fcf-417f-a491-f1d8f9aeef9b.aspx). For more information about what's required before installing Microsoft Exchange Server 2016 in an organization with an existing hybrid deployment with Office 365, see  [Hybrid Configuration Wizard Prerequisites](http://technet.microsoft.com/library/e7454db0-fed4-4662-8890-9501126b1ba2.aspx).Having problems? Ask for help in the Exchange forums. Visit the forums at:  [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612),  [Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or  [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351).Did you find what you're looking for? Please take a minute to  [send us feedback](mailto:ExchangeHelpFeedback@microsoft.com&amp;subject=Exchange%202016%20help%20feedback&amp;Body=Thanks%20for%20taking%20the%20time%20to%20send%20us%20feedback!%20We%20strive%20to%20respond%20to%20every%20message%20we%20receive,%20even%20though%20it%20might%20take%20us%20a%20while.%20Let%20us%20know%20what%20you%20think%20about%20Exchange%20content:%20What%20are%20we%20doing%20right%3F%20How%20can%20we%20make%20help%20better%3F%0APlease%20note%20that%20we're%20unable%20to%20respond%20to%20requests%20for%20support%20submitted%20via%20this%20email%20address.%20If%20you%20need%20help,%20please%20contact%20Exchange%20Server%20support%20at%20http://go.microsoft.com/fwlink/p/%3FLinkId=402506.%0AThanks!%0AThe%20Exchange%20Server%20Content%20Publishing%20team) about the information you were hoping to find.
