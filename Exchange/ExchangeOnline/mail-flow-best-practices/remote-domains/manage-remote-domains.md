---
title: "Manage remote domains in Exchange Online"
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
ms.date: 4/29/2016
ms.audience: End User
ms.topic: article
ms.service: exchange-online
localization_priority: Normal
ms.assetid: d3dca7b0-c84c-429a-9698-0e92a95a0985
description: "You can control the types and format of messages that are sent to domains outside your Exchange organization. Follow the procedures in this topic to create and configure a remote domain in Exchange Online, or to modify the default remote domain. For information about when to configure remote domains, descriptions of the available settings, and information about how remote domain settings override per-user settings, see Remote domains in Exchange Online."
---

# Manage remote domains in Exchange Online

You can control the types and format of messages that are sent to domains outside your Exchange organization. Follow the procedures in this topic to create and configure a remote domain in Exchange Online, or to modify the default remote domain. For information about when to configure remote domains, descriptions of the available settings, and information about how remote domain settings override per-user settings, see [Remote domains in Exchange Online](remote-domains.md).
  
## What do you need to know before you begin?

- The following table shows the default values for common settings. For more information about each setting and the per-user settings it overrides, see [Remote domains in Exchange Online](remote-domains.md). 
    
|**Setting**|**Default**|
|:-----|:-----|
|Out of office replies  <br/> |Send external out of office replies to people on the remote domain.  <br/> |
|Automatic replies  <br/> |Allow automatic replies or automatically forwarded messages to be sent to people on the remote domain.  <br/> |
|Delivery and non-delivery reports  <br/> |Allow delivery and non-delivery reports to be sent to people on the remote domain.  <br/> |
|Meeting forward notifications  <br/> |Don't allow meeting forward notifications to be sent to people on the remote domain.  <br/> |
|Rich Text format (RTF)  <br/> |Follow settings created by each user in Outlook or Outlook Web App when a message is sent to people on the remote domain.  <br/> |
|Supported character set  <br/> |Do not specify a MIME or non-MIME character set if the character set isn't specified in the message sent to the remote domain.  <br/> |
   
- Estimated time to complete each procedure: 5 minutes.
    
- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Mail flow" entry in the [Feature permissions in Exchange Online](../../permissions-exo/feature-permissions.md) topic. 
    
- For information about keyboard shortcuts that may apply to the procedures in this topic, see **Keyboard shortcuts in the Exchange admin center**.
    
> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612),[Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351). 
  
## What do you want to do?

> [!IMPORTANT]
> Using the Exchange admin center (EAC) to configure remote domain entries is only available in Exchange Online Dedicated. For Exchange Online, use the Exchange Management Shell instead. 
  
### Create and configure a remote domain

#### Use the EAC to create and configure a remote domain

1. In the EAC, go to **Mail flow** \> **Remote domains**.
    
2. To create a new domain:
    
1. Select **Add**![Add Icon](../../media/ITPro_EAC_AddIcon.gif).
    
2. In the **Name** box, enter a descriptive name for the domain. 
    
3. In the **Remote Domain** box, enter the full domain name. Use the wildcard character (\*) for all subdomains of a specified domain, for example, \*.contoso.com. 
    
3. To change settings for the default domain, select **Default**, and then select **Edit**.
    
4. Select the options you want:
    
  - In the **Out of Office reply types** section, specify which type of out of office replies should be sent to people at this domain. 
    
  - In the **Automatic replies** section, specify whether you want to allow automatic replies, automatic forwarding, or both. 
    
  - In the **Message reporting** section, specify: 
    
  - Whether you want to allow delivery reports and non-delivery reports.
    
  -  If a meeting set up by someone on the remote domain is forwarded to another person in your organization, whether the notification message should go to the meeting organizer on the remote domain. 
    
  -  In the **Use Rich-text format** section, specify whether to follow each user's message settings, or whether to always or never preserve RTF formatting. Selecting **Never** means that RTF messages are sent as plain text or HTML. 
    
  - In the **Supported Character Set** area, specify which character set to use if the message doesn't specify the character set. 
    
5. Click **Save**. If you created a new remote domain, it is added to the list.
    
#### Use the Exchange Management Shell to create and configure a remote domain

To create a new remote domain, use the **New-RemoteDomain** cmdlet. For a complete list of parameters, see [new-RemoteDomain](http://technet.microsoft.com/library/31442c97-1813-43d9-b9d1-da487e6b00ea.aspx). 
  
This example creates a remote domain for messages sent to the contoso.com domain.
  
```
New-RemoteDomain -Name Contoso -DomainName contoso.com
```

This example creates a remote domain for messages sent to the contoso.com domain and all its subdomains. 
  
```
New-RemoteDomain -Name 'Contoso and subdomains' -DomainName *.contoso.com
```

Use **Set-RemoteDomain** to change the settings for the default remote domain or for a remote domain you created using **New-RemoteDomain**. For a complete list of parameters, see [Set-RemoteDomain](http://technet.microsoft.com/library/4738bf25-39b8-4433-bd64-1d60252c2832.aspx).
  
- This example disables automatic replies, automatic forwarding, and out-of-office replies to recipients at all remote domains that aren't specified with their own remote domain. 
    
  ```
  Set-RemoteDomain Default -AutoReplyEnabled $false -AutoForwardEnabled $false -AllowedOOFType $None
  ```

- This example sends internal out of office replies to users at the remote domain named Contoso.
    
  ```
  Set-RemoteDomain Contoso -AllowedOOFType InternalLegacy
  ```

- This example disables prevents delivery reports and non-delivery reports from being sent to users at Contoso. 
    
  ```
  Set-RemoteDomain Contoso -DeliveryReportEnabled $false -NDREnabled $false
  ```

- This example sends all messages to Contoso using Transport Neutral Encapsulaltion Formation (TNEF) encoding, rather than MIME encoding. This preserves Rich Text format in messages. 
    
  ```
  Set-RemoteDomain Contoso -TNEFEnabled $true
  ```

    This example sends all messages to Contoso using MIME encoding, which means that all RTF messages are always converted to HTML or plain text. 
    
  ```
  Set-RemoteDomain Contoso -TNEFEnabled $false
  ```

    This example uses the message format settings the user has defined in Outlook or Outlook Web App for encoding messages.
    
  ```
  Set-RemoteDomain Contoso -TNEFEnabled $null
  ```

- This example uses the Korean (ISO) character set for MIME messages sent to Contoso. 
    
  ```
  Set-RemoteDomain Contoso -CharacterSet iso-2022-kr
  ```

    This example specifies using the Unicode character set for non-MIME messages sent to Contoso. 
    
  ```
  Set-RemoteDomain Contoso -NonMimeCharacterSet utf-8
  ```

For a complete list of remote domain settings you can change by using the Exchange Management Shell, see [Set-RemoteDomain](http://technet.microsoft.com/library/4738bf25-39b8-4433-bd64-1d60252c2832.aspx).
  
#### How do you know this worked?

To verify that you have successfully created and configured a remote domain using the Exchange Management Shell, run the command  `Get-RemoteDomain <Remote Domain Name> | Format-List`.
  
### Remove a remote domain

> [!NOTE]
> You can't remove the default remote domain. When you remove a remote domain, the default remote domain settings apply to messages sent to that domain. Removing a remote domain doesn't disable mail flow to the remote domain. 
  
#### Use the EAC to remove a remote domain

1. In the EAC, go to **Mail flow** \> **Remote domains**.
    
2. Select a remote domain, and then select **Delete**![Delete icon](../../media/ITPro_EAC_DeleteIcon.gif).
    
3. In the warning dialog box, select **Yes**.
    
The remote domain is removed from the list.
  
#### Use the Exchange Management Shell to remove a remote domain

To remove a remote domain, use the [Remove-RemoteDomain](http://technet.microsoft.com/library/7c17847a-310e-45df-8c0c-58b4297e6f8d.aspx) cmdlet. This example removes the remote domain named Contoso. 
  
```
Remove-RemoteDomain Contoso
```

#### How do you know this worked?

To verify that you have successfully removed the remote domain, run the command **Get-RemoteDomain**, and verify that the remote domain isn't listed. 
  
## What else should I know?

- Some of the settings for remote domains override settings that your users may configure in Outlook or Outlook Web App, or that you configure using the EAC or the Exchange Management Shell. For specific settings that are overridden by each remote domains setting, see [Remote domains in Exchange Online](remote-domains.md).
    
- A domain can be set up as a remote domain if it isn't listed on the **Office 365 admin center** \> **Domains** page. For example, if fabrikam.com is one of your domains, you can't create a remote domain for fabrikam.com. 
    
- Once you have created a remote domain, you can't change the domain name. Instead, create and configure a new remote domain with the new domain name.
    

