---
title: Learn more about dynamic distribution groups
ms.prod: EXCHANGE
ms.assetid: 3dc359e9-3490-4247-a0f1-fd86ad7805cf
---


# Learn more about dynamic distribution groups

Dynamic distribution groups are distribution groups whose membership is based on specific recipient filters rather than a defined set of recipients. Like distribution groups, dynamic distribution groups expedite the mass sending of email messages and other information within a Microsoft Exchange organization. But unlike regular distribution groups that contain a defined set of members, the membership list for dynamic distribution groups is calculated each time a message is sent to the group, based on the filters and conditions that you define. When an email message is sent to a dynamic distribution group, it's delivered to all recipients in the organization that match the criteria defined for that group.
  
    
    

You can use the Exchange Administration Center (EAC) to configure precanned filters that will help you create recipient filters for dynamic distribution groups. A precanned filter is a commonly used filter that you can use to meet a variety of recipient-filtering criteria. You can use these filters to specify the recipient types you want to include in a dynamic distribution group. You can also specify a list of conditions that the recipients must meet. Precanned conditions can be created based on the following properties:
- Custom attributes 1-15
    
  
- State or province
    
  
- Company
    
  
- Department
    
  
- Recipient container
    
  
You can also specify conditions based on recipient properties other than those previously listed. To do this, you must use the Exchange Management Shell to create a custom query for the dynamic distribution group. Remember that the filter and condition settings for dynamic distribution groups that have custom recipient filters can be managed only by using the Shell.
## For more information
<a name="Top"> </a>

 [Manage dynamic distribution groups](manage-dynamic-distribution-groups.md)
  
    
    
 [New-DynamicDistributionGroup](http://technet.microsoft.com/library/e9920bd1-06c1-4f75-992f-dd7fc98a5c2b.aspx)
  
    
    
 [View members of a dynamic distribution group](view-members-of-a-dynamic-distribution-group.md)
  
    
    

