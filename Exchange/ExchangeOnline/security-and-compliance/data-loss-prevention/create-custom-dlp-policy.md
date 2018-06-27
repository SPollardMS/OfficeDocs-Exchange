---
title: "Create a custom DLP policy"
ms.author: stephow
stephow-msft
manager: laurawi
ms.date: 6/23/2018
ms.audience: ITPro
ms.topic: article
ms.service: exchange-online
localization_priority: Normal
ms.assetid: b3299a39-9663-41e4-b76e-9d2f7879d486
description: "A custom data loss prevention (DLP) policy allows you to establish conditions, rules, and actions that can help meet the specific needs of your organization, and which may not be covered in one of the pre-existing DLP templates."
---

# Create a custom DLP policy

A custom data loss prevention (DLP) policy allows you to establish conditions, rules, and actions that can help meet the specific needs of your organization, and which may not be covered in one of the pre-existing DLP templates.
  
The rule conditions that are available to you in a single policy include all the traditional transport rules in addition to the sensitive information types presented in [Sensitive Information Types Inventory](http://technet.microsoft.com/library/98b81f9c-87bb-4905-8e53-04621c3ae74d.aspx). For more information about transport rules, see [Transport Rules](http://technet.microsoft.com/library/c3d2031c-fb7b-4866-8ae1-32928d0138ef.aspx) (Exchange 2016) or [Mail flow rules (transport rules) in Exchange Online](../../security-and-compliance/mail-flow-rules/mail-flow-rules.md).
  
> [!CAUTION]
> You should enable your DLP policies in test mode before running them in your production environment. During such tests, it is recommended that you configure sample user mailboxes and send test messages that invoke your test policies in order to confirm the results. for more information about testing, see [Test a mail flow rule](../../security-and-compliance/mail-flow-rules/test-mail-flow-rules.md). 
  
For additional management tasks related to creating a custom DLP policy, see [DLP Procedures](http://technet.microsoft.com/library/e2f575aa-552e-4dcc-8d7b-1ffd697d67df.aspx)(Exchange 2013) or [DLP Procedures](http://technet.microsoft.com/library/925290cc-f3b4-401e-b6c7-9a216a726f17.aspx) (Exchange Online). 
  
## What do you need to know before you begin?

- Estimated time to complete: 60 minutes
    
- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Data loss prevention (DLP)" entry in the [Messaging policy and compliance permissions](http://technet.microsoft.com/library/ec4d3b9f-b85a-4cb9-95f5-6fc149c3899b.aspx) topic. 
    
- In order to create a new custom DLP policy, you must follow the installation instructions for Exchange Server. For more information about deployment, see [Planning and Deployment](http://technet.microsoft.com/library/692c59e3-f0b0-4cef-a66e-751aa740abae.aspx).
    
- For information about keyboard shortcuts that may apply to the procedures in this topic, see **Keyboard shortcuts in the Exchange admin center**.
    
> [!NOTE]
> Due to the variances in customer environments, Microsoft Customer Support Services (CSS) cannot participate in the development or testing of custom Regular Expression scripts ("RegEx scripts"). For RegEX custom script development, testing and debugging, Office 365 customers will need to rely upon internal IT resources. Alternatively, Office 365 customers may choose to use an external consulting resource such as Microsoft Consulting Services (MCS). Regardless of the script development resource, CSS EXO and EOP support engineers are not available to assist customers with custom RegEx script inquiries. 
  
> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612),[Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351). 
  
## Use the EAC to create a custom DLP policy without any existing rules

1. In the EAC, navigate to **Compliance management** \> **Data loss prevention**. Any existing policies that you have configured are shown in a list.
    
2. Click the arrow that is beside the **Add**![Add Icon](../../media/ITPro_EAC_AddIcon.gif) icon, and select **New custom policy**. 
    
    > [!IMPORTANT]
    > If you click **Add**![Add Icon](../../media/ITPro_EAC_AddIcon.gif) icon instead of the arrow, you will create a new policy based on a template. For more information about using templates, see [Create a DLP policy from a template](create-dlp-policy-from-template.md). 
  
3. On the **New custom policy** page, complete the following fields: 
    
1. **Name** Add a name that will distinguish this policy from others. 
    
2. **Description** Add an optional description that summarizes this policy. 
    
3. **Choose a state** Select the mode or state for this policy. The new policy is not fully enabled until you specify that it should be. The default mode for a policy is test without notifications. 
    
4. Click **Save** to finish creating the new policy reference information. The policy is added to the list of all policies that you have configured, although there are not yet any rules or actions associated with this new custom policy. 
    
5. Double-click the policy that you just created or select it and click **Edit**![Edit icon](../../media/ITPro_EAC_EditIcon.gif).
    
6. On the **Edit DLP policy** page, click **Rules**.
    
    Click **Add**![Add Icon](../../media/ITPro_EAC_AddIcon.gif) to add a new blank rule. You can establish conditions using all the traditional transport rules in addition to the sensitive information types. 
    
    In order to avoid confusion, supply a unique name for each part of your policy or rule when you have the option to provide your own character string. There are several options additional options available to you:
    
1. Click the arrow that is beside the **Add**![Add Icon](../../media/ITPro_EAC_AddIcon.gif) icon to add a rule about sender notification or allowing overrides. 
    
2. To remove a rule, highlight the rule and click **Delete**![Delete icon](../../media/ITPro_EAC_DeleteIcon.gif).
    
3. Click **More options**![More Options Icon](../../media/ITPro_EAC_MoreOptionsIcon.gif) to add additional conditions and actions for this rule including time-bound limits of enforcement or effects on other rules in this policy. 
    
7. Click **Save** to finish modifying the policy and save your changes. 
    
DLP policy templates are one type of feature Microsoft Exchange that can help you design and apply a robust policy and compliance system for your messaging environment. For more information about compliance features, see [Messaging Policy and Compliance](http://technet.microsoft.com/library/65f20a20-27a4-4f6e-9b27-f8705d65b8d9.aspx) (Exchange 2016) or [Security and compliance for Exchange Online](../../security-and-compliance/security-and-compliance.md).
  
## For more information

[Data loss prevention](data-loss-prevention.md)
  
[Transport Rules](http://technet.microsoft.com/library/c3d2031c-fb7b-4866-8ae1-32928d0138ef.aspx) Exchange 2016 
  
[Mail flow rules (transport rules) in Exchange Online](../../security-and-compliance/mail-flow-rules/mail-flow-rules.md) Exchange Online 
  
[Integrating sensitive information rules with transport rules](integrate-sensitive-information-rules.md)
  

