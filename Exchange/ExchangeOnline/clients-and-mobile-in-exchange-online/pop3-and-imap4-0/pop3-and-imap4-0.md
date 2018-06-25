---
title: "POP3 and IMAP4"
ms.author: dmaguire
author: msdmaguire
manager: laurawi
ms.date: 6/24/2018
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: fce4cf21-02b4-4b42-82c8-ddb3c7eed4dc
description: "Summary: An overview of POP3 and IMAP4, and the differences between them."
---

# POP3 and IMAP4

 **Summary**: An overview of POP3 and IMAP4, and the differences between them.
  
By default, POP3 and IMAP4 are enabled for all users in Exchange Online.
  
- To enable or disable POP3 and IMAP4 for individual users, see [Enable or Disable POP3 or IMAP4 access for a user](enable-or-disable-pop3-or-imap4-access.md).
    
- To customize the POP3 or IMAP4 settings for a user, see [Set POP3 or IMAP4 settings for a user](pop3-or-imap4-settings.md).
    
Users can use any email programs that support POP3 and IMAP4 to connect to Exchange Online. These programs include Outlook, Microsoft Outlook Express, Entourage, and many third-party programs, such as Mozilla Thunderbird and Eudora. The features supported by each email client programs vary. For information about features offered by specific POP3 and IMAP4 client programs, see the documentation that's included with each application. 
  
POP3 and IMAP4 provide access to the basic email features of Exchange Online and allow for offline email access, but don't offer rich email, calendaring, and contact management, or other features that are available when users connect with Outlook, Exchange ActiveSync, Outlook Web App, or Outlook Voice Access.
  
> [!NOTE]
> Each time a person accesses a POP-based or IMAP-based email program to open his or her Office 365 email, that user will experience a delay of several seconds. The delay results from using a proxy server, which introduces an additional hop for authentication. The proxy server first looks up the assigned pod server (client access server) and then authenticates against that. 
  
## Settings users use to set up POP3 or IMAP4 access to their Exchange Online mailboxes
<a name="settings"> </a>

After you enable POP3 and IMAP4 client access, you have to give users the information in the following table so that they can connect their email programs to their Exchange Online mailboxes. 
  
POP3 and IMAP4 email programs don't use POP3 and IMAP4 to send messages to the email server. Email programs that use POP3 and IMAP4 rely on SMTP to send messages.
  
|||||
|:-----|:-----|:-----|:-----|
||**Server name** <br/> |**Port** <br/> |**Encryption method** <br/> |
|POP3  <br/> |Outlook.office365.com  <br/> |995  <br/> |TLS  <br/> |
|IMAP4  <br/> |Outlook.office365.com  <br/> |993  <br/> |TLS  <br/> |
|SMTP  <br/> |Smtp.office365.com  <br/> |587  <br/> |TLS  <br/> |
   
## Understanding the differences between POP3 and IMAP4
<a name="Differences"> </a>

By default, when POP3 email programs download email messages to a client computer, the downloaded messages are removed from the server. When a copy of your user's email isn't kept on the email server, the user can't access the same email messages from multiple computers. However, some POP3 email programs can be configured to keep copies of the messages on the server so that the same email messages can be accessed from another computer. POP3 client programs can be used to download messages from the email server to only a single folder (usually, the Inbox) on the client computer. POP3 can't synchronize multiple folders on the email server with multiple folders on the client computer. POP3 also doesn't support public folder access.
  
Email client programs that use IMAP4 are more flexible and generally offer more features than those that use POP3. By default, when IMAP4 email programs download email messages to a client computer, a copy of each downloaded message remains on the email server. Because a copy of the user's email message is kept on the email server, the user can access the same email message from multiple computers. With IMAP4 email, the user can access and create multiple email folders on the email server. Users can then access any of their messages on the server from computers in multiple locations. For example, most IMAP4 programs can be configured to keep a copy of a user's sent items on the server so that he or she can view the sent items from any other computer. IMAP4 supports additional features that are supported by most IMAP4 programs. For example, some IMAP4 programs include a feature that lets users view only the headers of their email messages on the server—who the messages are from and the subjects—and then download only the messages that they want to read.
  
## Send and receive options for POP3 and IMAP4 email programs
<a name="SendReceive"> </a>

POP3 and IMAP4 email programs let users choose when they want to connect to the server to send and receive email. This section discusses some of the most common connectivity options and provides some factors your users should consider when they choose connection options available in their POP3 and IMAP4 email programs.
  
### Common configuration settings

Three of the most common connection settings that can be set on the POP3 or IMAP4 client application are:
  
- To send and receive messages every time the email application is started. When this option is used, mail is sent and received only on starting the email application.
    
- To send and receive messages manually. When this option is used, messages are sent and received only when the user clicks a send-and-receive option in the client user interface.
    
- To send and receive messages every set number of minutes. When this option is used, the client application connects to the server every set number of minutes to send messages and download any new messages. 
    
For information about how to configure these settings for the email application that you use, see the Help documentation that's provided with the email application.
  
### Considerations when selecting send and receive options

The default setting on some email programs is to not keep a copy of messages on the server after they're retrieved. If the user wants to access messages from multiple email programs or devices, they should keep a copy of messages on the server.
  
If the device or computer that's running the POP3 or IMAP4 email application is always connected to the Internet, the user might want to configure the email application to send and receive messages every set number of minutes. Connecting to the server at frequent intervals lets the user keep the email application up-to-date with the most current information on the server. However, if the device or computer that's running the POP3 or IMAP4 email application isn't always connected to the Internet, the user might want to configure the email application to send and receive messages manually. 
  
> [!NOTE]
> If the user is using an IMAP4-compliant email application that supports the IMAP4 IDLE command, the user might be able to send email to and receive email from the Exchange mailbox in nearly real time. For this connection method to work, both the email server application and the client application must support the IMAP4 IDLE command. In most cases, users don't have to configure any settings in their IMAP4 programs to use this connection method. 
  

