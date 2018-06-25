---
title: "Create an Outlook Web App mailbox policy"
ms.author: dmaguire
author: msdmaguire
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 347207fa-cfb7-40a6-b19a-831dcdb54ad5
description: "You can create an Outlook Web App mailbox policy to apply a common set of policy settings. Outlook Web App mailbox policies are useful for applying and standardizing settings, for example, attachment settings, for specific groups of users."
---

# Create an Outlook Web App mailbox policy

You can create an Outlook Web App mailbox policy to apply a common set of policy settings. Outlook Web App mailbox policies are useful for applying and standardizing settings, for example, attachment settings, for specific groups of users.
  
## What do you need to know before you begin?

- Estimated time to complete each procedure: 5 minutes.
    
- You need to be assigned permissions before you can run this cmdlet. Although all parameters for this cmdlet are listed in this topic, you may not have access to some parameters if they're not included in the permissions assigned to you. To see what permissions you need, see the "Outlook Web App mailbox policies" entry in the [Client Access Permissions](http://technet.microsoft.com/library/57eca42a-5a7f-4c65-89f0-7a84f2dbea19.aspx) topic. 
    
- For information about keyboard shortcuts that may apply to the procedures in this topic, see **Keyboard shortcuts in the Exchange admin center**.
    
> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612),[Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351).. 
  
## What do you want to do?

### Use the EAC to create an Outlook Web App mailbox policy

1. In the EAC, click **Permissions** \> **Outlook Web App policies**.
    
2. Click the **New** button. 
    
3. Enter a name for your policy.
    
4. Use the check boxes to enable or disable features. By default, the most common features are displayed. To see all features that can be enabled or disabled, click **More options**.
    
    > [!NOTE]
    > Features settings for Outlook Web App mailbox policies override Outlook Web App virtual directory settings. You can change segmentation settings for individual users by using the **Set-CASMailbox** cmdlet in the Shell. 
  
5. Click **Save** to save the policy. 
    
### Use the Shell to create an Outlook Web App mailbox policy

This example creates an Outlook Web App mailbox policy named  `Policy1`.
  
- In the Shell, run the following command.
    
  ```
  New-OwaMailboxPolicy -Name Policy1
  ```

For more information about syntax and parameters, see [New-OwaMailboxPolicy](http://technet.microsoft.com/library/b2e46c22-7e99-4d04-b5ef-81ef64bf7445.aspx). For information about using the Shell to configure an Outlook Web App mailbox policy, see [Set-OwaMailboxPolicy](http://technet.microsoft.com/library/530166f7-ab42-4609-ba73-9b5a39b567be.aspx).
  
## How do you know this worked?

To verify that you've successfully created an Outlook Web App mailbox policy: 
  
- In the EAC, click **Permissions** \> **Outlook Web App Policies**, and look for your new mailbox policy. 
    

