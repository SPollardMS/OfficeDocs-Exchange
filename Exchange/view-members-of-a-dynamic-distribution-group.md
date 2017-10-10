---
title: View members of a dynamic distribution group
ms.prod: EXCHANGE
ms.assetid: 40b100c6-864e-4c82-9f98-08dd5c83e378
---


# View members of a dynamic distribution group
 **Summary**: Learn how to use the Exchange Admin Console (EAC) or the Exchange Management Shell to view dynamic distribution group membership.
Dynamic distribution groups are distribution groups whose membership is based on specific recipient filters rather than a defined set of recipients. Microsoft Exchange provides pre-canned filters to make it easier to create recipient filters for dynamic distribution groups. A precanned filter is a commonly used filter that you can use to meet a variety of recipient-filtering criteria. You can specify the recipient types you want to include in a dynamic distribution group. Additionally, you can also specify a list of conditions that the recipients must meet. You can use the Exchange Management Shell to preview the list of recipients for a dynamic distribution group that uses precanned filters.
  
    
    

You can also use the Exchange admin center (EAC) to see how many recipients received the most recent message that was sent to a dynamic distribution group.
## What do you need to know before you begin?


- Estimated time to complete: 2 minutes.
    
  
- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Dynamic distribution groups" entry in the  [Recipients Permissions](recipients-permissions.md) topic.
    
  
- For information about keyboard shortcuts that may apply to the procedures in this topic, see  [Keyboard shortcuts in the Exchange admin center](keyboard-shortcuts-in-the-exchange-admin-center.md).
    
  

> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at:  [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612),  [Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or  [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351).. 
  
    
    


## What do you want to do?


### Use the Exchange Management Shell to preview the list of members of a dynamic distribution group
<a name="Shell"> </a>

This example returns the list of members for the dynamic distribution group Full Time Employees. The first command stores the dynamic distribution group object in the variable  `$FTE`. The second command uses the **Get-Recipient** cmdlet to list the recipients that match the criteria defined for the dynamic distribution group.
  
    
    

```

$FTE = Get-DynamicDistributionGroup "Full Time Employees"
```


```
Get-Recipient -RecipientPreviewFilter $FTE.RecipientFilter
```

For detailed syntax and parameter information, see  [Get-DynamicDistributionGroup](http://technet.microsoft.com/library/d97ee738-dfa1-464b-855a-4242e8065473.aspx) and [Get-Recipient](http://technet.microsoft.com/library/2ce6250f-0ad3-4b29-870c-e1d6e1e154bc.aspx).
  
    
    

### Use the EAC to see how many recipients received a message sent to a dynamic distribution group
<a name="EAC"> </a>


1. In the EAC, navigate to **Recipients** > **Groups**.
    
  
2. Select a dynamic distribution group.
    
    In the details pane under **Membership**, the number of people who received the last message sent to the dynamic distribution group is displayed.
    
  

## How do you know this worked?

To verify that you've successfully viewed the members of a dynamic distribution group, do one of the following:
  
    
    

- In the Exchange Management Shell, a list of members is returned after you run the previous command to preview a list of dynamic distribution group members. For example, if you created a new user mailbox with properties that match the recipient filter for the dynamic distribution group, this new user should be displayed in the list of group members.
    
  
- The number of people who received the last message sent to the dynamic distribution group is displayed in the details pane in the EAC. If no one has received a message sent to this group, it's possible that a message hasn't been sent to the group or that the group doesn't have any members that meet the conditions of the recipient filter.
    
  

