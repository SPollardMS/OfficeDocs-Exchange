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


> [!NOTE]
> This article is for IT Pros and admins that are deploying and configuring Outlook 2016 for Windows for users in their enterprises. If you're a user trying to configure your Outlook settings, see [Turn on Cached Exchange Mode](https://support.office.com/article/7885af08-9a60-4ec3-850a-e221c1ed0c1c).  

## Comparison of Cached Exchange Mode and Online Mode

Cached Exchange Mode gives users a seamless online and offline Outlook experience by caching the user's mailbox and the Offline Address Book (OAB) locally. With Cached Exchange Mode, which is the default setting for users, Outlook no longer depends on continuous network connectivity for access to user information. When a user is connected, Outlook continuously updates users' mailboxes so that the mailboxes are kept up to date. If a user disconnects from the network, for example, by moving to an area without Wi-Fi access, the user can continue to access the last available email data.

> [!IMPORTANT]
> We recommend always using Cached Exchange Mode with an Office 365 account.
  
Online Mode works by using information directly from the server, and, as the name implies, it requires a connection. Mailbox data is only cached in memory and never written to disk.

Cached Exchange Mode is the preferred configuration in Outlook 2016 and is useful in the following situations:

- Users who frequently move in and out of connectivity.
- Users who frequently work offline or without connectivity.
- Users who have high-latency connections (greater than 500 ms) to the Exchange Server.

Online mode is useful in the following situations:

- Kiosk scenarios, where a particular computer has many users who access different Outlook accounts—and the delay to download email messages to a local cache is unacceptable.
- Heavily regulated compliance or secure environments where it is a risk to store data locally. In addition, we recommend that you consider using Encrypting File System (EFS) or BitLocker as a robust solution.
- Large mailboxes on computers that don’t have sufficient hard disk space for a local copy of the mailbox.

Even when it is configured in Cached Exchange Mode, Outlook 2016 must contact the server directly to do certain operations. These operations won't function when Outlook is not connected and can take longer to complete on high-latency connections. These operations include the following:

- Working with Shared Folders that were not made available offline.
- Retrieving Free/Busy information.
- Setting, changing, or canceling an Out of Office message.
- Accessing public folders that were not made available offline.
- Retrieving rights to a rights-protected message.
- Editing rules.
- Retrieving MailTips.
- Retrieving Policy Tips.

Delayed delivery options are client side in cached mode and server side in online mode. So, when you use Cached Exchange Mode, Outlook must be connected and open at the assigned delivery time for the delayed delivery message to be sent.

 Outlook 2016 supports running in Cached Exchange Mode in a Remote Desktop Services (RDS), formerly known as Terminal Services, environment that has multiple users. When you configure a computer running RDS to use Cached Exchange Mode, be sure to consider the additional storage space and disk I/O that are required for multiple client access. New Exchange accounts set up on computers running RDS use Online Mode by default. At setup, the user can decide to enable Cached Exchange Mode.


## Configure Cached Exchange Mode in Outlook 2016 for Windows

### Offline data file (.ost file) and Offline Address Book (OAB)

When an Outlook 2016 account is configured to use Cached Exchange Mode, there's always a local copy of a user's Exchange mailbox ready in an offline data file (.ost file) on the user's computer. By default, the .ost file is in the C:\Users\\<username\>\AppData\Local\Microsoft\Outlook folder.)

Whenever the user is offline and using Outlook 2016, the program works from this local copy and with the Offline Address Book (OAB). When the user is online, the cached mailbox and OAB are periodically updated from the Exchange Server computer in the background. Any email messages the user drafted while offline are automatically sent when that user is back online.

If a user upgrades from an earlier version of Outlook to Outlook 2016 and you previously configured Outlook for Cached Exchange Mode, those old Cached Exchange Mode settings are automatically applied, including a new synchronization control for shared mailboxes. The default location for new .ost or OAB files is: %userprofile%\AppData\Local\Microsoft\Outlook\Offline Address Books. As an administrator, you can configure a different .ost file location for users in your organization who do not already have .ost files. If you do not specify a different .ost file location, Outlook creates an .ost file in the default location when users start Outlook in Cached Exchange Mode.

### "Mail to keep offline" setting

The **Mail to keep offline** slider in the Server Settings dialog box in Outlook 2016 has been updated to apply to shared folders and lets you set a smaller synchronization window, available by default with Cached Exchange Mode in Outlook 2016. 

The slider allows an Outlook 2016 user to limit the email messages that are locally synchronized in an Microsoft Outlook data file (.ost). By default, if Cached Exchange Mode is enabled, Outlook 2016 caches email messages only from the last 12 months and removes anything older from the *local* cache for the PC. These default settings depend on the device, with mobile devices having smaller default settings. The email messages that are removed from the local cache are still available for users to view, but they’ll need to be connected to the Exchange Server to view them. Users can view messages that were removed from the local cache by scrolling to the end of a message list in a folder and clicking the message **Click here to view more on Microsoft Exchange**. Users can also change how much email to keep offline. You, the administrator, can change the default age or enforce the age of email messages that are removed from the local cache.

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