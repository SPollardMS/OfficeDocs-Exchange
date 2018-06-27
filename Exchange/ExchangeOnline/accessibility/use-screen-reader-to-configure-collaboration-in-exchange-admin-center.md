---
title: "Use a screen reader to configure collaboration in the Exchange admin center"
ms.author: v-maleo
Maggsl
ms.date: 12/9/2016
ms.audience: ITPro
ms.topic: article
ms.service: exchange-online
localization_priority: Normal
ms.custom: A11y_UseSR
ms.assetid: 2cb9cae4-3eee-4da1-8a01-3d37d4b6b8b2
description: "You can use your screen reader in the Exchange admin center (EAC) in Exchange Online to configure different methods of collaboration. These methods might include public folders, distribution groups, shared mailboxes, or—in conjunction with SharePoint—site mailboxes."
---

# Use a screen reader to configure collaboration in the Exchange admin center

You can use your screen reader in the Exchange admin center (EAC) in Exchange Online to configure different methods of collaboration. These methods might include public folders, distribution groups, shared mailboxes, or—in conjunction with SharePoint—site mailboxes. 
  
## In this topic

- [Get started](use-screen-reader-to-configure-collaboration-in-exchange-admin-center.md#BKMK_GetStarted)
    
- [Set up public folders](use-screen-reader-to-configure-collaboration-in-exchange-admin-center.md#BKMK_PublicFolders)
    
- [Create a distribution group](use-screen-reader-to-configure-collaboration-in-exchange-admin-center.md#BKMK_CreateDistGrp)
    
- [Work with a shared mailbox](use-screen-reader-to-configure-collaboration-in-exchange-admin-center.md#BKMK_WorkSharedMailbox)
    
- [Establish a site mailbox through SharePoint](use-screen-reader-to-configure-collaboration-in-exchange-admin-center.md#BKMK_EstablishSiteMailbox)
    
- [Accessibility Information](use-screen-reader-to-configure-collaboration-in-exchange-admin-center.md#BKMK_AcessInfo)
    
## Get started
<a name="BKMK_GetStarted"> </a>

Navigate with Internet Explorer and keyboard shortcuts, and make sure that you have the appropriate Office 365 subscription and admin role to work in the EAC. Then, open the EAC and get started.
  
### Use your browser and keyboard to navigate in the EAC

Exchange Online, which includes the EAC, is a web-based application, so the keyboard shortcuts and navigation may be different from those in Exchange 2016. [Accessibility in the Exchange admin center](accessibility-in-exchange-admin-center.md).
  
For best results when working in the EAC in Exchange Online, use Internet Explorer as your browser. [Learn more about Internet Explorer keyboard shortcuts](https://go.microsoft.com/fwlink/?LinkID=787614).
  
Many tasks in the EAC require the use of pop-up windows so, in your browser, be sure to [enable pop-up windows for Office 365](https://go.microsoft.com/fwlink/?LinkID=317550).
  
### Confirm your Office 365 subscription plan

Exchange Online is included in Office 365 business and enterprise subscription plans, but capabilities may differ by plan. If your EAC doesn't include a function described in this article, your plan might not include it.
  
For more information about the Exchange Online capabilities in your subscription plan, go to [What Office 36 business product or license do I have?](https://go.microsoft.com/fwlink/?LinkID=797552) and [Exchange Online Service Description](https://go.microsoft.com/fwlink/?LinkID=797553).
  
### Open the EAC, and confirm your admin role

To complete the tasks covered in this topic, [Use a screen reader to open the Exchange admin center](use-screen-reader-to-open-exchange-admin-center.md) and check that your Office 365 global administrator has assigned you to the [Organization Management](https://go.microsoft.com/fwlink/?LinkId=797868) and [Records Management](https://go.microsoft.com/fwlink/?LinkId=798797) admin role groups. [Use a screen reader to identify your admin role in the Exchange admin center](use-screen-reader-to-identify-admin-role-in-exchange-admin-center.md).
  
## Set up public folders
<a name="BKMK_PublicFolders"> </a>

Members of workgroups can use public folders as an easy way to collect, organize, and share information with others in the workgroup. 
  
Public folders organize content in a hierarchy that's easy to browse. Users can discover useful content by browsing through branches of the hierarchy that are relevant to their work. The full hierarchy is visible to users in their Outlook folder view. Public folders can be used for distribution group archiving. A public folder can be mail-enabled and added as a member of the distribution group, so that email sent to the distribution group is then automatically added to the public folder. Public folders also allow for simple document sharing.
  
### Create a public folder mailbox

To use public folders, you need to set up at least one public folder mailbox. 
  
1. In the EAC, press Ctrl+F6 until the primary navigation pane has the focus and you hear "Dashboard, Primary navigation link."
    
2. Tab to public folders and press Enter.
    
3. To move to the menu bar, press Ctrl+F6. You hear "Public folders, Secondary navigation link." 
    
4. Tab to **public folder mailboxes**. Press Enter. 
    
5. To move to the toolbar, press Ctrl+F6. You hear "New public folder mailbox button." Press Enter.
    
6. In the **Public Folder Mailbox** dialog box which opens, the **Name** text box has the focus. Type the name for your public folder mailbox. 
    
    Tip Public folder mailboxes contain the hierarchy information plus the content for public folders. The first public folder mailbox you create becomes the primary mailbox, which contains the one writable copy of the public folder hierarchy. Any additional public folder mailboxes you create will be secondary mailboxes, which contain a read-only copy of the hierarchy.
    
7. Tab to the **Save** button and press Enter. It might take up to a minute for the public folder mailbox to be created, after which you hear an alert that says the mailbox will be available in approximately 15 minutes. 
    
8. With the focus on the **OK** button, press Enter. The new public folder mailbox is added to the public folder mailboxes list view. 
    
[Learn more about creating public folders](https://go.microsoft.com/fwlink/?LinkId=799146).
  
### Create a public folder

After you create a public folder mailbox, you can add a public folder.
  
1. With the focus in the public folder mailboxes list view, to move to the menu bar, press Ctrl+Shift+F6 twice. You hear "Public folders, Secondary navigation link." Press Enter. 
    
2. To move to the toolbar, press Ctrl+F6. You hear "New public folder button." Press Enter. This creates a public folder at the root level in the public folder's hierarchy.
    
    > [!TIP]
    > You can create a subfolder within an existing public folder. First, with the focus in the public folders list view, to select the parent folder, press the Down Arrow key or the Up Arrow key, and then press the Tab key. To open the folder, press Enter. Then, to move to the toolbar, press Ctrl+Shift+F6. Select the **New public folder** button, which has the focus, press Enter, and then go on to Step 3. (If you want to move back to the parent folder, on the toolbar, tab to the **Go to the parent folder** button and press Enter.) 
  
3. In the **Public Folder** dialog box which opens, the **Name** text box has the focus. Type the name for your public folder. 
    
4. To move to the **Path** text box, press the Tab key. In this read-only text box, you hear the path for the public folder. For example, if you're creating a public folder at the root level, you hear "Backslash." 
    
5. Tab to the **Save** button and press Enter. The name of the new public folder is added to the public folders list view. 
    
### Add users of a public folder

After you create a public folder, specify the users who can access it. Also specify these users' roles in the public folder, including their read-write permissions.
  
1. With the focus in the public folders list view, to select the public folder you want to add users to, press the Up Arrow key or the Down Arrow key.
    
2. To move to the details pane, press Ctrl+F6. The mail settings **Enable** link has the focus. 
    
3. To move to the folder permissions **Manage** link, press the Tab key and then press Enter. 
    
4. In the **Public Folder Permissions** dialog box which opens, the **Add** button has the focus. Press Enter. 
    
5. In the dialog box which opens, the **Browse** button has the focus. Press Enter. 
    
6. In the **Select Recipient** dialog box which opens, the **Search** text box has the focus. You hear "Filter or search edit." Type all or part of the name of the first user you want to add to the shared mailbox and then, to search for the name, press Enter. 
    
7. Press the Tab key about six times until you hear the name of the user in the search results list. Press Enter.
    
    > [!TIP]
    > If the search results list includes multiple names, press the Up Arrow key or the Down Arrow key until you hear the name you want. Press Enter. 
  
8. Tab to the **Permission level** combo box. The default permission level is **Publishing Editor**, which allows selected users to create items and subfolders, read items, and edit or delete all items. Other permission levels include **Reviewer**, **Contributor**, **Non Editing Author**, **Author**, **Editor**, **Publishing Author**, and **Owner**. You can also create a custom permission level. 
    
9. To select the permission level for the selected user, press the Up Arrow key or the Down Arrow key.
    
    > [!TIP]
    > To review the rights allowed for a permission level, press the Tab key through the 10 check boxes that specify the rights for the selected permission level. If you change a check box setting, the permission level changes to **Custom**. If you select the **Custom** permission level, all check boxes are cleared for you to select what you want. 
  
10. Tab to the **Save** button and press Enter. The user and associated permission level are saved and added to the table of users in the **Public Folder Permissions** dialog box. 
    
11. To add another user, activate the **Add** button, which has the focus, by pressing Enter. Repeat steps 5 through 10. Do this for all users you want to add to the new public folder. 
    
12. When you finish adding users, in the **Public Folder Permissions** dialog box, tab to the **Save** button and press Enter. Wait several seconds for the information to be saved. An alert specifies that the save operation is complete, and you hear "Close button." To close the alert, press Enter. The **public folders** main page view has the focus again. 
    
> [!NOTE]
> Public folders have size limits, and subfolders inherit permission settings from parent folders in specific ways. In addition, you can enable mail settings for a public folder. [Learn more about creating public folders](https://go.microsoft.com/fwlink/?LinkId=799146). 
  
## Create a distribution group
<a name="BKMK_CreateDistGrp"> </a>

Another method for facilitating and configuring collaboration in Exchange Online is a distribution group—a collection of two or more recipients that appears in the shared address book. When an email message is sent to a distribution group, it's received by all members of the group. Distribution groups can be organized by a particular discussion subject (such as "Resource Management Best Practices") or by users who share a common work structure—as in a workgroup or project team—that requires them to communicate frequently. [Use a screen reader to create a new distribution group in the Exchange admin center](use-screen-reader-to-create-distribution-group-in-exchange-admin-center.md). [Learn more about managing distribution groups](https://go.microsoft.com/fwlink/?LinkId=613635).
  
## Work with a shared mailbox
<a name="BKMK_WorkSharedMailbox"> </a>

Shared mailboxes make it easy for a group of people to monitor and send email from a common account, such as info@contoso.com or support@contoso.com. When a group member replies to a message sent to the shared mailbox, the email looks like it was sent by the shared mailbox, not by the group member. [Use a screen reader to add a new shared mailbox in the Exchange admin center 2016](use-screen-reader-to-add-shared-mailbox-in-exchange-admin-center-2016.md). [Learn more about shared mailboxes](https://go.microsoft.com/fwlink/?LinkId=798937).
  
## Establish a site mailbox through SharePoint
<a name="BKMK_EstablishSiteMailbox"> </a>

If your organization uses SharePoint, a site mailbox can be an effective collaboration tool because it joins Exchange email with SharePoint documents. A site mailbox comprises owners and members of a SharePoint site, a shared Exchange mailbox for email messages, and a SharePoint site in which the site mailbox is stored and shared. 
  
A site mailbox serves as a central filing cabinet for project-specific email and documents that can be accessed and edited only by site members. Because projects typically have a specific start and finish date, site mailboxes have a corresponding life cycle. Learn more about [using site mailboxes](https://go.microsoft.com/fwlink/?LinkId=286170).
  
## Accessibility Information
<a name="BKMK_AcessInfo"> </a>

The [Microsoft Accessibility](https://go.microsoft.com/fwlink/p/?LinkID=21487) website provides more information about assistive technology. A free monthly electronic newsletter is available to help you stay current with accessibility topics about Microsoft products. To subscribe, visit the [Microsoft Accessibility Update Newsletter Subscription](https://go.microsoft.com/fwlink/p/?LinkID=14920) page. 
  
### Technical support for customers with disabilities

Microsoft wants to provide the best possible experience for all our customers. If you have a disability or have questions related to accessibility, please contact the [Microsoft Disability Answer Desk](https://go.microsoft.com/fwlink/p/?LinkID=518252) for technical assistance. 
  
The Disability Answer Desk support team is trained in using many popular assistive technologies and can offer assistance in English, Spanish, French, and American Sign Language. Please visit the [Microsoft Disability Answer Desk](https://go.microsoft.com/fwlink/p/?LinkID=518252) site to find the contact details for your region. 
  

