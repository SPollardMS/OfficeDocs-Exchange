---
title: "Configure the external postmaster address in Exchange Online"
ms.author: chrisda
author: chrisda
manager: laurawi
ms.date: 4/29/2016
ms.audience: ITPro
ms.topic: article
ms.service: exchange-online
localization_priority: Normal
ms.assetid: ece00da0-743b-4e26-83f5-a2eb68c7de4e
description: "Use the procedure here to change your organization's external postmaster address. The external postmaster address is used as the sender for system-generated messages and notifications sent to message senders that exist outside your Microsoft Exchange Online organization. An external sender is any sender that has an email address in a domain that isn't configured as an accepted domain in your organization."
---

# Configure the external postmaster address in Exchange Online

Use the procedure here to change your organization's external postmaster address. The external postmaster address is used as the sender for system-generated messages and notifications sent to message senders that exist outside your Microsoft Exchange Online organization. An external sender is any sender that has an email address in a domain that isn't configured as an accepted domain in your organization.
  
By default, the value of the external postmaster address setting is blank. This default value sets the external postmaster address to the value postmaster@\< _Default accepted domain_\> for your organization.
  
## What do you need to know before you begin?

- Estimated time to complete: 15 minutes
    
- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Transport configuration" entry in the [Mail flow permissions](http://technet.microsoft.com/library/f49f4fb5-af75-43cb-900f-c5f7b8cfa143.aspx) topic. 
    
- You can only use the Shell to perform this procedure. To learn how to use Windows PowerShell to connect to Exchange Online, see [Connect to Exchange Online PowerShell](https://go.microsoft.com/fwlink/p/?linkid=396554).
    
- For information about keyboard shortcuts that may apply to the procedures in this topic, see **Keyboard shortcuts in the Exchange admin center**.
    
## Use the Exchange Management Shell to configure the external postmaster address

To configure the external postmaster address, use the following syntax.
  
```
Set-TransportConfig -ExternalPostmasterAddress <postmaster address>

```

For example, to set the external postmaster address to the value  `postmaster@contoso.com`, run the following command
  
```
Set-TransportConfig -ExternalPostmasterAddress postmaster@contoso.com
```

To return the external postmaster address to the default value, run the following command:
  
```
Set-TransportConfig -ExternalPostmasterAddress $null

```

## How do you know this worked?

To verify that you have successfully configured the external postmaster address, do the following:
  
1. Run the following command to verify the external postmaster address value:
    
  ```
  Get-TransportConfig | Format-List ExternalPostmasterAddress
  
  ```

2. From an external email account, send a message to your Exchange organization that will generate a delivery status notification (DSN). To ensure a DSN will be sent from your external postmaster address, you can configure a transport rule to send a non-delivery report (NDR), which is a type of DSN, for a message from that sender that contains specific keywords. Verify that the sender's email address in the DSN matches the external postmaster address you specified. 
    
Having problems? Ask for help in the Exchange forums. Visit the forums at [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612),[Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351).
  

