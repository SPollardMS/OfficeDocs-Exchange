---
title: "Use a screen reader to create a new distribution group in the Exchange admin center"
ms.author: v-maleo
author: v-maleo
ms.date: 12/9/2016
ms.audience: ITPro
ms.topic: article
ms.service: exchange-online
localization_priority: Normal
ms.custom: A11y_UseSR
ms.assetid: 4de33fbd-00e8-4071-8d2c-2c1a696a8454
description: "Using a screen reader and keyboard shortcuts, you can create a new distribution group in the Exchange admin center (EAC) in Exchange Online. This topic explains how to create a new distribution group in your Exchange organization and how to mail-enable an existing group in Active Directory."
---

# Use a screen reader to create a new distribution group in the Exchange admin center

Using a screen reader and keyboard shortcuts, you can create a new distribution group in the Exchange admin center (EAC) in Exchange Online. This topic explains how to create a new distribution group in your Exchange organization and how to mail-enable an existing group in Active Directory.
  
## In this topic

- [Get started](use-screen-reader-to-create-distribution-group-in-exchange-admin-center.md#BKMK_GetStarted)
    
- [Use the EAC to create a distribution group](use-screen-reader-to-create-distribution-group-in-exchange-admin-center.md#BKMK_CreateDG)
    
- [Technical support for customers with disabilities ](use-screen-reader-to-create-distribution-group-in-exchange-admin-center.md#BKMK_DAD)
    
## Get started
<a name="BKMK_GetStarted"> </a>

Navigate with Internet Explorer and keyboard shortcuts, and make sure that you have the appropriate Office 365 subscription and admin role to work in the EAC. Then, open the EAC and get started.
  
> [!NOTE]
>  Two types of groups can be used to distribute messages. Mail-enabled universal distribution groups (also called  *distribution groups*  ) can be used only to distribute messages. Mail-enabled universal security groups (also called  *security groups*  ) can be used to distribute messages as well as to grant access permissions to resources in Active Directory. For more information, refer to the [Manage mail-enabled security groups](https://go.microsoft.com/fwlink/p/?LinkID=627033) article on TechNet. >  Active Directory and Exchange use the term  *distribution group*  differently. In Active Directory, a  *distribution group*  refers to any group that doesn't have a security context, regardless of whether it's mail-enabled. By contrast, in Exchange, all mail-enabled groups are referred to as  *distribution groups*  , regardless of whether they have a security context. >  This topic assumes you are using the EAC. For information about using the Shell to create distribution groups, refer to the [New-DistributionGroup](https://go.microsoft.com/fwlink/?LinkId=798650) article on TechNet. >  If your organization has configured a group naming policy, it's applied only to groups created by users. When you or other administrators use the EAC to create distribution groups, the group naming policy is ignored and isn't applied to the group name. For more information, refer to the [Create a distribution group naming policy](https://go.microsoft.com/fwlink/?LinkId=798657) and [Override the distribution group naming policy](https://go.microsoft.com/fwlink/?LinkId=798661) articles on TechNet. 
  
### Use your browser and keyboard to navigate in the EAC

Exchange Online, which includes the EAC, is a web-based application, so the keyboard shortcuts and navigation may be different from those in Exchange 2016. [Accessibility in the Exchange admin center](accessibility-in-exchange-admin-center.md).
  
For best results when working in the EAC in Exchange Online, use Internet Explorer as your browser. [Learn more about Internet Explorer keyboard shortcuts](https://go.microsoft.com/fwlink/?LinkID=787614).
  
Many tasks in the EAC require the use of pop-up windows so, in your browser, be sure to [enable pop-up windows for Office 365](https://go.microsoft.com/fwlink/?LinkID=317550).
  
### Confirm your Office 365 subscription plan

Exchange Online is included in Office 365 business and enterprise subscription plans. But capabilities may differ by plan. If your EAC doesn't include a function described in this article, your plan might not include it. 
  
For more information about the Exchange Online capabilities in your subscription plan, go to [What Office 365 business product or license do I have?](https://go.microsoft.com/fwlink/?LinkID=797552
) and [Exchange Online Service Description.](https://go.microsoft.com/fwlink/?LinkID=797553
).
  
### Open the EAC, and confirm your admin role

To complete the tasks covered in this topic, [Use a screen reader to open the Exchange admin center](use-screen-reader-to-open-exchange-admin-center.md) and check that your Office 365 global administrator has assigned you to the [Organization Management](https://go.microsoft.com/fwlink/?LinkId=797868) and [Records Management](https://go.microsoft.com/fwlink/?LinkId=798797) admin role groups. [Use a screen reader to identify your admin role in the Exchange admin center](use-screen-reader-to-identify-admin-role-in-exchange-admin-center.md).
  
## Use the EAC to create a distribution group
<a name="BKMK_CreateDG"> </a>

1. In the EAC, in the primary navigation pane, tab to **Recipients**. You hear "Recipients, Primary navigation." Press Enter. 
    
2. To move the focus to the menu bar, press Ctrl+F6. You hear, "Mailboxes, Secondary navigation link." 
    
3. Press the Left Arrow key until you hear "Groups, Secondary navigation link." 
    
4. Press Enter. You hear "Groups options." A list of distribution groups appears.
    
5. To move the focus to the **distribution group** menu, press Ctrl+F6. You hear " **New**," which is the first button. 
    
6. To open the **New** submenu, press Spacebar. 
    
7. In the **New** menu, press the Down Arrow key until you hear "Distribution group." Then, press Enter. (In Narrator, you may hear "Empty line" or nothing at all. The three items on this menu are **distribution group**, **security group**, and **dynamic distribution group**. Select the first item in the menu.) The **new distribution group** page opens in a new browser window. 
    
    > [!TIP]
    >  The **new distribution group** window includes two buttons named **Add** and two named **Remove**. The first set of **Add** and **Remove** buttons affects the **Select Owners** box. The second set applies to the **Select Members** box. 
  
8. Tab to the following options, and complete the group details: 
    
    > [!TIP]
    > Required boxes are designated with an asterisk. In screen readers, you hear "Star" or "Asterisk" before the label. For example, for the required **Display name** box, you hear "Star display name" or "Asterisk display name." You also hear the text of a tool tip that appears when you move the focus to an option. 
  
  - **\*Display name**. Type the name you want to appear in your organization's address book. This name appears on the **To**: line when email is sent to this group and in the **Groups** list in the EAC. The display name is required. Make it recognizable for users and unique in the forest. 
    
  - **\*Alias**. Type a name of 64 characters or less for the group's alias. Make it unique in the forest. When a user types the alias in the **To**: line of an email message, it resolves to the group's display name. 
    
  - **\*Email address**. If you want to change the default name used for this group's email address, type the name you want. The default is the alias you specified. 
    
  - **Notes**. If you want to add a description for this distribution group, type a note. The text you type appears on the group's contact card and in the address book. 
    
  - **Add**. To open the **Select Owners** window, where you can add owners to the distribution group, select **Add**. By default, the person who creates a group is the owner and is listed in the **Owners** box. All groups must have at least one owner. For help using the **Select Owners** window, refer to Use a screen reader in the Select Owners window later in this topic. 
    
  - **Remove**. To remove a selected name from the **Owners** box, use this option. 
    
  - **\*Owners**. This option lists the names of the distribution group's owners. Screen readers read the selected name, not the label. For example, you hear "Sara Davis, Button." 
    
  - **Add group owners as member**. By default, this check box is selected. 
    
  - **Add**. To add members to the distribution group, select this option. By default, the group owners are members and are listed in the **Members** box. When you select the **Add** button, the **Select Members** window opens and you can search for or select the names you want. To return to the **new distribution group** window, select the **OK** button. For detailed steps, refer to Use a screen reader to add a member to a distribution group. 
    
  - **Remove**. Use to remove the selected name from the **Members** box. 
    
  - **Members**. This option lists the names of the distribution group's members. In Narrator, you may hear "Please wait" or nothing, when this list is empty. 
    
  - **Choose whether owner approval is required to join the group**. Screen readers read the selected option. The default is **Open**. To require approval for people to join the group, use an arrow key to select one of the other two options: **Closed** or **Owner Approval**. 
    
  - **Choose whether the group is open to leave. Screen readers read the selected option**. The default is **Open**. To require approval for people to leave the group, use an arrow key to select **Closed**. 
    
9. When you've finished, tab to the **Save** button and press Enter. 
    
> [!NOTE]
> By default, new distribution groups require that all senders be authenticated. This prevents external senders from sending messages to distribution groups. To configure a distribution group to accept messages from all senders, you must modify the message delivery restriction settings for that distribution group. 
  
### Verify that you've successfully created a distribution group

1. In the EAC, tab to **Recipients** and press Enter. 
    
2. To move the focus to the menu bar, press Ctrl+F6. You hear, "Mailboxes, Secondary navigation."
    
3. Press the Left Arrow key until you hear "Groups, Secondary navigation," and then press Enter. The table of current distribution groups appear.
    
4. Press Ctrl+F6 until you hear the name of a distribution group, indicating that the focus is on the table of distribution groups.
    
5. To locate the distribution group you just created, use the Up Arrow and Down Arrow keys. The screen reader reads the display name, group type, and e-mail address.
    
### Use a screen reader in the Select Owners window

In the **new distribution group** window, the **Add** button for the \* **Owners** box opens the **Select Owners** window, which some screen readers have difficulty reading. To add an owner: 
  
1. In the **new distribution group** window, tab to the **Add** button and press Enter. The **Select Owner** window opens, and the focus is on a search box. 
    
2. Type all or part of the name of the user you want to add, and then press Enter. A list of names appears in the **Display Name** table. If there are no names, press Shift+Tab until you hear "Filter or search edit" or the text of your previous search and then type new search text. 
    
3. To select a name, tab until you hear a name, indicating that the focus is on the names in the **Display Name** table. (In JAWS, you hear "Out of table" and the name of the first user listed.) 
    
4. To select the name you want, use the arrow keys.
    
5. Tab until you hear "Add button" and then press Spacebar. The name is added to a text box. Each name you add includes a **Remove** link. 
    
6. To add more names, tab to the **Search** button and repeat the previous steps. 
    
7. When complete, tab to the **OK** button and press Enter. The **Select Owner** window closes, and the focus is in the **Owners** box in the **new distribution group** window. 
    
## Technical support for customers with disabilities
<a name="BKMK_DAD"> </a>

Microsoft wants to provide the best possible experience for all our customers. If you have a disability or have questions related to accessibility, please contact the [Microsoft Disability Answer Desk](https://go.microsoft.com/fwlink/p/?LinkID=518252) for technical assistance. 
  
The Disability Answer Desk support team is trained in using many popular assistive technologies and can offer assistance in English, Spanish, French, and American Sign Language. Please visit the [Microsoft Disability Answer Desk](https://go.microsoft.com/fwlink/p/?LinkID=518252) site to find the contact details for your region. 
  

