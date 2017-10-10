---
title: Procedures for mail flow rules in Exchange 2016
ms.prod: EXCHANGE
ms.assetid: e7a81372-b6d7-4d1f-bc9e-a845a7facac2
---


# Procedures for mail flow rules in Exchange 2016
Learn how to create, view, modify, delete, import, and export mail flow rules (transport rules) in Exchange 2016.
Mail flow rules (also known as transport rules) identify and take action on messages that flow through your Exchange organization. For more information about mail flow rules, see  [Mail flow rules in Exchange 2016](mail-flow-rules-in-exchange-2016.md).
  
    
    

On Mailbox servers, you can manage mail flow rules in the Exchange admin center (EAC) and in the Exchange Management Shell. On Edge Transport servers, you can only use the Exchange Management Shell.
> [!TIP]
> Verify that your rules work the way you expect. Be sure to thoroughly test each rule and the interactions between rules. 
  
    
    


## What do you need to know before you begin?


- Estimated time to complete each procedure: 5 minutes.
    
  
- For more information about the EAC, see  [Exchange admin center in Exchange 2016](exchange-admin-center-in-exchange-2016.md). To learn how to open the Exchange Management Shell in your on-premises Exchange organization, see **Open the Exchange Management Shell**.
    
  
- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Transport rules" entry in  [Messaging policy and compliance permissions in Exchange 2016](messaging-policy-and-compliance-permissions-in-exchange-2016.md) (Exchange Server), or in [Feature Permissions in Exchange Online](http://technet.microsoft.com/library/15073ce1-0917-403b-8839-02a2ebc96e16.aspx).
    
  
- For information about keyboard shortcuts that may apply to the procedures in this topic, see  [Keyboard shortcuts in the Exchange admin center](keyboard-shortcuts-in-the-exchange-admin-center.md).
    
  

> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at:  [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612),  [Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or  [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351). 
  
    
    


## What do you want to do?


### Create mail flow rules
<a name="Create"> </a>


- Creating mail flow rules is mostly about the scenarios that you want to fulfill. For examples, see the following topics:
    
  -  [Use mail flow rules to inspect message attachments](http://technet.microsoft.com/library/c0de687e-e33c-4e8a-b253-771494678795.aspx)
    
  
  -  [Add an Email Disclaimer, Legal Disclaimer, Common Signature, or Email Footer or Header](http://technet.microsoft.com/library/29ac61c2-77f1-4071-b14e-8cc64e3e76ba.aspx)
    
  
  -  [Manage message approval in Exchange Server 2016](http://technet.microsoft.com/library/43a89f71-8002-4cb0-b3c8-1c2b2597f227.aspx)
    
  
- Data Loss Prevention (DLP) policies are collections of mail flow rules. To create DLP policies, see  [Exchange Server 2016 DLP Procedures](http://technet.microsoft.com/library/e2f575aa-552e-4dcc-8d7b-1ffd697d67df%28Office.14%29.aspx).
    
  

#### Use the EAC to create mail flow rules
<a name="CreateEAC"> </a>

The EAC allows you to create mail flow rules by using a template (a filtered list of conditions and actions), by copying an existing rule, or by creating a rule from scratch.
  
    
    

1. In the EAC, go to **Mail flow** > **Rules**, and then select one of the following options:
    
  - To create a rule from a template, click **Add** (
  
    
    
![Add icon](images/ITPro_EAC_AddIcon.png)
  
    
    
) and select a template (a value other than **Create new rule**).
    
  
  - To copy a rule, select the rule, and then select **Copy** (
  
    
    
![Copy icon](images/ITPro_EAC_CopyIcon.png)
  
    
    
). Note that the option to copy a rule is only available in the EAC.
    
  
  - To create a new rule from scratch, **Add** (
  
    
    
![Add icon](images/ITPro_EAC_AddIcon.png)
  
    
    
) and then select **Create a new rule**.
    
  
2. In the **New rule** page that opens, configure the following settings:
    
  - **Name** Enter a unique, descriptive name for the rule.
    
  
  - **Apply this rule if** Select a condition for the rule. If you want the rule to apply to all messages, select **[Apply to all messages]**. For an explanation of the available conditions, see  [Mail flow rule conditions and exceptions (predicates) in Exchange 2016](mail-flow-rule-conditions-and-exceptions-predicates-in-exchange-2016.md).
    
  
  - **Do the following**, Select an action for the rule. The action is applied to messages that match the conditions. For an explanation of the available conditions, see  [Mail flow rule actions in Exchange 2016](mail-flow-rule-actions-in-exchange-2016.md).
    
    Optional properties:
    
  
  - **Audit this rule with severity level** For DLP policies, this setting specifies how rule match data is displayed in the DLP policy detection reports. For more information, [View DLP policy detection reports](http://technet.microsoft.com/library/84295dda-5bf7-4fa5-a1ee-3f761501cfe8.aspx). If you clear the check box, or select the value **Not specified**, rule matches won't appear in the rule reports.
    
  
  - **Choose a mode for this rule** You can use one of the two test modes to test the rule without impacting mail flow. In both test modes, when the conditions are met, an entry is added to the message tracking log. Select one of the following values:
    
  - **Enforce** This turns on the rule and it starts processing messages immediately. All actions on the rule will be performed. This is the default value.
    
  
  - **Test with Policy Tips** This turns on the rule, and any Policy Tip actions ( **Notify the sender with a Policy Tip**) will be sent, but no actions related to message delivery will be performed. DLP is required to use this mode. To learn more, see  [Policy Tips](http://technet.microsoft.com/library/4266b83c-dd8a-4b3d-99ff-402e68fc810c.aspx).
    
  
  - **Test without Policy Tips** For DLP policies, only the **Generate incident report and send it to** action will be enforced. No actions related to message delivery are performed.
    
  
3. You can create the rule by clicking **Save**, or you can click **More options** to configure the following additional settings:
    
  - To add more conditions, click **Add condition**. If you have more than one condition, you can remove a condition by clicking **Remove X**. Note that there are more conditions available after you click **More options**.
    
  
  - To add more actions, click **Add action**. If you have more than one action, you can remove an action by clicking **Remove X**. Note that there are more actions available after you click **More options**.
    
  
  - To add exceptions for the rule, click **Add exception**, and then select an exception by using the **Except if** drop down. You can remove an exception by clicking **Remove X**.
    
  
  - **Activate this rule on the following date** Specify the start date if you want the rule to take effect after a certain date. Note that the rule will still be enabled prior to that date, but it won't be processed.
    
  
  - **Deactivate this rule on the following date** Specify the end date if you want the rule to stop processing messages on a certain date. Note that the rule will still be enabled after that date, but it won't be processed.
    
  
  - **Stop processing more rules** Select this check box to avoid applying additional rules after this rule processes a message.
    
  
  - **Defer the message if rule processing doesn't complete** Select this check box to resubmit the message for processing. By default, the rule will be ignored, and delivery of the message will continue as normal.
    
  
  - **Match sender address in message** For conditions and exceptions that examine the sender's address, you can specify where the rule looks for the sender's address: in the message header (default), the message envelope, or the header and envelope. For more information, see [Senders](mail-flow-rule-conditions-and-exceptions-predicates-in-exchange-2016.md#Senders).
    
  
  - **Comments** Specify a descriptive comment for the rule.
    
  

    When you're finished, click **Save**.
    
  

#### Use the Exchange Management Shell to create mail flow rules
<a name="CreateEAC"> </a>

There are two settings that you can configure on new mail flow rules in the Exchange Management Shell that aren't available in the EAC (until after you create the rule):
  
    
    

- Create the new rule as disabled ( _Enabled_ `$false`)
    
  
- Set the priority of the rule ( _Priority_ _<Number>_).
    
  
To create mail flow rules in the Exchange Management Shell, use the following syntax:
  
    
    



```

New-TransportRule -Name <RuleName> [<Conditions>] [<Exceptions>] <Actions> [<Properties>]
```

This example creates a new rule with the following settings:
  
    
    

- **Name** Mark messages from the Internet to Sales DG.
    
  
- **Conditions**
    
  - Messages from external senders.
    
    And
    
  
  - Messages sent to the distribution group named Sales Department.
    
  
- **Action** Prepend the message's **Subject** field with the value `"External message to Sales DG: "`. The trailing colon and space help to distinguish the added text from the original value.
    
  



```
New-TransportRule -Name "Mark messages from the Internet to Sales DG" -FromScope NotInOrganization -SentTo "Sales Department" -PrependSubject "External message to Sales DG: "
```

For detailed syntax and parameter information, see  [New-TransportRule](http://technet.microsoft.com/library/eb3546bf-ca37-474e-9c22-962fe95af276.aspx).
  
    
    
 **Note**: The conditions and actions in the example are for illustrative purposes only. Review the available mail flow rule conditions, exceptions, and actions to determine which ones meet your requirements.
  
    
    

#### How do you know this worked?
<a name="CreateEAC"> </a>

To verify that you've successfully created a mail flow rule, use either of the following procedures:
  
    
    

- In the EAC, go to **Mail flow** > **Rules**, and verify that the rule you created is in the list.
    
  
- In the Exchange Management Shell, use either of the following procedures:
    
  - Run the following command to see the new rule in the list of rules:
    
  ```
  Get-TransportRule
  ```

  - Replace  _<RuleName>_ with the name of the rule, and run the following command to see the details of the rule:
    
  ```
  Get-TransportRule -Identity "<RuleName>" | Format-List
  ```


### View mail flow rules
<a name="Create"> </a>

Mail flow rules that you create on a Mailbox server are stored in Active Directory, so when you view the rules on a Mailbox server, you see all rules in your organization. When you use the Exchange Management Shell to view mail flow rules on an Edge Transport server, you see the rules that are stored on the local server.
  
    
    

#### Use the EAC to view mail flow rules


1. In the EAC, go to **Mail flow** > **Rules**.
    
  
2. When you select a rule, information about the rule is displayed in the details pane. To see more information about the rule, click **Edit** (
  
    
    
![Edit icon](images/ITPro_EAC_EditIcon.png)
  
    
    
).
    
     ![In the EAC, go to Mail flow > Rules and select a rule](images/37502067-8f3f-49d1-aaea-91c7f3eb8e8a.png)
  

    In the EAC, the **Version** property is only visible in the details pane. This property indicates the compatibility of the rule with previous versions of Exchange (14. *n*  . *n*  . *n*  is Exchange 2010, 15.0. *n*  . *n*  is Exchange 2013).
    
  

#### Use the Exchange Management Shell to view mail flow rules

To return a summary list of all mail flow rules, run the following command:
  
    
    

```
Get-TransportRule
```

To return detailed information about a specific rule, use the following syntax:
  
    
    



```
Get-TransportRule -Identity "<RuleName>" | Format-List [<Specific properties to view>]
```

This example returns all the property values for the rule named "Sender is a member of marketing".
  
    
    



```
Get-TransportRule -Identity "Sender is a member of marketing" | Format-List
```

This example returns only the specified properties for the same rule.
  
    
    



```
Get-TransportRule -Identity "Sender is a member of marketing" | Format-List Name,State,Mode,Priority,Comments,Conditions,Exceptions,RuleVersion
```

For detailed syntax and parameter information, see  [Get-TransportRule](http://technet.microsoft.com/library/63a14c30-331d-458b-91d1-71d28a6e3d5a.aspx).
  
    
    

#### Use the Exchange Management Shell to view the available conditions and exceptions (predicates) for mail flow rules

The conditions and exceptions in mail flow rules are collectively known as predicates because for every condition, there's a corresponding exception that uses the exact same settings and syntax. The only difference is: conditions specify messages to include, while exceptions specify messages to exclude. You can only view the list of conditions and exceptions in the Exchange Management Shell.
  
    
    
To view the conditions and exceptions that are available in mail flow rules, run the following command:
  
    
    



```
Get-TransportRulePredicate
```

For detailed syntax and parameter information, see  [Get-TransportRulePredicate](http://technet.microsoft.com/library/3054220d-0973-4832-840e-b9ef9e7c9064.aspx).
  
    
    
 **Notes**:
  
    
    

- Exceptions aren't distinguished from conditions.
    
  
- The predicates that are available on Edge Transport servers are a small subset of those available on Mailbox servers. For more information, see  [Mail flow rule conditions and exceptions (predicates) in Exchange 2016](mail-flow-rule-conditions-and-exceptions-predicates-in-exchange-2016.md).
    
  
- Some of the predicate names are different than the corresponding condition and exception parameter names on the **New-TransportRule** and **Set-TransportRule** cmdlets. And, some predicates require multiple parameters.
    
  

#### Use the Exchange Management Shell to view the available actions for mail flow rules

 You can only view the list of actions in the Exchange Management Shell.
  
    
    
To view the actions that are available in mail flow rules, run the following command:
  
    
    



```
Get-TransportRuleAction
```

For detailed syntax and parameter information, see  [Get-TransportRuleAction](http://technet.microsoft.com/library/60829f04-94a0-4228-a66c-f467aaca438b.aspx).
  
    
    
 **Notes**:
  
    
    

- A small subset of actions that are available on Mailbox servers are also available on Edge Transport servers, but some actions are only available on Edge Transport servers. For more information, see  [Mail flow rule actions in Exchange 2016](mail-flow-rule-actions-in-exchange-2016.md).
    
  
- Some of the action names are different than the corresponding action parameter names on the **New-TransportRule** and **Set-TransportRule** cmdlets. And, some actions require multiple parameters.
    
  

### Modify mail flow rules
<a name="ModifyRule"> </a>


#### Use the EAC to modify mail flow rules

No additional settings are available when you modify a mail flow rule in the EAC. They're the same settings that were available when you created the rule.
  
    
    

1. In the EAC, go to **Mail flow** > **Rules**.
    
  
2. Select the rule, and then click **Edit** (
  
    
    
![Edit icon](images/ITPro_EAC_EditIcon.png)
  
    
    
). Note that the properties of the rule are fully expanded (there's no **More options** link available). For more information about the rule properties, see the [Use the EAC to create mail flow rules](procedures-for-mail-flow-rules-in-exchange-2016.md#CreateEAC) section in this topic.
    
  

#### Use the Exchange Management Shell to modify mail flow rules

When you modify a mail flow rule in the Exchange Management Shell, you can't disable or enable the rule (there's no  _Enabled_ parameter on the **Set-TransportRule** cmdlet). Instead, you use the **Disable-TransportRule** and **Enable-TransportRule** cmdlets as describe later in this topic.
  
    
    
To modify a mail flow rule in the Exchange Management Shell, use the following syntax:
  
    
    



```
Set-MailFlowRule -Identity "<RuleName>" [<Conditions>] [<Exceptions>] [<Actions>] [<Properties>]
```

This example adds an exception to the rule named "Sender is a member of marketing" so that it won't apply to messages that are sent by the user named Kelly Rollin.
  
    
    



```
Set-TransportRule -Identity "Sender is a member of marketing" -ExceptIfFrom "Kelly Rollin"
```

For detailed syntax and parameter information, see  [Set-TransportRule](http://technet.microsoft.com/library/8328125b-e166-436f-95e6-1afafdbdb89a.aspx).
  
    
    

#### How do you know this worked?

To verify that you have successfully modified a mail flow rule, use either of the following procedures:
  
    
    

- In the EAC, go to **Mail flow** > **Rules**, select the rule, and view the information in details pane. To see more settings, click **Edit** (
  
    
    
![Edit icon](images/ITPro_EAC_EditIcon.png)
  
    
    
).
    
  
- In the Exchange Management Shell, replace  _<RuleName>_ with the name of the rule, and run the following command:
    
  ```
  Get-TransportRule -Identity "<RuleName>" | Format-List
  ```


### Set the priority of mail flow rules
<a name="priority"> </a>

By default, mail flow rules are given a priority that's based on the order they were created in (newer rules are lower priority than older rules). A lower priority number indicates a higher priority for the rule, and rules are processed in priority order (higher priority rules are processed before lower priority rules). No two rules can have the same priority.
  
    
    
 **Notes**:
  
    
    

-  You can prevent a message from being acted on by subsequent lower priority rules by including the **Stop processing more rules** ( _StopRuleProcessing_ `$true`) action in the rule.
    
  
- In the EAC, you can only change the priority of the rule after you create it. In the Exchange Management Shell, you can override the default priority when you create the rule (which can affect the priority of existing rules).
    
  

#### Use the EAC to set the priority of mail flow rules

In the EAC, rules are processed in the order that they're displayed (the first rule has the **Priority** value 0). To change the priority of a rule, move the rule up or down in the list (you can't directly modify the **Priority** number in the EAC).
  
    
    

1. In the EAC, go to **Mail flow** > **Rules**.
    
  
2. Select a rule, and then click **Move up** (
  
    
    
![Up Arrow Icon](images/ITPro_EAC_UpArrowIcon.png)
  
    
    
) or **Move down** (
  
    
    
![Down Arrow Icon](images/ITPro_EAC_DownArrowIcon.png)
  
    
    
) to move the rule up or down in the list.
    
  

#### Use the Exchange Management Shell to set the priority of mail flow rules

The highest priority value you can set on a rule is 0. The lowest value you can set depends on the number of rules. For example, if you have five rules, you can use the priority values 0 through 4. Changing the priority of an existing rule can have a cascading effect on other rules. For example, if you have five rules (priorities 0 through 4), and you change the priority of a rule to 2, the existing rule with priority 2 is changed to priority 3, and the rule with priority 3 is changed to priority 4.
  
    
    
To set the priority of a rule in the Exchange Management Shell, use the following syntax:
  
    
    



```
Set-TransportRule -Identity "<RuleName>" -Priority <Number>
```

This example sets the priority of the rule named "Sender is a member of marketing" to 2. All existing rules that have a priority less than or equal to 2 are decreased by 1 (their priority numbers are increased by 1).
  
    
    



```
Set-TransportRule -Identity "Sender is a member of marketing" -Priority 2
```

 **Note**: To set the priority of a new rule when you create it, use the  _Priority_ parameter on the **New-TransportRule** cmdlet.
  
    
    

#### How do you know this worked?

To verify that you have successfully modified the priority of a mail flow rule, use either of the following procedures:
  
    
    

- In the EAC, go to **Mail flow** > **Rules**, and verify the **Priority** value of the rule in the list.
    
  
- In the Exchange Management Shell, use either of the following procedures:
    
  - Run the following command to see the list of rules and their **Priority** values:
    
  ```
  Get-TransportRule
  ```

  - Replace  _<RuleName>_ with the name of the rule, and run the following command:
    
  ```
  Get-TransportRule -Identity "<RuleName>" | Format-List Name,Priority
  ```


### Enable or disable mail flow rules
<a name="enable"> </a>

Disabling a rule prevents the rule from acting on messages, but allows you to preserve the settings of the rule.
  
    
    
By default, mail flow rules are enabled when you create them in the EAC or the Exchange Management Shell, but you can use the Exchange Management Shell to create a disabled rule (use the  _Enabled_ parameter with the value `$false`).
  
    
    

#### Use the EAC to enable or disable mail flow rules


1. In the EAC, go to **Mail flow** > **Rules**.
    
  
2. Select the rule from the list, and then configure one of the following settings:
    
  - **Disable the rule** Clear the check box in the **On** column.
    
  
  - **Enable the rule** Select the check box in the **On** column.
    
  

#### Use the Exchange Management Shell to enable or disable mail flow rules

To enable or disable a mail flow rule in the Exchange Management Shell, use the following syntax:
  
    
    

```
<Enable-TransportRule | Disable-TransportRule> -Identity "<RuleName>"
```

This example disables the mail flow rule named "Sender is a member of marketing".
  
    
    



```
Disable-TransportRule "Sender is a member of marketing"
```

This example enables the mail flow rule named "Sender is a member of marketing".
  
    
    



```
Enable-TransportRule "Sender is a member of marketing"
```

For detailed syntax and parameter information, see  [Enable-TransportRule](http://technet.microsoft.com/library/203d2fa8-83fe-4643-bbc2-db746ffd76a7.aspx) and [Disable-TransportRule](http://technet.microsoft.com/library/f1b5c2d6-cfcd-4180-89f5-13723d87a1b4.aspx).
  
    
    

#### How do you know this worked?

To verify that you have successfully enabled or disabled a mail flow rule, use either of the following procedures:
  
    
    

- In the EAC, go to **Mail flow** > **Rules**, and in the list of rules verify the status of the check box in the **On** column.
    
  
- In the Exchange Management Shell, use either of the following procedures:
    
  - Run the following command to see the list of rules and their **State** values:
    
  ```
  Get-TransportRule
  ```

  - Replace  _<RuleName>_ with the name of the rule, and run the following command:
    
  ```
  Get-TransportRule -Identity "<RuleName>" | Format-List Name,State
  ```


### Remove mail flow rules
<a name="remove"> </a>


#### Use the EAC to remove mail flow rules


1. From the EAC, go to **Mail flow** > **Rules**.
    
  
2. Select the rule you want to remove from the list, and then click **Delete** (
  
    
    
![Delete icon](images/ITPro_EAC_DeleteIcon.png)
  
    
    
).
    
  

#### Use the Exchange Management Shell to remove mail flow rules

To remove mail flow rules in the Exchange Management Shell, use the following syntax:
  
    
    

```
Remove-TransportRule -Identity "<RuleName>"
```

This example removes the mail flow rule named "Sender is a member of marketing":
  
    
    



```
Remove-TransportRule -Identity "Sender is a member of marketing"
```

For detailed syntax and parameter information, see  [Remove-TransportRule](http://technet.microsoft.com/library/f4628cfd-3628-4015-8e9e-274f4a331d01.aspx).
  
    
    

#### How do you know this worked?

To verify that you have successfully removed a mail flow rule, use either of the following procedures:
  
    
    

- In the EAC, go to **Mail flow** > **Rules**, and verify that the rule you removed is no longer in the list.
    
  
- In the Exchange Management Shell, run the following command to verify that the rule you removed is no longer listed:
    
  ```
  Get-TransportRule
  ```


### Import or export mail flow rule collections
<a name="import"> </a>

You can import a mail flow rule collection that you've previously exported as a backup, or import rules that you've exported from a previous version of Exchange.
  
    
    
 **Notes**:
  
    
    

- You can't import or export mail flow rule collections in the EAC. You can only use the Exchange Management Shell.
    
  
- You can't import a mail flow rule collection into Exchange 2010 if that rule collection was exported from Exchange 2013 or Exchange 2016 .
    
  

#### Use the Exchange Management Shell to export a transport rule collection


1. Run the following command:
    
  ```
  $File = Export-TransportRuleCollection
  ```

2. Use the following syntax:
    
  ```
  Set-Content -Path "<OutputFile>" -Value $file.FileData -Encoding Byte
  ```


    For example, to save the exported mail flow rule collection to the file C:\\My Documents\\Exported Rules.xml, run the following command:
    


  ```
  Set-Content -Path "C:\\My Documents\\Exported Rules.xml" -Value $file.FileData -Encoding Byte
  ```

For detailed syntax and parameter information, see  [Export-TransportRuleCollection](http://technet.microsoft.com/library/bfdb6ced-cd81-49f1-a929-4d76dbaf5590.aspx).
  
    
    

#### Use the Exchange Management Shell to import a transport rule collection


1. Use the following syntax:
    
  ```
  [Byte[]]$Data = Get-Content -Path "<OutputFile>" -Encoding Byte -ReadCount 0
  ```


    For example, to import the mail flow rule collection from C:\\My Documents\\Exported Rules.xml, run the following command:
    


  ```
  Byte[]]$Data = Get-Content -Path "C:\\My Documents\\Exported Rules.xml" -Encoding Byte -ReadCount 0
  ```

2. Run the following command:
    
  ```
  Import-TransportRuleCollection -FileData $Data
  ```

For detailed syntax and parameter information, see  [Import-TransportRuleCollection](http://technet.microsoft.com/library/880b3124-76c5-4212-a8b9-8f4523f8cbe6.aspx).
  
    
    

## Need more help?


- Resources for Exchange Server 2016:
    
  -  [Mail flow rules in Exchange 2016](mail-flow-rules-in-exchange-2016.md)
    
  
  -  [Mail flow rule conditions and exceptions (predicates) in Exchange 2016](mail-flow-rule-conditions-and-exceptions-predicates-in-exchange-2016.md)
    
  
  -  [Mail flow rule actions in Exchange 2016](mail-flow-rule-actions-in-exchange-2016.md)
    
  
- Resources for Exchange Online:
    
  -  [Transport Rules](http://technet.microsoft.com/library/743bd525-0ca2-426d-b76c-b4a052bc8886.aspx)
    
  
  -  [Transport Rule Conditions](http://technet.microsoft.com/library/7235e5ed-f7f4-41b1-b1a0-47bb96223a2f.aspx)
    
  
  -  [Transport Rule Actions](http://technet.microsoft.com/library/a5dfe768-fe26-4290-a801-84b3499f1bc4.aspx)
    
  
  -  [Transport and inbox rule limits](https://go.microsoft.com/fwlink/p/?LinkId=324584)
    
  
- Resources for Exchange Online Protection:
    
  -  [Transport rules](http://technet.microsoft.com/library/9c2cf227-eff7-48ef-87fb-487186e47363.aspx)
    
  
  -  [Transport Rule Conditions](http://technet.microsoft.com/library/04edeaba-afd4-4207-b2cb-51bcc44e483c.aspx)
    
  
  -  [Transport Rule Actions](http://technet.microsoft.com/library/f8621ecb-a177-4025-9011-a6569999746a.aspx)
    
  
  -  [Transport and inbox rule limits](https://go.microsoft.com/fwlink/p/?LinkId=324584)
    
  

