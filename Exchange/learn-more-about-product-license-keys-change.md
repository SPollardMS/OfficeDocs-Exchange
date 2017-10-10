---
title: Learn more about product license keys [change]
ms.prod: EXCHANGE
ms.assetid: 638ed8ee-0f28-4ac4-9cb9-5784ab5b8cc5
---


# Learn more about product license keys [change]

When you install Microsoft Exchange Server 2013 without entering any product key, it's running as a Trial Edition. The Trial Edition expires 120 days after the date of installation. The Trial Edition functions as an Exchange Standard Edition server, but it isn't eligible for support from Microsoft Support Services. As the expiration of the Trial Edition gets near, the Exchange Administration Center (EAC) will display warnings that your trial period is about to expire. After the trial period has expired, the EAC will display a warning dialog for each expired server.
  
    
    

To use a server after the trial period, you must enter a product key. The product key determines whether your server is licensed as a Standard Edition server or as an Enterprise Edition server. After you enter the product key, you must restart the Microsoft Exchange Information Store service so that the change is applied. Depending on the product key that you enter, Exchange will determine if the server is running the Standard Edition or Enterprise Edition of Exchange 2013 and update any necessary settings.
If you've previously licensed the server using a Standard Edition product key, you can upgrade to the Enterprise Edition by entering an Enterprise Edition product key. However, you can't downgrade from the Enterprise Edition to the Standard Edition.
  
    
    

For more information about the Standard and Enterprise Editions of Exchange 2013, see  [How to Buy Exchange](https://go.microsoft.com/fwlink/p/?LinkID=63906).
## Use the Shell to enter the product key

You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Product key" entry in the  [Exchange infrastructure and PowerShell permissions](exchange-infrastructure-and-powershell-permissions.md) topic.
  
    
    
To enter the product key using the Exchange Management Shell, use the following command.
  
    
    



```

Set-ExchangeServer -Identity ExServer01 -ProductKey aaaaa-aaaaa-aaaaa-aaaaa-aaaaa
```


