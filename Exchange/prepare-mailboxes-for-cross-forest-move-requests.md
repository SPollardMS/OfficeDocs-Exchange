---
title: Prepare mailboxes for cross-forest move requests
ms.prod: EXCHANGE
ms.assetid: fdbed4fc-a77e-40d5-a211-863b05d74784
---



# Prepare mailboxes for cross-forest move requests
 **Summary**: Learn about preparing mailboxes for cross-forest moves in Exchange 2016.
Mailbox moves and mailbox migrations in Exchange 2016 from one forest to another require that you prepare the destination forest, which is made easier by Exchange tools and cmdlets. Exchange 2016 supports mailbox moves and migrations using the Exchange Management Shell, specifically the **New-MoveRequest** and **New-MigrationBatch** cmdlets. You can also move the mailbox in the Exchange admin center (EAC).
  
    
    

To move a mailbox from an Exchange 2016 forest to another Exchange 2016 forest, the Exchange 2016 target forest needs to contain a valid mail-enabled user with a specified set of Active Directory attributes. If there is at least one Exchange 2016 Mailbox server deployed in the forest, the forest is considered an Exchange 2016 forest.
To prepare for the mailbox move, you have to create mail-enabled users with the required attributes in the target forest. Here are two recommended approaches to creating mail-enable users with the necessary attributes:
  
    
    


- If you deployed Identity Lifecycle Manager (ILM) for cross-forest global address list (GAL) synchronization, the recommended approach to creating the mail-enabled user is to use Microsoft Identity Manager 2016 Service Pack 1. We've created sample code that you can use to learn how to customize ILM to synchronize the source mailbox user and target mail user.
    
    For more information, including how to download the sample code, see  [Prepare Mailboxes for Cross-Forest Moves Using Sample Code](http://technet.microsoft.com/library/f35ac7a5-bb84-4653-b6d0-65906e93627b.aspx).
    
  
- If you created the target mail user using an Active Directory tool other than ILM or Microsoft Identity Integration Server (MIIS), use the **Update-Recipient** cmdlet with the _Identity_ parameter to run the Address List service to generate the **LegacyExchangeDN** for the target mail user. We have created a sample PowerShell script that reads from and writes to Active Directory and calls the **Update-Recipient** cmdlet.
    
    For more information about using the sample script, see  [Prepare mailboxes for cross-forest moves using the Exchange Management Shell](prepare-mailboxes-for-cross-forest-moves-using-the-exchange-management-shell.md).
    
  
After creating the target mail user, you can then run the **New-MoveRequest** or the **New-MigrationBatch** cmdlets to move the mailbox to the target Exchange 2016 forest.For more information about remote move requests, see the following topics:
-  [New-MigrationBatch](http://technet.microsoft.com/library/4f797f11-e4ef-48f9-83ab-dda8a3f61e2b.aspx)
    
  
-  [New-MoveRequest](http://technet.microsoft.com/library/c28ca2ce-963f-4676-81c3-cef3c290ee7b.aspx)
    
  
For more information about remote mailbox moves and remote legacy moves, see  [Move Mailboxes to Exchange 2016](https://technet.microsoft.com/en-us/library/mt473797%28v=exchg.150%29.aspx).The remainder of this topic describes the Active Directory mail user attributes that are required for a mailbox move. These attributes are configured for you when you use either the code or the script to prepare for the mailbox move. However, you can manually copy these attributes using an Active Directory editor.
## Active Directory user attributes required for a mailbox move

To support a remote mailbox move, the mail user object in the target Exchange 2016 forest must have the Active Directory attributes that are described in this section:
  
    
    

- Mandatory attributes
    
  
- Optional attributes
    
  
- Linked attributes
    
  
- Linked user attributes
    
  
- Resource mailbox attributes
    
  
- Additional attributes
    
  

### Mandatory attributes

The following table lists the minimum set of attributes that need to be configured in ILM on the target mail user for the **New-MoveRequest** cmdlet to function correctly.
  
    
    

**Mail user's attributes**


|**Mail user's Active Directory attributes**|**Action**|
|:-----|:-----|
|**displayName** <br/> |Copy the corresponding attribute of the source mailbox or generate a new value.  <br/> |
|**Mail** <br/> |Directly copy the corresponding attribute of the source mailbox.  <br/> |
|**mailNickname** <br/> |Copy the corresponding attribute of the source mailbox or generate a new value.  <br/> |
|**msExchArchiveGUID and msExchArchiveName** <br/> |Directly copy the corresponding attribute of the source mailbox. Attributes are only available if the source mailbox is Exchange 2010 or later.  <br/> |
|**msExchMailboxGUID** <br/> |Directly copy the corresponding attribute of the source mailbox.  <br/> |
|**msExchRecipientDisplayType** <br/> |-2147483642 (decimal) //equivalent to 0x80000006 (hex).  <br/> |
|**msExchRecipientTypeDetails** <br/> |128 (decimal) /0x80 (hex).  <br/> |
|**msExchUserCulture** <br/> |Directly copy the corresponding attribute of the source mailbox.  <br/> |
|**msExchVersion** <br/> |44220983382016 (decimal).  <br/> |
|**cn** <br/> |Copy the corresponding attribute of the source mailbox or generate a new value.  <br/> |
|**proxyAddresses** <br/> |Copy source mailbox's **proxyAddresses** attribute. Additionally, copy source mailbox's **LegacyExchangeDN** as an X500 address in the **proxyAddresses** attribute of the target mail user. <br/> > [!NOTE]> The **proxyAddresses** of the source mailbox user must contain an SMTP address that matches the authoritative domain of the target forest. This allows the **New-MoveRequest** cmdlet to correctly select the **targetAddress** of the source mail-enabled user (converted from the source mailbox user after the mailbox move request is complete) to ensure that mail routing is still functional.          |
|**sAMAccountName** <br/> |Copy the corresponding attribute of the source mailbox or generate a new value.  <br/> Ensure that the value is unique within the target forest domain that the target mail user belongs to.  <br/> |
|**targetAddress** <br/> |Set to an SMTP address in the **proxyAddresses** attribute of the source mailbox. <br/> This SMTP address must belong to the authoritative domain of the source forest.  <br/> |
|**userAccountControl** <br/> |Constant: 514 //equivalent to 0x202, ACCOUNTDISABLE | NORMAL_ACCOUNT.  <br/> |
|**userPrincipalName** <br/> |Copy the corresponding attribute of the source mailbox or generate a new value. Because the mail user is logon disabled, this **userPrincipalName** isn't used. <br/> |
   

### Optional attributes

It isn't mandatory that the following attributes are configured for the **New-MoveRequest** cmdlet to function correctly; however, synchronizing them provides a better end-to-end user experience after moving the mailbox. Because the GAL in the target forest displays this target mail user, you should set the following GAL-related attributes.
  
    
    

**GAL-related attributes**


|**Mail user's Active Directory attributes**|**Action**|
|:-----|:-----|
|**c** <br/> |Directly copy the corresponding attribute of the source mailbox.  <br/> |
|**co** <br/> |Directly copy the corresponding attribute of the source mailbox.  <br/> |
|**countryCode** <br/> |Directly copy the corresponding attribute of the source mailbox.  <br/> |
|**company** <br/> |Directly copy the corresponding attribute of the source mailbox.  <br/> |
|**department** <br/> |Directly copy the corresponding attribute of the source mailbox.  <br/> |
|**facsimileTelephoneNumber** <br/> |Directly copy the corresponding attribute of the source mailbox.  <br/> |
|**givenName** <br/> |Directly copy the corresponding attribute of the source mailbox.  <br/> |
|**homePhone** <br/> |Directly copy the corresponding attribute of the source mailbox.  <br/> |
|**info** <br/> |Directly copy the corresponding attribute of the source mailbox.  <br/> |
|**initials** <br/> |Directly copy the corresponding attribute of the source mailbox.  <br/> |
|**l** <br/> |Directly copy the corresponding attribute of the source mailbox.  <br/> |
|**mobile** <br/> |Directly copy the corresponding attribute of the source mailbox.  <br/> |
|**msExchAssistantName** <br/> |Directly copy the corresponding attribute of the source mailbox.  <br/> |
|**msExchHideFromAddressLists** <br/> |Directly copy the corresponding attribute of the source mailbox.  <br/> |
|**otherHomePhone** <br/> |Directly copy the corresponding attribute of the source mailbox.  <br/> |
|**otherTelephone** <br/> |Directly copy the corresponding attribute of the source mailbox.  <br/> |
|**pager** <br/> |Directly copy the corresponding attribute of the source mailbox.  <br/> |
|**physicalDeliveryOfficeName** <br/> |Directly copy the corresponding attribute of the source mailbox.  <br/> |
|**postalCode** <br/> |Directly copy the corresponding attribute of the source mailbox.  <br/> |
|**sn** <br/> |Directly copy the corresponding attribute of the source mailbox.  <br/> |
|**st** <br/> |Directly copy the corresponding attribute of the source mailbox.  <br/> |
|**streetAddress** <br/> |Directly copy the corresponding attribute of the source mailbox.  <br/> |
|**telephoneAssistant** <br/> |Directly copy the corresponding attribute of the source mailbox.  <br/> |
|**telephoneNumber** <br/> |Directly copy the corresponding attribute of the source mailbox.  <br/> |
|**title** <br/> |Directly copy the corresponding attribute of the source mailbox.  <br/> |
   

### Linked attributes

A linked attribute is an Active Directory attribute that references other Active Directory objects in the local forest. You can't directly copy the linked attribute values from a mailbox in the source forest to a mail user in the target forest. First, you need to find the Active Directory objects that the source mailbox attribute refers to in the source forest. Then, you need to find the corresponding Active Directory objects in the target forest for the previously mentioned Active Directory object in the source forest. And finally, set the target mail user's attribute to refer to the Active Directory objects in the target forest.
  
    
    

**Linked attributes**


|**Mail User's Active Directory attributes**|**Action**|
|:-----|:-----|
|**altRecipient** <br/> |Correspond to the source mailbox's **altRecipient** attribute. <br/> |
|**deliverAndRedirect** <br/> |Directly copy the corresponding attribute of the source mailbox. This attribute is a Boolean value that should be set along with **altRecipient**. <br/> |
|**Manager** (and its backlinks) <br/> |Correspond to the source mailbox's manager attribute.  <br/> |
|**MemberOf** (backlinks) <br/> |This is the backlink of group member attribute.  <br/> |
|**publicDelegates** (and its backlinks) <br/> |Correspond to the source mailbox's **publicDelegates** attribute. <br/> |
   

### Linked user attributes

If you want to move a mailbox to an Exchange 2016 resource forest, the mailbox in the resource forest is considered a linked mailbox. In this scenario, you need to create a linked mail user in the (target) resource forest. To create a linked mail user, you need to set the attributes shown in the following table.
  
    
    

**Linked mail user attributes**


|**Mail user's Active Directory attributes**|**Action**|
|:-----|:-----|
|**msExchMasterAccountHistory** <br/> |Directly copy the corresponding attribute of the source mailbox.  <br/> |
|**msExchMasterAccountSid** <br/> |If the source mailbox has **msExchMasterAccountSid**, copy it. Otherwise, copy the source mailbox's **objectSid**. <br/> |
|**msExchRecipientDisplayType** <br/> |Constant:-1073741818 (decimal) //equivalent to *unsigned* 0xC0000006.  <br/> |
   

> [!NOTE]
> A linked mailbox can only be created if there's forest trust between the source forest and target forest. 
  
    
    

If the source object is disabled and the **msExchMasterAccountSid** attribute is set to self (resource mailbox, shared mailbox), don't stamp anything on the target user.
  
    
    
If the source object is disabled and the **msExchMasterAccountSid** attribute isn't set, the mailbox is invalid.
  
    
    
If the source object is enabled and the **msExchMasterAccountSid** attribute is set, the mailbox is invalid.
  
    
    

### Resource mailbox attributes

If you want to move a resource mailbox to an Exchange 2016 forest, you need to set the attributes shown in the following table on the target mail user.
  
    
    

**Resource mailbox attributes**


|**Mail user's Active Directory attributes**|**Action**|
|:-----|:-----|
|**msExchRecipientDisplayType** <br/> | If the source mailbox is a conference room: <br/> **Constant** -2147481850 (decimal) //equivalent to *unsigned* 0x80000706. <br/>  If the source mailbox is an equipment mailbox: <br/> **Constant** -2147481594 (decimal) //equivalent to *unsigned* 0x80000806. <br/> |
|**msExchResourceCapacity** <br/> |Directly copy the corresponding attribute of the source mailbox.  <br/> |
|**msExchResourceDisplay** <br/> |Directly copy the corresponding attribute of the source mailbox.  <br/> |
|**msExchResourceMetaData** <br/> |Directly copy the corresponding attribute of the source mailbox.  <br/> |
|**msExchResourceSearchProperties** <br/> |Directly copy the corresponding attribute of the source mailbox.  <br/> |
   

### Additional attributes


**Resource mailbox attributes**


|**Mail User's Active Directory attributes**|**Description**|
|:-----|:-----|
|**comment** <br/> |Directly copy the corresponding attribute of the source mailbox.  <br/> |
|**deletedItemFlags** <br/> |Directly copy the corresponding attribute of the source mailbox.  <br/> |
|**delivContLength** <br/> |Directly copy the corresponding attribute of the source mailbox.  <br/> |
|**departmentNumber** <br/> |Directly copy the corresponding attribute of the source mailbox.  <br/> |
|**description** <br/> |Directly copy the corresponding attribute of the source mailbox.  <br/> |
|**division** <br/> |Directly copy the corresponding attribute of the source mailbox.  <br/> |
|**employeeID** <br/> |Directly copy the corresponding attribute of the source mailbox.  <br/> |
|**employeeNumber** <br/> |Directly copy the corresponding attribute of the source mailbox.  <br/> |
|**employeeType** <br/> |Directly copy the corresponding attribute of the source mailbox.  <br/> |
|**extensionAttribute1-15** <br/> |Directly copy the corresponding attribute of the source mailbox.  <br/> |
|**homePostalAddress** <br/> |Directly copy the corresponding attribute of the source mailbox.  <br/> |
|**internationalISDNNumber** <br/> |Directly copy the corresponding attribute of the source mailbox.  <br/> |
|**ipPhone** <br/> |Directly copy the corresponding attribute of the source mailbox.  <br/> |
|**language** <br/> |Directly copy the corresponding attribute of the source mailbox.  <br/> |
|**lmPwdHistory** <br/> |Directly copy the corresponding attribute of the source mailbox.  <br/> |
|**localeID** <br/> |Directly copy the corresponding attribute of the source mailbox.  <br/> |
|**mAPIRecipient** <br/> |Directly copy the corresponding attribute of the source mailbox.  <br/> |
|**middleName** <br/> |Directly copy the corresponding attribute of the source mailbox.  <br/> |
|**msDS-PhoneticCompanyName** <br/> |Directly copy the corresponding attribute of the source mailbox.  <br/> |
|**msDS-PhoneticDepartment** <br/> |Directly copy the corresponding attribute of the source mailbox.  <br/> |
|**msDS-PhoneticDisplayName** <br/> |Directly copy the corresponding attribute of the source mailbox.  <br/> |
|**msDS-PhoneticFirstName** <br/> |Directly copy the corresponding attribute of the source mailbox.  <br/> |
|**msDS-PhoneticLastName** <br/> |Directly copy the corresponding attribute of the source mailbox.  <br/> |
|**msExchBlockedSendersHash** <br/> |Directly copy the corresponding attribute of the source mailbox.  <br/> |
|**msExchELCExpirySuspensionEnd** <br/> |Directly copy the corresponding attribute of the source mailbox.  <br/> |
|**msExchELCExpirySuspensionStart** <br/> |Directly copy the corresponding attribute of the source mailbox.  <br/> |
|**msExchELCMailboxFlags** <br/> |Directly copy the corresponding attribute of the source mailbox.  <br/> |
|**msExchExternalOOFOptions** <br/> |Directly copy the corresponding attribute of the source mailbox.  <br/> |
|**msExchMessageHygieneFlags** <br/> |Directly copy the corresponding attribute of the source mailbox.  <br/> |
|**msExchMessageHygieneSCLDeleteThreshold** <br/> |Directly copy the corresponding attribute of the source mailbox.  <br/> |
|**msExchMessageHygieneSCLJunkThreshold** <br/> |Directly copy the corresponding attribute of the source mailbox.  <br/> |
|**msExchMessageHygieneSCLQuarantineThreshold** <br/> |Directly copy the corresponding attribute of the source mailbox.  <br/> |
|**msExchMessageHygieneSCLRejectThreshold** <br/> |Directly copy the corresponding attribute of the source mailbox.  <br/> |
|**msExchMDBRulesQuota** <br/> |Directly copy the corresponding attribute of the source mailbox.  <br/> |
|**msExchPoliciesExcluded** <br/> |Directly copy the corresponding attribute of the source mailbox.  <br/> |
|**msExchSafeRecipientsHash** <br/> |Directly copy the corresponding attribute of the source mailbox.  <br/> |
|**msExchSafeSendersHash** <br/> |Directly copy the corresponding attribute of the source mailbox.  <br/> |
|**msExchUMSpokenName** <br/> |Directly copy the corresponding attribute of the source mailbox.  <br/> |
|**otherFacsimileTelephoneNumber** <br/> |Directly copy the corresponding attribute of the source mailbox.  <br/> |
|**otherIpPhone** <br/> |Directly copy the corresponding attribute of the source mailbox.  <br/> |
|**otherMobile** <br/> |Directly copy the corresponding attribute of the source mailbox.  <br/> |
|**otherPager** <br/> |Directly copy the corresponding attribute of the source mailbox.  <br/> |
|**preferredDeliveryMethod** <br/> |Directly copy the corresponding attribute of the source mailbox.  <br/> |
|**personalPager** <br/> |Directly copy the corresponding attribute of the source mailbox.  <br/> |
|**personalTitle** <br/> |Directly copy the corresponding attribute of the source mailbox.  <br/> |
|**photo** <br/> |Directly copy the corresponding attribute of the source mailbox.  <br/> |
|**pOPCharacterSet** <br/> |Directly copy the corresponding attribute of the source mailbox.  <br/> |
|**pOPContentFormat** <br/> |Directly copy the corresponding attribute of the source mailbox.  <br/> |
|**postalAddress** <br/> |Directly copy the corresponding attribute of the source mailbox.  <br/> |
|**postOfficeBox** <br/> |Directly copy the corresponding attribute of the source mailbox.  <br/> |
|**primaryInternationalISDNNumber** <br/> |Directly copy the corresponding attribute of the source mailbox.  <br/> |
|**primaryTelexNumber** <br/> |Directly copy the corresponding attribute of the source mailbox.  <br/> |
|**showInAdvancedViewOnly** <br/> |Directly copy the corresponding attribute of the source mailbox.  <br/> |
|**street** <br/> |Directly copy the corresponding attribute of the source mailbox.  <br/> |
|**terminalServer** <br/> |Directly copy the corresponding attribute of the source mailbox.  <br/> |
|**textEncodedORAddress** <br/> |Directly copy the corresponding attribute of the source mailbox.  <br/> |
|**thumbnailLogo** <br/> |Directly copy the corresponding attribute of the source mailbox.  <br/> |
|**thumbnailPhoto** <br/> |Directly copy the corresponding attribute of the source mailbox.  <br/> |
|**url** <br/> |Directly copy the corresponding attribute of the source mailbox.  <br/> |
|**userCert** <br/> |Directly copy the corresponding attribute of the source mailbox.  <br/> |
|**userCertificate** <br/> |Directly copy the corresponding attribute of the source mailbox.  <br/> |
|**userSMIMECertificate** <br/> |Directly copy the corresponding attribute of the source mailbox.  <br/> |
|**wWWHomePage** <br/> |Directly copy the corresponding attribute of the source mailbox.  <br/> |
   
