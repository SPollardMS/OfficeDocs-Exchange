---
title: "Create a DLP policy from a template"
ms.author: stephow
author: stephow
manager: laurawi
ms.date: 6/23/2018
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 4432ef8b-6108-48d3-b2af-43ef5b40d2bc
description: "In Microsoft Exchange, you can use data loss prevention (DLP) policy templates to help meet the messaging policy and compliance needs of your organization. These templates contain pre-built sets of rules that can help you manage message data that is associated with several common legal and regulatory requirements. To see a list of all the templates supplied by Microsoft, see DLP policy templates supplied in Exchange. Example DLP templates that are supplied can help you manage:"
---

# Create a DLP policy from a template

In Microsoft Exchange, you can use data loss prevention (DLP) policy templates to help meet the messaging policy and compliance needs of your organization. These templates contain pre-built sets of rules that can help you manage message data that is associated with several common legal and regulatory requirements. To see a list of all the templates supplied by Microsoft, see [DLP policy templates supplied in Exchange](dlp-policy-templates.md). Example DLP templates that are supplied can help you manage:
  
- Gramm-Leach-Bliley Act (GLBA) data
    
- Payment Card Industry Data Security Standard (PCI-DSS)
    
- United States Personally Identifiable Information (U.S. PII)
    
You can customize any of these DLP templates or use them as-is. DLP policy templates are built on top of transport rules that include new conditions or predicates and actions. DLP policies support the full range of traditional transport rules, and you can add the additional rules after a DLP policy has been established. For more information about policy templates, see [DLP Policy Templates](http://technet.microsoft.com/library/c7b1a8e4-30d9-4409-85c5-f85ae023737d.aspx). To learn more about transport rule capabilities, see [Transport Rules](http://technet.microsoft.com/library/c3d2031c-fb7b-4866-8ae1-32928d0138ef.aspx) (Exchange Server 2016) or [Mail flow rules (transport rules) in Exchange Online](../../security-and-compliance/mail-flow-rules/mail-flow-rules.md). Once you have started enforcing a policy, you can learn about how to observe the results by reviewing the following topics:
  
Exchange 2013: [DLP Policy Detection Management](http://technet.microsoft.com/library/5c3f1cf6-d8c7-4d83-bb24-641ea9d50cbc.aspx)
  
Exchange Online: [DLP policy detection reports](http://technet.microsoft.com/library/84295dda-5bf7-4fa5-a1ee-3f761501cfe8.aspx)
  
> [!CAUTION]
> You should enable your DLP policies in test mode before running them in your production environment. During such tests, it is recommended that you configure sample user mailboxes and send test messages that invoke your test policies in order to confirm the results. 
  
## What do you need to know before you begin?

- Estimated time to complete: 30 minutes
    
- Ensure that Exchange Server is set up as described in [Planning and Deployment](http://technet.microsoft.com/library/692c59e3-f0b0-4cef-a66e-751aa740abae.aspx).
    
- Configure both administrator and user accounts within your organization and validate basic mail flow.
    
- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Data loss prevention (DLP)" entry in the [Messaging policy and compliance permissions](http://technet.microsoft.com/library/ec4d3b9f-b85a-4cb9-95f5-6fc149c3899b.aspx) topic 
    
- For information about keyboard shortcuts that may apply to the procedures in this topic, see **Keyboard shortcuts in the Exchange admin center**.
    
> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612),[Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351). 
  
## Use the EAC to configure a DLP policy from a template

1. In the EAC, navigate to **Compliance management** \> **Data loss prevention**, and then click **Add**![Add Icon](../../media/ITPro_EAC_AddIcon.gif).
    
    > [!NOTE]
    > You can also select this action if you click the arrow next to the **Add**![Add Icon](../../media/ITPro_EAC_AddIcon.gif) icon and select **New DLP policy from template** from the drop down menu. 
  
2. On the **Create a new DLP policy from a template** page, complete the following fields: 
    
1. **Name** Add a name that will distinguish this policy from others. 
    
2. **Description** Add an optional description that summarizes this policy. 
    
3. **Choose a template** Select the appropriate template to begin creating a new policy. 
    
4. **More options** Select the mode or state. The new policy is not fully enabled until you specify that it should be. The default mode for a policy is test without notifications. 
    
5. Click **Save** to finish creating the policy. 
    
> [!NOTE]
> In addition to the rules within a specific template, your organization may have additional expectations or company policies that apply to regulated data within your messaging environment. Exchange 2013 makes it easy for you to change the basic template in order to add actions so that your Exchange messaging environment complies with your own requirements. 
  
You can modify policies by editing the rules within them once the policy has been saved in your Exchange 2013 environment. An example rule change might include making specific people exempt from a policy or sending a notice and blocking message delivery if a message is found to have sensitive content. For more information about editing policies and rules, see [Manage DLP Policies](http://technet.microsoft.com/library/ba81fabd-7f7f-4ef7-968f-ce851ada9d70.aspx). 
  
You have to navigate to the specific policy's rule set on the **Edit DLP policy** page and use the tools available on that page in order to change a DLP policy you have already created in Exchange 2013. 
  
Some policies allow the addition of rules that invoke RMS for messages. You must have RMS configured on the Exchange server before adding the actions to make use of these types of rules.
  
For any of the DLP policies, you can change the rules, actions, exceptions, enforcement time period or whether other rules within the policy are enforced and you can add your own custom conditions for each.
  
## For more information

[Data loss prevention](data-loss-prevention.md)
  
[DLP policy templates](http://technet.microsoft.com/library/c7b1a8e4-30d9-4409-85c5-f85ae023737d.aspx)
  

