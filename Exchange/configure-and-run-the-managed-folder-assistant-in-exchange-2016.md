---
title: Configure and run the Managed Folder Assistant in Exchange 2016
ms.prod: EXCHANGE
ms.assetid: 9fcfb9b6-bd24-4218-a163-bc599cd5476a
---


# Configure and run the Managed Folder Assistant in Exchange 2016
Learn how to configure the Managed Folder Assistant in Exchange 2016.
The Managed Folder Assistant is an Exchange Mailbox Assistant that applies and processes the message retention settings configured in retention policies.
  
    
    


## What do you need to know before you begin?


- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Messaging records management" entry in the  [Messaging policy and compliance permissions in Exchange 2016](messaging-policy-and-compliance-permissions-in-exchange-2016.md) topic.
    
  
- You can't use the Exchange admin center (EAC) to configure the Managed Folder Assistant. You must use the Exchange Management Shell. To learn how to open the Exchange Management Shell in your on-premises Exchange organization, see **Open the Exchange Management Shell**.
    
  

## Use the Exchange Management Shell to configure the Managed Folder Assistant

This example configures the interval each week when the Managed Folder Assistant processes mailboxes. The command in this example configures the Managed Folder Assistant to run on Sundays, Tuesdays, and Thursdays from 12:30 AM to 5:30 AM. 
  
    
    

```

Set-MailboxServer <identity of mailbox server> -ManagedFolderAssistantSchedule "Sunday.12:30 AM-Sunday.5:30 AM","Tuesday.12:30 AM-Tuesday.5:30 AM","Thursday.12:30 AM-Thursday.5:30 AM"
```

To specify the days, you can use the full name of the day, the abbreviated name of the day, or an integer from 0 through 6 (where 0 equals Sunday and 6 equals Saturday). To specify the time, you can use a 12-hour (see the previous example) or 24-hour format; for example, "22:00" or "23:45".
  
    
    
For detailed syntax and parameter information, see  [Set-MailboxServer](http://technet.microsoft.com/library/6a229126-b863-4f07-b024-a39c93b253f7.aspx).
  
    
    

### How do I know this worked?

To verify that you have successfully configured the Managed Folder Assistant, use the  [Get-MailboxServer](http://technet.microsoft.com/library/838bc72a-e3bb-4583-934f-d93a7c93252c.aspx) cmdlet to check the _ManagedFolderAssistantSchedule_ parameter.
  
    
    
This command retrieves all Mailbox servers in the organization and outputs the Managed Folder Assistant's workcycle properties from each server in a table format. The  _Auto_ switch is used to automatically fit column width.
  
    
    



```
Get-MailboxServer | Format-Table Name,ManagedFolderAssistantSchedule -Auto
```


## Use the Exchange Management Shell to start the Managed Folder Assistant

This example triggers the Managed Folder Assistant to immediately process Morris Cornejo's mailbox.
  
    
    

```
Start-ManagedFolderAssistant -Identity morris.cornejo@contoso.com
```

For detailed syntax and parameter information, see  [Start-ManagedFolderAssistant](http://technet.microsoft.com/library/75d840ea-5abc-44bb-b361-e81561fa1b04.aspx).
  
    
    

