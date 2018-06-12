---
title: "Manage permissions for recipients"
ms.author: serdars
author: SerdarSoysal
manager: scotv
ms.date: 6/8/2018
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 749cdfe3-496b-453f-96eb-20a0bf28fd52
description: "Summary: Learn how to assign permissions for mailboxes and groups in Exchange 2016 so other users can open the mailbox, send mail from the mailbox, or send mail from the group."
---

# Manage permissions for recipients

 **Summary**: Learn how to assign permissions for mailboxes and groups in Exchange 2016 so other users can open the mailbox, send mail from the mailbox, or send mail from the group.
  
In Exchange Server 2016, you can use the Exchange admin center (EAC) or the Exchange Management Shell to assign permissions to a mailbox or group so that other users can access the mailbox (the Full Access permission), or send email messages that appear to come from the mailbox or group (the Send As or Send on Behalf permissions). The users that are assigned these permissions on other mailboxes or groups are called  *delegates*  . 
  
The permissions that you can assign to delegates for mailboxes and groups in Exchange 2016 are described in the following table:
  
 **Note**: Although you can use the Exchange Management Shell to assign some or all of these permissions to other delegate types on other kinds of recipient objects, this topic focuses on the delegate and recipient object types that produce useful results.
  
|**Permission**|**Description**|**Available on objects in the EAC**|**Available on addtional objects in the Exchange Management Shell**|**Available delegate types in the EAC**|**Additional delegate types available in the Exchange Management Shell**|
|:-----|:-----|:-----|:-----|:-----|:-----|
|**Full Access** <br/> | Allows the delegate to open the mailbox, and view, add and remove the contents of the mailbox. Doesn't allow the delegate to send messages from the mailbox.  <br/>  If you assign this permission to a mailbox that's hidden from address lists, the delegate won't be able to open the mailbox. By default, arbitration and discovery mailboxes are hidden from address lists.  <br/>  By default, the mailbox auto-mapping feature uses Autodiscover to automatically open the mailbox in the delegate's Outlook profile (in addition to their own mailbox). If you don't want this to happen, you need to take one of the following actions:  <br/>  Use the Add-MailboxPermission cmdlet in the Exchange Management Shell to assign the Full Access permission with the  `-AutoMapping $false` setting. For more information, see the [Use the Exchange Management Shell to assign the Full Access permission to mailboxes](mailbox-permissions.md#PowerShellFullAccess) section in this topic.  <br/>  Assign the Full Access permission to a (mail-enabled) security group. The mailbox won't open in the Outlook profile of each member.  <br/> |User mailboxes  <br/> Linked mailboxes  <br/> Resource mailboxes  <br/> Shared mailboxes  <br/> |Arbitration mailboxes  <br/> Discovery mailboxes  <br/> |Mailboxes with user accounts  <br/> Mail users with accounts  <br/> Mail-enabled security groups.  <br/> |User accounts that aren't mail-enabled.  <br/> Universal, global, and domain local security groups that aren't mail-enabled.  <br/> |
|**Send As** <br/> |Allows the delegate to send messages as if they came directly from the mailbox or group. There's no indication that the message was sent by the delegate.  <br/> Doesn't allow the delegate to read the contents of the mailbox.  <br/> |User mailboxes  <br/> Linked mailboxes  <br/> Resource mailboxes  <br/> Shared mailboxes  <br/> Distribution groups  <br/> Dynamic distribution groups  <br/> Mail-enabled security groups  <br/> |n/a  <br/> |Mailboxes with user accounts  <br/> Mail users with accounts  <br/> Mail-enabled security groups.  <br/> |n/a  <br/> |
|**Send on Behalf** <br/> |Allows the delegate to send messages from the mailbox or group. The From address of these messages clearly shows that the message was sent by the delegate (" _\<Delegate\>_ on behalf of  _\<MailboxOrGroup\>_"). However, replies to these messages are sent to the mailbox or group, not to the delegate.  <br/> Doesn't allow the delegate to read the contents of the mailbox.  <br/> |User mailboxes  <br/> Linked mailboxes  <br/> Resource mailboxes  <br/> Distribution groups  <br/> Dynamic distribution groups  <br/> Mail-enabled security groups  <br/> |Shared mailboxes  <br/> |Mailboxes with user accounts  <br/> Mail users with accounts  <br/> Mail-enabled security groups.  <br/> Distribution groups  <br/> |n/a  <br/> |
   
## What do you need to know before you begin?

- Estimated time to complete each procedure: 2 minutes.
    
- To learn how to open the Exchange Management Shell in your on-premises Exchange organization, see **Open the Exchange Management Shell**.
    
- Procedures in this topic require specific permissions. See each procedure for its permissions information.
    
- For information about keyboard shortcuts that may apply to the procedures in this topic, see [Keyboard shortcuts in the Exchange admin center](../about-documentation/eac-keyboard-shortcuts.md).
    
> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at: [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351).. 
  
## Use the EAC to assign permissions to individual mailboxes

1. In the EAC, click **Recipients** in the feature pane. Depending on the type of mailbox that you want to assign permissions for, click on one of the following tabs: 
    
  - **Mailboxes**: User or linked mailboxes.
    
  - **Resources**: Room or equipment mailboxes.
    
  - **Shared**: Shared mailboxes.
    
2. In the list of mailboxes, select the mailbox that you want to assign permissions for, and then click **Edit**![Edit icon](../media/ITPro_EAC_EditIcon.png).
    
3. On the mailbox properties page that opens, click **Mailbox delegation** and configure one or more of the following permissions: 
    
  - **Send As**: Messages sent by a delegate appear to come from the mailbox.
    
  - **Send on Behalf**: Messages sent by a delegate have " _\<Delegate\>_ on behalf of  _\<Mailbox\>_" in the From address. Note that this permission isn't available in the EAC for shared mailboxes.
    
  - **Full Access**: The delegate can open the mailbox and do anything except send messages.
    
    To assign permissions to delegates, click **Add**![Add icon](../media/ITPro_EAC_AddIcon.png) under the appropriate permission. A dialog box appears that lists the users or groups that can have the permission assigned to them. Select the user or group from the list, and then click **Add**. Repeat this process as many times as necessary. You can also search for users or groups in the search box by typing all or part of the name, and then clicking **Search**![Search icon](../media/ITPro_EAC_.png). When you are finished selecting delegates, click **OK**.
    
    To remove a permission from a delegate, select the delegate in the list under the appropriate permission, and then click **Remove**![Remove icon](../media/ITPro_EAC_RemoveIcon.png).
    
4. When you are finished, click **Save**.
    
## Use the EAC to assign permissions to multiple mailboxes at the same time

1. In the EAC, navigate to **Recipients** \> **Mailboxes**.
    
2. Select the mailboxes that you want to assign permissions for. Use click + Shift key + click to select a range of mailboxes, or Ctrl key + click to select multiple individual mailboxes. The title of the details pane changes to **Bulk Edit** as shown in the following diagram. 
    ![Bulk select mailboxes in the EAC](../media/ee6acd85-a6b8-44f4-8eb1-a6e84e4dfff1.png)
  
    Note that the mailboxes that you select need to be the same type. For example, if you select both user mailboxes and linked mailboxes, you'll get a warning in the details pane that says bulk edit won't work.
    
3. At the bottom of the details pane, click **More options**. Under the **Mailbox Delegation** option that appears, choose **Add** or **Remove**. Depending on your selection, do one of the following steps:
    
  - **Add**: In the **Bulk Add Delegation** dialog box that appears, click **Add**![Add icon](../media/ITPro_EAC_AddIcon.png) under the appropriate permission ( **Send As**, **Send on Behalf**, or **Full Access**). When you are finished selecting users or groups to add as delegates, click **Save**.
    
  - **Remove**: In the **Bulk Remove Delegation** dialog box that appears, click **Add**![Add icon](../media/ITPro_EAC_AddIcon.png) under the appropriate permission ( **Send As**, **Send on Behalf**, or **Full Access**). When you are finished selecting users or groups to remove from the existing delegates, click **Save**.
    
## Use the EAC to assign permissions to groups

1. In the EAC, navigate to **Recipients** \> **Groups**.
    
2. In the list of groups, select the group that you want to assign permissions for, and then click **Edit**![Edit icon](../media/ITPro_EAC_EditIcon.png).
    
3. On the group properties page that opens, click **Group delegation** and configure one of the following permissions: 
    
  - **Send As**: Messages sent by a delegate appear to come from the group.
    
  - **Send on Behalf**: Messages sent by a delegate have " _\<Delegate\>_ on behalf of  _\<Group\>_" in the From address.
    
4. To assign permissions to delegates, click **Add**![Add icon](../media/ITPro_EAC_AddIcon.png) under the appropriate permission. A dialog box appears that lists the users or groups that can have the permission assigned to them. Select the user or group from the list, and then click **Add**. Repeat this process as many times as necessary. You can also search for users or groups in the search box by typing all or part of the name, and then clicking **Search**![Search icon](../media/ITPro_EAC_.png). When you are finished selecting delegates, click **OK**.
    
    To remove a permission from a delegate, select the delegate in the list under the appropriate permission, and then click **Remove**![Remove icon](../media/ITPro_EAC_RemoveIcon.png).
    
5. When you are finished, click **Save**.
    
## Use the Exchange Management Shell to assign the Full Access permission to mailboxes
<a name="PowerShellFullAccess"> </a>

You use the **Add-MailboxPermission** and **Remove-MailboxPermission** cmdlets to manage the Full Access permission for mailboxes. These cmdlets use the same basic syntax: 
  
```
Add-MailboxPermission -Identity <MailboxIdentity> -User <DelegateIdentity> -AccessRights FullAccess -InheritanceType All [-AutoMapping $false]
```

For more information, see [Add-MailboxPermission](http://technet.microsoft.com/library/a9aacbf5-5e6c-47ef-95d6-e24547e95d01.aspx).
  
```
Remove-MailboxPermission -Identity <MailboxIdentity> -User <DelegateIdentity> -AccessRights FullAccess -InheritanceType All 
```

For more information, see [Remove-MailboxPermission](http://technet.microsoft.com/library/eda30705-6070-413a-88c5-db262fbad8d3.aspx).
  
This example assigns the delegate Raymond Sam the Full Access permission to the mailbox of Terry Adams.
  
```
Add-MailboxPermission -Identity "Terry Adams" -User raymonds -AccessRights FullAccess -InheritanceType All
```

This example assigns Esther Valle the Full Access permission to the organization's default discovery search mailbox, and prevents the mailbox from automatically opening in Esther Valle's Outlook.
  
```
Add-MailboxPermission -Identity "DiscoverySearchMailbox{D919BA05-46A6-415f-80AD-7E09334BB852}" -User estherv -AccessRights FullAccess -InheritanceType All -AutoMapping $false
```

This example assigns members of the Helpdesk mail-enabled security group the Full Access permission to the shared mailbox named Helpdesk Tickets.
  
```
Add-MailboxPermission -Identity "Helpdesk Tickets" -User Helpdesk -AccessRights FullAccess -InheritanceType All
```

This example removes Full Access permission for Jim Hance from Ayla Kol's mailbox.
  
```
Remove-MailboxPermission -Identity ayla -User "Jim Hance" -AccessRights FullAccess -InheritanceType All
```

Note: If you've already assigned the Full Access permission to a delegate in the EAC or without using the -AutoMapping $false setting on
  
### How do you know this worked?

To verify that you've assigned or removed the Full Access permission for a delegate on a mailbox, use either of the following procedures:
  
- In the properties of the mailbox in the EAC, verify the delegate is or isn't listed in **Mailbox delegation** \> **Full Access**.
    
- Run the following command in the Exchange Management Shell to verify the delegate is or isn't listed. Be sure to replace  _\<MailboxIdentity\>_ with the identity of the mailbox. 
    
  ```
  Get-MailboxPermission <MailboxIdentity> | where {$_.AccessRights -like 'Full*'} | Format-Table -Auto User,Deny,IsInherited,AccessRights
  ```

    For more information, see [Get-MailboxPermission](http://technet.microsoft.com/library/56bcc678-1598-4c9b-8b4f-4fa11c89ec41.aspx).
    
### Use the Exchange Management Shell to assign the Send As permission to mailboxes and groups

You use the **Add-AdPermission** and **Remove-AdPermission** cmdlets to manage Send As permission for mailboxes. These cmdlets use the same basic syntax: 
  
```
<Add-AdPermission | Remove-AdPermission> -Identity <MailboxOrGroupNameOrDN> -User <DelegateIdentity> [-AccessRights ExtendedRight] -ExtendedRights "Send As"
```

For more information, see [Add-AdPermission](http://technet.microsoft.com/library/bef9f3db-84f6-4a40-81cb-c9cb9b9ee201.aspx) and [Remove-AdPermission](http://technet.microsoft.com/library/0e45951a-2b5a-4aa9-a709-def61d7d4972.aspx).
  
 **Notes**:
  
- The  _Identity_ parameter requires you to use the **Name** or **DistinguishedName** (DN) value of the mailbox or group. 
    
  - **Name**: This value may or may not be the same as the display name. For example,  `Felipe Apodaca`.
    
  - **DistinguishedName**: This value always contains the **Name** value and uses Active Directory LDAP syntax. For example,  `CN=Felipe Apodaca,CN=Users,DC=contoso,DC=com`.
    
    To find these values for a mailbox or group, you can use the **Get-Recipient** cmdlet, which accepts many different values for the  _Identity_ parameter. For example: 
    
  ```
  Get-Recipient -Identity helpdesk@contoso.com | Format-List Name,DistinguishedName
  ```

- The commands work with or without  `-AccessRights ExtendedRight`, which is why it's shown as optional in the syntax.
    
This example assigns the Send As permission to the Helpdesk mail-enabled security group on the shared mailbox named Helpdesk Support Team.
  
```
Add-ADPermission -Identity "Helpdesk Support Team" -User Helpdesk -ExtendedRights "Send As"
```

This example removes the Send As permission for the user Pilar Pinilla on the mailbox of James Alvord.
  
```
Remove-ADPermission -Identity "James Alvord" -User pilarp -ExtendedRights "Send As"
```

#### How do you know this worked?

To verify that you've assigned or removed the Send As permission for a delegate on a mailbox or group, use either of the following procedures:
  
- In the properties of the mailbox or group in the EAC, verify the delegate is or isn't listed in **Mailbox delegation** \> **Send As** or **Group delegation** \> **Send As**.
    
- Run the following command in the Exchange Management Shell to verify the delegate is or isn't listed. Be sure to replace  _\<MailboxOrGroupNameOrDN\>_ with the name or distinguished name of the mailbox or group. 
    
  ```
  Get-ADPermission -Identity <MailboxOrGroupNameOrDN> | where {$_.ExtendedRights -like 'Send*'} | Format-Table -Auto User,Deny,ExtendedRights
  ```

    For more information, see [Get-AdPermission](http://technet.microsoft.com/library/f20251dc-ab54-4dd5-b80c-de0808fd4dc2.aspx).
    
### Use the Exchange Management Shell to assign the Send on Behalf permission to mailboxes and groups

You use the **Set-** cmdlets for the various mailbox and group cmdlets to manage Send on Behalf permission for mailboxes and groups: 
  
- **Set-Mailbox**
    
- **Set-DistributionGroup**: Distribution groups and mail-enabled security groups. 
    
- **Set-DynamicDistributionGroup**
    
The basic syntax for these cmdlets is:
  
```
<Cmdlet> -Identity <MailboxOrGroupIdentity> -GrantSendOnBehalfTo <DelegateIdentity>
```

 _\<DelegateIdentity\>_ can be one of the following values: 
  
- To replace any existing delegates with the values you specify, use the syntax  `<DelegateIdentity1>,<DelegateIdentity2>...`. If the delegate identity value contains spaces, you need to use quotation marks:  `"<DelegateIdentity1>","<DelegateIdentity2>"...`.
    
- To add new delegates without affecting other existing entries, use the syntax  `@{Add="<DelegateIdentity1>","<DelegateIdentity2>"...}`.
    
- To remove existing delegates without affecting other delegates, use the syntax  `@{Remove="<DelegateIdentity1>","<DelegateIdentity2>"...}`.
    
- To erase all existing delegates, use the value  `$null`.
    
This example assigns the delegate Holly Holt the Send on Behalf permission to the mailbox of Sean Chai.
  
```
Set-Mailbox -Identity seanc@contoso.com -GrantSendOnBehalfTo hollyh
```

This example adds the group named Temporary Executives to the list of delegates that have Send on Behalf permission to the Contoso Executives shared mailbox.
  
```
Set-Mailbox "Contoso Executives" -GrantSendOnBehalfTo @{Add="tempassistants@contoso.com"}
```

This example assigns the delegate Sara Davis the Send on Behalf permission to the Printer Support distribution group.
  
```
Set-DistributionGroup -Identity printersupport@contoso.com -GrantSendOnBehalfTo sarad
```

This example removes the Send on Behalf permission that was assigned to the administrator on the All Employees dynamic distribution group.
  
```
Set-DynamicDistributionGroup "All Employees" -GrantSendOnBehalfTo @{Remove="Administrator"}
```

#### How do you know this worked?

To verify that you've assigned or removed the Send on Behalf permission for a delegate on a mailbox or group, use either of the following procedures:
  
- In the properties of the mailbox or group in the EAC, verify the delegate is or isn't listed in **Mailbox delegation** \> **Send As** or **Group delegation** \> **Send As**.
    
- Run the one of the following commands in the Exchange Management Shell to verify the delegate is or isn't listed. Be sure to replace  _\<MailboxIdentity\>_ or  _\<GroupIdentity\>_ with the identity of the mailbox or group. 
    
  - Mailbox:
    
  ```
  Get-Mailbox -Identity <MailboxIdentity> | Format-List GrantSendOnBehalfTo
  ```

  - Group:
    
  ```
  Get-DistributionGroup -Identity <GroupIdentity> | Format-List GrantSendOnBehalfTo
  ```

  - Dynamic distribution group:
    
  ```
  Get-DynamicDistributionGroup -Identity <GroupIdentity> | Format-List GrantSendOnBehalfTo
  ```

### Next steps

For more information about how delegates can use the permissions that are assigned to them on mailboxes and groups, see the following topics:
  
- [Access another person's mailbox](https://go.microsoft.com/fwlink/p/?LinkId=823179)
    
- [Open and use a shared mailbox in Outlook 2016 and Outlook 2013](https://go.microsoft.com/fwlink/p/?LinkId=816868)
    
- [Open and use a shared mailbox in Outlook on the Web](https://go.microsoft.com/fwlink/p/?LinkId=816870)
    
- [Send email from another person or group in Outlook on the Web](https://go.microsoft.com/fwlink/p/?LinkId=823180)
    

