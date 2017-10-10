---
title: Learn more about the witness directory for a database availability group
ms.prod: EXCHANGE
ms.assetid: 1e176f59-2bbc-4ecf-9aa7-48470a2e367f
---


# Learn more about the witness directory for a database availability group

Every database availability group (DAG) must be assigned a witness server and witness directory. On the **General** page you can configure and modify the witness directory for the DAG. If the witness server you specify isn't an Exchange 2013 or Exchange 2010 server, you must add the Exchange Trusted Subsystem universal security group to the local Administrators group on the witness server. These security permissions are necessary to ensure that Exchange can create a directory and share on the witness server as needed. If the proper permissions aren't configured, the following error is returned:
  
    
    

 *Error: An error occurred during discovery of the database availability group topology. Error: An error occurred while attempting a cluster operation. Error: Cluster API "AddClusterNode() (MaxPercentage=12) failed with 0x80070005. Error: Access is denied."* 
## For More Information

 [Create a database availability group](create-a-database-availability-group.md)
  
    
    
 [Configure database availability group properties](configure-database-availability-group-properties.md)
  
    
    
 [Set-DatabaseAvailabilityGroup](http://technet.microsoft.com/library/4353c3ab-75b7-485e-89ae-d4b09b44b646.aspx)
  
    
    
 [Get-DatabaseAvailabilityGroup](http://technet.microsoft.com/library/ea64d731-55ae-4a39-9eec-a72aa36d6dad.aspx)
  
    
    

