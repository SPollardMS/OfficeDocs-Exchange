---
title: Can't install Exchange 2016 in a forest that contains Exchange 2000 or Exchange 2003 servers. [Exchange2000or2003PresentInOrg]
ms.prod: EXCHANGE
ms.assetid: a115b182-cbd2-4d31-aa0e-375240939301
---


# Can't install Exchange 2016 in a forest that contains Exchange 2000 or Exchange 2003 servers. [Exchange2000or2003PresentInOrg]

Microsoft Exchange Server 2016 can't continue because one or more computers are running Exchange 2007 or older were found in the Active Directory forest. Before you can install Exchange 2016, all computers running Exchange 2007 or older must be removed from the forest. Mailboxes, public folders, and all other Exchange objects or components must be upgraded to the latest release of Exchange Server 2010.
  
    
    

The path you need to follow to install Exchange 2016 in your organization depends on the version of Exchange you currently have installed in your forest. See the following table for more information.

|**If you have the following installed in your organization**|**You must take this path to upgrade to Exchange 2016**|
|:-----|:-----|
|Exchange 2000  <br/> | Install Exchange 2007 into your Exchange 2000 organization. <br/>  Configure Exchange 2007 and Exchange 2000 coexistence. <br/>  Migrate Exchange 2000 mailboxes, public folders, and other components to Exchange 2007. <br/>  Decommission and remove all Exchange 2000 servers. <br/>  Install Exchange 2013 into your Exchange 2007 organization. <br/>  Configure Exchange 2013 and Exchange 2007 coexistence. <br/>  Migrate Exchange 2007 mailboxes, public folders, and other components to Exchange 2013. <br/>  Decommission and remove all Exchange 2007 servers. <br/>  Install Exchange 2016 into your Exchange 2013 organization. <br/>  Configure Exchange 2016 and Exchange 2013 coexistence. <br/>  Migrate Exchange 2013 mailboxes, public folders, and other components to Exchange 2016. <br/>  Decommission and remove all Exchange 2013 servers. <br/> |
|Exchange 2003  <br/> | Install Exchange 2010 into your Exchange 2003 organization. <br/>  Configure Exchange 2010 and Exchange 2003 coexistence. <br/>  Migrate Exchange 2003 mailboxes, public folders, and other components to Exchange 2010. <br/>  Decommission and remove all Exchange 2003 servers. <br/>  Install Exchange 2016 into your Exchange 2010 organization. <br/>  Configure Exchange 2016 and Exchange 2010 coexistence. <br/>  Migrate Exchange 2010 mailboxes, public folders, and other components to Exchange 2016. <br/>  Decommission and remove all Exchange 2010 servers. <br/> |
|Exchange 2007  <br/> | Install Exchange 2013 into your Exchange 2007 organization. <br/>  Configure Exchange 2013 and Exchange 2007 coexistence. <br/>  Migrate Exchange 2007 mailboxes, public folders, and other components to Exchange 2013. <br/>  Decommission and remove all Exchange 2007 servers. <br/>  Install Exchange 2016 into your Exchange 2013 organization. <br/>  Configure Exchange 2016 and Exchange 2013 coexistence. <br/>  Migrate Exchange 2013 mailboxes, public folders, and other components to Exchange 2016. <br/>  Decommission and remove all Exchange 2013 servers. <br/> |
   
When upgrading to Exchange 2010 or later, you can use the Exchange Deployment Assistant to help you complete your deployment. For more information, see the following links:
-  [Exchange 2010 Deployment Assistant](https://go.microsoft.com/fwlink/p/?LinkId=171086)
    
  
-  [Exchange 2013 Deployment Assistant](https://go.microsoft.com/fwlink/p/?LinkId=277105)
    
  
Having problems? Ask for help in the Exchange forums. Visit the forums at:  [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612),  [Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or  [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351).Did you find what you're looking for? Please take a minute to  [send us feedback](mailto:ExchangeHelpFeedback@microsoft.com&amp;subject=Exchange%202016%20help%20feedback&amp;Body=Thanks%20for%20taking%20the%20time%20to%20send%20us%20feedback!%20We%20strive%20to%20respond%20to%20every%20message%20we%20receive,%20even%20though%20it%20might%20take%20us%20a%20while.%20Let%20us%20know%20what%20you%20think%20about%20Exchange%20content:%20What%20are%20we%20doing%20right%3F%20How%20can%20we%20make%20help%20better%3F%0APlease%20note%20that%20we're%20unable%20to%20respond%20to%20requests%20for%20support%20submitted%20via%20this%20email%20address.%20If%20you%20need%20help,%20please%20contact%20Exchange%20Server%20support%20at%20http://go.microsoft.com/fwlink/p/%3FLinkId=402506.%0AThanks!%0AThe%20Exchange%20Server%20Content%20Publishing%20team) about the information you were hoping to find.
