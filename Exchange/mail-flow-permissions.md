---
title: Mail flow permissions
ms.prod: EXCHANGE
ms.assetid: f49f4fb5-af75-43cb-900f-c5f7b8cfa143
---


# Mail flow permissions

The permissions required to perform tasks related to mail flow vary depending on the procedure being performed or the cmdlet you want to run. For more information about transport features, see  [Mail flow and the transport pipeline](mail-flow-and-the-transport-pipeline.md). 
  
    
    

This topic lists the permissions required to manage the mail flow features in Microsoft Exchange Server 2016. For information about how Office 365 permissions relate to Exchange permissions, see  [Permissions in Office 365](https://go.microsoft.com/fwlink/p/?LinkID=335814).
To find out what permissions you need to perform the procedure or run the cmdlet, do the following:
  
    
    


1. In the table below, find the feature that is most related to the procedure you want to perform or the cmdlet you want to run.
    
  
2. Next, look at the permissions required for the feature. You must be assigned one of those role groups, an equivalent custom role group, or an equivalent management role. You can also click on a role group to see its management roles. If a feature lists more than one role group, you only need to be assigned one of the role groups to use the feature. For more information about role groups and management roles, see **Understanding Role Based Access Control**.
    
  
3. Now, run the **Get-ManagementRoleAssignment** cmdlet to look at the role groups or management roles assigned to you to see if you have the permissions that are necessary to manage the feature.
    
    > [!NOTE]
      > You must be assigned the Role Management management role to run the **Get-ManagementRoleAssignment** cmdlet. If you don't have permissions to run the **Get-ManagementRoleAssignment** cmdlet, ask your Exchange administrator to retrieve the role groups or management roles assigned to you.
If you want to delegate the ability to manage a feature to another user, see **Delegate a Management Role**.
> [!NOTE]
> Some features that you want to manage might exist on Edge Transport servers. To manage features on Edge Transport servers, you need to become a member of the Local Administrators group on the Edge Transport server you want to manage. Edge Transport servers don't use Role Based Access Control (RBAC). Features that can be managed on Edge Transport servers have Edge Transport Local Administrator in the "Permissions required" column in the table below. 
  
    
    


> [!NOTE]
> Some features may require that you have local administrator permissions on the server you want to manage. To manage these features, you must be a member of the Local Administrators group on that server. 
  
    
    


## Mail flow permissions

You can use the features in the following tables to configure mail flow settings in the Front End Transport, Mailbox Transport, and Transport services on Mailbox servers, and on Edge Transport servers. The permissions that are required to configure each feature are listed.
  
    
    
Users who are assigned the View Only Management role group can view the configuration of the features shown in the following table. For more information, see  [View Only Organization Management](http://technet.microsoft.com/library/c514c6d0-0157-4c52-9ec6-441d9a30f3df.aspx).
  
    
    
 **Mailbox servers**
  
    
    


|**Feature**|**Permissions required**|
|:-----|:-----|
|Accepted domains  <br/> | [Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> |
|Active Directory site and site link management  <br/> | [Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> |
|Anti-spam features  <br/> | [Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/>  [Hygiene Management](http://technet.microsoft.com/library/fc0a9ec2-9c3d-42f6-8442-8603fb29d464.aspx) <br/> |
|Anti-spam updates  <br/> | [Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/>  [Hygiene Management](http://technet.microsoft.com/library/fc0a9ec2-9c3d-42f6-8442-8603fb29d464.aspx) <br/> |
|Certificate management  <br/> | [Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> |
|Delivery Agent connectors  <br/> | [Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/>  [Server Management](http://technet.microsoft.com/library/30cbc4de-adb3-42e8-922f-7661095bdb8c.aspx) <br/> |
|DSNs  <br/> | [Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> |
|EdgeSync  <br/> | [Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> |
|Foreign connectors  <br/> | [Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> |
|Front End Transport service  <br/> | [Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/>  [Server Management](http://technet.microsoft.com/library/30cbc4de-adb3-42e8-922f-7661095bdb8c.aspx) <br/>  [Hygiene Management](http://technet.microsoft.com/library/fc0a9ec2-9c3d-42f6-8442-8603fb29d464.aspx) <br/> |
|Journaling  <br/> | [Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/>  [Records Management](http://technet.microsoft.com/library/0e0c95ce-6109-4591-b86d-c6cfd44d21f5.aspx) <br/> |
|Mailbox access  <br/> | [Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> |
|Mailbox junk email configuration  <br/> | [Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/>  [Records Management](http://technet.microsoft.com/library/0e0c95ce-6109-4591-b86d-c6cfd44d21f5.aspx) <br/>  [Recipient Management](http://technet.microsoft.com/library/669d602e-68e3-41f9-a455-b942d212d130.aspx) <br/>  [Help Desk](http://technet.microsoft.com/library/e7958752-22e4-4155-a2fc-948099dec6f7.aspx) <br/> |
|Mailbox Transport service  <br/> | [Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/>  [Server Management](http://technet.microsoft.com/library/30cbc4de-adb3-42e8-922f-7661095bdb8c.aspx) <br/>  [Hygiene Management](http://technet.microsoft.com/library/fc0a9ec2-9c3d-42f6-8442-8603fb29d464.aspx) <br/> |
|MailTips  <br/> | [Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> |
|Message classifications  <br/> | [Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/>  [Records Management](http://technet.microsoft.com/library/0e0c95ce-6109-4591-b86d-c6cfd44d21f5.aspx) <br/> |
|Message tracking  <br/> | [Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/>  [Records Management](http://technet.microsoft.com/library/0e0c95ce-6109-4591-b86d-c6cfd44d21f5.aspx) <br/>  [Recipient Management](http://technet.microsoft.com/library/669d602e-68e3-41f9-a455-b942d212d130.aspx) <br/> |
|Moderated transport  <br/> | [Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/>  [Recipient Management](http://technet.microsoft.com/library/669d602e-68e3-41f9-a455-b942d212d130.aspx) <br/> |
|Queues  <br/> | [Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/>  [Server Management](http://technet.microsoft.com/library/30cbc4de-adb3-42e8-922f-7661095bdb8c.aspx) <br/> |
|Receive connectors  <br/> | [Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/>  [Server Management](http://technet.microsoft.com/library/30cbc4de-adb3-42e8-922f-7661095bdb8c.aspx) <br/>  [Hygiene Management](http://technet.microsoft.com/library/fc0a9ec2-9c3d-42f6-8442-8603fb29d464.aspx) <br/> |
|Remote domains  <br/> | [Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> |
|SafeList aggregation  <br/> | [Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/>  [Records Management](http://technet.microsoft.com/library/0e0c95ce-6109-4591-b86d-c6cfd44d21f5.aspx) <br/> |
|Send connectors  <br/> | [Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> |
|Shadow redundancy  <br/> | [Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> |
|Testing mail flow  <br/> | [Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/>  [Server Management](http://technet.microsoft.com/library/30cbc4de-adb3-42e8-922f-7661095bdb8c.aspx) <br/> |
|Testing Transport rule processing  <br/> | [Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> |
|Transport agents  <br/> | [Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/>  [Records Management](http://technet.microsoft.com/library/0e0c95ce-6109-4591-b86d-c6cfd44d21f5.aspx) <br/> |
|Transport configuration  <br/> | [Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> |
|Transport logs  <br/> | [Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/>  [Server Management](http://technet.microsoft.com/library/30cbc4de-adb3-42e8-922f-7661095bdb8c.aspx) <br/> |
|Transport rules  <br/> | [Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/>  [Records Management](http://technet.microsoft.com/library/0e0c95ce-6109-4591-b86d-c6cfd44d21f5.aspx) <br/> |
|Transport service  <br/> | [Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/>  [Server Management](http://technet.microsoft.com/library/30cbc4de-adb3-42e8-922f-7661095bdb8c.aspx) <br/>  [Hygiene Management](http://technet.microsoft.com/library/fc0a9ec2-9c3d-42f6-8442-8603fb29d464.aspx) <br/> |
|X.400 domains  <br/> | [Organization Management](http://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> |
   
 **Edge Transport servers**
  
    
    


|**Feature**|**Permissions required**|
|:-----|:-----|
|Accepted domains - Edge Transport  <br/> |Edge Transport server local administrator  <br/> |
|Address Rewriting - Edge Transport  <br/> |Edge Transport server local administrator  <br/> |
|Edge Transport server  <br/> |Edge Transport server local administrator  <br/> |
|EdgeSync - Edge Transport  <br/> |Edge Transport server local administrator  <br/> |
|Queues - Edge Transport  <br/> |Edge Transport server local administrator  <br/> |
|Receive connectors - Edge Transport  <br/> |Edge Transport server local administrator  <br/> |
|Send connectors - Edge Transport  <br/> |Edge Transport server local administrator  <br/> |
|Transport configuration - Edge Transport  <br/> |Edge Transport server local administrator  <br/> |
|Transport logs - Edge Transport  <br/> |Edge Transport server local administrator  <br/> |
|Transport rules - Edge Transport  <br/> |Edge Transport server local administrator  <br/> |
   

