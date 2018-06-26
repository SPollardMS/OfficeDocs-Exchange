---
title: "Message properties and search operators for In-Place eDiscovery"
ms.author: markjjo
author: markjjo
manager: scotv
ms.date: 12/9/2016
ms.audience: Admin
ms.topic: overview
ms.service: exchange-online
localization_priority: Normal
ms.assetid: 402b74e4-8853-4c51-9737-1a9c19f8e3dd
description: "This topic describes the properties of Exchange email messages that you can search by using In-Place eDiscovery &amp; Hold in Exchange Server 2013 and Exchange Online. The topic also describes Boolean search operators and other search query techniques that you can use to refine eDiscovery search results."
---

# Message properties and search operators for In-Place eDiscovery

This topic describes the properties of Exchange email messages that you can search by using In-Place eDiscovery &amp; Hold in Exchange Server 2013 and Exchange Online. The topic also describes Boolean search operators and other search query techniques that you can use to refine eDiscovery search results.
  
In-Place eDiscovery uses Keyword Query Language (KQL). For more details, see [Keyword Query Language syntax reference](https://go.microsoft.com/fwlink/?LinkId=269603).
  
## Searchable properties in Exchange

The following table lists email message properties that can be searched using an In-Place eDiscovery search or by using the **New-MailboxSearch** or the **Set-MailboxSearch** cmdlet. The table includes an example of the  _property:value_ syntax for each property and a description of the search results returned by the examples. 
  
|**Property**|**Property description**|**Examples**|**Search results returned by the examples**|
|:-----|:-----|:-----|:-----|
|Attachment  <br/> |The names of files attached to an email message.  <br/> |attachment:annualreport.ppt  <br/> attachment:annual\*  <br/> |Messages that have an attached file named annualreport.ppt.  <br/> In the second example, using the wildcard returns messages with the word "annual" in the file name of an attachment.  <br/> |
|Bcc  <br/> |The BCC field of an email message.<sup>1</sup> <br/> |bcc:pilarp@contoso.com  <br/> bcc:pilarp  <br/> bcc:"Pilar Pinilla"  <br/> |All examples return messages with Pilar Pinilla included in the Bcc field.  <br/> |
|Category  <br/> | The categories to search. Categories can be defined by users by using Outlook or Outlook Web App. The possible values are:  <br/>  blue  <br/>  green  <br/>  orange  <br/>  purple  <br/>  red  <br/>  yellow  <br/> |category:"Red Category"  <br/> |Messages that have been assigned the red category in the source mailboxes.  <br/> |
|Cc  <br/> |The CC field of an email message.<sup>1</sup> <br/> |cc:pilarp@contoso.com  <br/> cc:"Pilar Pinilla"  <br/> |In both examples, messages with Pilar Pinilla specified in the CC field.  <br/> |
|From  <br/> |The sender of an email message.<sup>1</sup> <br/> |from:pilarp@contoso.com  <br/> from:contoso.com  <br/> |Messages sent by the specified user or sent from a specified domain.  <br/> |
|Importance  <br/> |The importance of an email message, which a sender can specify when sending a message. By default, messages are sent with normal importance, unless the sender sets the importance as **high** or **low**.  <br/> |importance:high  <br/> importance:medium  <br/> importance:low  <br/> |Messages that are marked as high importance, medium importance, or low importance.  <br/> |
|Kind  <br/> | The message type to search. Possible values:  <br/>  contacts  <br/>  docs  <br/>  email  <br/>  faxes  <br/>  im  <br/>  journals  <br/>  meetings  <br/>  notes  <br/>  posts  <br/>  rssfeeds  <br/>  tasks  <br/>  voicemail  <br/> |kind:email  <br/> kind:email OR kind:im OR kind:voicemail  <br/> |Email messages that meet the search criteria. The second example returns email messages, instant messaging conversations, and voice messages that meet the search criteria.  <br/> |
|Participants  <br/> |All the people fields in an email message; these fields are From, To, CC, and BCC.<sup>1</sup> <br/> |participants:garthf@contoso.com  <br/> participants:contoso.com  <br/> |Messages sent by or sent to garthf@contoso.com.  <br/> The second example returns all messages sent by or sent to a user in the contoso.com domain.  <br/> |
|Received  <br/> |The date that an email message was received by a recipient.  <br/> |received:04/15/2014  <br/> received\>=01/01/2014 AND received\<=03/31/2014  <br/> |Messages that were received on April 15, 2014. The second example returns all messages received between January 1, 2014 and March 31, 2014.  <br/> |
|Recipients  <br/> |All recipient fields in an email message; these fields are To, CC, and BCC.<sup>1</sup> <br/> |recipients:garthf@contoso.com  <br/> recipients:contoso.com  <br/> |Messages sent to garthf@contoso.com.  <br/> The second example returns messages sent to any recipient in the contoso.com domain.  <br/> |
|Sent  <br/> |The date that an email message was sent by the sender.  <br/> |sent:07/01/2014  <br/> sent\>=06/01/2014 AND sent\<=07/01/2014  <br/> |Messages that were sent on the specified date or sent within the specified date range.  <br/> |
|Size  <br/> |The size of an item, in bytes.  <br/> |size\>26214400  <br/> size:1..1048576  <br/> |Messages larger than 25 MB.  <br/> The second example returns messages from 1 through 1,048,576 bytes (1 MB) in size.  <br/> |
|Subject  <br/> |The text in the subject line of an email message.  <br/> |subject:"Quarterly Financials"  <br/> subject:northwind  <br/> |Messages that contain the exact phrase "Quarterly Financials" anywhere in the text of the subject line.  <br/> The second example returns all messages that contain the word northwind in the subject line.  <br/> |
|To  <br/> |The To field of an email message.<sup>1</sup> <br/> |to:annb@contoso.com  <br/> to:annb  <br/> to:"Ann Beebe"  <br/> |All examples return messages where Ann Beebe is specified in the To: line.  <br/> |
   
> [!NOTE]
> <sup>1</sup> For the value of a recipient property, you can use the SMTP address, display name, or alias to specify a user. For example, you can use annb@contoso.com, annb, or "Ann Beebe" to specify the user Ann Beebe. 
  
## Supported search operators

Boolean search operators, such as **AND**, **OR**, help you define more-precise mailbox searches by including or excluding specific words in the search query. Other techniques, such as using property operators (such as \>= or ..), quotation marks, parentheses, and wildcards, help you refine eDiscovery search queries. The following table lists the operators that you can use to narrow or broaden search results. 
  
> [!IMPORTANT]
>  You must use uppercase Boolean operators in a search query. For example, use **AND**; don't use **and**. Using lowercase operators in search queries will return an error. 
  
|**Operator**|**Usage**|**Description**|
|:-----|:-----|:-----|
|AND  <br/> |keyword1 AND keyword2  <br/> |Returns messages that include all of the specified keywords or  `property:value` expressions.  <br/> |
|+  <br/> |keyword1 +keyword2 +keyword3  <br/> |Returns items that contain  *either*  `keyword2` or  `keyword3` *and*  that also contain  `keyword1`. Therefore, this example is equivalent to the query  `(keyword2 OR keyword3) AND keyword1`.  <br/> Note that the query  `keyword1 + keyword2` (with a space after the **+** symbol) isn't the same as using the ** AND ** operator. This query would be equivalent to  `"keyword1 + keyword2"` and return items with the exact phase  `"keyword1 + keyword2"`.  <br/> |
|OR  <br/> |keyword1 OR keyword2  <br/> |Returns messages that include one or more of the specified keywords or  `property:value` expressions.  <br/> |
|NOT  <br/> |keyword1 NOT keyword2  <br/> NOT from:"Ann Beebe"  <br/> |Excludes messages specified by a keyword or a  `property:value` expression. For example,  `NOT from:"Ann Beebe"` excludes messages sent by Ann Beebe.  <br/> |
|-  <br/> |keyword1 -keyword2  <br/> |The same as the **NOT** operator. This query returns items that contain  `keyword1` and excludes items that contain  `keyword2`.  <br/> |
|NEAR  <br/> |keyword1 NEAR(n) keyword2  <br/> |Returns messages with words that are near each other, where n equals the number of words apart. For example,  `best NEAR(5) worst` returns messages where the word "worst" is within five words of "best". If no number is specified, the default distance is eight words.  <br/> |
|:  <br/> |property:value  <br/> |The colon (:) in the  `property:value` syntax specifies that the property value being searched for equals the specified value. For example,  `recipients:garthf@contoso.com` returns any message sent to garthf@contoso.com.  <br/> |
|\<  <br/> |property\<value  <br/> |Denotes that the property being searched is less than the specified value. <sup>1</sup> <br/> |
|\>  <br/> |property\>value  <br/> |Denotes that the property being searched is greater than the specified value.<sup>1</sup> <br/> |
|\<=  <br/> |property\<=value  <br/> |Denotes that the property being searched is less than or equal to a specific value.<sup>1</sup> <br/> |
|\>=  <br/> |property\>=value  <br/> |Denotes that the property being searched is greater than or equal to a specific value.<sup>1</sup> <br/> |
|..  <br/> |property:value1..value2  <br/> |Denotes that the property being searched is greater than or equal to value1 and less than or equal to value2.<sup>1</sup> <br/> |
|" "  <br/> |"fair value"  <br/> subject:"Quarterly Financials"  <br/> |Use double quotation marks (" ") to search for an exact phrase or term in keyword and  `property:value` search queries.  <br/> |
|\*  <br/> |cat\*  <br/> subject:set\*  <br/> |Prefix wildcard searches (where the asterisk is placed at the end of a word) match for zero or more characters in keywords or  `property:value` queries. For example,  `subject:set*` returns messages that contain the word set, setup, and setting (and other words that start with "set") in the subject line.  <br/> |
|( )  <br/> | (fair OR free) AND from:contoso.com  <br/>  (IPO OR initial) AND (stock OR shares)  <br/>  (quarterly financials)  <br/> |Parentheses group together Boolean phrases,  `property:value` items, and keywords. For example,  `(quarterly financials)` returns items that contain the words quarterly and financials.  <br/> |
   
> [!NOTE]
> <sup>1</sup> Use this operator for properties that have date or numeric values. 
  
## Unsupported characters in search queries

Unsupported characters in a search query typically cause a search error or return unintended results. Unsupported characters are often hidden and they're typically added to a query when you copy the query or parts of the query from other applications (such as Microsoft Word or Microsoft Excel) and copy them to the keyword box on the query page of In-Place eDiscovery search.
  
Here's a list of the unsupported characters for an In-Place eDiscovery search query. 
  
- **Smart quotation marks** Smart single and double quotation marks (also called curly quotes) aren't supported. Only straight quotation marks can be used in a search query. 
    
- **Non-printable and control characters** Non-printable and control characters don't represent a written symbol, such as a alpha-numeric character. Examples of non-printable and control characters include characters that format text or separate lines of text. 
    
- **Left-to-right and right-to-left marks** These are control characters used to indicate text direction for left-to-right languages (such as English and Spanish) and right-to-left languages (such as Arabic and Hebrew). 
    
- **Lowercase Boolean operators** As previous explained, you have to use uppercase Boolean operators, such as **AND** and **OR**, in a search query. Note that the query syntax will often indicate that a Boolean operator is being used even though lowercase operators might be used; for example,  `(WordA or WordB) and (WordC or WordD)`.
    
 **How to prevent unsupported characters in your search queries?**The best way to prevent unsupported characters is to just type the query in the keyword box. Alternatively, you can copy a query from Word or Excel and then paste it to file in a plain text editor, such as Microsoft Notepad. Then save the text file and select **ANSI** in the **Encoding** drop-down list. This will remove any formatting and unsupported characters. Then you can copy and paste the query from the text file to the keyword query box. 
  
## Search tips and tricks

- Keyword searches are not case sensitive. For example, **cat** and **CAT** return the same results. 
    
- A space between two keywords or two  `property:value` expressions is the same as using **AND**. For example,  `from:"Sara Davis" subject:reorganization` returns all messages sent by Sara Davis that contain the word **reorganization** in the subject line. 
    
- Use syntax that matches the  `property:value` format. Values are not case-sensitive, and they can't have a space after the operator. If there is a space, your intended value will just be full-text searched. For example **to: pilarp** searches for "pilarp" as a keyword, rather than for messages that were sent to pilarp. 
    
- When searching a recipient property, such as To, From, Cc, or Recipients, you can use an SMTP address, alias, or display name to denote a recipient. For example, you can use pilarp@contoso.com, pilarp, or "Pilar Pinilla".
    
- You can use only prefix wildcard searches—for example, **cat\*** or **set\***. Suffix wildcard searches (\*cat) or substring wildcard searches (\*cat\*) aren't supported.
    
- When searching a property, use double quotation marks (" ") if the search value consists of multiple words. For example **subject:budget Q1** returns messages that contain **budget** in the in the subject line and that contain **Q1** anywhere in the message or in any of the message properties. Using **subject:"budget Q1"** returns all messages that contain **budget Q1** anywhere in the subject line. 
    

