---
title: Suspend or resume a mailbox database copy
ms.prod: EXCHANGE
ms.assetid: 96aa1b82-3e15-4215-843e-3d583af9504b
---


# Suspend or resume a mailbox database copy
 **Summary**: How to suspend or resume a mailbox database copy in Exchange 2016.
You may need to suspend or resume a database copy for a variety of reasons, such as maintenance on the disk that contains the database copy. Or you may need to suspend an individual database copy from activation for disaster recovery purposes.
  
    
    

Looking for other management tasks related to mailbox database copies? Check out  [Managing mailbox database copies](http://technet.microsoft.com/library/06df16b4-f209-4d3a-8c68-0805c745f9b2.aspx).
## What do you need to know before you begin?


- Estimated time to complete this task: 1 minute
    
  
- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Mailbox database copies" entry in the  [High availability and site resilience permissions](high-availability-and-site-resilience-permissions.md) topic.
    
  
- For information about keyboard shortcuts that may apply to the procedures in this topic, see  [Keyboard shortcuts in the Exchange admin center](keyboard-shortcuts-in-the-exchange-admin-center.md).
    
  

> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at:  [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612),  [Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or  [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351). 
  
    
    


## What do you want to do?


  
    
    

### Use the EAC to suspend a mailbox database copy


1. In the EAC, go to **Servers** > **Databases**.
    
  
2. Select the database whose copy you want to suspend.
    
  
3. In the Details pane, under **Database Copies**, click **Suspend** under the database copy you want to suspend.
    
  
4. In the **Comments** field, add an optional comment of up to 512 characters specifying the reason for the suspension.
    
  
5. To suspend the database copy from automatic activation, select the **This copy can only be activated by manual intervention** check box.
    
  
6. Click **save** to suspend the database copy.
    
  

### Use the EAC to resume a mailbox database copy


1. In the EAC, go to **Servers** > **Databases**.
    
  
2. Select the database whose copy you want to resume.
    
  
3. In the Details pane, under **Database Copies**, click **Resume** under the database copy you want to resume.
    
  
4. Click **yes** to resume the database copy.
    
  

### Use the Shell to suspend a mailbox database copy

This example suspends continuous replication for a copy of the database DB1 hosted on the server MBX1. An optional comment has also been specified.
  
    
    

```

Suspend-MailboxDatabaseCopy -Identity DB1\\MBX1 -SuspendComment "Maintenance on MBX1" -Confirm:$False

```

This example suspends activation for a copy of the database DB2 hosted on the server MBX2.
  
    
    



```

Suspend-MailboxDatabaseCopy -Identity DB2\\MBX2 -ActivationOnly -Confirm:$False
```


### Use the Shell to resume a mailbox database copy
<a name="UseShellResume"> </a>

This example resumes a copy of the database DB1 on the server MBX1.
  
    
    

```
Resume-MailboxDatabaseCopy -Identity DB1\\MBX1
```

This example resumes a copy of the database DB2 on the server MBX2 for replication only.
  
    
    



```
Resume-MailboxDatabaseCopy -Identity DB2\\MBX2 -ReplicationOnly
```


## How do you know this worked?

To verify that you have successfully suspended or resumed a mailbox database copy, do one of the following:
  
    
    

- In the EAC, navigate to **Servers** > **Databases**. Select the appropriate database, and in the Details pane, click **View details** to view the database copy properties.
    
  
- In the Shell, run the following command to display status information for a database copy.
    
  ```
  Get-MailboxDatabaseCopyStatus <DatabaseCopyName> | Format-List
  ```


