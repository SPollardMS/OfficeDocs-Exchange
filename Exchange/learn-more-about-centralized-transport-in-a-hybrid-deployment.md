---
title: Learn more about centralized transport in a hybrid deployment
ms.prod: EXCHANGE
ms.assetid: c0c4a8bf-746b-4a4e-8cfd-7462e6abf7ec
---


# Learn more about centralized transport in a hybrid deployment

> [!IMPORTANT]
> This feature of Exchange 2016 isn't fully compatible with Office 365 operated by 21Vianet in China and some feature limitations may apply. For more information, see  [Learn about Office 365 operated by 21Vianet](https://go.microsoft.com/fwlink/?LinkId=313640). 
  
    
    

On the **Transport** page of the Hybrid Configuration wizard, you can select the option for centralized mail transport for your hybrid deployment.
If you select the **enable centralized mail transport** check box, you'll configure the routing of all mail from mailboxes in the Exchange Online organization through the on-premises organization before they're delivered to the Internet. Because the Hybrid Configuration wizard doesn't update the MX record for your organization, incoming email for Exchange Online-based mailboxes from external recipients is also routed through the on-premises Exchange organization. This approach is helpful mainly in compliance scenarios where all mail to and from the Internet must be processed by on-premises servers.
  
    
    

If you don't select the **enable centralized mail transport** check box, Exchange Online mailboxes will be configured to deliver messages for external recipients directly to the Internet and bypass your on-premises organization.Unless you have a defined need to have outbound mail from your Exchange Online-based mailboxes routed through your on-premises organization, we recommend that you don't enable centralized mail transport in your hybrid deployment. Enabling centralized mail transport complicates the routing configuration and can be more difficult to troubleshoot in the event of routing difficulties.
## For more information

 [Transport Options in Exchange 2013 Hybrid Deployments](http://technet.microsoft.com/library/da605a78-5429-4de8-8b04-bc4c45a41ba1.aspx)
  
    
    

