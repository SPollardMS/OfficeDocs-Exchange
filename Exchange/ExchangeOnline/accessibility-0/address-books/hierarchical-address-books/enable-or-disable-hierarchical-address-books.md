---
title: "Enable or disable hierarchical address books"
ms.author: kwekua
author: kwekua
manager: scotv
ms.date: 12/9/2016
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: b4c3a175-ce5e-4bfb-a4a0-92d25f3644b3
description: "You can configure a hierarchical address book (HAB), which is a feature available to end users in Microsoft Outlook 2010 or later. With an HAB, users can look for recipients in their Exchange organization by using an organizational hierarchy based on seniority or management structure. To learn more about HABs, see Hierarchical address books."
---

# Enable or disable hierarchical address books

You can configure a hierarchical address book (HAB), which is a feature available to end users in Microsoft Outlook 2010 or later. With an HAB, users can look for recipients in their Exchange organization by using an organizational hierarchy based on seniority or management structure. To learn more about HABs, see [Hierarchical address books](hierarchical-address-books.md).
  
## What do you need to know before you begin?

- Estimated time to complete: 1 hour.
    
- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Distribution groups" entry in the [Recipients permissions](http://technet.microsoft.com/library/5b690bcb-c6df-4511-90e1-08ca91f43b37.aspx) topic. 
    
- You can't use the Exchange Administration Center (EAC) to perform this procedure. You must use the Shell.
    
- Before you get started, read the topic [Hierarchical address books](hierarchical-address-books.md). You should understand if a HAB is appropriate for your Exchange organization.
    
- Understand how organizational units (OUs), groups, users, and contacts are currently configured in your Exchange organization.
    
- Understand the cmdlets and associated parameters in the following table, which are required to configure a HAB.
    
|**Cmdlet**|**Parameter**|
|:-----|:-----|
|[Set-OrganizationConfig](http://technet.microsoft.com/library/3b6df0fe-27c8-415f-ad0c-8b265f234c1a.aspx) <br/> | _HierarchicalAddressBookRoot_ <br/> |
|[Set-Group](http://technet.microsoft.com/library/924e6eb5-bb06-4e15-b122-cab414291cef.aspx) <br/> | _IsHierarchicalGroup_ <br/>  _SeniorityIndex_ <br/>  _PhoneticDisplayName_ <br/> |
|[Set-User](http://technet.microsoft.com/library/56d7fc86-2ac3-4e28-bc7a-761e91ac655a.aspx) <br/> | _SeniorityIndex_ <br/>  _PhoneticDisplayName_ <br/> |
|[Set-Contact](http://technet.microsoft.com/library/c86ca5af-bb1d-4619-8af8-9f04c83d84c5.aspx) <br/> | _SeniorityIndex_ <br/>  _PhoneticDisplayName_ <br/> |
   
- For information about keyboard shortcuts that may apply to the procedures in this topic, see **Keyboard shortcuts in the Exchange admin center**.
    
> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612),[Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351). 
  
## What do you want to do?

### Use the Shell to enable a HAB

> [!NOTE]
> Although you can't use the EAC to enable a HAB, after it's enabled you can use the EAC to manage the membership of the groups in the organizational hierarchy. 
  
For this example, an OU called HAB will be created for the HAB. The name of the domain for the organization is Contoso-dom, and Contoso,Ltd will be the name of the top-level organization in the hierarchy (the root organization). Subordinate groups named Corporate Office, Product Support Organization, and Sales &amp; Marketing Organization will be created as child organizations under Contoso,Ltd. Additionally, the groups Human Resources, Accounting Group, and Administration Group will be created as child organizations under Corporate Office.
  
For detailed information about creating distribution groups, see [Create and manage distribution groups](../../recipients-in-exchange-online/manage-distribution-groups/manage-distribution-groups.md).
  
1. Create an OU named HAB in the Contoso organization. You can use Active Directory Users and Computers or type the following at a command prompt.
    
    > [!NOTE]
    > Alternatively, you can use an existing OU in your Exchange forest. 
  
  ```
  dsadd ou "OU=HAB,DC=Contoso-dom,DC=Contoso,DC=com"
  ```

    > [!NOTE]
    > For details, see [Create a New Organizational Unit](https://go.microsoft.com/fwlink/p/?linkId=198986). 
  
2. Create the root distribution group Contoso,Ltd for the HAB. 
    
    > [!NOTE]
    > For the purposes of this topic, the Shell example is provided. However, you can also use the EAC to create a distribution group. For details, see [Create and manage distribution groups](../../recipients-in-exchange-online/manage-distribution-groups/manage-distribution-groups.md). 
  
  ```
  New-DistributionGroup -Name "Contoso,Ltd" -DisplayName "Contoso,Ltd" -Alias "ContosoRoot" -OrganizationalUnit "Contoso-dom.Contoso.com/HAB" -SamAccountName "ContosoRoot" -Type "Distribution"
  ```

3. Designate Contoso,Ltd as the root organization for the HAB.
    
  ```
  Set-OrganizationConfig -HierarchicalAddressBookRoot "Contoso,Ltd"
  ```

4. Create distribution groups for the other tiers in the HAB. For this example, you would create the following groups: Corporate Office, Product Support Organization, Sales &amp; Marketing Organization, Human Resources, Accounting Group, and Administration Group. This example creates the distribution group Corporate Office.
    
    > [!NOTE]
    > For the purposes of this topic, the Shell example is provided. However, you can also use the EAC to create distribution groups. For details, see [Create and manage distribution groups](../../recipients-in-exchange-online/manage-distribution-groups/manage-distribution-groups.md). 
  
  ```
  New-DistributionGroup -Name "Corporate Office" -DisplayName "Corporate Office" -Alias "CorporateOffice" -OrganizationalUnit "Contoso-dom.Contoso.com/HAB" -SamAccountName "CorporateOffice" -Type "Distribution"
  ```

5. Designate each of the groups as members of the HAB. For this example, you would designate the following groups as being hierarchical groups: Contoso,Ltd, Corporate Office, Product Support Organization, Sales &amp; Marketing Organization, Human Resources, Accounting Group, and Administration Group. This example designates the distribution group Contoso,Ltd as a member of the HAB.
    
  ```
  Set-Group -Identity "Contoso,Ltd" -IsHierarchicalGroup $true
  ```

6. Add each of the subordinate groups as members of the root organization. For this example, distribution groups Corporate Office, Product Support Organization, and Sales &amp; Marketing Organization, are added as members of the root organization Contoso,Ltd in the HAB. This example adds the Corporate Office distribution group as a member of the Contoso,Ltd root distribution group.
    
    > [!NOTE]
    > This example uses the alias of the distribution groups. 
  
  ```
  Add-DistributionGroupMember -Identity "ContosoRoot" -Member "CorporateOffice"
  ```

7. Add each of the groups that are subordinate to the distribution group Corporate Office as members of the group. For this example, distribution groups Human Resources, Accounting Group, and Administration Group, are added as members of the distribution group Corporate Office. This example adds the Human Resources distribution group as a member of the Corporate Office distribution group.
    
    > [!NOTE]
    > This example uses the alias of the distribution groups and assumes the Human Resources distribution group alias is HumanResources. 
  
  ```
  Add-DistributionGroupMember -Identity "CorporateOffice" -Member "HumanResources"
  ```

8. Add users to the groups in the HAB. For this example, David Hamilton (SMTP address DHamilton@contoso.com) is an existing user in the OU Contoso-dom.Contoso.com/Users and will be added to the group Corporate Office. Repeat this step to add other users to groups in the HAB.
    
  ```
  Add-DistributionGroupMember -Identity "CorporateOffice" -Member "DHamilton"
  ```

9. Set the  _SeniorityIndex_ parameter for groups in the HAB. For this example, the Corporate Office group contains three child groups: Human Resources, Accounting Group, and Administration Group. Instead of having the groups listed in ascending alphabetical order, which is the default, the preferred sorting will be Human Resources (  _SeniorityIndex_ = 100), Accounting Group (  _SeniorityIndex_ = 50), and then Administration Group (  _SeniorityIndex_ = 25). This example sets the  _SeniorityIndex_ parameter for the Human Resources group to 100. 
    
  ```
  Set-Group -Identity "Human Resources" -SeniorityIndex 100
  ```

    > [!NOTE]
    > The  _SeniorityIndex_ parameter is a numerical value used to sort groups or users in descending numerical order in a HAB. If the  _SeniorityIndex_ parameter isn't set or is equal for two or more users, the HAB sorting order uses the  _PhoneticDisplayName_ parameter value to list the users in ascending alphabetical order. If the  _PhoneticDisplayName_ value isn't set, the HAB sorting order defaults to the  _DisplayName_ parameter value and lists the users in ascending alphabetical order. 
  
10. Set the  _SeniorityIndex_ parameter for users in the HAB groups. For this example, the Corporate Office group contains three users: Amy Alberts, David Hamilton, and Rajesh M. Patel. Instead of having the users listed in ascending alphabetical order by default, the preferred sorting will be David Hamilton (  _SeniorityIndex_ = 100), Rajesh M. Patel (  _SeniorityIndex_ = 50), and then Amy Alberts (  _SeniorityIndex_ = 25). This example sets the  _SeniorityIndex_ parameter for the user David Hamilton to 100. 
    
  ```
  Set-User -Identity "DHamilton@contoso.com" -SeniorityIndex 100
  ```

After completing the preceding steps, the HAB will be visible in Outlook. To view the HAB, open Outlook and click **Address Book**. The HAB is displayed on the **Organization** tab, similar to the following figure. 
  
**Example HAB for Contoso,Ltd**

![Hierarchical Address Book dialog](../../media/ITPro_Mailbox_HABDisplay.gif)
  
After the HAB is created, you can use the EAC to manage the membership of the groups in the organizational hierarchy. However, you must use the Shell to modify the  _SeniorityIndex_ parameter for any new groups or users. 
  
For detailed syntax and parameter information, see the following:
  
- [New-DistributionGroup](http://technet.microsoft.com/library/7446962a-cf07-47a1-90d8-45df44057065.aspx)
    
- [Set-OrganizationConfig](http://technet.microsoft.com/library/3b6df0fe-27c8-415f-ad0c-8b265f234c1a.aspx)
    
- [Set-Group](http://technet.microsoft.com/library/924e6eb5-bb06-4e15-b122-cab414291cef.aspx)
    
- [Add-DistributionGroupMember](http://technet.microsoft.com/library/b586ea3a-8243-460a-a400-9ab5823ba782.aspx)
    
- [Set-User](http://technet.microsoft.com/library/56d7fc86-2ac3-4e28-bc7a-761e91ac655a.aspx)
    
### Use the Shell to disable a hierarchical address book

This example disables the root organization used for the HAB.
  
```
Set-OrganizationConfig -HierarchicalAddressBookRoot $null
```

> [!NOTE]
> This command doesn't delete the root organization or child groups used in the HAB structure or reset the  _SeniorityIndex_ values for groups or users. It only prevents the HAB from being displayed in Outlook. To enable the HAB with the same configuration settings again, you only need to enable the root organization again. 
  
For detailed syntax and parameter information, see [Set-OrganizationConfig](http://technet.microsoft.com/library/3b6df0fe-27c8-415f-ad0c-8b265f234c1a.aspx).
  

