---
title: "Public attachment handling in Exchange Online"
ms.author: dmaguire
author: msdmaguire
manager: laurawi
ms.date: 12/9/2016
ms.audience: ITPro
ms.topic: article
ms.service: exchange-online
localization_priority: Normal
ms.assetid: 2b5b8f6a-1bce-4872-8989-bac53ffafaa4
description: "As an admin, you can set up both private and public attachment handling in Outlook Web App depending on how you configure your Outlook Web App mailbox policies. The settings for private (internal) and public (external) networks define how users can open, view, send, or receive attachments depending on whether a user is signed in to Outlook Web App on a computer that is part of a private or of a public network."
---

# Public attachment handling in Exchange Online

As an admin, you can set up both private and public attachment handling in Outlook Web App depending on how you configure your Outlook Web App mailbox policies. The settings for private (internal) and public (external) networks define how users can open, view, send, or receive attachments depending on whether a user is signed in to Outlook Web App on a computer that is part of a private or of a public network. 
  
## How can I control public attachment handling?

Although there are both private (internal network) and public (external network) settings to control attachments using Outlook Web App mailbox policies, admins require more consistent and reliable attachment handling when a user signs in to Outlook Web App from a computer on a public network such as at a coffee shop or library. To set up the ability to enforce attachment handling from external networks for an entire organization in Exchange Online, first use the [Set-OrganizationConfig](http://technet.microsoft.com/library/3b6df0fe-27c8-415f-ad0c-8b265f234c1a.aspx) cmdlet, set the  _PublicComputersDetectionEnabled_ parameter to  `$true`, configure the correct Outlook Web App mailbox policy either by using the Exchange admin center (EAC) or the [Set-OwaMailboxPolicy](http://technet.microsoft.com/library/530166f7-ab42-4609-ba73-9b5a39b567be.aspx) cmdlet and create claim rules in AD FS. Enabling this setting the on the [Set-OrganizationConfig](http://technet.microsoft.com/library/3b6df0fe-27c8-415f-ad0c-8b265f234c1a.aspx) cmdlet and creating the claim rules will enable Exchange Online to tell if a user is signing in to Outlook Web App from a private and public network or computer. 
  
The Outlook Web App mailbox policy parameters in the following table should be set to  `$true` to enable an admin to control attachment handling for public computers and networks. 
  
|****Exchange Management Shell parameter****|****Description****|
|:-----|:-----|
| _DirectFileAccessOnPublicComputersEnabled_ <br/> |Specifies left-click and other options available for attachments when the user has signed in to Outlook Web App from a computer outside of a private or corporate network. If this parameter is set to  `$true`, **Open** and other options are available. If it's set to  `$false`, the **Open** option is disabled.  <br/> |
| _ForceWacViewingFirstOnPublicComputers_ <br/> |Specifies whether a user who signed in to Outlook Web App from a computer outside of a private or corporate network can open an Office file directly without first viewing it as a webpage.  <br/> |
| _ForceWebReadyDocumentViewingFirstOnPublicComputers_ <br/> |Specifies whether a user who has signed in to Outlook Web App can open a document directly without first viewing it as a webpage.  <br/> |
| _WacViewingOnPublicComputersEnabled_ <br/> |Specifies whether a user who has signed into Outlook Web App from a computer outside of the corporate network can view supported Office files using Outlook Web App.  <br/> |
| _WebReadyDocumentViewingOnPublicComputersEnabled_ <br/> |Specifies whether WebReady Document Viewing is enabled when the user has signed in from a computer outside of the corporate network.  <br/> |
   
## What do you need to know before you begin?

- Procedures in this topic require specific permissions. See each procedure for its permissions information.
    
- [Create one or more mailboxes for users](../../recipients-in-exchange-online/create-user-mailboxes.md).
    
- [Enable Outlook Web App on a user's mailbox](../../recipients-in-exchange-online/manage-user-mailboxes/enable-or-disable-outlook-web-app.md) if it has been disabled. 
    
- Verify that cookies have been enabled in the Web browser for all of the users in your organization.
    
- Set up and configure single sign on using AD FS:
    
  - [Checklist: Use AD FS to implement and manage single sign-on](https://go.microsoft.com/fwlink/p/?LinkId=281821)
    
  - [Setting Up Single Sign On with Office 365 using AD FS 2.0](https://go.microsoft.com/fwlink/p/?LinkId=329949 )
    
  - [Configure single sign on](https://go.microsoft.com/fwlink/p/?LinkId=329950)
    
- To learn how to use Windows PowerShell to connect to Exchange Online, see [Connect to Exchange Online PowerShell](https://go.microsoft.com/fwlink/p/?linkid=396554).
    
- For information about keyboard shortcuts that may apply to the procedures in this topic, see **Keyboard shortcuts in the Exchange admin center**.
    
> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612),[Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351).. 
  
## Task 1 - Enable public attachment handling for your organization

Run the following command:  `Set-OrganizationConfig -PublicComputersDetectionEnabled $true`
  
> [!NOTE]
>  Setting this parameter to  `$true` won't affect the settings for the following parameters: >  _ForceWacViewingFirstOnPublicComputers_>  _WSSAccessOnPublicComputersEnabled_>  _UNCAccessOnPublicComputersEnabled_
  
## Task 2 - Add and create claim rules in AD FS 2.0

You must create a custom claim rule because an AD FS server relies on the presence of the  `x-ms-proxy` claim to detect whether user is coming from an internal or external network. When an AD FS proxy is deployed for external or public access, and if the user is coming from outside a private network, there will be an  `x-ms-proxy` claim sent from AD FS proxy to an AD FS server. To learn more about claim rules in AD FS, see [Create a Rule to Send Claims Using a Custom Rule](https://go.microsoft.com/fwlink/p/?LinkId=329966)
  
1. On the **Start Screen**, type **AD FS Management**, and then press **Enter**.
    
2. In AD FS console tree, under **AD FS\Trust Relationships** \> **Relying Party Trusts** and select **O365 Identity Platform**.
    
3. In **O365 Identity Platform**, click **Edit Claim Rules** \> **Add Rule** \> **Issuance Transform Rules**.
    
4. On the **Select Rule Template** page, under **Claim rule template**, select **Send Claims Using a Custom Rule** from the list, and then click **Next**.
    
5. On the **Configure Rule** page under **Claim rule name** type the display name for this rule. 
    
6. Under **Custom rule**, input the following: `exists ([Type == "http://schemas.microsoft.com/2012/01/requestcontext/claims/x-ms-proxy"]) => issue(Type = "http://schemas.microsoft.com/ws/2012/01/insidecorporatenetwork", Value = "false");`
    
7. Next, input the following:  `NOT exists ([Type == "http://schemas.microsoft.com/2012/01/requestcontext/claims/x-ms-proxy"]) => issue(Type = "http://schemas.microsoft.com/ws/2012/01/insidecorporatenetwork", Value = "true");`
    
8. Click **Finish**.
    
9. In the **Edit Claim Rules** dialog box, click **OK** to save the rule. 
    
## Task 3 - Enable public attachment handling on an Outlook Web App mailbox policy

### Use EAC to enable public attachment handling settings

1. In the EAC, click **Permissions** \> **Outlook Web App policies**.
    
2. In the result pane, click the mailbox policy you want to view or configure, and click **Edit**.
    
3. On **File Access**, use the check boxes to configure the file access and viewing options for users. File access lets a user open or view the contents of files attached to an email message.
    
    File access can be controlled based on whether a user has logged on to a public or private computer. The option for users to select private computer access or public computer access is available only when you're using forms-based authentication. All other forms of authentication default to private computer access.
    
  - **Direct file access** Select this check box if you want to enable direct file access. Direct file access lets users open files attached to email messages. 
    
  - **WebReady Document Viewing** Select this check box if you want to enable supported documents to be converted to HTML and displayed in a web browser. 
    
  - **Force WebReady Document Viewing when a converter is available** Select this check box if you want to force documents to be converted to HTML and displayed in a web browser before users can open them in the viewing application. Documents can be opened in the viewing application only if direct file access has been enabled. 
    
4. Click **Save** to update the policy. 
    
### Use the Exchange Management Shell to enable public attachment handling settings

Run the following command:  `Set-OwaMailboxPolicy -id MyOWAPublicPolicy -DirectFileAccessOnPublicComputersEnabled $true -ForceWacViewingFirstOnPublicComputers $true -WacViewingOnPublicComputersEnabled $true -WebReadyDocumentViewingOnPublicComputersEnabled $true`
  
## What you need to know about attachments?

An attachment can be a file that's created in any program, for example, a Word document, an Excel spreadsheet, a .wav file, or a bitmap file. Users can attach or include one or more files on any item that they create in their mailbox, for example, an email message, calendar item, or contact. Outlook Web App allows you to send and receive many common files types. Continuously
  
Some attachments might be removed or blocked by antivirus software used by your organization, by the organization of the recipients of your email, or you might be required to save them on your computer before you can open them. By default, Outlook Web App allows you to open attached Word, Excel, PowerPoint, text files and many media files directly. The files you can open from Outlook Web App vary depending on your account settings. The following table lists the default file name extensions that you can open in Outlook Web App.
  
|||
|:-----|:-----|
|**File name extensions allowed by default** <br/> |.rpmsg, xls, .xlsx, .xlsm, .xlsb, .pptx, .pptm, .ppsx, .ppsm, .doc, .docx, .docm, .xls, .wmv, .wma, .wav, vsd, .txt, .tif, .rtf, .pub, .ppt, .png, .pdf, .one, .mp3, .jpeg, .gif, .doc, .bmp, .avi  <br/> |
   

