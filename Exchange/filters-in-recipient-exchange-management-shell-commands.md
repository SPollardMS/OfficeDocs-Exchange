---
title: Filters in recipient Exchange Management Shell commands
ms.prod: EXCHANGE
ms.assetid: fb4b1396-9aae-4037-be1a-b09e336b890e
---


# Filters in recipient Exchange Management Shell commands
Learn about creating different kinds of recipient filters by using the Exchange Management Shell.
You can use several Exchange Management Shell commands to filter a set of recipients. You can create the following types of filters in an Exchange command:
  
    
    


- Precanned filters
    
  
- Custom filters using the  _RecipientFilter_ parameter
    
  
- Custom filters using the  _Filter_ parameter
    
  
- Custom filters using the  _ContentFilter_ parameter
    
  

Older versions of Exchange used LDAP filtering syntax to create custom address lists, global address lists (GALs), email address policies, and distribution groups. In Exchange Server 2007 and later versions, the OPATH filtering syntax replaced the LDAP filtering syntax. 
  
    
    


## Precanned filters
<a name="PF"> </a>

A precanned filter is a commonly used Exchange filter that you can use to meet a variety of recipient-filtering criteria for creating dynamic distribution groups, email address policies, address lists, or GALs. With precanned filters, you can use either the Exchange Management Shell or the Exchange admin center (EAC). Using precanned filters, you can do the following:
  
    
    

- Determine the scope of recipients.
    
  
- Add conditional filtering based on properties such as company, department, and state or region.
    
  
- Add custom attributes for recipients. For more information, see  [Custom attributes](custom-attributes.md).
    
  
The following parameters are considered precanned filters:
  
    
    

-  _IncludedRecipients_
    
  
-  _ConditionalCompany_
    
  
-  _ConditionalDepartment_
    
  
-  _ConditionalStateOrProvince_
    
  
-  _ConditionalCustomAttribute1_-15.
    
  
Precanned filters are available for the following cmdlets:
  
    
    

-  [New-DynamicDistributionGroup](http://technet.microsoft.com/library/e9920bd1-06c1-4f75-992f-dd7fc98a5c2b.aspx)
    
  
-  [Set-DynamicDistributionGroup](http://technet.microsoft.com/library/943626ad-8455-4867-ab9a-855bab62c9c3.aspx)
    
  
-  [New-EmailAddressPolicy](http://technet.microsoft.com/library/23b6e364-b56e-4c5a-bc71-ff5652d7e42b.aspx)
    
  
-  [Set-EmailAddressPolicy](http://technet.microsoft.com/library/c5829edd-8b7d-4437-b17f-bae76ea237e8.aspx)
    
  
-  [New-AddressList](http://technet.microsoft.com/library/2bcee6db-01d4-40ad-9595-33356a4025c5.aspx)
    
  
-  [Set-AddressList](http://technet.microsoft.com/library/72f87402-659c-4ae0-966b-42e1098e0fee.aspx)
    
  
-  [New-GlobalAddressList](http://technet.microsoft.com/library/9349a281-f92f-40f9-bf29-2a2e138c2783.aspx)
    
  
-  [Set-GlobalAddressList](http://technet.microsoft.com/library/96bf236f-0fb8-44db-9b22-ddc0933db951.aspx)
    
  

### Example

This example describes using precanned filters in the Exchange Management Shell to create a dynamic distribution group. The syntax in this example is similar but not identical to the syntax you would use to create an email address policy, address list, or GAL. When creating a precanned filter, you should ask the following questions: 
  
    
    

- From which organizational unit (OU) do you want to include recipients? (This question corresponds to the  _RecipientContainer_ parameter.)
    
    > [!NOTE]
      > Selecting the OU for this purpose applies only when creating dynamic distribution groups, and not when creating email address policies, address lists, or GALs. 
- What type of recipients do you want to include? (This question corresponds to the  _IncludedRecipients_ parameter.)
    
  
- What additional conditions do you want to include in the filter? (This question corresponds to the  _ConditionalCompany_,  _ConditionalDepartment_,  _ConditionalStateOrProvince_, and  _ConditionalCustomAttribute_ parameters.)
    
  
This example creates the dynamic distribution group Contoso Finance for user mailboxes in the OU Contoso.com/Users and specifies the condition to include only recipients who have the **Department** attribute defined as Finance and the **Company** attribute defined as Contoso.
  
    
    



```

New-DynamicDistributionGroup -Name "Contoso Finance" -OrganizationalUnit Contoso.com/Users -RecipientContainer Contoso.com/Users -IncludedRecipients MailboxUsers -ConditionalDepartment "Finance" -ConditionalCompany "Contoso"
```

This example displays the properties of this new dynamic distribution group.
  
    
    



```
Get-DynamicDistributionGroup -Identity "Contoso Finance" | Format-List Recipient*,Included*
```

 [Precanned filters](#PF)
  
    
    

## Custom filters using the RecipientFilter parameter
<a name="RFP"> </a>

If precanned filters don't meet your needs for creating or modifying dynamic distribution groups, email address policies, and address lists, you can create a custom filter by using the  _RecipientFilter_ parameter.
  
    
    
The recipient filter parameter is available for the following cmdlets:
  
    
    

-  [New-DynamicDistributionGroup](http://technet.microsoft.com/library/e9920bd1-06c1-4f75-992f-dd7fc98a5c2b.aspx)
    
  
-  [Set-DynamicDistributionGroup](http://technet.microsoft.com/library/943626ad-8455-4867-ab9a-855bab62c9c3.aspx)
    
  
-  [New-EmailAddressPolicy](http://technet.microsoft.com/library/23b6e364-b56e-4c5a-bc71-ff5652d7e42b.aspx)
    
  
-  [Set-EmailAddressPolicy](http://technet.microsoft.com/library/c5829edd-8b7d-4437-b17f-bae76ea237e8.aspx)
    
  
-  [New-AddressList](http://technet.microsoft.com/library/2bcee6db-01d4-40ad-9595-33356a4025c5.aspx)
    
  
-  [Set-AddressList](http://technet.microsoft.com/library/72f87402-659c-4ae0-966b-42e1098e0fee.aspx)
    
  
-  [New-GlobalAddressList](http://technet.microsoft.com/library/9349a281-f92f-40f9-bf29-2a2e138c2783.aspx)
    
  
-  [Set-GlobalAddressList](http://technet.microsoft.com/library/96bf236f-0fb8-44db-9b22-ddc0933db951.aspx)
    
  
For more information about the filterable properties you can use with the  _RecipientFilter_ parameter, see [Filterable properties for the -RecipientFilter parameter](filterable-properties-for-the-recipientfilter-parameter.md).
  
    
    

### Example

The following example uses the  _RecipientFilter_ parameter to create a dynamic distribution group. The syntax in this example is similar but not identical to the syntax you use to create an email address policy, address list, or GAL.
  
    
    
This example uses custom filters to create a dynamic distribution group for user mailboxes that have the **Company** attribute defined as Contoso and the **Office** attribute defined as North Building.
  
    
    



```
New-DynamicDistributionGroup -Name AllContosoNorth -OrganizationalUnit contoso.com/Users -RecipientFilter { ((RecipientType -eq 'UserMailbox') -and (Company -eq 'Contoso') -and (Office -eq 'North Building')) }
```

 [Precanned filters](#PF)
  
    
    

## Custom filters using the Filter parameter
<a name="FP"> </a>

You can use the  _Filter_ parameter to filter the results of a command to specify which objects to retrieve. For example, instead of retrieving all users or groups, you can specify a set of users or groups by using a filter string. This type of filter doesn't modify any configuration or attributes of objects. It only modifies the set of objects that the command returns.
  
    
    
Using the  _Filter_ parameter to modify command results is known asserver-side filtering. Server-side filtering submits the command and the filter to the server for processing. The Exchange Management Shell also supports client-side filtering, in which the command retrieves all objects from the server and then applies the filter in the local console window. To perform client-side filtering, use the **Where-Object** cmdlet. For more information about server-side and client-side filtering, see "How to Filter Data" in [Working with Command Output](http://technet.microsoft.com/library/8320e1a5-d3f5-4615-878d-b23e2aaa6b1e.aspx).
  
    
    
To find the filterable properties for cmdlets that have the  _Filter_ parameter, you can run the **Get** command against an object and format the output by pipelining the **Format-List** parameter. Most of the returned values will be available for use in the _Filter_ parameter. The following example returns a detailed list for the mailbox Ayla.
  
    
    



```
Get-Mailbox -Identity Ayla | Format-List
```

The  _Filter_ parameter is available for the following cmdlets:
  
    
    

-  [Get-ActiveSyncDevice](http://technet.microsoft.com/library/06a82fdc-9bf7-43c7-8471-d977034d3560.aspx)
    
  
-  [Get-ActiveSyncDeviceClass](http://technet.microsoft.com/library/f87f0260-b1f3-4315-b71b-e381bd0ebc15.aspx)
    
  
-  [Get-CASMailbox](http://technet.microsoft.com/library/d80a5990-9106-4eb8-bba8-b3975805c325.aspx)
    
  
-  [Get-Contact](http://technet.microsoft.com/library/59315afb-fab5-4984-b3a1-ba1f82df8a10.aspx)
    
  
-  [Get-DistributionGroup](http://technet.microsoft.com/library/d84f5670-f3ac-4d63-a6ac-af9de67677c5.aspx)
    
  
-  [Get-DynamicDistributionGroup](http://technet.microsoft.com/library/d97ee738-dfa1-464b-855a-4242e8065473.aspx)
    
  
-  [Get-Group](http://technet.microsoft.com/library/1dff448b-e4ac-45b8-9a60-2ab3b5859559.aspx)
    
  
-  [Get-Mailbox](http://technet.microsoft.com/library/8a5a6eb9-4a75-47f9-ae3b-a3ba251cf9a8.aspx)
    
  
-  [Get-MailboxStatistics](http://technet.microsoft.com/library/cec76f70-941f-4bc9-b949-35dcc7671146.aspx)
    
  
-  [Get-MailContact](http://technet.microsoft.com/library/d254bdd5-d497-424c-97ad-d7e8f7e73c27.aspx)
    
  
-  [get-MailPublicFolder](http://technet.microsoft.com/library/da05e6cb-8ab1-4ba9-ae42-d0f631daec85.aspx)
    
  
-  [Get-MailUser](http://technet.microsoft.com/library/37b36f1c-95ec-4896-a08a-985ef4aa23b7.aspx)
    
  
-  [Get-Message](http://technet.microsoft.com/library/d6020f77-c852-46f6-b7c5-5ca6feae0fdf.aspx)
    
  
-  [Get-MobileDevice](http://technet.microsoft.com/library/ce8a4142-23c1-47d5-89c5-961bd6e9d162.aspx)
    
  
-  [Get-Queue](http://technet.microsoft.com/library/df73c45e-3797-4da5-95e3-8478f48d06c1.aspx)
    
  
-  [Get-QueueDigest](http://technet.microsoft.com/library/64a6d710-0297-453b-aa35-3ae0a65bd81e.aspx)
    
  
-  [Get-Recipient](http://technet.microsoft.com/library/2ce6250f-0ad3-4b29-870c-e1d6e1e154bc.aspx)
    
  
-  [get-RemoteMailbox](http://technet.microsoft.com/library/8a668da4-9582-470f-a7fd-27b72e748b47.aspx)
    
  
-  [Get-RoleGroup](http://technet.microsoft.com/library/369800ff-fced-4d1c-adb0-1ddbe798670d.aspx)
    
  
-  [Get-SecurityPrincipal](http://technet.microsoft.com/library/98d70e10-6972-4317-88d0-59f99845cf15.aspx)
    
  
-  [Get-StoreUsageStatistics](http://technet.microsoft.com/library/0fd00fe0-de0e-48d2-b9fd-44220455cb8e.aspx)
    
  
-  [Get-ThrottlingPolicyAssociation](http://technet.microsoft.com/library/45e1248f-89c2-467c-8d5d-de1367111e08.aspx)
    
  
-  [Get-UMMailbox](http://technet.microsoft.com/library/4c652c1a-2f0e-45ff-99ca-d194057f1550.aspx)
    
  
-  [Get-User](http://technet.microsoft.com/library/2a33c9e6-33da-438c-912d-28ce3f4c9afb.aspx)
    
  
-  [Get-UserPhoto](http://technet.microsoft.com/library/a9b22e66-a511-4a47-ba50-a0fc9c204fcc.aspx)
    
  
-  [Remove-Message](http://technet.microsoft.com/library/15d5987b-bedd-437e-b86a-6b0e80619fde.aspx)
    
  
-  [Resume-Message](http://technet.microsoft.com/library/c15f872c-af1b-48ca-b95d-cca1b0a78977.aspx)
    
  
-  [Resume-Queue](http://technet.microsoft.com/library/ca3da195-5f4f-45b4-9941-ee6aec79ea3d.aspx)
    
  
-  [Retry-Queue](http://technet.microsoft.com/library/a75a524b-2491-47b2-83e6-922cd0887c6d.aspx)
    
  
-  [Suspend-Message](http://technet.microsoft.com/library/3c35583b-8691-4ec8-83e3-daa3090a4185.aspx)
    
  
-  [Suspend-Queue](http://technet.microsoft.com/library/7dca48c4-69a1-4157-a50e-88907dd32d04.aspx)
    
  
For more information about the filterable properties you can use with the  _Filter_ parameter, see [Filterable Properties for the -Filter Parameter](http://technet.microsoft.com/library/b02b0005-2fb6-4bc2-8815-305259fa5432.aspx).
  
    
    

### Example

This example uses the  _Filter_ parameter to return information about users whose title contains the word "manager".
  
    
    

```
Get-User -Filter {Title -like 'Manager*'}
```

 [Precanned filters](#PF)
  
    
    

## Custom filters using the ContentFilter parameter
<a name="CFP"> </a>

You can use the  _ContentFilter_ parameter to select specific message content to export when using the [New-MailboxExportRequest](http://technet.microsoft.com/library/1625c25a-7cc9-459c-97ea-281ac421bbce.aspx) cmdlet. If the command finds a message that contains the match to the content filter, it exports the message to a .pst file.
  
    
    

### Example

This example creates an export request that searches Ayla's mailbox for messages where the body contains the phrase "company prospectus". If that phrase is found, the command exports all messages with that phrase to a .pst file.
  
    
    

```
New-MailboxExportRequest -Mailbox Ayla -ContentFilter {Body -like "company prospectus*"}
```

For more information about the filterable properties you can use with the  _ContentFilter_ parameter, see [Filterable Properties for the -ContentFilter Parameter](http://technet.microsoft.com/library/cf504a59-1938-489c-bb48-b27b2ac3234e.aspx).
  
    
    
 [Precanned filters](#PF)
  
    
    

## Additional OPATH syntax information
<a name="OPATH"> </a>

When creating your own custom filters, be aware of the following:
  
    
    

- Use braces { } around the entire OPATH syntax string with the  _Filter_ or _RecipientFilter_ parameter.
    
  
- Include the hyphen before all operators. The most common operators include:
    
  - **-and**
    
  
  - **-or**
    
  
  - **-not**
    
  
  - **-eq** (equals)
    
  
  - **-ne** (not equal)
    
  
  - **-lt** (less than)
    
  
  - **-gt** (greater than)
    
  
  - **-like** (string comparison)
    
  
  - **-notlike** (string comparison)
    
  
- Many of the properties for the  _RecipientFilter_ and _ Filter_ parameters accept wildcard characters. If you use a wildcard character, use the **like** operator instead of the **eq** operator. The **like** operator is used to find pattern matches in rich types, such as strings, whereas the **eq** operator is used to find an exact match.
    
  
- Run the following commands to get information about operators you can use:
    
  -  `Help about_logical_operator`
    
  
  -  `Help about_comparison_operator`
    
  
- You can use most properties of recipient types to create filter strings. For information about filterable properties you can use with a specific cmdlet, see the cmdlet reference topics in  [Exchange Management Shell](http://technet.microsoft.com/library/925ad66f-2f05-4269-9923-c353d9c19312.aspx).
    
  

## Recipient filter documentation
<a name="documentation"> </a>

The following table contains links to topics that will help you learn more about the filterable properties that you can use with Exchange recipient commands.
  
    
    


|**Topic**|**Description**|
|:-----|:-----|
| [Filterable properties for the -RecipientFilter parameter](filterable-properties-for-the-recipientfilter-parameter.md) <br/> |Learn more about the filterable properties for the  _RecipientFilter_ parameter. <br/> |
| [Filterable Properties for the -Filter Parameter](http://technet.microsoft.com/library/b02b0005-2fb6-4bc2-8815-305259fa5432.aspx) <br/> |Learn more about the filterable properties for the  _Filter_ parameter. <br/> |
| [Filterable Properties for the -ContentFilter Parameter](http://technet.microsoft.com/library/cf504a59-1938-489c-bb48-b27b2ac3234e.aspx) <br/> |Learn more about using the  _ContentFilter_ parameter when using the **New-MailboxExportRequest** cmdlet. <br/> |
   
 [Precanned filters](#PF)
  
    
    

