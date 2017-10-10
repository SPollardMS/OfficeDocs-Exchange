---
title: Learn more about adding an email address for a recipient
ms.prod: EXCHANGE
ms.assetid: 897c3fcd-07b6-4a6b-b8f1-95477da57b4d
---


# Learn more about adding an email address for a recipient

Use the **Email Address** page to view, add, change, or delete the email addresses associated with different types of recipients. The primary SMTP address (also known as thedefault reply address) is displayed in bold text in the address list, with the uppercase **SMTP** value in the **Type** column.
  
    
    

Use the **Add**
  
    
    
![Add icon](images/ITPro_EAC_AddIcon.png)
  
    
    
 or **Remove**
  
    
    
![Remove icon](images/ITPro_EAC_RemoveIcon.png)
  
    
    
 buttons to add or remove an email address associated with the recipient. You can add the following types of email addresses:
- **SMTP address** This is the default address type. You can add, change, or delete any SMTP address for the recipient.
    
    > [!NOTE]
      > To assign a different SMTP address as the primary SMTP address for a recipient, you must disable the option to automatically update an email address based on the email address policy applied to the recipient. Alternatively, you can use the Exchange Management Shell to change the primary SMTP address. For instructions about how to do this for a user mailbox, see  [Set-Mailbox](http://technet.microsoft.com/library/a0d413b9-d949-4df6-ba96-ac0906dedae2.aspx). 
- **EUM address** An EUM (Exchange Unified Messaging) address is used by the Microsoft Exchange Unified Messaging service to locate UM-enabled users within an Exchange organization. EUM addresses consist of the extension number and the UM dial plan for the UM-enabled user. You have to specify a dial plan when you add an EUM address.
    
  
- **Custom address type** You can add one of the following supported non-SMTP email address types for the recipient:
    
  - EX (Legacy DN Proxy Address Prefix DisplayName)
    
  
  - X.500
    
  
  - X.400
    
  
  - MSMail
    
  
  - CcMail
    
  
  - Lotus Notes
    
  
  - Novell GroupWise
    
  

    With the exception of X.400 addresses, Exchange doesn't validate custom addresses for correct formatting. You must make sure that the custom address you specify complies with the format requirements for that address type.
    
  
You can also choose to automatically update email addresses based on the email address policy applied to this recipient. If you select this option, all the email addresses associated with a recipient are automatically updated based on changes that are made to email address policies in your organization. For more information, see  [Email address policies in Exchange 2016](email-address-policies-in-exchange-2016.md).
## For more information

 [Manage User Mailboxes](http://technet.microsoft.com/library/957ca61c-1fa1-42ab-a0e6-8488e4782566.aspx)
  
    
    
 [Manage linked mailboxes](manage-linked-mailboxes.md)
  
    
    
 [Manage Distribution Groups](http://technet.microsoft.com/library/c4c43493-55e1-46d2-bd4b-d6f6cecd747f.aspx)
  
    
    
 [Manage mail-enabled security groups in Exchange 2016](manage-mail-enabled-security-groups-in-exchange-2016.md)
  
    
    
 [Manage Mail Users](http://technet.microsoft.com/library/bb8b8804-f730-4ad7-9173-896a4965b90f.aspx)
  
    
    
 [Create and manage room mailboxes](create-and-manage-room-mailboxes.md)
  
    
    
 [Manage equipment mailboxes](manage-equipment-mailboxes.md)
  
    
    
 [Email Address Policy Procedures](http://technet.microsoft.com/library/7b49b51d-265e-4857-a283-4368e858f8a5.aspx)
  
    
    

