---
title: Learn more about hybrid transport paths
ms.prod: EXCHANGE
ms.assetid: 9b290dca-4241-4b6f-999a-1339a59c6f85
---


# Learn more about hybrid transport paths

> [!IMPORTANT]
> This feature of Exchange 2016 isn't fully compatible with Office 365 operated by 21Vianet in China and some feature limitations may apply. For more information, see  [Learn about Office 365 operated by 21Vianet](https://go.microsoft.com/fwlink/?LinkId=313640). 
  
    
    

On the **Transport path** page, select how you want to route secure mail transport between your on-premises Microsoft Exchange and Exchange Online organizations.
- **Client Access and Mailbox servers** The typical transport configuration is for your on-premises Client Access and Mailbox servers to handle message delivery and connect with the Exchange Online Protection (EOP) service in the Office 365 tenant organization. In this configuration, a Receive connector is configured on your on-premises Client Access servers to accept secure inbound connections from the EOP service in your Office 365 tenant organization. Additionally, a Send connector is configured on your on-premises Mailbox servers to initiate outbound connections to the EOP service in your Office 365 tenant organization. Together, these two connectors help to enable secure bi-directional mail transport between the on-premises and Exchange Online organizations.
    
  
- **Edge Transport servers** If you have Edge Transport servers in your organization, you can choose to configure the Edge Transport servers to handle message delivery and connect with the EOP service in the Office 365 tenant organization. In this configuration, a Receive connector is configured on your on-premises Edge Transport servers to accept secure inbound connections from the EOP service in your Office 365 tenant organization. Additionally, a Send connector is configured on your on-premises Edge Transport servers to initiate outbound connections to the EOP service in your Office 365 tenant organization. Together, these two connectors help to enable secure bi-directional mail transport between the on-premises and Exchange Online organizations.
    
  

## For more information

 [Understanding Transport Options in Exchange 2013 Hybrid Deployments](http://technet.microsoft.com/library/da605a78-5429-4de8-8b04-bc4c45a41ba1.aspx)
  
    
    
 [Edge Transport Servers with Hybrid Deployments](http://technet.microsoft.com/library/166b1490-5c56-40df-a17b-e8bb36224fd9.aspx)
  
    
    

