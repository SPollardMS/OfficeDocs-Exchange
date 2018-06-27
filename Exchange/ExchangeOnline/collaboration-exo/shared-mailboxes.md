---
title: "Shared mailboxes in Exchange Online [Online]"
ms.author: kwekua
author: kwekua
manager: scotv
ms.date: 6/24/2018
ms.audience: ITPro
ms.topic: article
ms.service: exchange-online
localization_priority: Normal
ms.assetid: fdce3587-ed95-4433-9931-4cf74b52e8e0
description: "Summary: About shared mailboxes in Exchange Online, and how to create them."
---

# Shared mailboxes in Exchange Online [Online]

 **Summary**: About shared mailboxes in Exchange Online, and how to create them.
  
Shared mailboxes makes it easy for a group of people in your company to monitor and send email from a common account, such as info@contoso.com or support@contoso.com. When a person in the group replies to a message sent to the shared mailbox, the email looks like it was sent by the shared mailbox, not from the individual user.
  
> [!IMPORTANT]
>  If you're using Office 365 for business, you should create your shared mailbox in the Office 365 admin center. > [Create shared mailboxes in Office 365](https://go.microsoft.com/fwlink/p/?LinkId=834766)
  
If your organization uses a hybrid Exchange environment, you should use the on-premises Exchange admin center (EAC) to create and manage shared mailboxes. To learn more about shared mailboxes, see [Shared Mailboxes](http://technet.microsoft.com/library/1d71c01b-e261-408e-a633-1d1c9d00032a.aspx).
  
## Use the EAC to create a shared mailbox

You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "User mailboxes" entry in the [Recipients permissions](http://technet.microsoft.com/library/5b690bcb-c6df-4511-90e1-08ca91f43b37.aspx) topic. 
  
1. Go to **Recipients** \> **Shared** \> **Add**![Add Icon](../media/ITPro_EAC_AddIcon.gif).
    
2. Fill-in the required fields:
    
  - **Display name**
    
  - **Email address**
    
3. To grant Full Access or Send As permissions, click **Add**![Add Icon](../media/ITPro_EAC_AddIcon.gif), and then select the users you want to grant permissions to. You can use the CTRL key to select multiple users. Confused about which permission to use? See [Which permission should you use?](http://technet.microsoft.com/library/d34bc827-1e83-4a7f-a219-8ba9c19fe24b.aspx#TypesOfPerms) later in this topic. 
    
    > [!NOTE]
    > The Full Access permission allows a user to open the mailbox as well as create and modify items in it. The Send As permission allows anyone other than the mailbox owner to send email from this shared mailbox. Both permissions are required for successful shared mailbox operation. 
  
4. Click **Save** to save your changes and create the shared mailbox. 
    
### Use the EAC to edit shared mailbox delegation

1. Go to **Recipients** \> **Shared** \> **Edit**![Edit icon](../media/ITPro_EAC_EditIcon.gif).
    
2. Click **Mailbox delegation**
    
3. To grant or remove Full Access and Send As permissions, click **Add**![Add Icon](../media/ITPro_EAC_AddIcon.gif) or **Remove**![Remove icon](../media/ITPro_EAC_RemoveIcon.gif) and then select the users you want to grant permissions to. 
    
    > [!NOTE]
    > The Full Access permission allows a user to open the mailbox as well as create and modify items in it. The Send As permission allows anyone other than the mailbox owner to send email from this shared mailbox. Both permissions are required for successful shared mailbox operation. 
  
4. Click **Save** to save your changes. 
    
## Use a shared mailbox

To learn how users can access and use shared mailboxes, check out the following:
  
- [Open and use a shared mailbox in Outlook 2016 and Outlook 2013 ](https://go.microsoft.com/fwlink/p/?LinkId=834764)
    
- [Open and use a shared mailbox in Outlook on the web for business](https://go.microsoft.com/fwlink/p/?LinkId=834766)
    
## Use the Shell to create a shared mailbox

This example creates the shared mailbox Sales Department and grants Full Access and Send on Behalf permissions for the security group MarketingSG. Users who are members of the security group will be granted the permissions to the mailbox.
  
> [!NOTE]
> This example assumes that you've already created the security group MarketingSG and that security group is mail-enabled. See [Manage mail-enabled security groups](../recipients-in-exchange-online/manage-mail-enabled-security-groups.md). 
  
```
New-Mailbox -Shared -Name "Sales Department" -DisplayName "Sales Department" -Alias Sales | Set-Mailbox -GrantSendOnBehalfTo MarketingSG | Add-MailboxPermission -User MarketingSG -AccessRights FullAccess -InheritanceType All
```

For detailed syntax and parameter information, see [new-Mailbox](http://technet.microsoft.com/library/42dbb25a-0b23-4775-ae15-7af62c089565.aspx).
  
## Which permissions should you use?
<a name="TypesOfPerms"> </a>

You can use the following permissions with a shared mailbox.
  
- **Full Access** The Full Access permission lets a user open the shared mailbox and act as the owner of that mailbox. After accessing the shared mailbox, a user can create calendar items; read, view, delete, and change email messages; create tasks and calendar contacts. However, a user with Full Access permission can't send email from the shared mailbox unless they also have Send As or Send on Behalf permission. 
    
- **Send As** The Send As permission lets a user impersonate the shared mailbox when sending mail. For example, if Kweku logs into the shared mailbox Marketing Department and sends an email, it will look like the Marketing Department sent the email. 
    
- **Send on Behalf** The Send on Behalf permission lets a user send email on behalf of the shared mailbox. For example, if John logs into the shared mailbox Reception Building 32 and sends an email, it look like the mail was sent by "John on behalf of Reception Building 32". You can't use the EAC to grant Send on Behalf permissions, you must use **Set-Mailbox** cmdlet with the  _GrantSendonBehalf_ parameter. 
    
## More information
<a name="TypesOfPerms"> </a>

For information about keyboard shortcuts that may apply to the procedures in this topic, see **Keyboard shortcuts in the Exchange admin center**.
  
> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612),[Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351). 
  

