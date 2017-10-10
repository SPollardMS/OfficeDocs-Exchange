---
title: Active Directory
ms.prod: EXCHANGE
ms.assetid: 8e8464df-2d1d-4d68-82de-b0c158c549c3
---


# Active Directory
 **Summary**: How Exchange 2016 interacts with Active Directory. 
Microsoft Exchange Server 2016 uses Active Directory to store and share directory information with Windows. Starting with Exchange 2013, we made some changes to how Exchange works with Active Directory. These changes are discussed below.
  
## Test view
Test test test

One Two Threeeee.....

## Active Directory driver

The Active Directory driver is the core Microsoft Exchange component that allows Exchange services to create, modify, delete, and query for Active Directory Domain Services (AD DS) data. In Exchange 2013 and later, all access to Active Directory is done using the Active Directory driver itself. In previous versions of Exchange, DSAccess provided directory lookup services for components such as SMTP, message transfer agent (MTA), and the Exchange store. 
  
    
    
The Active Directory driver also uses Microsoft Exchange Active Directory Topology (MSExchangeADTopology), which allows the Active Directory driver to use Directory Service Access (DSAccess) topology data. This data includes the list of available domain controllers and global catalog servers available to handle Exchange requests. For more information about the Active Directory Driver, see  [Active Directory Domain Services](https://go.microsoft.com/fwlink/p/?linkid=110942).
  
    
    

## Active Directory schema changes

Exchange 2016 adds new attributes to the Active Directory domain service schema and also makes other modifications to existing classes and attributes. For more information about Active Directory changes when you install Exchange 2016, see  [Exchange 2016 Active Directory schema changes](exchange-2016-active-directory-schema-changes.md).
  
    
    

## For more information

To learn more about how Exchange 2016 stores and retrieves information in Active Directory so that you can plan access to it, see  [Access to Active Directory](access-to-active-directory.md).
  
    
    
For more information about Active Directory forest design, see  [AD DS Design Guide](https://go.microsoft.com/fwlink/p/?LinkId=264957).
  
    
    
To learn more about computers running Windows in an Active Directory domain and deploying Exchange 2016 in a domain that has a disjoint namespace, see  [Disjoint Namespace Scenarios](http://technet.microsoft.com/library/90101d49-6f45-44be-8a93-eeb2c8283e3b.aspx).
  
    
    

