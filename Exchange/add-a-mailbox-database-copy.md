---
title: Add a mailbox database copy
ms.prod: EXCHANGE
ms.assetid: 784bf48f-8af5-422c-a63f-2f01fc0cf151
---


# Add a mailbox database copy
 **Summary**: Use these steps to create a copy of a mailbox database in Exchange 2016.
When you add a copy of a mailbox database, continuous replication is automatically enabled between the existing database and the database copy. Database copies are automatically assigned an identity in the format of < _DatabaseName_>\\< _HostMailboxServerName_>. For example, a copy of the database DB1 that's hosted on the server MBX3 would be DB1\\MBX3.
  
    
    

Looking for other management tasks related to mailbox database copies? Check out  [Managing mailbox database copies](http://technet.microsoft.com/library/06df16b4-f209-4d3a-8c68-0805c745f9b2.aspx).
## What do you need to know before you begin?


- Estimated time to complete this task: 2 minutes, plus the time to seed the database copy, which depends on a variety of factors, such as the size of the database, the speed, available bandwidth and latency of the network, and storage speeds.
    
  
- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Mailbox database copies" entry in the  [High availability and site resilience permissions](high-availability-and-site-resilience-permissions.md) topic.
    
  
- The active copy of the database must be mounted.
    
  
- The specified Mailbox server must not already host a copy of the database.
    
  
- The path for the database copy and its log files must be available on the selected Mailbox server.
    
  
- The server hosting the active copy and the server that will host the passive copy must be in the same database availability group (DAG). The DAG must also have quorum and be healthy.
    
  
- If you're adding the second copy of a database (for example, creating the first passive copy of the database), circular logging must not be enabled for the specified mailbox database. If circular logging is enabled, you must first disable it. After the mailbox database copy has been added, circular logging can be enabled. After circular logging is enabled for a replicated mailbox database, continuous replication circular logging (CRCL) is used instead of JET circular logging. If you're adding the third or subsequent copy of a database, CRCL can remain enabled.
    
  
- For information about keyboard shortcuts that may apply to the procedures in this topic, see  [Keyboard shortcuts in the Exchange admin center](keyboard-shortcuts-in-the-exchange-admin-center.md).
    
  

> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at:  [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612),  [Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or  [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351).. 
  
    
    


## What do you want to do?


  
    
    

### Use the EAC to add a mailbox database copy
<a name="UseEMC"> </a>


1. In the EAC, go to **Servers** > **Databases**.
    
  
2. Select the database that you want to copy, click **More** (the three dots to the right of the Refresh icon), and then click **Add database copy**.
    
  
3. On the **add mailbox database copy** page, click **Browse...**, select the Mailbox server that will host the database copy, and then click **OK**.
    
  
4. Optionally, configure the **Activation preference number** for the database copy.
    
  
5. Click **More options…** to designate the database copy as a lagged database copy by configuring a replay lag time, or to postpone automatic seeding of the database copy.
    
  
6. Click **Save** to save the configuration changes and add the mailbox database copy.
    
  
7. Click **OK** to acknowledge any messages that appear.
    
  

### Use the Shell to add a mailbox database copy
<a name="UseShell"> </a>

This example adds a copy of mailbox database DB1 to the Mailbox server MBX3. Replay lag time and truncation lag time are left at the default values of zero, and the activation preference is configured with a value of 2.
  
    
    

```

Add-MailboxDatabaseCopy -Identity DB1 -MailboxServer MBX3 -ActivationPreference 2
```

This example adds a copy of mailbox database DB2 to the Mailbox server MBX4. Replay lag time and truncation lag time are left at the default values of zero, and the activation preference is configured with a value of  `5`. In addition, seeding is being postponed for this copy so that it can be seeded using a local source server instead of the current active database copy, which is geographically distant from MBX4.
  
    
    



```
Add-MailboxDatabaseCopy -Identity DB2 -MailboxServer MBX4 -ActivationPreference 5 -SeedingPostponed
```

This example adds a copy of mailbox database DB3 to the Mailbox server MBX5. Replay lag time is set to 3 days, truncation lag time is left at the default value of zero, and the activation preference is configured with a value of  `4`.
  
    
    



```
Add-MailboxDatabaseCopy -Identity DB3 -MailboxServer MBX5 -ReplayLagTime 3.00:00:00 -ActivationPreference 4
```


## How do you know this worked?

To verify that you have successfully created a mailbox database copy, do one of the following:
  
    
    

- In the EAC, navigate to **Servers** > **Databases**. Select the database that was copied. In the Details pane, the status of the database copy and its content index are displayed, along with the current copy queue length.
    
  
- In the Shell, run the following command to verify the mailbox database copy was created and is healthy.
    
  ```
  Get-MailboxDatabaseCopyStatus <DatabaseCopyName>
  ```


    The Status and Content Index State should both be Healthy.
    
  

## For more information

 [Mailbox database copies](mailbox-database-copies.md)
  
    
    
 [Managing mailbox database copies](http://technet.microsoft.com/library/06df16b4-f209-4d3a-8c68-0805c745f9b2.aspx)
  
    
    

