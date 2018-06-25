---
title: "Manage mail flow rules"
ms.author: chrisda
author: chrisda
manager: scotv
ms.date: 6/23/2018
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: e7a81372-b6d7-4d1f-bc9e-a845a7facac2
description: "You can use mail flow rules, also known as transport rules, to look for specific conditions on messages that pass through your organization and take action on them. This topic shows you how to create, copy, adjust the order, enable or disable, delete, or import or export rules, and how to monitor rule usage."
---

# Manage mail flow rules

You can use mail flow rules, also known as transport rules, to look for specific conditions on messages that pass through your organization and take action on them. This topic shows you how to [create](#create.md), [copy](#create.md), [adjust the order](#priority.md), [enable or disable](#enable.md), [delete](#remove.md), or [import or export](#import.md) rules, and how to [monitor rule usage](#monitor.md).
  
> [!TIP]
> To make sure your rules work the way you expect, be sure to thoroughly test each rule and interactions between rules. 
  
Interested in scenarios where these procedures are used? See the following topics:
  
- **Organization-wide disclaimers, signatures, footers, or headers in Exchange 2013**
    
- **Use transport rules to inspect message attachments in Exchange 2013**
    
- [Common attachment blocking scenarios for mail flow rules](common-attachment-blocking-scenarios.md)
    
- [Use mail flow rules to route email based on a list of words, phrases, or patterns](use-rules-to-route-email.md)
    
- [Common message approval scenarios](common-message-approval-scenarios.md)
    
- [Use mail flow rules so messages can bypass Clutter](use-rules-to-bypass-clutter.md)
    
- [Best practices for configuring mail flow rules](configuration-best-practices.md)
    
- [Use mail flow rules to inspect message attachments in Office 365](inspect-message-attachments.md)
    
- **Use transport rules to configure bulk email filtering**
    
- [Define rules to encrypt or decrypt messages](https://go.microsoft.com/fwlink/p/?Linkid=402846)
    
- **Create organization-wide safe sender or blocked sender lists in Office 365**
    
## What do you need to know before you begin?

- Estimated time to complete each procedure: 5 minutes.
    
- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Transport rules" entry in [Messaging policy and compliance permissions](http://technet.microsoft.com/library/ec4d3b9f-b85a-4cb9-95f5-6fc149c3899b.aspx) (Exchange Server), or in [Feature permissions in Exchange Online](../../permissions/feature-permissions.md). 
    
- When a rule is listed as **version 14**, this means that the rule is based on an Exchange Server 2010 mail flow rule format. All options are available for these rules.
    
- For information about keyboard shortcuts that may apply to the procedures in this topic, see **Keyboard shortcuts in the Exchange admin center**.
    
> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612),[Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351). 
  
## What do you want to do?

### Create a mail flow rule
<a name="Create"> </a>

You can create a mail flow rule by setting up a Data Loss Prevention (DLP) policy, creating a new rule, or by copying a rule. You can use the Exchange admin center (EAC) or the Exchange Management Shell.
  
> [!NOTE]
> After you create or modify a mail flow rule, it can take up to 30 minutes for the new or updated rule to be applied to email. 
  
#### Use a DLP policy to create mail flow rules

Each DLP policy is a collection of mail flow rules. After you create the DLP policy, you can fine-tune the rules using the procedures below.
  
1. Create a DLP policy. For instructions, see:
    
  - [Exchange Server 2013 DLP Procedures](http://technet.microsoft.com/library/e2f575aa-552e-4dcc-8d7b-1ffd697d67df%28Office.14%29.aspx)
    
  - [Exchange Online DLP procedures](http://technet.microsoft.com/library/e2f575aa-552e-4dcc-8d7b-1ffd697d67df%28Office.14%29.aspx)
    
2. Modify the mail flow rules created by the DLP policy. See [View or modify a mail flow rule](manage-mail-flow-rules.md#ModifyRule).
    
#### Use the EAC to create a mail flow rule
<a name="CreateEAC"> </a>

The EAC allows you to create mail flow rules by using a template, copying an existing rule, or from scratch. 
  
1. Go to **Mail flow** \> **Rules**. 
    
2. Create the rule by using one of the following options:
    
  - To create a rule from a template, click **Add**![Add Icon](../../media/ITPro_EAC_AddIcon.gif) and select a template. 
    
  - To copy a rule, select the rule, and then select **Copy**![Copy Icon](../../media/ITPro_EAC_CopyIcon.gif).
    
  - To create a new rule from scratch, **Add**![Add Icon](../../media/ITPro_EAC_AddIcon.gif) and then select **Create a new rule**.
    
3. In the **New rule** dialog box, name the rule, and then select the conditions and actions for this rule: 
    
1. In **Apply this rule if…**, select the condition you want from the list of available conditions. 
    
  - Some conditions require you to specify values. For example, if you select **The sender is…** condition, you must specify a sender address. If you're adding a word or phrase, note that trailing spaces are not allowed. 
    
  - If the condition you want isn't listed, or if you need to add exceptions, select **More options**. Additional conditions and exceptions will be listed.
    
  - If you don't want to specify a condition, and want this rule to apply to every message in your organization, select **[Apply to all messages]** condition. 
    
2. In **Do the following…**, select the action you want the rule to take on messages matching the criteria from the list of available actions. 
    
  - Some of the actions will require you to specify values. For example, if you select the **Forward the message for approval to…** condition, you will need to select a recipient in your organization. 
    
  - If the condition you want isn't listed, select **More options**. Additional conditions will be listed.
    
3. Specify how rule match data for this rule is displayed in the [Data Loss Prevention (DLP) reports](https://go.microsoft.com/fwlink/p/?LinkId=402768) and the [transport rule reports](https://go.microsoft.com/fwlink/p/?LinkId=402769). 
    
  - Under **Audit this rule with severity level**, select a level to specify the severity level for this rule. The Office 365 activity reports for mail flow rules group rule matches by severity level. Severity level is just a filter to make the reports easier to use. The severity level has no impact on the priority in which the rule is processed.
    
    > [!NOTE]
    > If you clear the **Audit this rule with severity level** checkbox, rule matches will not show up in the rule reports. 
  
4. Set the mode for the rule. You can use one of the two test modes to test the rule without impacting mail flow. In both test modes, when the conditions are met, an entry is added to the message trace. 
    
  - **Enforce** This turns on the rule and it starts processing messages immediately. All actions on the rule will be performed. 
    
  - **Test with Policy Tips** This turns on the rule, and any Policy Tip actions ( **Notify the sender with a Policy Tip**) will be sent, but no actions related to message delivery will be performed. Data Loss Prevention (DLP) is required in order to use this mode. To learn more, see [Policy Tips](../../security-and-compliance/data-loss-prevention/policy-tips.md).
    
  - **Test without Policy Tips** Only the Generate incident report action will be enforced. No actions related to message delivery are performed. 
    
4. If you are satisfied with the rule, go to step 5. If you want to add more conditions or actions, or if you want to specify exceptions or set additional properties, click **More options**. After you click **More options**, complete the following fields to create your rule:
    
1. To add more conditions, click **Add condition**. If you have more than one condition, you can remove any one of them by clicking **Remove X** next to it. Note that there are a larger variety of conditions available once you click **More options**.
    
2. To add more actions, click **Add action**. If you have more than one action, you can remove any one of them by clicking **Remove X** next to it. Note that there are a larger variety of actions available once you click **More options**.
    
3. To specify exceptions, click **Add exception**, then select exceptions using the **Except if...** dropdown. You can remove any exceptions from the rule by clicking the **Remove X** next to it. 
    
4. If you want this rule to take effect after a certain date, click **Activate this rule on the following date:** and specify a date. Note that the rule will still be enabled prior to that date, but it won't be processed. 
    
    Similarly, you can have the rule stop processing at a certain date. To do so, click **Deactivate this rule on the following date:** and specify a date. Note that the rule will remain enabled, but it won't be processed. 
    
5. You can choose to avoid applying additional rules once this rule processes a message. To do so, click **Stop processing more rules**. If you select this, and a message is processed by this rule, no subsequent rules are processed for that message.
    
6. You can specify how the message should be handled if the rule processing can't be completed. By default, the rule will be ignored and the message will be processed regularly, but you can choose to resubmit the message for processing. To do so, check the **Defer the message if rule processing doesn't complete** check box. 
    
7. If your rule analyzes the sender address, it only examines the message headers by default. However, you can configure your rule to also examine the SMTP message envelope. To specify what's examined, click one of the following values for **Match sender address in message**:
    
  - **Header** Only the message headers will be examined. 
    
  - **Envelope** Only the SMTP message envelope will be examined. 
    
  - **Header or envelope** Both the message headers and SMTP message envelope will be examined. 
    
8. You can add comments to this rule in the **Comments** box. 
    
5. Click **Save** to complete creating the rule. 
    
#### Use the Exchange Management Shell to create a mail flow rule
<a name="CreateEAC"> </a>

This example uses the [New-TransportRule](http://technet.microsoft.com/library/eb3546bf-ca37-474e-9c22-962fe95af276.aspx) cmdlet to create a new mail flow rule that prepends "  `External message to Sales DG:`" to messages sent from outside the organization to the Sales Department distribution group.
  
```
New-TransportRule -Name "Mark messages from the Internet to Sales DG" -FromScope NotInOrganization -SentTo "Sales Department" -PrependSubject "External message to Sales DG:"
```

The rule parameters and action used in the above procedure are for illustration only. Review all the available mail flow rule conditions and actions to determine which ones meet your requirements.
  
#### How do you know this worked?
<a name="CreateEAC"> </a>

To verify that you have successfully created a new mail flow rule, do the following:
  
- From the EAC, verify that the new mail flow rule you created is listed in the **Rules** list. 
    
- From the Exchange Management Shell, verify that you created the new mail flow rule successfully by running the following command (the example below verifies the rule created in the Exchange Management Shell example above):
    
  ```
  Get-TransportRule "Mark messages from the Internet to Sales DG"
  ```

### View or modify a mail flow rule
<a name="ModifyRule"> </a>

> [!NOTE]
> After you create or modify a mail flow rule, it can take up to 30 minutes for the new or updated rule to be applied to email. 
  
#### Use the EAC to view or modify a mail flow rule

1. From the EAC, go to **Mail flow** \> **Rules**.
    
2. When you select a rule in the list, the conditions, actions, exceptions and select properties of that rule are displayed in the details pane. To view all the properties of a specific rule, double click it. This opens the rule editor window, where you can make changes to the rule. For more information about rule properties, see [Use the EAC to create a mail flow rule](manage-mail-flow-rules.md#CreateEAC) section, earlier in this topic. 
    
#### Use the Exchange Management Shell to view or modify a mail flow rule

The following example gives you a list of all rules configured in your organization:
  
```
Get-TransportRule
```

To view the properties of a specific mail flow rule, you provide the name of that rule or its GUID. It is usually helpful to send the output to the **Format-List** cmdlet to format the properties. The following example returns all the properties of the mail flow rule named Sender is a member of Marketing:
  
```
Get-TransportRule "Sender is a member of marketing" | Format-List
```

To modify the properties of an existing rule, use the [Set-TransportRule](http://technet.microsoft.com/library/8328125b-e166-436f-95e6-1afafdbdb89a.aspx) cmdlet. This cmdlet allows you to change any property, condition, action or exception associated with a rule. The following example adds an exception to the rule "Sender is a member of marketing" so that it won't apply to messages sent by the user Kelly Rollin: 
  
```
Set-TransportRule "Sender is a member of marketing" -ExceptIfFrom "Kelly Rollin"
```

#### How do you know this worked?

To verify that you have successfully modified a mail flow rule, do the following:
  
- From the rules list in the EAC, click the rule you modified in the **Rules** list and view the details pane. 
    
- From the Exchange Management Shell, verify that you modified the mail flow rule successfully by running the following command to list the properties you modified along with the name of the rule (the example below verifies the rule modified in the Exchange Management Shell example above):
    
  ```
  Get-TransportRule "Sender is a member of marketing" | Format-List Name,ExceptIfFrom
  ```

### Mail flow rule properties
<a name="ModifyRule"> </a>

You can also use the Set-TransportRule cmdlet to modify existing transport rules in your organization. Below is a list properties not available in the EAC that you can change. For more information on using the Set-TransportRule cmdlet to make these changes see [Set-TransportRule](http://technet.microsoft.com/library/8328125b-e166-436f-95e6-1afafdbdb89a.aspx)
  
|**Condition Name in the EAC**|**Condition name in Exchange Management Shell**|**Properties**|**Description**|
|:-----|:-----|:-----|:-----|
|**Stop Processing Rules** <br/> | `StopRuleProcessing` <br/> | ` Not applicable ` <br/> |Enables you to stop processing additional rules  <br/> |
|**Header/Envelope matching** <br/> | `SenderAddressLocation` <br/> |Not applicable  <br/> |Enables you to examine the SMTP message envelope to ensure the header and envelop match  <br/> |
|**Audit severity ** <br/> | `SetAuditSeverity` <br/> | `Not applicable` <br/> |Enables you to select a severity level for the audit  <br/> |
|**Rule modes** <br/> | `Mode` <br/> | `Not applicable` <br/> |Enables you to set the mode for the rule  <br/> |
   
### Set the priority of a mail flow rule
<a name="priority"> </a>

The rule at the top of the list is processed first. This rule has a **Priority** of 0. 
  
#### Use the EAC to set the priority of a rule

1. From the EAC, go to **Mail flow** \> **Rules**. This displays the rules in the order in which they are processed.
    
2. Select a rule, and use the arrows to move the rule up or down the list.
    
#### Use the Exchange Management Shell to set the priority of a rule

The following example sets the priority of "Sender is a member of marketing" to 2:
  
```
Set-TransportRule "Sender is a member of marketing" priority "2"
```

#### How do you know this worked?

To verify that you have successfully modified a mail flow rule, do the following:
  
- From the rules list in the EAC, look at the order of the rules.
    
- From the Exchange Management Shell, verify the priority of the rules (the example below verifies the rule modified in the Exchange Management Shell example above):
    
  ```
  Get-TransportRule * | Format-List Name,Priority
  ```

### Enable or disable a mail flow rule
<a name="enable"> </a>

Rules are enabled when you create them. You can disable a mail flow rule.
  
#### Use the EAC to enable or disable a mail flow rule

1. From the EAC, go to **Mail flow** \> **Rules**. 
    
2. To disable a rule, clear the check box next to its name.
    
3. To enable a disabled rule, select the check box next to its name.
    
#### Use the Exchange Management Shell to enable or disable a mail flow rule

The following example disables the mail flow rule "Sender is a member of marketing":
  
```
Disable-TransportRule "Sender is a member of marketing"
```

The following example enables the mail flow rule "Sender is a member of marketing":
  
```
Enable-TransportRule "Sender is a member of marketing"
```

#### How do you know this worked?

To verify that you have successfully enabled or disabled a mail flow rule, do the following:
  
- From the EAC, view the list of rules in the **Rules** list and check the status of the check box in the **ON** column. 
    
- From the Exchange Management Shell, run the following command which will return a list of all rules in your organization along with their status:
    
  ```
  Get-TransportRule | Format-Table Name,State
  ```

### Remove a mail flow rule
<a name="remove"> </a>

#### Use the EAC to remove a mail flow rule

1. From the EAC, go to **Mail flow** \> **Rules**. 
    
2. Select the rule you want to remove and then click **Delete**![Delete icon](../../media/ITPro_EAC_DeleteIcon.gif). 
    
#### Use the Exchange Management Shell to remove a mail flow rule

The following example removes the mail flow rule "Sender is a member of marketing":
  
```
Remove-TransportRule "Sender is a member of marketing"
```

#### How do you know this worked?

To verify that you have successfully removed the mail flow rule, do the following:
  
- From the EAC, view the rules in the **Rules** list and verify that the rule you removed is no longer shown. 
    
- From the Exchange Management Shell, run the following command and verify that the rule you remove is no longer listed:
    
  ```
  Get-TransportRule
  ```

### Monitor rule usage
<a name="monitor"> </a>

If you're using Exchange Online or Exchange Online Protection, you can check the number of times each rule is matched by using a rules report. In order to be included in the reports, a rule must have the **Audit this rule with severity level** check box selected. You can look at a report online, or download an Excel version of all the mail protection reports. 
  
> [!NOTE]
> While most data is in the report within 24 hours, some data may take as long as 5 days to appear. 
  
#### Use the Office 365 admin center to generate a rules report

1. In the Office 365 admin center, select **Reports**.
    
2. In the **Rules** section, select **Top rule matches for mail** or **Rule matches for mail**.
    
To learn more, see [View mail protection reports](https://go.microsoft.com/fwlink/p/?LinkId=402958).
  
#### Download an Excel version of the reports

1. On the Reports page in the Office 365 admin center, select **Mail protection reports (Excel)**.
    
2. If it is your first time using the Excel mail protection reports, a tab opens to the download page. 
    
1. Select **Download** to download the Microsoft Office 365 Excel Plugin for Exchange Online Reporting. 
    
2. Open the download.
    
3. In the **Mail Protection reports for Office 365 Setup** dialog box, select **Next**, accept the terms of the license agreement, and then select **Next**.
    
4. Select the service you are using, and then select **Next**.
    
5. Verify the prerequisites, and then select **Next**.
    
6. Select **Install**. A shortcut to the reports is placed on your desktop.
    
3. On your desktop, select **Office 365 Mail Protection Reports**.
    
4. In the report, select the **Rules** tab. 
    
### Import or export a mail flow rule collection
<a name="import"> </a>

You must use the Exchange Management Shell to import or export a mail flow rule collection. For information about how to import a mail flow rule collection from an XML file, see [Import-TransportRuleCollection](http://technet.microsoft.com/library/880b3124-76c5-4212-a8b9-8f4523f8cbe6.aspx). For information about how to export a mail flow rule collection to an XML file, see [Export-TransportRuleCollection](http://technet.microsoft.com/library/bfdb6ced-cd81-49f1-a929-4d76dbaf5590.aspx).
  
## Need more help?

Resources for Exchange Online:
  
[Mail flow rules (transport rules) in Exchange Online](mail-flow-rules.md)
  
[Mail flow rule conditions and exceptions (predicates) in Exchange Online](conditions-and-exceptions.md)
  
[Mail flow rule actions in Exchange Online](mail-flow-rule-actions.md)
  
[Transport and inbox rule limits](https://go.microsoft.com/fwlink/p/?LinkId=324584)
  
Resources for Exchange Online Protection: 
  
[Transport rules](http://technet.microsoft.com/library/9c2cf227-eff7-48ef-87fb-487186e47363.aspx)
  
[Transport Rule Conditions](http://technet.microsoft.com/library/04edeaba-afd4-4207-b2cb-51bcc44e483c.aspx)
  
[Transport Rule Actions](http://technet.microsoft.com/library/f8621ecb-a177-4025-9011-a6569999746a.aspx)
  
[Transport and inbox rule limits](https://go.microsoft.com/fwlink/p/?LinkId=324584)
  
Resources for Exchange Server 2016:
  
[Transport Rules](http://technet.microsoft.com/library/c3d2031c-fb7b-4866-8ae1-32928d0138ef.aspx)
  
[Transport Rule Conditions](http://technet.microsoft.com/library/c918ea00-1e68-4b8b-8d51-6966b4432e2d.aspx)
  
[Transport Rule Actions](http://technet.microsoft.com/library/5d11a955-b1cc-4150-a0b9-a8cc48ba9bde.aspx)
  

