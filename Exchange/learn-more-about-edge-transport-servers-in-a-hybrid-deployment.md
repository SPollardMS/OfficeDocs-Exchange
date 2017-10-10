---
title: Learn more about Edge Transport servers in a hybrid deployment
ms.prod: EXCHANGE
ms.assetid: 945f7d52-5366-43d8-971d-6f9c204502da
---


# Learn more about Edge Transport servers in a hybrid deployment

> [!IMPORTANT]
> This feature of Exchange 2016 isn't fully compatible with Office 365 operated by 21Vianet in China and some feature limitations may apply. For more information, see  [Learn about Office 365 operated by 21Vianet](https://go.microsoft.com/fwlink/?LinkId=313640). 
  
    
    

On the **Select Edge Transport server** page, select a server in your Microsoft Exchange on-premises organization that has the Edge Transport server role installed.
When you add an Edge Transport server to your hybrid deployment, it communicates with the Microsoft Exchange Online Protection (EOP) service in your Office 365 tenant organization on behalf of the internal Client Access and Mailbox servers. The Edge Transport server acts as a relay between the on-premises Client Access servers and EOP. All connection security handled by the Client Access server in the hybrid deployment is handled by the Edge Transport server. However, all recipient lookup, compliance policies, and other message inspection actions are done on the Client Access servers.
  
    
    


> [!IMPORTANT]
> The Hybrid Configuration wizard can't completely configure your Edge Transport servers for hybrid transport because they aren't joined to your on-premises domain. After the completion of the Hybrid Configuration wizard, you'll need to manually configure parameters on your Edge Transport servers if you've selected the Edge Transport server routing path in the wizard. 
  
    
    


## For more information

 [Edge Transport Servers with Hybrid Deployments](http://technet.microsoft.com/library/166b1490-5c56-40df-a17b-e8bb36224fd9.aspx)
  
    
    

