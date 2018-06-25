---
title: "Use mail flow rules to automatically add meetings to calendars in Exchange Online"
ms.author: chrisda
author: chrisda
ms.date: 5/5/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: c93c31a4-fe5e-479b-83b6-ee114d4f236c
description: "With the Direct to Calendar feature in Exchange Online, administrators can configure mail flow rules (also known as transport rules) that allow designated users to add meetings to calendars. The benefits of Direct to Calendar are:"
---

# Use mail flow rules to automatically add meetings to calendars in Exchange Online

With the Direct to Calendar feature in Exchange Online, administrators can configure mail flow rules (also known as transport rules) that allow designated users to add meetings to calendars. The benefits of Direct to Calendar are:
  
- The event is automatically added to the recipient's calendar without any action from them. If the user received the meeting invitation, it's on their calendar.
    
- The sender doesn't need to deal with Out of Office or other unwanted response messages that result from sending meeting invitations to a large number of recipients.
    
- No meeting-related messages are seen by attendees unless the meeting is cancelled.
    
Direct to Calendar requires two mail flow rules with specific conditions and actions. These rules are described in the following table:
  
****

|**Rule description**|**Condition**|**Action**|**Comments**|
|:-----|:-----|:-----|:-----|
|This mail flow rule turns regular meeting invitations into Direct to Calendar meeting invitations.  <br/> |**The sender is** or **The sender** \> **is this person** (the  _From_ parameter).  <br/> This condition identifies the users who are authorized to send Direct to Calendar meeting invitations. Although you can use other conditions, restricting the invitations by sender helps prevent unauthorized use of Direct to Calendar meeting invitations.  <br/> |**Set the message header to this value** or **Modify the message properties** \> **set a message header** (the  _SetHeaderName_ and  _SetHeaderValue_ parameters).  <br/> This action sets the **X-MS-Exchange-Organization-CalendarBooking-Response** header to the value  `Accept`. Other valid values are  `Tentative` and  `Decline`.  <br/> |We recommend that you use dedicated mailboxes (shared mailboxes are OK) for sending Direct to Calendar meeting invitations, because  *any*  meeting invitations from these senders will be automatically added to recipient calendars.  <br/> The dedicated mailboxes require no special permissions to send Direct to Calendar meeting invitations.  <br/> |
|This mail flow rule prevents Direct to Calendar meeting invitations from appearing in the Inbox of recipients.  <br/> |**The sender is** or **The sender** \> **is this person** (the  _From_ parameter).  <br/> |**Set the message header to this value** or **Modify the message properties** \> **set a message header** (the  _SetHeaderName_ and  _SetHeaderValue_ parameters).  <br/> This action sets the **X-MS-Exchange-Organization-CalendarBooking-TriageAction** header to the value  `MoveToDeletedItems`. The other valid value is  `None`.  <br/> |Technically, this rule is optional (without it, meetings are still automatically added to recipient calendars).  <br/> Note that this rule doesn't prevent meeting cancellation messages for Direct to Calendar meetings from appearing in the Inbox of recipients.  <br/> |
   
For more information about mail flow rules, see [Mail flow rules (transport rules) in Exchange Online](mail-flow-rules.md).
  
## What do you need to know before you begin?

- Estimated time to complete: 10 minutes
    
- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Mail flow" entry in the [Feature permissions in Exchange Online](../../permissions/feature-permissions.md) topic. 
    
- The designated accounts for sending Direct to Calendar meeting invitations need to exist.
    
- For more information about opening and using the Exchange admin center (EAC), see [Exchange admin center in Exchange Online](../../exchange-admin-center.md).
    
- To learn how to use Windows PowerShell to connect to Exchange Online, see [Connect to Exchange Online PowerShell](https://go.microsoft.com/fwlink/p/?linkid=396554).
    
- For information about keyboard shortcuts that may apply to the procedures in this topic, see **Keyboard shortcuts in the Exchange admin center**.
    
> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612),[Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351). 
  
## Use the Exchange admin center to create Direct to Calendar mail flow rules

1. Open the EAC and go to **Mail flow** \> **rules**.
    
2. Click **New** ( ![Add Icon](../../media/ITPro_EAC_AddIcon.gif)), and then select **Create a new rule**.
    
3. In the **New rule** page that opens, click **More options**.
    
    ![In the new mail flow rule window, click More options](../../media/d91f0335-f3b4-4760-bd50-6cdc46b84ce8.png)
  
4. Configure these additional settings on the **New rule** page: 
    
  - **Name** Direct to Calendar response (or anything descriptive). 
    
  - **Apply this rule if** \> **The sender** \> **is this person** Select one or more users to send Direct to Calendar meeting invitations. 
    
  - **Do the following** \> **Modify the message properties** \> **set a message header** Enter the following values: 
    
  - **Set the message header** `X-MS-Exchange-Organization-CalendarBooking-Response`
    
  - **to the value** `Accept`
    
    When you're finished, click **Save**.
    
    ![Settings for the Direct to Calendar capture mail flow rule.](../../media/52f4cb2c-5a86-46e7-a31b-231ae89931ab.png)
  
5. Back at **Mail flow** \> **rules**, click **New** ( ![Add Icon](../../media/ITPro_EAC_AddIcon.gif)) again, and then select **Create a new rule**.
    
6. In the **New rule** page that opens, click **More options**.
    
    ![In the new mail flow rule window, click More options](../../media/d91f0335-f3b4-4760-bd50-6cdc46b84ce8.png)
  
7. Configure these additional settings on the **New rule** page: 
    
  - **Name** Direct to Calendar triage action (or anything descriptive). 
    
  - **Apply this rule if** \> **The sender** \> **is this person** Select the same users as in step 3. 
    
  - **Do the following** \> **Modify the message properties** \> **set a message header** Enter the following values: 
    
  - **Set the message header** `X-MS-Exchange-Organization-CalendarBooking-TriageAction`
    
  - **to the value** `MoveToDeletedItems`
    
    When you're finished, click **Save**.
    
    ![Settings for the Direct to Calendar triage action mail flow rule.](../../media/52384435-eb38-449b-928b-94e0394e8f6a.png)
  
## Use Exchange Online PowerShell to create Direct to Calendar mail flow rules

1. To create the mail flow rule that turns regular meeting invitations into Direct to Calendar meeting invitations, use the following syntax:
    
  ```
  New-TransportRule -Name "Direct to Calendar response" -From "<designated sender 1>","<designated sender 2>"... -SetHeaderName "X-MS-Exchange-Organization-CalendarBooking-Response" -SetHeaderValue Accept
  ```

    This example configures the rule using the dedicated mailbox named Direct to Calendar invites.
    
  ```
  New-TransportRule -Name "Direct to Calendar response" -From "Direct to Calendar invites" -SetHeaderName "X-MS-Exchange-Organization-CalendarBooking-Response" -SetHeaderValue Accept
  ```

2. To create the mail flow rule that prevents Direct to Calendar meeting invitations from appearing in the Inbox of recipients, use the following syntax:
    
  ```
  New-TransportRule -Name "Direct to Calendar triage action" -From "<designated sender 1>","<designated sender 2>"... -SetHeaderName "X-MS-Exchange-Organization-CalendarBooking-TriageAction -SetHeaderValue MoveToDeletedItems
  ```

    This example configures the rule using the dedicated mailbox named Direct to Calendar invites.
    
  ```
  New-TransportRule -Name "Direct to Calendar triage action" -From "Direct to Calendar invites" -SetHeaderName "X-MS-Exchange-Organization-CalendarBooking-TriageAction" -SetHeaderValue MoveToDeletedItems
  ```

For detailed syntax and parameter information, see [New-TransportRule](http://technet.microsoft.com/library/eb3546bf-ca37-474e-9c22-962fe95af276.aspx).
  
## How do you know this worked?

To verify that you have successfully configured Direct to Calendar meeting invitations, use the designated sender mailbox to send a test meeting invitation to a small number of recipients. Verify that the meeting automatically appears in the calendars of the recipients, and verify there are no meeting-related messages in the Inbox (the second rule should automatically move these messages to the Deleted Items folder).
  
## More information

- The designated sender mailbox will receive meeting acceptance responses to Direct to Calendar meetings. Use the following strategies to help minimize the impact of these messages on the designated sender:
    
  - In Outlook, enable the **Update tracking information, and then delete responses that don't contain comments** and **After updating tracking information, move receipt to \<Deleted Items\>** settings in **Mail** \> **Tracking** for the designated sender mailbox. For more information, see [Change how meeting requests, polls, and read or delivery receipts are processed](https://go.microsoft.com/fwlink/p/?linkid=847058).
    
  - Clearing the **Request Responses** setting in Direct to Calendar meeting invitations doesn't prevent responses from being sent back to the designated sender mailbox. 
    
- If the designated mailbox sends a meeting cancellation for a Direct to Calendar meeting, the cancelled meeting title is always changed to **CANCELED: \<previous meeting title\>**, and the cancelled meeting remains in the calendars of attendees until they manually remove it.
    
- Meeting cancellation messages for Direct to Calendar meetings will always appear in the Inbox of recipients.
    

