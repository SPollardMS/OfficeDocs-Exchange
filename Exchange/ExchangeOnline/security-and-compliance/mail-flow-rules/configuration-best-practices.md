---
title: "Best practices for configuring mail flow rules"
ms.author: chrisda
author: chrisda
ms.date: 6/23/2018
ms.audience: End User
ms.topic: article
ms.service: exchange-online
localization_priority: Normal
ms.assetid: abd863c3-c0ce-42f3-9470-a573adc3cbba
description: "Follow these best practice recommendations for Exchange transport rules in order to avoid common configuration errors. Each recommendation links to a topic with an example and step-by-step instructions."
---

# Best practices for configuring mail flow rules

Follow these best practice recommendations for Exchange transport rules in order to avoid common configuration errors. Each recommendation links to a topic with an example and step-by-step instructions.
  
## Test your rules

To make sure unexpected things don't happen to people's email, and to make sure you're really meeting the business, legal, or compliance intentions of your rule, be sure to test it thoroughly. There are many options, and rules can interact with each other, so it's important to test messages that you expect both will match the rule and won't match the rule in case you inadvertently made a rule too general. To learn all the options for testing rules, see [Test a mail flow rule](test-mail-flow-rules.md). 
  
## Scope your rule

Make sure your rule applies only to the messages you intend it to. For example:
  
- **Restrict a rule to messages either coming into or going out of the organization**
    
    By default, a new rule applies to messages that are either sent or received by people in your organization. So if you want the rule to apply only one way, be sure to specify that in the conditions for the rule. For an example, see [Common attachment blocking scenarios for mail flow rules](common-attachment-blocking-scenarios.md).
    
- **Restrict a rule based on the sender's or receiver's domain**
    
    By default, a new rule applies to messages sent from or received at any domain. Sometimes you want a rule to apply to all domains except for one, or to just one domain. For examples, see [Create a Domain or User-Based Safe Sender or Blocked Sender List Using Transport Rules](http://technet.microsoft.com/library/9721b46d-cbea-4121-be51-542395e6fd21.aspx).
    
For a complete list of all the conditions and exceptions that are available for transport rules, see:
  
- [Mail flow rule conditions and exceptions (predicates) in Exchange Online](conditions-and-exceptions.md)
    
- [Transport Rule Conditions (Exchange Server)](http://technet.microsoft.com/library/c918ea00-1e68-4b8b-8d51-6966b4432e2d.aspx)
    
- [Transport Rule Conditions (Exchange Online Protection) ](http://technet.microsoft.com/library/04edeaba-afd4-4207-b2cb-51bcc44e483c.aspx)
    
## Know when you need two rules

Sometimes it takes two rules to do what you want. Transport rules are processed in order, so multiple rules can apply to the same message. For example, if one of the actions is to block the message, and you also have another action you'd like to apply, such as copying the message to the sender's manager or changing the subject for the notification message, you would need two rules. The first rule could copy the message to the sender's manager and change the subject, and the second rule could block the message.
  
If you use two rules like this, be sure that the conditions are identical. To see examples, look at example 3 in [Common message approval scenarios](common-message-approval-scenarios.md), example 3 in [Common attachment blocking scenarios for mail flow rules](common-attachment-blocking-scenarios.md), and [Organization-wide disclaimers, signatures, footers, or headers](http://technet.microsoft.com/library/e45e33c9-e53b-427c-ada5-70901bc399b8.aspx).
  
## Don't repeat an action on every email in a conversation

The chain of email in a conversation can include many individual messages, and repeating the action on each message in the thread might get annoying. For example, if you have an action such as adding a disclaimer, you might want it to apply only to the first message in the thread. If so, add an exception for messages that already include the disclaimer text. For an example, see [Organization-wide disclaimers, signatures, footers, or headers](http://technet.microsoft.com/library/e45e33c9-e53b-427c-ada5-70901bc399b8.aspx).
  
## Know when to stop rule processing

Sometimes it makes sense to stop rule processing once a rule is matched. For example, if you have one rule to block messages with attachments and one to insert a disclaimer in messages that match a pattern, you probably should stop rule processing once the message is blocked. There's no need for further action. 
  
To stop rule processing after a rule is triggered, in the rule, select the **Stop processing more rules** check box. 
  
## If you have lots of keywords or patterns to match, load them from a file

For example, you might want to prevent emails from being sent if they contain a list of unacceptable or bad words. You can create a text file containing these words and phrases, and then use Windows PowerShell to set up a transport rule that blocks messages that use them.
  
The text file can contain regular expressions for patterns. These expressions are not case-sensitive. Common regular expressions include:
  
|||
|:-----|:-----|
|**Expression** <br/> |**Matches** <br/> |
|**.** <br/> |Any single character  <br/> |
|**\*** <br/> |Any additional characters  <br/> |
|**\d** <br/> |Any decimal digit  <br/> |
|[ *character_group*  ]  <br/> |Any single character in  *character_group*  .  <br/> |
   
For an example that shows a text file with regular expressions and the Exchange module Windows PowerShell commands to use, see [Use mail flow rules to route email based on a list of words, phrases, or patterns](use-rules-to-route-email.md).
  
To learn how to specify patterns using regular expressions, see [Regular Expression Reference](https://go.microsoft.com/fwlink/p/?LinkId=532394).
  

