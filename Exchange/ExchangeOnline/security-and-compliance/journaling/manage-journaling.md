---
title: "Manage journaling"
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: 6/23/2018
ms.audience: End User
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: d517f27e-f80a-4a06-988c-cbbf981c701d
description: "Journaling can help your organization respond to legal, regulatory, and organizational compliance requirements by recording inbound and outbound email communications. This topic shows you how to perform basic tasks related to managing journaling in Exchange 2013 and Exchange Online."
---

# Manage journaling

Journaling can help your organization respond to legal, regulatory, and organizational compliance requirements by recording inbound and outbound email communications. This topic shows you how to perform basic tasks related to managing journaling in Exchange 2013 and Exchange Online.
  
Standard journaling is configured on a mailbox database. It enables the Journaling agent to journal all messages sent to and from mailboxes located on a specific mailbox database. You can also use premium journaling enables the Journaling agent to perform more granular journaling by using journal rules. Instead of journaling all mailboxes residing on a mailbox database, you can configure journal rules to match your organization's needs by journaling individual recipients or members of distribution groups. You must have an Exchange Enterprise client access license (CAL) to use premium journaling.
  
## What do you need to know before you begin?

- Estimated time to complete each procedure: 5 minutes.
    
- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Journaling" entry in the [Messaging policy and compliance permissions](http://technet.microsoft.com/library/ec4d3b9f-b85a-4cb9-95f5-6fc149c3899b.aspx) topic. 
    
- A journaling mailbox has been created, or an existing mailbox is available for use as the journaling mailbox. You can't designate an Exchange Online mailbox as a journaling mailbox. You can deliver journal reports to an on-premises archiving system or a third-party archiving service. If you're running a hybrid deployment with your mailboxes split between on-premises servers and Exchange Online, you can designate an on-premises mailbox as the journaling mailbox for your Exchange Online and on-premises mailboxes. 
    
    > [!IMPORTANT]
    > If you've configured a journaling rule in Exchange Online to send the journal reports to a journaling mailbox that doesn't exist or is an invalid destination, the journal report remains in the transport queue on Microsoft datacenter servers. If this happens, Microsoft datacenter personnel will attempt to contact your organization and ask you to fix the problem so that the journal reports can be successfully delivered to a journaling mailbox. If you haven't resolved the issue after two days of being contacted, Microsoft will disable the problematic journaling rule. 
  
- For information about keyboard shortcuts that may apply to the procedures in this topic, see **Keyboard shortcuts in the Exchange admin center**.
    
> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612),[Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351). If you're having trouble with the **JournalingReportDNRTo** mailbox, see [Transport and Mailbox Rules in Exchange Online don't work as expected](https://go.microsoft.com/fwlink/p/?LinkId=331674). 
  
## Create a journal rule
<a name="create"> </a>

### Use the EAC to create a journal rule
<a name="newjournalrule"> </a>

1. In the EAC, go to **Compliance management** \> **Journal rules**, and then click **Add**![Add Icon](../../media/ITPro_EAC_AddIcon.gif).
    
2. In **Journal rule**, provide a name for the journal rule and then compete the following fields:
    
  - **If the message is sent to or received from** Specify the recipient that the rule will target. You can either select a specific recipient or apply the rule to all messages. 
    
  - **Journal the following messages** Specify the scope of the journal rule. You can journal only the internal messages, only the external messages, or all messages regardless of origin or destination. 
    
  - **Send journal reports to** Type the address of the journaling mailbox that will receive all the journal reports. 
    
    > [!NOTE]
    > You can also type the display name or alias of a mail user or a mail contact as the journal mailbox. In this case, journal reports will be sent to the external email address of the mail user or mail contact. But as previously explained, the external email address of a mail user or mail contact can't be the address of an Exchange Online mailbox. 
  
3. Click **Save** to create the journal rule. 
    
### Use the Shell to create a journal rule
<a name="newjournalrule"> </a>

This example creates the journal rule Discovery Journal Recipients to journal all messages sent from and received by the recipient user1@contoso.com.
  
```
New-JournalRule -Name "Discovery Journal Recipients" -Recipient user1@contoso.com -JournalEmailAddress "Journal Mailbox" -Scope Global -Enabled $True
```

### How do you know this worked?
<a name="newjournalrule"> </a>

To verify that you have successfully created the journal rule, do one of the following:
  
- From the EAC, verify that the new journal rule you created is listed on the **Journal rules** tab. 
    
- From the Shell, verify that the new journal rule exists by running the following command (the example below verifies the rule created in the Shell example above):
    
  ```
  Get-JournalRule "Discovery Journal Recipients"
  ```

[Return to top](manage-journaling.md#top)
  
## View or modify a journal rule
<a name="viewormodify"> </a>

### Use the EAC to view or modify a journal rule

1. In the EAC, go to **Compliance management** \> **Journal rules**.
    
2. In the list view, you'll see all the journal rules in your organization.
    
3. Double-click the rule you want to view or modify.
    
4. In **Journal Rule**, modify the settings you want. For more information about the settings in this dialog box, see the procedure [Use the EAC to create a journal rule](manage-journaling.md#newjournalrule) earlier in this topic. 
    
### Use the Shell to view or modify a journal rule

This example displays a summary list of all journal rules in the Exchange organization:
  
```
Get-JournalRule
```

This example retrieves the journal rule Brokerage Journal Rule, and pipes the output to the **Format-List** command to display rule properties in a list format: 
  
```
Get-JournalRule "Brokerage Journal Rule" | Format-List
```

If you want to modify the properties of a specific rule, you need to use the [Set-JournalRule](http://technet.microsoft.com/library/e72562c6-64d2-43c3-81b0-062e7d7b28c9.aspx) cmdlet. This example changes the name of the journal rule  `JR-Sales` to  `TraderVault`. The following rule settings are also changed:
  
- Recipient
    
- JournalEmailAddress
    
- Scope
    
```
Set-JournalRule JR-Sales -Name TraderVault -Recipient traders@woodgrovebank.com -JournalEmailAddress tradervault@woodgrovebank.com -Scope Internal
```

### How do you know this worked?

To verify that you have successfully modified a journal rule, do one of the following:
  
- From the EAC, navigate to **Compliance management**, \> **Journal rules**. Double-click the rule you modified and verify your changes were saved.
    
- From the Shell, verify that you modified the journal rule successfully by running the following command. This command will list the properties you modified along with the name of the rule (the example below verifies the rule modified in the Shell example above):
    
  ```
  Get-TransportRule "TraderVault" | Format-List Name,Recipient,JournalEmailAddress,Scope
  ```

[Return to top](manage-journaling.md#top)
  
## Enable or disable a journal rule
<a name="enableordisable"> </a>

> [!IMPORTANT]
> When you disable a journal rule, the journaling agent will stop journaling messages targeted by that rule. While a journal rule is disabled, any messages that would have normally been journaled by the rule aren't journaled. Make sure that you don't compromise the regulatory or compliance requirements of your organization by disabling a journaling rule. 
  
### Use the EAC to enable or disable a journal rule

1. In the EAC, go to **Compliance management** \> **Journal rules**.
    
2. In the list view, in the **On** column next to the rule's name, select the check box to enable the rule or clear it to disable the rule. 
    
### Use the Shell to enable or disable a journal rule

This example enables the rule Contoso.
  
```
Enable-JournalRule "Contoso Journal Rule"
```

This example disables the rule Contoso.
  
```
Disable-JournalRule "Contoso Journal Rule"
```

### How do you know this worked?

To verify that you have successfully enabled or disabled a journal rule, do one of the following:
  
- From the EAC, view the list of journal rules check the status of the check box in the **On** column. 
    
- From the Shell, run the following command to return a list of all journal rules in your organization along, including their status:
    
  ```
  Get-JournalRule | Format-Table Name,Enabled
  ```

[Return to top](manage-journaling.md#top)
  
## Remove a journal rule
<a name="remove"> </a>

### Use the EAC to remove a journal rule

1. In the EAC, go to **Compliance management** \> **Journal rules**.
    
2. In the list view, select the rule you want to remove, and then click **Delete**![Delete icon](../../media/ITPro_EAC_DeleteIcon.gif).
    
### Use the Shell to remove a journal rule

This example removes the rule Brokerage Journal Rule.
  
```
Remove-JournalRule "Brokerage Journal Rule"
```

### How do you know this worked?

To verify that you have successfully removed the journal rule, do one of the following:
  
- From the EAC, verify that the rule you removed is no longer listed on the **Journal rules** tab. 
    
- From the Shell, run the following command to verify that the rule you remove is no longer listed:
    
  ```
  Get-JournalRule
  ```

[Return to top](manage-journaling.md#top)
  
## Enable or disable per-mailbox database journaling
<a name="databasejournaling"> </a>

> [!CAUTION]
> Disabling message journaling on a mailbox database may result in your organization being out of compliance with any applicable messaging retention policies. When you disable message journaling on a mailbox database, journal receipts are no longer sent for messages sent or received by mailboxes on that mailbox database. 
  
### Use the EAC enable or disable per-mailbox database journaling

1. In the EAC, go to **Servers** \> **Databases**.
    
2. In the list view, double-click the mailbox database for which you want to enable journaling.
    
3. Click **Maintenance**, and then click **Browse** next to the **Journal recipient** box to select the journaling mailbox. Specifying a journal recipient enables journaling for the database. 
    
    To disable journaling, remove the journal recipient by clicking **Remove X**.
    
### Use the Shell to enable or disable per-mailbox database journaling

This example enables journaling for the mailbox database Sales Database and sets Sales Database journal mailbox as the journal recipient. 
  
```
Set-MailboxDatabase "Sales Database" -JournalRecipient "Sales Database Journal Mailbox"
```

This example disables per-mailbox database journaling on the Sales Database mailbox database.
  
```
Set-MailboxDatabase "Sales Database" -JournalRecipient $Null
```

This example disables per-mailbox database journaling on all mailbox databases in the Exchange organization. The [Get-MailboxDatabase](http://technet.microsoft.com/library/e12bd6d3-3793-49cb-9ab6-948d42dd409e.aspx) cmdlet is used to retrieve all mailbox databases in the Exchange organization, and results from the cmdlet are piped to the [Set-MailboxDatabase](http://technet.microsoft.com/library/a01edc66-bc10-4f65-9df4-432cb9e88f58.aspx) cmdlet. 
  
```
Get-MailboxDatabase | Set-MailboxDatabase -JournalRecipient $Null
```

### How do you know this worked?

To verify that you have successfully enabled or disabled per-mailbox database journaling, do one of the following:
  
1. In the EAC, go to **Servers** \> **Databases**. 
    
2. Double click the database you want to verify, and then select the **Maintenance** tab. 
    
3. If the correct journaling recipient is listed in the **Journal recipient** box, you have successfully enabled journaling for the mailbox database. If there is no journaling recipient listed, journaling is disabled for the database. 
    
- From the Shell, run the following command to return a list of all mailbox databases in your organization, including the journal recipients associated with them. Journaling is enabled for databases that have a journal recipient listed, otherwise it's disabled.
    
  ```
  Get-MailboxDatabase | Format-Table Name,JournalRecipient
  ```

[Return to top](manage-journaling.md#top)
  
## For more information
<a name="databasejournaling"> </a>

[Disable or Enable Journaling of Voice Mail and Missed Call Notifications](http://technet.microsoft.com/library/5164a92e-69e6-4339-b80c-0cfbf0dc0198.aspx)
  
[New-JournalRule](http://technet.microsoft.com/library/fcad9ef1-b3f2-442d-a1a7-cd1bbe442054.aspx)
  
[Get-JournalRule](http://technet.microsoft.com/library/7620913f-cf28-4e82-983f-61a79f0b6e5a.aspx)
  
[Set-JournalRule](http://technet.microsoft.com/library/e72562c6-64d2-43c3-81b0-062e7d7b28c9.aspx)
  
[Enable-JournalRule](http://technet.microsoft.com/library/9a4b01b9-27d4-41e6-9573-86e27e82de2d.aspx)
  
[Disable-JournalRule](http://technet.microsoft.com/library/0324144b-2818-4e7f-a483-d6d6a19f8276.aspx)
  
[Remove-JournalRule](http://technet.microsoft.com/library/7cb9d691-2b0c-4f64-982d-ce69f3c3e757.aspx)
  
[Set-MailboxDatabase](http://technet.microsoft.com/library/a01edc66-bc10-4f65-9df4-432cb9e88f58.aspx)
  

