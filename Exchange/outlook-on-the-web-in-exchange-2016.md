---
title: Outlook on the web in Exchange 2016
ms.prod: EXCHANGE
ms.assetid: 3814b665-01e8-4881-9a44-163f14789ee4
---


# Outlook on the web in Exchange 2016
Learn about administrative tasks for managing Outlook on the web (Outlook Web App) in Exchange 2016.
The user interface in Outlook on the web (formerly known as Outlook Web App) for Exchange Server 2016 has been optimized and simplified for use with phones and tablets. Supported web browsers give users access to more Outlook features. Unsupported web browsers give users the light version of Outlook on the web that has less features. For more information about features and supported web browsers, see  [Outlook on the web (formerly Outlook Web App)](what-s-new-in-exchange-2016.md#OutlookAppfrom2013) and [Outlook on the web (formerly Outlook Web App)](what-s-new-in-exchange-2016.md#OutlookAppfrom2010).
  
    
    

When you install Exchange 2016, Outlook on the web is automatically available for internal users at  `https://<ServerName>/owa` (for example, `https://mailbox01.contoso.com/owa`). But, you'll likely want to configure Outlook on the web for external access (for example,  `https://mail.contoso.com/owa`). For more information, see  [Step 4: Configure external URLs](configure-mail-flow-and-client-access.md#ConfigExternalURL).
 In an Outlook 2010 or later installation that's connected to an Exchange mailbox, you can typically see the Outlook on the web URL at **File** > **Info** > **Account Information** in the **Account Settings** section.
  
    
    


  
    
    
![The Account Information page in Outlook 2016](images/1329d53d-0627-4377-8085-9eb63dcc7f97.png)
  
    
    
Outlook on the web is provided by the Client Access (frontend) services on Mailbox servers. In Exchange 2016, Client Access services are part of the Mailbox server, so you can't configure a standalone Client Access server like you could in previous versions of Exchange. For more information, see  [Client access protocol architecture](exchange-2016-architecture.md#ClientAccessProtocol).If you're looking for information about Outlook on the web in Office 365, see  [Welcome to Outlook on the web](https://go.microsoft.com/fwlink/p/?LinkId=799535).
## Administrative tasks for managing Outlook on the web
<a name="Managing"> </a>

The configuration and management tasks that are documented for Outlook on the web in Outlook 2016 are listed in the following table.
  
    
    


|**Topic**|**Description**|
|:-----|:-----|
| [View or configure Outlook on the web virtual directories in Exchange 2016](view-or-configure-outlook-on-the-web-virtual-directories-in-exchange-2016.md) <br/> |View and configure the properties of Outlook on the web for all users that connect to the server.  <br/> |
| [Configure http to https redirection for Outlook on the web in Exchange 2016](configure-http-to-https-redirection-for-outlook-on-the-web-in-exchange-2016.md) <br/> |Redirect Outlook on the web unencrypted http requests to https.  <br/> |
| [Create a theme for Outlook on the web in Exchange 2016](create-a-theme-for-outlook-on-the-web-in-exchange-2016.md) <br/> |Outlook on the web comes with built-in themes that define the colors and icons that are used in Outlook on the web, but you can also create your own themes.  <br/> |
| [Customize the Outlook on the web sign-in, language selection, and error pages in Exchange 2016](customize-the-outlook-on-the-web-sign-in-language-selection-and-error-pages-in-e.md) <br/> |Customize key pages in Outlook on the web.  <br/> |
| [Use AD FS claims-based authentication with Outlook on the web](use-ad-fs-claims-based-authentication-with-outlook-on-the-web.md) <br/> |Centralize Outlook on the web authentication by using Active Directory Federation Services.  <br/> |
   

