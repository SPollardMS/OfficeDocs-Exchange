---
title: "Plan and configure Cached Exchange Mode in Outlook 2016 for Windows"
ms.author: danbrown
author: DHB-MSFT
manager: laurawi
ms.date: 6/27/2018
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-perpetual-itpro
localization_priority: Normal
ms.collection: Ent_Office_Outlook
description: "Helps IT Pros learn about planning and configuring Cached Exchange Mode in Outlook 2016 for Windows"
---

# Plan and configure Cached Exchange Mode in Outlook 2016 for Windows




## Configure Cached Exchange Mode in Outlook 2016 for Windows

### Offline data file (.ost file) and Offline Address Book (OAB)

When an Outlook 2016 account is configured to use Cached Exchange Mode, there's always a local copy of a user's Exchange mailbox ready in an offline data file (.ost file) on the user's computer. By default, the .ost file is in the C:\Users\\<username\>\AppData\Local\Microsoft\Outlook folder.)

Whenever the user is offline and using Outlook 2016, the program works from this local copy and with the Offline Address Book (OAB). When the user is online, the cached mailbox and OAB are periodically updated from the Exchange Server computer in the background. Any email messages the user drafted while offline are automatically sent when that user is back online.

If a user upgrades from an earlier version of Outlook to Outlook 2016 and you previously configured Outlook for Cached Exchange Mode, those old Cached Exchange Mode settings are automatically applied, including a new synchronization control for shared mailboxes. The default location for new .ost or OAB files is: %userprofile%\AppData\Local\Microsoft\Outlook\Offline Address Books. As an administrator, you can configure a different .ost file location for users in your organization who do not already have .ost files. If you do not specify a different .ost file location, Outlook creates an .ost file in the default location when users start Outlook in Cached Exchange Mode.

### "Mail to keep offline" setting

The **Mail to keep offline** slider in the Server Settings dialog box in Outlook 2016 has been updated to apply to shared folders and lets you set a smaller synchronization window, available by default with Cached Exchange Mode in Outlook 2016. 

The slider allows an Outlook 2016 user to limit the email messages that are locally synchronized in an Microsoft Outlook data file (.ost). By default, if Cached Exchange Mode is enabled, Outlook 2016 caches email messages only from the last 12 months and removes anything older from the *local* cache for the PC. These default settings depend on the device, with mobile devices having smaller default settings. Users can view messages that were removed from the local cache by scrolling to the end of a message list in a folder and clicking the message **Click here to view more on Microsoft Exchange**. Users can also change how much email to keep offline. You, the administrator, can change the default age or enforce the age of email messages that are removed from the local cache.

### Using Group Policy and the Office Customization Tool (OCT)

Use the following procedures to configure Cached Exchange Mode settings by using the OCT or Group Policy. Remember that customizing Cached Exchange Mode settings is optional.

> [!NOTE]
> - To get the Group Policy and Office Customization Tool (OCT) files, download the [Office 2016 Administrative Template files (ADMX/ADML) and Office Customization Tool](https://www.microsoft.com/download/details.aspx?id=49030) from the Microsoft Download Center.
> - The Office Customization Tool can only be used to configure volume licensed versions of Outlook, such as the version of Outlook that comes with Office Standard 2016.
  
### To configure Cached Exchange Mode settings by using the OCT

1. In the OCT tree view, find **Outlook**, and click **Add Accounts**. In the **Account Name** column, click the account you want to configure, and click **Modify** to display the **Exchange Settings** dialog box. 
    
2. Click **More settings**.
    
3. Click the **Cached Mode** tab. 
    
4. Click **Configure Cached Exchange Mode**, and select the **Use Cached Exchange Mode** check box to enable Cached Exchange Mode for users. (By default, Cached Exchange Mode is disabled.) 
    
5. Choose a default download option on the **Cached Mode** tab: 
    
  - **Download only headers** Users see header information and the beginning of the message. They can download the full message in several ways—for example, by double-clicking to open the message or by clicking **Download the rest of this message now** in the reading pane. 
    
  - **Download headers followed by the full item** All headers are downloaded first, and then full items are downloaded. The download order might not be chronological, but that shouldn't be noticeable to the user. Microsoft Outlook downloads headers followed by full items in the folder that the user is currently accessing, and then it downloads headers followed by full items in folders that the user has recently viewed. 
    
  - **Download full items** Full items are downloaded. We recommend this option unless you have a slow network connection. The download order might not be chronological, but that shouldn't be noticeable to the user. Microsoft Outlook downloads full items in the folder that the user is currently accessing, and then it downloads full items in folders that the user has recently viewed. You might want to pair this with the **On slow connections, download only headers** option. 
    
### To configure Cached Exchange Mode settings using Group Policy

1. In Group Policy, load the Outlook 2016 template.
    
2. Open the Group Policy Management Console (GPMC), and in the tree view, expand **Domains**, and expand **Group Policy Objects**.
    
3. Right-click the policy object that you want, and click **Edit**. The Group Policy Management Editor window opens.
    
4. In the tree view, go to  **User Configuration** > **Policies** > **Administrative Templates** > **Microsoft Outlook 2016** > **Account Settings** > **Exchange** > **Cached Exchange Mode**.
    
5. In the reading pane, in the **Setting** column, open the policy that you want to set by double-clicking it. For example, in the **Exchange** reading pane, open **Use Cached Exchange Mode for new and existing Outlook profiles**.
    
6. Select **Enabled**, and select an option (if appropriate).
    
7. Click **OK**.
    
### To configure a default .ost location by using Group Policy

1. In Group Policy, load the Outlook 2016 template.
    
2. Open the Group Policy Management Console (GPMC), and in the tree view, expand **Domains**, and then expand **Group Policy Objects**.
    
3. Right-click the policy object that you want, and click **Edit**. The Group Policy Management Editor window opens.
    
4. In the tree view, go to **User Configuration** > **Policies** > **Administrative Templates** > **Microsoft Outlook 2016** > **Miscellaneous** > **PST Settings**.
    
5. Double-click **Default location for OST files** to open it. 
    
6. Click **Enabled** to enable the policy setting. 
    
7. In the **Default location for OST files** text box, enter the default location for .ost files. For example: 
    
    %userprofile%\Local Settings\Application Data\Microsoft\ _newfolder_.
    
8. Click **OK**.
    
    You can define a new default location for both Personal Microsoft Outlook data files (.pst) and .ost files. After you click **PST Settings** in the tree view, double-click to open the **Default location for PST files** setting in the reading pane. 
    
### To prevent a new .ost file from being created

1. In Group Policy, load the Outlook 2016 template.
    
2. Open the Group Policy Management Console (GPMC), and in the tree view, expand **Domains**, and expand **Group Policy Objects**.
    
3. Right-click the policy object that you want, and click **Edit**. The Group Policy Management Editor window opens.
    
4. In the tree view, go to  **User Configuration** > **Policies** > **Administrative Templates** > **Microsoft Outlook 2016** > **Account Settings** > **Exchange**.
    
5. Double-click **Do not create new OST file on upgrade** to open it. 
    
6. Click **Enabled** to enable the policy setting, and then click **OK**.