---
title: "Enter your Exchange 2016 product key"
ms.author: dstrome
author: dstrome
manager: serdars
ms.date: 4/19/2018
ms.audience: ITPro
ms.topic: get-started-article
f1_keywords:
- 'Microsoft.Exchange.Management.SnapIn.Esm.Servers.EnterProductKeyWizardForm.EnterProductKeyWizardPage'
ms.prod: office-online-server
localization_priority: Normal
ms.collection: Strat_EX_Admin
ms.assetid: ccb14685-4bdc-42a4-a985-35cd2a1a415c
description: "Summary: Learn ways to enter your Exchange 2016 product key. If you're looking for product key information about Office, we've also provided links to get you to the correct articles for that."
---

# Enter your Exchange 2016 product key

 **Summary**: Learn ways to enter your Exchange 2016 product key. If you're looking for product key information about Office, we've also provided links to get you to the correct articles for that.
  
A product key tells Exchange Server 2016 that you've purchased a Standard or Enterprise Edition license. If the product key you purchased is for an Enterprise Edition license, it lets you mount more than five databases per server in addition to everything that's available with a Standard Edition license. If you want to read more about Exchange licensing, see [Exchange 2016 editions and versions](../../plan-and-deploy/deployment-reference/editions-and-versions.md).
  
If you don't enter a product key, your server is automatically licensed as a trial edition. The trial edition functions just like an Exchange Standard Edition server and is helpful if you want to try out Exchange before you buy it, or to run tests in a lab. The only difference is that you can only use an Exchange server licensed as a trial edition for up to 180 days. If you want to keep using the server beyond 180 days, you'll need to enter a product key or the Exchange Admin Center (EAC) will start to show reminders that you need to enter a product key to license the server.
  
> [!TIP]
>  We've noticed some visitors to this page are looking for information on how to install or activate Office. If that's you, check out these pages: > [Install Office](https://go.microsoft.com/fwlink/p/?LinkId=403360)> [Need help with your Office product key?](https://go.microsoft.com/fwlink/p/?LinkId=403361)>  If you want to enter a product key on an Exchange 2010 or Exchange 2013, check out these pages: > [Enter an Exchange 2010 product key](https://go.microsoft.com/fwlink/p/?LinkId=403370)> [Enter an Exchange 2013 product key](https://go.microsoft.com/fwlink/p/?LinkId=620781)>  If you want to enter a product key on an Exchange 2016 server, you're in the right place! Read on. 
  
## What do you need to know before you begin?

- Estimated time to complete this procedure: less than 5 minutes.
    
- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Product key" entry in the [Exchange infrastructure and PowerShell permissions](../../permissions/feature-permissions/exchange-infrastructure-and-powershell-permissions.md) topic. 
    
- If you're licensing an Exchange server that's running the Mailbox server role, you'll need to restart the Microsoft Exchange Information Store service on the server after you enter the product key.
    
- If you want to upgrade an Exchange server from a Standard Edition license to an Enterprise Edition license, follow the steps in this topic.
    
- If you want to downgrade an Exchange server from an Enterprise Edition license to a Standard Edition license, you need to reinstall Exchange.
    
- For information about keyboard shortcuts that may apply to the procedures in this topic, see [Keyboard shortcuts in the Exchange admin center](../../about-documentation/keyboard-shortcuts-in-eac.md).
    
> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at: [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351). 
  
## What do you want to do?

### Use the EAC to enter the product key

1. Open the EAC by browsing to https://< _Client Access server name_>/ecp.
    
2. Enter your user name and password in **Domain\user name** and **Password**, and then click **Sign in**.
    
3. Go to **Servers** > **Servers**. Select the server you want to license, and then click **Edit**![Edit icon](../../media/ITPro_EAC_EditIcon.png).
    
4. (Optional) If you want to upgrade the server from a Standard Edition license to an Enterprise Edition license, on the **General** page, select **Change product key**. You'll only see this option if the server is already licensed.
    
5. On the **General** page, enter your product key in the **Enter a valid product key** text boxes. 
    
6. Click **Save**.
    
7. If you licensed an Exchange server running the Mailbox server role, do the following to restart the Microsoft Exchange Information Store service:
    
1. Open **Control Panel**, go to **Administrative Tools**, and then open **Services**.
    
2. Right-click on **Microsoft Exchange Information Store** and click **Restart**.
    
### Use the Exchange Management Shell to enter the product key

This example uses the **set-ExchangeServer** cmdlet to enter the product key. 
  
> [!NOTE]
> You can run this command again on the same server to upgrade it from a Standard Edition license to an Enterprise Edition license. 
  
```
Set-ExchangeServer ExServer01 -ProductKey XXXXX-XXXXX-XXXXX-XXXXX-XXXXX
```

For detailed syntax and parameter information, see [Set-ExchangeServer](http://technet.microsoft.com/library/8e8d3fca-59b3-4355-a637-28bf5e5ca4cf.aspx).
  
If you licensed an Exchange server running the Mailbox server role, do the following to restart the Microsoft Exchange Information Store service:
  
1. Open **Control Panel**, go to **Administrative Tools**, and then open **Services**.
    
2. Right-click **Microsoft Exchange Information Store** and click **Restart**.
    
## How do you know this worked?

To use the EAC to verify that you've successfully licensed the server as Standard Edition or Enterprise Edition, do the following:
  
1. Enter your user name and password in **Domain\user name** and **Password**, and then click **Sign in**.
    
2. Go to **Servers** > **Servers**.
    
3. Select the server you want to view, and then look in the server details pane. If the product key has been accepted, **Licensed** will appear along with the Exchange 2016 edition. 
    
To use the Exchange Management Shell to verify that you've successfully licensed the server as Standard Edition or Enterprise Edition, do the following:
  
1. Open the Exchange Management Shell.
    
2. Run the following command to view the licensing status of a specific Exchange server.
    
  ```
  Get-ExchangeServer ExServer01 | Format-Table Edition,*Trial*
  ```

3. (Optional) Run the following command to view the licensing status of all Exchange servers in your organization.
    
  ```
  Get-ExchangeServer | Format-Table Name, Edition, *Trial* -Auto
  ```


