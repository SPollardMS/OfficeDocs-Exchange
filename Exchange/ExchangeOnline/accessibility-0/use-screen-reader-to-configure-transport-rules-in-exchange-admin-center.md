---
title: "Use a screen reader to configure transport rules in the Exchange admin center"
ms.author: v-maleo
author: v-maleo
ms.date: 12/9/2016
ms.audience: ITPro
ms.topic: article
ms.service: exchange-online
localization_priority: Normal
ms.custom: A11y_UseSR
ms.assetid: 708c71d5-7d6a-40b8-966b-eed82bc0d186
description: "Using a screen reader and keyboard shortcuts, you can create transport rules in Exchange Online in the Exchange admin center (EAC) to look for specific conditions in messages that pass through your organization and take action on them. The main difference between transport rules and Inbox rules you would set up in an email client application (such as Outlook) is that transport rules take action on messages while they're in transit as opposed to after the message is delivered. Transport rules also contain a richer set of conditions, exceptions, and actions, which provides you with the flexibility to implement many types of messaging policies."
---

# Use a screen reader to configure transport rules in the Exchange admin center

Using a screen reader and keyboard shortcuts, you can create transport rules in Exchange Online in the Exchange admin center (EAC) to look for specific conditions in messages that pass through your organization and take action on them. The main difference between transport rules and Inbox rules you would set up in an email client application (such as Outlook) is that transport rules take action on messages while they're in transit as opposed to after the message is delivered. Transport rules also contain a richer set of conditions, exceptions, and actions, which provides you with the flexibility to implement many types of messaging policies.
  
 **Note** To learn more about transport rules, go to [Transport rules](https://go.microsoft.com/fwlink/?LinkId=798795).
  
- [Get started](use-screen-reader-to-configure-transport-rules-in-exchange-admin-center.md#BKMK_getstarted)
    
- [Create a transport rule](use-screen-reader-to-configure-transport-rules-in-exchange-admin-center.md#BKMK_transportrule)
    
## Get started
<a name="BKMK_getstarted"> </a>

Navigate with Internet Explorer and keyboard shortcuts, and make sure that you have the appropriate Office 365 subscription and admin role to perform this task. Then, open the EAC and get started.
  
### Use your browser and keyboard to navigate in the EAC

Exchange Online, which includes the EAC, is a web-based application, so the keyboard shortcuts and navigation may be different from those in Exchange 2016. [Accessibility in the Exchange admin center](accessibility-in-exchange-admin-center.md).
  
For best results when working in the EAC in Exchange Online, use Internet Explorer as your browser. [Learn more about Internet Explorer keyboard shortcuts](https://go.microsoft.com/fwlink/?LinkID=787614).
  
Many tasks in the EAC require the use of pop-up windows so, in your browser, be sure to [enable pop-up windows for Office 365](https://go.microsoft.com/fwlink/?LinkID=317550).
  
### Confirm your Office 365 subscription plan

Exchange Online is included in Office 365 business and enterprise subscription plans, but capabilities may differ by plan. If your EAC doesn't include a function described in this article, your plan might not include it.
  
For more information about the Exchange Online capabilities in your subscription plan, go to [What Office 36 business product or license do I have?](https://go.microsoft.com/fwlink/?LinkID=797552) and [Exchange Online Service Description](https://go.microsoft.com/fwlink/?LinkID=797553).
  
### Open the EAC, and confirm your admin role

To complete the tasks covered in this topic, [Use a screen reader to open the Exchange admin center](use-screen-reader-to-open-exchange-admin-center.md) and check that your Office 365 global administrator has assigned you to the [Organization Management](https://go.microsoft.com/fwlink/?LinkId=797868) and [Records Management](https://go.microsoft.com/fwlink/?LinkId=798797) admin role groups. Learn how to [Use a screen reader to identify your admin role in the Exchange admin center](use-screen-reader-to-identify-admin-role-in-exchange-admin-center.md).
  
## Create a transport rule
<a name="BKMK_transportrule"> </a>

1. In the EAC, to move the focus to the first link in the navigation pane— **Dashboard** —press Ctrl+F6  *twice*  . You hear "Dashboard, Primary navigation link." 
    
2. To move the focus to the **mail flow** link in the navigation pane, press the Tab key until you hear "Mail flow, Primary navigation link." Press Enter. 
    
3. To move the focus to the mail flow settings in the content area of the page, the first of which is the **rules** link, press Ctrl+F6. You hear "Rules, Secondary navigation link." 
    
4. To create a new rule, move the focus to the **New** button by pressing the Tab key until you hear "New button." Press Enter. You hear "Menu." To select the **Create a new rule** option from the list of options that opens for the button, press the Down Arrow key. You hear "Create a new rule." Press Enter. 
    
5. As the focus moves to the **Name** text box in the **new rule** pop-up window, you hear "New rule, Name, Edit." Type the name of the new rule. To move to the next option in the window, press the Tab key. 
    
6. As the focus moves to the **Apply this rule if** drop-down box, you hear "Apply this rule if, Combo box." Press the Down Arrow or Up Arrow key until you hear the condition you want to select. Press Enter. As the focus moves to the first user interface (UI) element in the pop-up window that opens for the selected condition, you hear the name of the pop-up window followed by the name of the first UI element in the window. The following table gives you an overview of the UI elements in each condition's pop-up window. 
    
    > [!TIP]
    > To move the focus to each setting that's listed in a pop-up window, press the Tab key. As you select each setting, you hear information about it. To open drop-down box lists, press Spacebar. To move between and select options in drop-down box lists, press the Down Arrow and Up Arrow keys. To choose an option, press Enter. You can also use the Spacebar to select or clear the selection for check boxes. 
  
    Each condition and the UI elements in its pop-up window
    
|**Condition**|**UI elements in the condition's pop-up window**|
|:-----|:-----|
| The sender is  <br/>  The recipient is  <br/>  The sender is a member of  <br/>  The recipient is a member of  <br/> |
Search, Refresh , and More  buttons Display Name  and Email Address  column headers List of names and email addresses Add  button and text box that includes the selected names Check names  button and text box in which you type the name you want to check OK  and Cancel  buttons |
| The sender is located  <br/>  The recipient is located  <br/> |
	Drop-down box that opens a list of locations OK  and Cancel  buttons |
| The subject or body includes  <br/>  The sender address includes  <br/>  The recipient address includes  <br/>  Any attachment's content includes  <br/> |
Edit  and Remove  buttons 	Text box in which you type words, and an Add  button to add each entry 	List of entries OK  and Cancel  buttons |
|[Apply to all messages]  <br/> |No pop-up window opens  <br/> |
   
7. After you've accepted your condition settings in the appropriate pop-up window, move to the next option in the ** new rule ** pop-up window by pressing the Tab key. 
    
8. As the focus moves to the **Do the following** drop-down box, you hear "Do the following, Combo box." Press the Down Arrow or Up Arrow key until you hear the action you want to select. Press Enter. As the focus moves to the first UI element in the pop-up window that opens for the selected action, you hear the name of the pop-up window followed by the name of the first UI element in the window. The following table gives you an overview of the UI elements in each action's pop-up window. 
    
    Each action and the UI elements in its pop-up window
    
|**Action**|**UI elements in the pop-up window**|
|:-----|:-----|
| Forward the message for approval to  <br/>  Redirect the message to  <br/>  Bcc the message to  <br/> |
Search, Refresh , and More  buttons Display Name  and Email Address  column headers List of names and email addresses Add  button and text box that includes the selected names Check names  button and text box in which you type the name you want to check OK  and Cancel  buttons |
|Reject the message with the explanation  <br/> |
Text box in which you type the explanation OK  and Cancel  buttons |
|Delete the message without notifying anyone  <br/> |No pop-up window opens  <br/> |
|Append the disclaimer  <br/> | No pop-up window opens, but an Enter text link and a Select one link are inserted in the window after the drop-down box  <br/>  If you select the **Enter text** link, a pop-up window opens that includes a text box in which you type the disclaimer, and the **OK** and **Cancel** buttons  <br/>  If you select the **Select one** link, a pop-up window opens that includes a drop-down box that opens a list of fallback actions in case the disclaimer can't be inserted, and the **OK** and **Cancel** buttons  <br/> |
   
9. After you've accepted your action settings in the appropriate pop-up window, move to the next option in the **new rule** pop-up window by pressing the Tab key. 
    
10. As the focus moves to the **Audit this rule with severity level** check box, you hear "Checked" or "Unchecked" depending on whether the box is selected or not, followed by "Audit this rule with severity level, Check box." To select or clear the selection for the check box, press Spacebar. You hear "Checked" or "Unchecked." Do either of the following two actions: 
    
  - If you selected the **Audit this rule with severity level** check box, when you press the Tab key, the focus moves to a drop-down box that lists severity levels ( **Low**, **Medium**, or **High** ). To move between severity levels in the list, press the Up Arrow or Down Arrow key. You hear the name of each severity level. To select a severity level, press Enter. To move to the next option in the window, press the Tab key. 
    
  - If you didn't select the ** Audit this rule with severity level ** check box, to move to the next available option in the window, press the Tab key. 
    
11. As the focus moves to the first of three available modes for the rule, you hear the name of the first mode ( **Enforce** ) followed by "Radio button." Do any of the following three actions: 
    
  - The **Enforce** mode is selected by default. To move to and select the next mode, press the Down Arrow key. After you've selected the mode you want, to move to the next area of options in the window, press the Tab key. 
    
  - To select the **Test with Policy Tips** mode, press the Down Arrow key. You hear "Test with Policy Tips" followed by "Radio button." To move to and select the next mode, press the Down Arrow key. After you've selected the mode you want, to move to the next area of options in the window, press the Tab key. 
    
  - To select the **Test without Policy Tips** mode, press the Down Arrow key. You hear "Test without Policy Tips" followed by "Radio button." To move to and select the next mode, press the Down Arrow key. After you've selected the mode you want, to move to the next area of options in the window, press the Tab key. 
    
12. As the focus moves to the **More options** link, you hear "More options link." If you want to add more options for the rule, press Enter. The following nine UI elements are added to the window: 
    
  - After the **Apply this rule if** drop-down box, an **add condition** button is added. 
    
  - After the **Do the following** drop-down box, an **add action** button is added. 
    
  - After the **add action** button, an **add exception** button is added. 
    
  - After the options for the modes for the rule, the following UI elements are added:
    
  - **Activate this rule on the following date** check box, followed by a date drop-down box and a time drop-down box 
    
  - **Deactivate this rule on the following date** check box, followed by a date drop-down box and a time drop-down box 
    
  - **Stop processing more rules** check box 
    
  - **Defer the message if rule processing doesn't complete** check box 
    
  - **Match sender address in message** drop-down box that includes **Header**, **Envelope**, and **Header or Envelope** options 
    
  - **Comment** text box 
    
13. To save the new rule, move the focus to the **Save** button by pressing the Tab key until you hear "Save button." Press Enter. 
    
14. As the focus moves back to the **New** button on the ** rules ** content area of the page, you hear "Rules, New button." The new rule is turned on by default. 
    
    > [!TIP]
    > To turn off a new rule, press the Tab key to tab through the elements of the **rules** content area of the page, use the Up Arrow and Down Arrow keys to select a rule, and then press Spacebar. To hear the settings for a selected rule, press the Tab key until the focus moves to the details pane for the selected rule, and you hear the details for the rule. 
  

