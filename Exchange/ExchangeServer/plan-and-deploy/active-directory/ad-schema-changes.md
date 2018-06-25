---
title: "Exchange 2016 Active Directory schema changes"
ms.author: dstrome
author: dstrome
manager: serdars
ms.date: 4/19/2018
ms.audience: ITPro
ms.topic: conceptual
ms.prod: exchange-server-itpro
localization_priority: Critical
ms.collection: Strat_EX_Admin
ms.assetid: 7e879e4e-1124-4a41-94d2-c64500beb24e
description: "Summary: What new schema classes and attributes Exchange Server 2016 adds to Active Directory, and which existing ones it modifies."
---

# Exchange 2016 Active Directory schema changes

 **Summary**: What new schema classes and attributes Exchange Server 2016 adds to Active Directory, and which existing ones it modifies.
  
This reference topic provides a summary of the Active Directory schema changes that are made when you install Exchange 2016. Refer to the .ldf files for more information about changes to the Active Directory schema. The .ldf files are located in the \amd64\Setup\Data\ directory in the Exchange installation files.
  
Exchange 2016 schema updates are cumulative. Each release includes all of the changes included in previous releases. This means that if you skip a release, you may still need to apply schema updates even if the release you're installing doesn't include its own changes. The following table gives examples of when your Active Directory will be updated, and when it's already up-to-date.
  
|
|
|**Current Exchange 2016 release installed**|**New Exchange 2016 release being installed**|**Are schema updates required?**|
|:-----|:-----|:-----|
|Release to Manufacturing  <br/> |Cumulative Update 4  <br/> |**Yes**, updates are required. Schema updates included in CU1, CU2, and CU3 need to be applied.  <br/> |
|Cumulative Update 2  <br/> |Cumulative Update 4  <br/> |**Yes**, updates are required. Schema updates included in CU3 need to be applied.  <br/> |
|Cumulative Update 3  <br/> |Cumulative Update 4  <br/> |**No**, no updates are required. No changes were made in CU4.  <br/> |
   
> [!NOTE]
> The Active Directory schema changes identified in this topic may not apply to all editions of an Exchange Server version. > To verify that Active Directory has been successfully prepared, see the "How do you know this worked?" section in [Prepare Active Directory and domains](../../plan-and-deploy/prepare-ad-and-domains.md). 
  
## Exchange 2016 CU9 Active Directory schema changes

No changes were made to the Active Directory schema in Exchange 2016 in CU9.
  
## Exchange 2016 CU8 Active Directory schema changes

No changes were made to the Active Directory schema in Exchange 2016 in CU8.
  
## Exchange 2016 CU7 Active Directory schema changes

This section summarizes the changes that are made to the Active Directory schema when you install Exchange 2016 CU3. This section includes the following subsections:
  
- [Classes added by Exchange 2016 CU7](ad-schema-changes.md#ClassesAddCU7)
    
- [Classes modified by Exchange 2016 CU7](ad-schema-changes.md#ClassesModCU7)
    
- [Attributes added by Exchange 2016 CU7](ad-schema-changes.md#AttribAddCU7)
    
- [Attributes modified by Exchange 2016 CU7](ad-schema-changes.md#AttribModCU7)
    
- [Object IDs added by Exchange 2016 CU7](ad-schema-changes.md#ObjIDsAddCU7)
    
### Classes added by Exchange 2016 CU7
<a name="ClassesAddCU7"> </a>

This section contains the classes added in Exchange 2016 CU7.
  
|**Class**|**Change**|
|:-----|:-----|
|ms-Exch-Http-Delivery-Connector  <br/> |ntdsSchemaAdd  <br/> |
   
### Classes modified by Exchange 2016 CU7
<a name="ClassesModCU7"> </a>

This section contains the classes modified in Exchange 2016 CU7.
  
|**Class**|**Change**|**Attribute/Class**|
|:-----|:-----|:-----|
|Mail-Recipient  <br/> |add: mayContain  <br/> |msExchImmutableSid  <br/> |
   
### Attributes added by Exchange 2016 CU7
<a name="AttribAddCU7"> </a>

This section contains the attributes added in Exchange 2016 CU7.
  
- ms-Exch-Immutable-Sid
    
### Attributes modified by Exchange 2016 CU7
<a name="AttribModCU7"> </a>

This section contains the classes modified in Exchange 2016 CU7.
  
|**Class**|**Change**|**Attribute/Class**|
|:-----|:-----|:-----|
|ms-Exch-Group-Security-Flags  <br/> |ntdsSchemaModify  <br/> |replace: mapiId: 36111  <br/> |
   
### Object IDs added by Exchange 2016 CU7
<a name="ObjIDsAddCU7"> </a>

The following attribute object IDs are added when you install Exchange 2016 CU7:
  
- 1.2.840.113556.1.5.7000.62.50214
    
- 1.2.840.113556.1.4.7000.102.52161
    
## Exchange 2016 CU4 - CU6 Active Directory schema changes

No changes were made to the Active Directory schema in Exchange 2016 in CU4, CU5, or CU6.
  
## Exchange 2016 CU3 Active Directory schema changes

This section summarizes the changes that are made to the Active Directory schema when you install Exchange 2016 CU3. This section includes the following subsections:
  
- [Classes modified by Exchange 2016 CU3](ad-schema-changes.md#ClassesModCU3)
    
- [Attributes added by Exchange 2016 CU3](ad-schema-changes.md#AttribAddCU3)
    
- [Global catalog attributes added by Exchange 2016 CU3](ad-schema-changes.md#GcAttribAddCU3)
    
- [Object IDs added by Exchange 2016 CU3](ad-schema-changes.md#ObjIDsAddCU3)
    
### Classes modified by Exchange 2016 CU3
<a name="ClassesModCU3"> </a>

This section contains the classes modified in Exchange 2016 CU3.
  
|**Class**|**Change**|**Attribute/Class**|
|:-----|:-----|:-----|
|Mail-Recipient  <br/> |add: mayContain  <br/> |msExchUGEventSubscriptionLink  <br/> |
|Top  <br/> |add: mayContain  <br/> |msExchUGEventSubscriptionBL  <br/> |
   
### Attributes added by Exchange 2016 CU3
<a name="AttribAddCU3"> </a>

This section contains the attributes added in Exchange 2016 CU3.
  
- ms-Exch-UG-Event-Subscription-Link
    
- ms-Exch-UG-Event-Subscription-BL
    
### Global catalog attributes added by Exchange 2016 CU3
<a name="GcAttribAddCU3"> </a>

This section contains the global catalog attributes added in Exchange 2016 CU3.
  
- ms-Exch-UG-Event-Subscription-Link
    
- ms-Exch-UG-Event-Subscription-BL
    
### Object IDs added by Exchange 2016 CU3
<a name="ObjIDsAddCU3"> </a>

The following attribute object IDs are added when you install Exchange 2016 CU3:
  
- 1.2.840.113556.1.4.7000.102.52159
    
- 1.2.840.113556.1.4.7000.102.52160
    
## Exchange 2016 CU2 Active Directory schema changes

This section summarizes the changes that are made to the Active Directory schema when you install Exchange 2016 CU2. This section includes the following subsections:
  
- [Classes modified by Exchange 2016 CU2](ad-schema-changes.md#ClassesModCU2)
    
- [Attributes added by Exchange 2016 CU2](ad-schema-changes.md#AttribAddCU2)
    
- [Global catalog attributes added by Exchange 2016 CU2](ad-schema-changes.md#GcAttribAddCU2)
    
- [Object IDs added by Exchange 2016 CU2](ad-schema-changes.md#ObjIDsAddCU2)
    
### Classes modified by Exchange 2016 CU2
<a name="ClassesModCU2"> </a>

This section contains the classes modified in Exchange 2016 CU2.
  
|**Class**|**Change**|**Attribute/Class**|
|:-----|:-----|:-----|
|Mail-Recipient  <br/> |add: mayContain  <br/> |msExchAdministrativeUnitLink  <br/> |
|ms-Exch-Container  <br/> |add: mayContain  <br/> |msExchScopeFlags  <br/> |
|Top  <br/> |add: mayContain  <br/> |msExchAdministrativeUnitBL  <br/> |
|ms-Exch-Base-Class  <br/> |add: mayContain  <br/> |msExchUserHoldPolicies  <br/> |
   
### Attributes added by Exchange 2016 CU2
<a name="AttribAddCU2"> </a>

This section contains the attributes added in Exchange 2016 CU2.
  
- ms-Exch-Administrative-Unit-Link
    
- ms-Exch-Administrative-Unit-BL
    
### Global catalog attributes added by Exchange 2016 CU2
<a name="GcAttribAddCU2"> </a>

This section contains the global catalog attributes added in Exchange 2016 CU2.
  
- ms-Exch-Administrative-Unit-Link
    
- ms-Exch-Administrative-Unit-BL
    
### Object IDs added by Exchange 2016 CU2
<a name="ObjIDsAddCU2"> </a>

The following attribute object IDs are added when you install Exchange 2016 CU2:
  
- 1.2.840.113556.1.4.7000.102.52157
    
- 1.2.840.113556.1.4.7000.102.52158
    
## Exchange 2016 CU1 Active Directory schema changes

This section summarizes the changes that are made to the Active Directory schema when you install Exchange 2016 CU1. This section includes the following subsections:
  
- [Classes added by Exchange 2016 CU1](ad-schema-changes.md#ClassesAddCU1)
    
- [Classes modified by Exchange 2016 CU1](ad-schema-changes.md#ClassesModCU1)
    
- [Attributes added by Exchange 2016 CU1](ad-schema-changes.md#AttribAddCU1)
    
- [Indexed attributes added by Exchange 2016 CU1](ad-schema-changes.md#IndexAttribAddCU1)
    
- [Global catalog attributes added by Exchange 2016 CU1](ad-schema-changes.md#GcAttribAddCU1)
    
- [Object IDs added by Exchange 2016 CU1](ad-schema-changes.md#ObjIDsAddCU1)
    
### Classes added by Exchange 2016 CU1
<a name="ClassesAddCU1"> </a>

This section contains the classes added in Exchange 2016 CU1.
  
|**Class**|**Change**|
|:-----|:-----|
|ms-Exch-Mailbox-Policy  <br/> |ntdsSchemaAdd  <br/> |
|ms-Exch-Auth-Policy  <br/> |ntdsSchemaAdd  <br/> |
   
### Classes modified by Exchange 2016 CU1
<a name="ClassesModCU1"> </a>

This section contains the classes modified in Exchange 2016 CU1.
  
|**Class**|**Change**|**Attribute/Class**|
|:-----|:-----|:-----|
|ms-Exch-Mail-Storage  <br/> |add: mayContain  <br/> |msExchDataEncryptionPolicyLink  <br/> |
|ms-Exch-Organization-Container  <br/> |add: mayContain  <br/> |msExchDataEncryptionPolicyLink  <br/> |
|Top  <br/> |add: mayContain  <br/> |msExchDataEncryptionPolicyBL  <br/> |
|Top  <br/> |add: mayContain  <br/> |msExchAuthPolicyBL  <br/> |
|Mail-Recipient  <br/> |add: mayContain  <br/> |msExchAuthPolicyLink  <br/> |
|ms-Exch-Configuration-Unit-Container  <br/> |add: mayContain  <br/> |msExchAuthPolicyLink  <br/> |
|ms-Exch-Configuration-Unit-Container  <br/> |add: mayContain  <br/> |msExchMSOForwardSyncReplayList  <br/> |
   
### Attributes added by Exchange 2016 CU1
<a name="AttribAddCU1"> </a>

This section contains the attributes added in Exchange 2016 CU1.
  
- ms-Exch-Data-Encryption-Policy-Link
    
- ms-Exch-Data-Encryption-Policy-BL
    
- ms-Exch-Auth-Policy-Link
    
- ms-Exch-Auth-Policy-BL
    
### Indexed attributes added by Exchange 2016 CU1
<a name="IndexAttribAddCU1"> </a>

This section contains the indexed attributes added in Exchange 2016 CU1.
  
|**Attribute**|**Search flag value**|
|:-----|:-----|
|ms-Exch-Data-Encryption-Policy-Link  <br/> |1  <br/> |
   
### Global catalog attributes added by Exchange 2016 CU1
<a name="GcAttribAddCU1"> </a>

This section contains the global catalog attributes added in Exchange 2016 CU1.
  
- ms-Exch-Data-Encryption-Policy-Link
    
- ms-Exch-Data-Encryption-Policy-BL
    
- ms-Exch-Auth-Policy-Link
    
### Object IDs added by Exchange 2016 CU1
<a name="ObjIDsAddCU1"> </a>

The following class object IDs are added when you install Exchange 2016 CU1:
  
- 1.2.840.113556.1.5.7000.62.50212
    
- 1.2.840.113556.1.5.7000.62.50213
    
The following attribute object IDs are added when you install Exchange 2016 CU1:
  
- 1.2.840.113556.1.4.7000.102.52151
    
- 1.2.840.113556.1.4.7000.102.52152
    
- 1.2.840.113556.1.4.7000.102.52155
    
- 1.2.840.113556.1.4.7000.102.52156
    
## Exchange 2016 RTM Active Directory schema changes

This section summarizes the changes that are made to the Active Directory schema when you install Release to Manufacturing (RTM) version of Exchange 2016. This section includes the following subsections:
  
- [Classes added by Exchange 2016 RTM](ad-schema-changes.md#ClassesAddRTM)
    
- [Classes modified by Exchange 2016 RTM](ad-schema-changes.md#ClassesModRTM)
    
- [Attributes added by Exchange 2016 RTM](ad-schema-changes.md#AttribAddRTM)
    
- [Global catalog attributes added by Exchange 2016 RTM](ad-schema-changes.md#GlobalCatRTM)
    
- [Attributes modified by Exchange 2016 RTM](ad-schema-changes.md#AttribModRTM)
    
- [Object IDs added by Exchange 2016 RTM](ad-schema-changes.md#ObjIDsAddRTM)
    
- [Indexed attributes added by Exchange 2016 RTM](ad-schema-changes.md#IndexAttRTM)
    
- [Property sets modified by Exchange 2016 RTM](ad-schema-changes.md#PropSetsRTM)
    
- [MAPI IDs added by Exchange 2016 RTM](ad-schema-changes.md#MAPIaddRTM)
    
- [Extended rights added by Exchange 2016 RTM](ad-schema-changes.md#ExtendedAddRTM)
    
> [!NOTE]
> No changes to the Active Directory schema were made between Exchange 2016 Preview and Exchange 2016 RTM. 
  
### Classes added by Exchange 2016 RTM
<a name="ClassesAddRTM"> </a>

This section contains the classes added in Exchange 2016 RTM.
  
|**Class**|**Change**|
|:-----|:-----|
|Exch-Mapi-Virtual-Directory  <br/> |ntdsSchemaAdd  <br/> |
|Exch-Push-Notifications-App  <br/> |ntdsSchemaAdd  <br/> |
|ms-Exch-Account-Forest  <br/> |ntdsSchemaAdd  <br/> |
|ms-Exch-ActiveSync-Device-Autoblock-Threshold  <br/> |ntdsSchemaAdd  <br/> |
|ms-Exch-Auth-Auth-Config  <br/> |ntdsSchemaAdd  <br/> |
|ms-Exch-Auth-Auth-Server  <br/> |ntdsSchemaAdd  <br/> |
|ms-Exch-Auth-Partner-Application  <br/> |ntdsSchemaAdd  <br/> |
|ms-Exch-Client-Access-Rule  <br/> |ntdsSchemaModify  <br/> |
|ms-Exch-Config-Settings  <br/> |ntdsSchemaAdd  <br/> |
|ms-Exch-Encryption-Virtual-Directory  <br/> |ntdsSchemaAdd  <br/> |
|ms-Exch-Exchange-Transport-Server  <br/> |ntdsSchemaAdd  <br/> |
|ms-Exch-Hosted-Content-Filter-Config  <br/> |ntdsSchemaAdd  <br/> |
|ms-Exch-Hygiene-Configuration  <br/> |ntdsSchemaAdd  <br/> |
|ms-Exch-Intra-Organization-Connector  <br/> |ntdsSchemaModify  <br/> |
|ms-Exch-MSO-Forward-Sync-Divergence  <br/> |ntdsSchemaAdd  <br/> |
|ms-Exch-MSO-Sync-Service-Instance  <br/> |ntdsSchemaAdd  <br/> |
|ms-Exch-Mailflow-Policy  <br/> |ntdsSchemaAdd  <br/> |
|ms-Exch-Mailflow-Policy-Collection  <br/> |ntdsSchemaAdd  <br/> |
|ms-Exch-Malware-Filter-Config  <br/> |ntdsSchemaAdd  <br/> |
|ms-Exch-Organization-Upgrade-Policy  <br/> |ntdsSchemaAdd  <br/> |
|ms-Exch-Protocol-Cfg-SIP-Container  <br/> |ntdsSchemaAdd  <br/> |
|ms-Exch-Protocol-Cfg-SIP-FE-Server  <br/> |ntdsSchemaAdd  <br/> |
|ms-Exch-Resource-Policy  <br/> |ntdsSchemaAdd  <br/> |
|ms-Exch-Safe-Attachment-Protection-Config  <br/> |ntdsSchemaAdd  <br/> |
|ms-Exch-Smart-Links-Protection-Config  <br/> |ntdsSchemaAdd  <br/> |
|ms-Exch-Team-Mailbox-Provisioning-Policy  <br/> |ntdsSchemaAdd  <br/> |
|ms-Exch-Throttling-Policy  <br/> |ntdsSchemaModify  <br/> |
|ms-Exch-Unified-Policy  <br/> |ntdsSchemaAdd  <br/> |
|ms-Exch-Unified-Rule  <br/> |ntdsSchemaAdd  <br/> |
|ms-Exch-Workload-Policy  <br/> |ntdsSchemaAdd  <br/> |
   
### Classes modified by Exchange 2016 RTM
<a name="ClassesModRTM"> </a>

This section contains the classes modified in Exchange 2016 RTM.
  
|**Class**|**Change**|**Attribute/Class**|
|:-----|:-----|:-----|
|Exch-Accepted-Domain  <br/> |add:mayContain  <br/> |msExchOfflineOrgIdHomeRealmRecord  <br/> |
|Exch-Base-Class  <br/> |add:mayContain  <br/> |msExchCapabilityIdentifiers  <br/> |
|Exch-Base-Class  <br/> |add:mayContain  <br/> |msExchObjectID  <br/> |
|Exch-Base-Class  <br/> |add:mayContain  <br/> |msExchProvisioningTags  <br/> |
|Exch-Configuration-Unit-Container  <br/> |add:mayContain  <br/> |msExchArchiveRelease  <br/> |
|Exch-Configuration-Unit-Container  <br/> |add:mayContain  <br/> |msExchMailboxRelease  <br/> |
|Exch-Exchange-Server  <br/> |add:mayContain  <br/> |msExchArchiveRelease  <br/> |
|Exch-Exchange-Server  <br/> |add:mayContain  <br/> |msExchMailboxRelease  <br/> |
|Exch-MDB-Availability-Group  <br/> |add:mayContain  <br/> |msExchEvictedMembersLink  <br/> |
|Exch-OAB  <br/> |add:mayContain  <br/> |msExchLastUpdateTime  <br/> |
|Exch-OWA-Mailbox-Policy  <br/> |add:mayContain  <br/> |msExchConfigurationXML  <br/> |
|Exch-OWA-Virtual-Directory  <br/> |add:mayContain  <br/> |msExchConfigurationXML  <br/> |
|Exch-On-Premises-Organization  <br/> |add:mayContain  <br/> |msExchTrustedDomainLink  <br/> |
|Exch-Organization-Container  <br/> |add:mayContain  <br/> |msExchMaxABP  <br/> |
|Exch-Organization-Container  <br/> |add:mayContain  <br/> |msExchMaxOAB  <br/> |
|Exch-Organization-Container  <br/> |add:mayContain  <br/> |pFContacts  <br/> |
|Exch-Team-Mailbox-Provisioning-Policy  <br/> |add:mayContain  <br/> |msExchConfigurationXML  <br/> |
|Group  <br/> |add: auxiliaryClass  <br/> |msExchMailStorage  <br/> |
|Mail-Recipient  <br/> |add:mayContain  <br/> |msExchLocalizationFlags  <br/> |
|Mail-Recipient  <br/> |add:mayContain  <br/> |msExchRoleGroupType  <br/> |
|Mail-Recipient  <br/> |add:mayContain  <br/> |ms-DS-GeoCoordinates-Altitude  <br/> |
|Mail-Recipient  <br/> |add:mayContain  <br/> |ms-DS-GeoCoordinates-Latitude  <br/> |
|Mail-Recipient  <br/> |add:mayContain  <br/> |ms-DS-GeoCoordinates-Longitude  <br/> |
|Mail-Recipient  <br/> |add:mayContain  <br/> |msExchRecipientSoftDeletedStatus  <br/> |
|Mail-Recipient  <br/> |add:mayContain  <br/> |msExchWhenSoftDeletedTime  <br/> |
|Mail-Recipient  <br/> |add:mayContain  <br/> |msExchHomeMTASL  <br/> |
|Mail-Recipient  <br/> |add:mayContain  <br/> |msExchMailboxMoveSourceArchiveMDBLinkSL  <br/> |
|Mail-Recipient  <br/> |add:mayContain  <br/> |msExchMailboxMoveSourceMDBLinkSL  <br/> |
|Mail-Recipient  <br/> |add:mayContain  <br/> |msExchMailboxMoveTargetArchiveMDBLinkSL  <br/> |
|Mail-Recipient  <br/> |add:mayContain  <br/> |msExchMailboxMoveTargetMDBLinkSL  <br/> |
|Mail-Recipient  <br/> |add:mayContain  <br/> |ms-exch-group-external-member-count  <br/> |
|Mail-Recipient  <br/> |add:mayContain  <br/> |ms-exch-group-member-count  <br/> |
|Mail-Recipient  <br/> |add:mayContain  <br/> |msExchGroupExternalMemberCount  <br/> |
|Mail-Recipient  <br/> |add:mayContain  <br/> |msExchGroupMemberCount  <br/> |
|Mail-Recipient  <br/> |add:mayContain  <br/> |msExchShadowWhenSoftDeletedTime  <br/> |
|Mail-Recipient  <br/> |add:mayContain  <br/> |msExchPublicFolderMailbox  <br/> |
|Mail-Recipient  <br/> |add:mayContain  <br/> |msExchPublicFolderSmtpAddress  <br/> |
|Mail-Recipient  <br/> |add: mayContain  <br/> |msExchAuxMailboxParentObjectIdLink  <br/> |
|Mail-Recipient  <br/> |add: mayContain  <br/> |msExchStsRefreshTokensValidFrom  <br/> |
|Mail-Recipient  <br/> |add:mayContain  <br/> |msDS-ExternalDirectoryObjectId  <br/> |
|Mail-Recipient  <br/> |add:mayContain  <br/> |msExchGroupSecurityFlags  <br/> |
|Mail-Recipient  <br/> |add:mayContain  <br/> |msExchMultiMailboxDatabasesLink  <br/> |
|Ms-Exch-Organization-Container  <br/> |add:mayContain  <br/> |ms-exch-organization-flags-2  <br/> |
|Top  <br/> |add:mayContain  <br/> |msExchMultiMailboxDatabasesBL  <br/> |
|Top  <br/> |add:mayContain  <br/> |msExchMultiMailboxLocationsBL  <br/> |
|Top  <br/> |add:mayContain  <br/> |msExchAccountForestBL  <br/> |
|Top  <br/> |add:mayContain  <br/> |msExchTrustedDomainBL  <br/> |
|Top  <br/> |add:mayContain  <br/> |msExchAcceptedDomainBL  <br/> |
|Top  <br/> |add:mayContain  <br/> |msExchHygieneConfigurationMalwareBL  <br/> |
|Top  <br/> |add:mayContain  <br/> |msExchHygieneConfigurationSpamBL  <br/> |
|Top  <br/> |add:mayContain  <br/> |msExchEvictedMemebersBL  <br/> |
|Top  <br/> |add: mayContain  <br/> |msExchOABGeneratingMailboxBL  <br/> |
|Top  <br/> |add: mayContain  <br/> |msExchAuxMailboxParentObjectIdBL  <br/> |
|ms-Exch-Accepted-Domain  <br/> |add:mayContain  <br/> |msExchHygieneConfigurationLink  <br/> |
|ms-Exch-Accepted-Domain  <br/> |add:mayContain  <br/> |msExchTransportResellerSettingsLinkSL  <br/> |
|ms-Exch-Account-Forest  <br/> |possSuperiors  <br/> |msExchContainer  <br/> |
|ms-Exch-Account-Forest  <br/> |Add:mayContain  <br/> |msExchPartnerId  <br/> |
|ms-Exch-Active-Sync-Device  <br/> |add:mayContain  <br/> |msExchDeviceClientType  <br/> |
|ms-Exch-Availability-Address-Space  <br/> |add:mayContain  <br/> |msExchFedTargetAutodiscoverEPR  <br/> |
|ms-Exch-Base-Class  <br/> |add:mayContain  <br/> |msExchDirsyncAuthorityMetadata  <br/> |
|ms-Exch-Base-Class  <br/> |add:mayContain  <br/> |msExchDirsyncStatusAck  <br/> |
|ms-Exch-Base-Class  <br/> |add:mayContain  <br/> |msExchEdgeSyncConfigFlags  <br/> |
|ms-Exch-Base-Class  <br/> |add:mayContain  <br/> |msExchHABRootDepaPreviewentLink  <br/> |
|ms-Exch-Base-Class  <br/> |add:mayContain  <br/> |msExchDefaultPublicFolderMailbox  <br/> |
|ms-Exch-Base-Class  <br/> |add:mayContain  <br/> |msExchForestModeFlag  <br/> |
|ms-Exch-Base-Class  <br/> |add:mayContain  <br/> |msExchELCMailboxFlags  <br/> |
|ms-Exch-Base-Class  <br/> |add:mayContain  <br/> |msExchCanaryData0  <br/> |
|ms-Exch-Base-Class  <br/> |add:mayContain  <br/> |msExchCanaryData1  <br/> |
|ms-Exch-Base-Class  <br/> |add:mayContain  <br/> |msExchCanaryData2  <br/> |
|ms-Exch-Base-Class  <br/> |add:mayContain  <br/> |msExchCorrelationId  <br/> |
|ms-Exch-Base-Class  <br/> |Add:mayContain  <br/> |msExchTenantCountry  <br/> |
|ms-Exch-Base-Class  <br/> |Add:mayContain  <br/> |msExchConfigurationXML  <br/> |
|ms-Exch-Base-Class  <br/> |add: mayContain  <br/> |msExchMultiMailboxGUIDs  <br/> |
|ms-Exch-Base-Class  <br/> |add: mayContain  <br/> |msExchMultiMailboxLocationsLink  <br/> |
|ms-Exch-Coexistence-Relationship  <br/> |add:mayContain  <br/> |msExchCoexistenceOnPremisesSmartHost  <br/> |
|ms-Exch-Coexistence-Relationship  <br/> |add:mayContain  <br/> |msExchCoexistenceSecureMailCertificateThumbprint  <br/> |
|ms-Exch-Coexistence-Relationship  <br/> |add:mayContain  <br/> |msExchCoexistenceTransportServers  <br/> |
|ms-Exch-Configuration-Unit-Container  <br/> |add:mayContain  <br/> |msExchDirsyncStatus  <br/> |
|ms-Exch-Configuration-Unit-Container  <br/> |add:mayContain  <br/> |msExchIsDirsyncStatusPending  <br/> |
|ms-Exch-Configuration-Unit-Container  <br/> |add:mayContain  <br/> |msExchDirSyncServiceInstance  <br/> |
|ms-Exch-Configuration-Unit-Container  <br/> |add:mayContain  <br/> |msExchOrganizationUpgradePolicyLink  <br/> |
|ms-Exch-Configuration-Unit-Container  <br/> |add:mayContain  <br/> |msExchManagementSiteLinkSL  <br/> |
|ms-Exch-Configuration-Unit-Container  <br/> |add:mayContain  <br/> |msExchOrganizationUpgradePolicyLinkSL  <br/> |
|ms-Exch-Configuration-Unit-Container  <br/> |add:mayContain  <br/> |msExchRelocateTenantCompletionTargetVector  <br/> |
|ms-Exch-Configuration-Unit-Container  <br/> |add:mayContain  <br/> |msExchRelocateTenantFlags  <br/> |
|ms-Exch-Configuration-Unit-Container  <br/> |add:mayContain  <br/> |msExchRelocateTenantSafeLockdownSchedule  <br/> |
|ms-Exch-Configuration-Unit-Container  <br/> |add:mayContain  <br/> |msExchRelocateTenantSourceForest  <br/> |
|ms-Exch-Configuration-Unit-Container  <br/> |add:mayContain  <br/> |msExchRelocateTenantStartLockdown  <br/> |
|ms-Exch-Configuration-Unit-Container  <br/> |add:mayContain  <br/> |msExchRelocateTenantStartRetired  <br/> |
|ms-Exch-Configuration-Unit-Container  <br/> |add:mayContain  <br/> |msExchRelocateTenantStartSync  <br/> |
|ms-Exch-Configuration-Unit-Container  <br/> |add:mayContain  <br/> |msExchRelocateTenantStatus  <br/> |
|ms-Exch-Configuration-Unit-Container  <br/> |add:mayContain  <br/> |msExchRelocateTenantTargetForest  <br/> |
|ms-Exch-Configuration-Unit-Container  <br/> |add:mayContain  <br/> |msExchRelocateTenantTransitionCounter  <br/> |
|ms-Exch-Configuration-Unit-Container  <br/> |add:mayContain  <br/> |msExchSyncCookie  <br/> |
|ms-Exch-Control-Point-Config  <br/> |add:mayContain  <br/> |msExchRMSOnlineCertificationLocationUrl  <br/> |
|ms-Exch-Control-Point-Config  <br/> |add:mayContain  <br/> |msExchRMSOnlineKeySharingLocationUrl  <br/> |
|ms-Exch-Control-Point-Config  <br/> |add:mayContain  <br/> |msExchRMSOnlineLicensingLocationUrl  <br/> |
|ms-Exch-Custom-Attributes  <br/> |add:mayContain  <br/> |msExchExtensionCustomAttribute1  <br/> |
|ms-Exch-Custom-Attributes  <br/> |add:mayContain  <br/> |msExchExtensionCustomAttribute2  <br/> |
|ms-Exch-Custom-Attributes  <br/> |add:mayContain  <br/> |msExchExtensionCustomAttribute3  <br/> |
|ms-Exch-Custom-Attributes  <br/> |add:mayContain  <br/> |msExchExtensionCustomAttribute4  <br/> |
|ms-Exch-Custom-Attributes  <br/> |add:mayContain  <br/> |msExchExtensionCustomAttribute5  <br/> |
|ms-Exch-Domain-Content-Config  <br/> |add:mayContain  <br/> |msExchContentByteEncoderTypeFor7BitCharsets  <br/> |
|ms-Exch-Domain-Content-Config  <br/> |add:mayContain  <br/> |msExchContentPreferredInternetCodePageForShiftJis  <br/> |
|ms-Exch-Domain-Content-Config  <br/> |add:mayContain  <br/> |msExchContentRequiredCharSetCoverage  <br/> |
|ms-Exch-Exchange-Server  <br/> |add:mayContain  <br/> |msExchWorkloadManagementPolicyLink  <br/> |
|ms-Exch-Exchange-Server  <br/> |add:mayContain  <br/> |msExchMalwareFilteringDeferAttempts  <br/> |
|ms-Exch-Exchange-Server  <br/> |add:mayContain  <br/> |msExchMalwareFilteringDeferWaitTime  <br/> |
|ms-Exch-Exchange-Server  <br/> |add:mayContain  <br/> |msExchMalwareFilteringFlags  <br/> |
|ms-Exch-Exchange-Server  <br/> |add:mayContain  <br/> |msExchMalwareFilteringPrimaryUpdatePath  <br/> |
|ms-Exch-Exchange-Server  <br/> |add:mayContain  <br/> |msExchMalwareFilteringSecondaryUpdatePath  <br/> |
|ms-Exch-Exchange-Server  <br/> |add:mayContain  <br/> |msExchMalwareFilteringUpdateFrequency  <br/> |
|ms-Exch-Exchange-Server  <br/> |add:mayContain  <br/> |msExchMalwareFilteringUpdateTimeout  <br/> |
|ms-Exch-Exchange-Server  <br/> |add:mayContain  <br/> |msExchMalwareFilteringScanTimeout  <br/> |
|ms-Exch-Fed-OrgId  <br/> |add:mayContain  <br/> |msExchFedDelegationTrustSL  <br/> |
|ms-Exch-Hosted-Content-Filter-Config  <br/> |add:mayContain  <br/> |msExchSpamCountryBlockList  <br/> |
|ms-Exch-Hosted-Content-Filter-Config  <br/> |add:mayContain  <br/> |msExchSpamLanguageBlockList  <br/> |
|ms-Exch-Hosted-Content-Filter-Config  <br/> |add:mayContain  <br/> |msExchSpamNotifyOutboundRecipients  <br/> |
|ms-Exch-Hosted-Content-Filter-Config  <br/> |add:mayContain  <br/> |msExchSpamDigestFrequency  <br/> |
|ms-Exch-Hosted-Content-Filter-Config  <br/> |add:mayContain  <br/> |msExchSpamQuarantineRetention  <br/> |
|ms-Exch-MDB  <br/> |add:mayContain  <br/> |msExchCalendarLoggingQuota  <br/> |
|ms-Exch-MRS-Request  <br/> |add:mayContain  <br/> |msExchMailboxMoveSourceMDBLinkSL  <br/> |
|ms-Exch-MRS-Request  <br/> |add:mayContain  <br/> |msExchMailboxMoveStorageMDBLinkSL  <br/> |
|ms-Exch-MRS-Request  <br/> |add:mayContain  <br/> |msExchMailboxMoveTargetMDBLinkSL  <br/> |
|ms-Exch-MSO-Sync-Service-Instance  <br/> |add:mayContain  <br/> |msExchMSOForwardSyncNonRecipientCookie  <br/> |
|ms-Exch-MSO-Sync-Service-Instance  <br/> |add:mayContain  <br/> |msExchMSOForwardSyncRecipientCookie  <br/> |
|ms-Exch-MSO-Sync-Service-Instance  <br/> |add:mayContain  <br/> |msExchMSOForwardSyncReplayList  <br/> |
|ms-Exch-MSO-Sync-Service-Instance  <br/> |add:mayContain  <br/> |msExchAccountForestLink  <br/> |
|ms-Exch-MSO-Sync-Service-Instance  <br/> |add:mayContain  <br/> |msExchActiveInstanceSleepInterval  <br/> |
|ms-Exch-MSO-Sync-Service-Instance  <br/> |add:mayContain  <br/> |msExchPassiveInstanceSleepInterval  <br/> |
|ms-Exch-MSO-Sync-Service-Instance  <br/> |add:mayContain  <br/> |msExchSyncDaemonMaxVersion  <br/> |
|ms-Exch-MSO-Sync-Service-Instance  <br/> |add:mayContain  <br/> |msExchSyncDaemonMinVersion  <br/> |
|ms-Exch-MSO-Sync-Service-Instance  <br/> |add:mayContain  <br/> |msExchSyncServiceInstanceNewTenantMaxVersion  <br/> |
|ms-Exch-MSO-Sync-Service-Instance  <br/> |add:mayContain  <br/> |msExchSyncServiceInstanceNewTenantMinVersion  <br/> |
|ms-Exch-Mail-Gateway  <br/> |add:mayContain  <br/> |msExchHomeMDBSL  <br/> |
|ms-Exch-Mail-Gateway  <br/> |add:mayContain  <br/> |msExchHomeMTASL  <br/> |
|ms-Exch-Mail-Storage  <br/> |add:mayContain  <br/> |msExchPreviousArchiveDatabase  <br/> |
|ms-Exch-Mail-Storage  <br/> |add:mayContain  <br/> |msExchTeamMailboxExpiration  <br/> |
|ms-Exch-Mail-Storage  <br/> |add:mayContain  <br/> |msExchTeamMailboxOwners  <br/> |
|ms-Exch-Mail-Storage  <br/> |add:mayContain  <br/> |msExchTeamMailboxSharePointLinkedBy  <br/> |
|ms-Exch-Mail-Storage  <br/> |add:mayContain  <br/> |msExchTeamMailboxSharePointUrl  <br/> |
|ms-Exch-Mail-Storage  <br/> |add:mayContain  <br/> |msExchTeamMailboxShowInClientList  <br/> |
|ms-Exch-Mail-Storage  <br/> |add:mayContain  <br/> |msExchCalendarLoggingQuota  <br/> |
|ms-Exch-Mail-Storage  <br/> |add:mayContain  <br/> |msExchArchiveDatabaseLinkSL  <br/> |
|ms-Exch-Mail-Storage  <br/> |add:mayContain  <br/> |msExchDisabledArchiveDatabaseLinkSL  <br/> |
|ms-Exch-Mail-Storage  <br/> |add:mayContain  <br/> |msExchHomeMDBSL  <br/> |
|ms-Exch-Mail-Storage  <br/> |add:mayContain  <br/> |msExchMailboxMoveTargetMDBLinkSL  <br/> |
|ms-Exch-Mail-Storage  <br/> |add:mayContain  <br/> |msExchPreviousArchiveDatabaseSL  <br/> |
|ms-Exch-Mail-Storage  <br/> |add:mayContain  <br/> |msExchPreviousHomeMDBSL  <br/> |
|ms-Exch-Mail-Storage  <br/> |add: mayContain  <br/> |msExchMailboxContainerGuid  <br/> |
|ms-Exch-Mail-Storage  <br/> |add: mayContain  <br/> |msExchUnifiedMailbox  <br/> |
|ms-Exch-Mail-Storage  <br/> |add:mayContain  <br/> |msExchUserCulture  <br/> |
|ms-Exch-Mailflow-Policy  <br/> |add:mayContain  <br/> |msExchImmutableId  <br/> |
|ms-Exch-Malware-Filter-Config  <br/> |add:mayContain  <br/> |msExchMalwareFilterConfigExternalSenderAdminAddress  <br/> |
|ms-Exch-Malware-Filter-Config  <br/> |add:mayContain  <br/> |msExchMalwareFilterConfigInternalSenderAdminAddress  <br/> |
|ms-Exch-OAB  <br/> |add:mayContain  <br/> |msExchOffLineABServerSL  <br/> |
|ms-Exch-OAB  <br/> |add: mayContain  <br/> |msExchOABGeneratingMailboxLink  <br/> |
|ms-Exch-OWA-Mailbox-Policy  <br/> |add:mayContain  <br/> |msExchOWASetPhotoURL  <br/> |
|ms-Exch-OWA-Virtual-Directory  <br/> |add:mayContain  <br/> |msExchOWASetPhotoURL  <br/> |
|ms-Exch-Organization-Container  <br/> |add:mayContain  <br/> |msExchOrganizationFlags2  <br/> |
|ms-Exch-Organization-Container  <br/> |add:mayContain  <br/> |msExchUMAvailableLanguages  <br/> |
|ms-Exch-Organization-Container  <br/> |add:mayContain  <br/> |msExchWACDiscoveryEndpoint  <br/> |
|ms-Exch-Organization-Container  <br/> |add:mayContain  <br/> |msExchAdfsAuthenticationRawConfiguration  <br/> |
|ms-Exch-Organization-Container  <br/> |add:mayContain  <br/> |msExchServiceEndPointURL  <br/> |
|ms-Exch-Private-MDB  <br/> |add:mayContain  <br/> |msExchMailboxDatabaseTransportFlags  <br/> |
|ms-Exch-Public-Folder  <br/> |add:mayContain  <br/> |msExchPublicFolderEntryId  <br/> |
|ms-Exch-Resource-Policy  <br/> |add:mayContain  <br/> |msExchCustomerExpectationCritical  <br/> |
|ms-Exch-Resource-Policy  <br/> |add:mayContain  <br/> |msExchDiscretionaryCritical  <br/> |
|ms-Exch-Resource-Policy  <br/> |add:mayContain  <br/> |msExchInternalMaintenanceCritical  <br/> |
|ms-Exch-Resource-Policy  <br/> |add:mayContain  <br/> |msExchUrgentCritical  <br/> |
|ms-Exch-Routing-Group-Connector  <br/> |add:mayContain  <br/> |msExchHomeMTASL  <br/> |
|ms-Exch-Safe-Attachment-Protection-Config  <br/> |add:mayContain  <br/> |msExchMalwareFilterConfigFlags  <br/> |
|ms-Exch-Safe-Attachment-Protection-Config  <br/> |add:mayContain  <br/> |msExchMalwareFilterConfigFromAddress  <br/> |
|ms-Exch-Safe-Attachment-Protection-Config  <br/> |add:mayContain  <br/> |msExchMalwareFilterConfigInternalBody  <br/> |
|ms-Exch-Safe-Attachment-Protection-Config  <br/> |add:mayContain  <br/> |msExchMalwareFilterConfigInternalSenderAdminAddress  <br/> |
|ms-Exch-Safe-Attachment-Protection-Config  <br/> |add:mayContain  <br/> |msExchMalwareFilterConfigInternalSubject  <br/> |
|ms-Exch-Safe-Attachment-Protection-Config  <br/> |add:mayContain  <br/> |msExchMalwareFilteringScanTimeout  <br/> |
|ms-Exch-Safe-Attachment-Protection-Config  <br/> |add:mayContain  <br/> |msExchMalwareFilteringUpdateFrequency  <br/> |
|ms-Exch-Site-Connector  <br/> |add:mayContain  <br/> |msExchHomeMTASL  <br/> |
|ms-Exch-Smart-Links-Protection-Config  <br/> |add:mayContain  <br/> |msExchAddressRewriteExceptionList  <br/> |
|ms-Exch-Smart-Links-Protection-Config  <br/> |add:mayContain  <br/> |msExchSpamFlags  <br/> |
|ms-Exch-Tenant-Perimeter-Settings  <br/> |add:mayContain  <br/> |msExchTransportResellerSettingsLinkSL  <br/> |
|ms-Exch-Throttling-Policy  <br/> |add:mayContain  <br/> |msExchThrottlingPolicyFlags  <br/> |
|ms-Exch-Throttling-Policy  <br/> |add:mayContain  <br/> |msExchAnonymousThrottlingPolicyStateEx  <br/> |
|ms-Exch-Throttling-Policy  <br/> |add:mayContain  <br/> |msExchEASThrottlingPolicyStateEx  <br/> |
|ms-Exch-Throttling-Policy  <br/> |add:mayContain  <br/> |msExchEWSThrottlingPolicyStateEx  <br/> |
|ms-Exch-Throttling-Policy  <br/> |add:mayContain  <br/> |msExchGeneralThrottlingPolicyStateEx  <br/> |
|ms-Exch-Throttling-Policy  <br/> |add:mayContain  <br/> |msExchIMAPThrottlingPolicyStateEx  <br/> |
|ms-Exch-Throttling-Policy  <br/> |add:mayContain  <br/> |msExchOWAThrottlingPolicyStateEx  <br/> |
|ms-Exch-Throttling-Policy  <br/> |add:mayContain  <br/> |msExchPOPThrottlingPolicyStateEx  <br/> |
|ms-Exch-Throttling-Policy  <br/> |add:mayContain  <br/> |msExchPowershellThrottlingPolicyStateEx  <br/> |
|ms-Exch-Throttling-Policy  <br/> |add:mayContain  <br/> |msExchRCAThrottlingPolicyStateEx  <br/> |
|ms-Exch-Transport-Rule  <br/> |add:mayContain  <br/> |msExchTransportRuleImmutableId  <br/> |
|ms-Exch-Transport-Rule  <br/> |add:mayContain  <br/> |msExchImmutableId  <br/> |
|ms-Exch-Transport-Settings  <br/> |add:mayContain  <br/> |msExchTranspoPreviewaxRetriesForLocalSiteShadow  <br/> |
|ms-Exch-Transport-Settings  <br/> |add:mayContain  <br/> |msExchTranspoPreviewaxRetriesForRemoteSiteShadow  <br/> |
|ms-Exch-Transport-Settings  <br/> |add:mayContain  <br/> |msExchConfigurationXML  <br/> |
|ms-Exch-Virtual-Directory  <br/> |add:mayContain  <br/> |msExchMRSProxyFlags  <br/> |
|ms-Exch-Virtual-Directory  <br/> |add:mayContain  <br/> |msExchMRSProxyMaxConnections  <br/> |
   
### Attributes added by Exchange 2016 RTM
<a name="AttribAddRTM"> </a>

This section contains the attributes added in Exchange 2016 RTM.
  
- ms-DS-GeoCoordinates-Altitude
    
- ms-DS-GeoCoordinates-Latitude
    
- ms-DS-GeoCoordinates-Longitude
    
- ms-Exch-Accepted-Domain-BL
    
- ms-Exch-Account-Forest-BL
    
- ms-Exch-Account-Forest-Link
    
- ms-Exch-ActiveSync-Device-AutoBlock-Duration
    
- ms-Exch-ActiveSync-Device-Autoblock-Threshold-Incidence-Duration
    
- ms-Exch-ActiveSync-Device-Autoblock-Threshold-Incidence-Limit
    
- ms-Exch-ActiveSync-Device-Autoblock-Threshold-Type
    
- ms-Exch-Adfs-Authentication-Raw-Configuration
    
- ms-Exch-Anonymous-Throttling-Policy-State-Ex
    
- ms-Exch-Archive-Database-Link-SL
    
- ms-Exch-Auth-App-Secret
    
- ms-Exch-Auth-Application-Identifier
    
- ms-Exch-Auth-Auth-Server-Type
    
- ms-Exch-Auth-Authorization-Url
    
- ms-Exch-Auth-Certificate-Data
    
- ms-Exch-Auth-Certificate-Thumbprint
    
- ms-Exch-Auth-Flags
    
- ms-Exch-Auth-Issuer-Name
    
- ms-Exch-Auth-Issuing-Url
    
- ms-Exch-Auth-Linked-Account
    
- ms-Exch-Auth-Metadata-Url
    
- ms-Exch-Auth-Realm
    
- ms-Exch-Aux-Mailbox-Parent-Object-Id-BL
    
- ms-Exch-Aux-Mailbox-Parent-Object-Id-Link
    
- ms-Exch-Canary-Data-0
    
- ms-Exch-Canary-Data-1
    
- ms-Exch-Canary-Data-2
    
- ms-Exch-Content-Byte-Encoder-Type-For-7-Bit-Charsets
    
- ms-Exch-Content-Preferred-Internet-Code-Page-For-Shift-Jis
    
- ms-Exch-Content-Required-Char-Set-Coverage
    
- ms-Exch-Correlation-Id
    
- ms-Exch-Customer-Expectation-Critical
    
- ms-Exch-Customer-Expectation-Overloaded
    
- ms-Exch-Customer-Expectation-Underloaded
    
- ms-Exch-Default-Public-Folder-Mailbox
    
- ms-Exch-Device-Client-Type
    
- ms-Exch-Dir-Sync-Service-Instance
    
- ms-Exch-Dirsync-Authority-Metadata
    
- ms-Exch-Dirsync-Status
    
- ms-Exch-Dirsync-Status-Ack
    
- ms-Exch-Disabled-Archive-Database-Link-SL
    
- ms-Exch-Discretionary-Critical
    
- ms-Exch-Discretionary-Overloaded
    
- ms-Exch-Discretionary-Underloaded
    
- ms-Exch-EAS-Throttling-Policy-State-Ex
    
- ms-Exch-EWS-Throttling-Policy-State-Ex
    
- ms-Exch-Edge-Sync-Config-Flags
    
- ms-Exch-Encryption-Throttling-Policy-State-Ex
    
- ms-Exch-Extension-Custom-Attribute-1
    
- ms-Exch-Extension-Custom-Attribute-2
    
- ms-Exch-Extension-Custom-Attribute-3
    
- ms-Exch-Extension-Custom-Attribute-4
    
- ms-Exch-Extension-Custom-Attribute-5
    
- ms-Exch-External-Directory-Object-Class
    
- ms-Exch-Fed-Delegation-Trust-SL
    
- ms-Exch-Forest-Mode-Flag
    
- ms-Exch-General-Throttling-Policy-State-Ex
    
- ms-Exch-Group-External-Member-Count
    
- ms-Exch-Group-Member-Count
    
- ms-Exch-Home-MDB-SL
    
- ms-Exch-Home-MTA-SL
    
- ms-Exch-Hosted-Content-Filter-Config-Link
    
- ms-Exch-Hygiene-Configuration-Link
    
- ms-Exch-Hygiene-Configuration-Malware-BL
    
- ms-Exch-Hygiene-Configuration-Spam-BL
    
- ms-Exch-IMAP-Throttling-Policy-State-Ex
    
- ms-Exch-Internal-Maintenance-Critical
    
- ms-Exch-Internal-Maintenance-Overloaded
    
- ms-Exch-Internal-Maintenance-Underloaded
    
- ms-Exch-Is-Dirsync-Status-Pending,
    
- ms-Exch-Localization-Flags
    
- ms-Exch-MRS-Proxy-Flags
    
- ms-Exch-MRS-Proxy-Max-Connections
    
- ms-Exch-MSO-Forward-Sync-Divergence-Count
    
- ms-Exch-MSO-Forward-Sync-Divergence-Related-Object-Link
    
- ms-Exch-MSO-Forward-Sync-Divergence-Timestamp
    
- ms-Exch-Mailbox-Database-Transport-Flags
    
- ms-Exch-Mailbox-Move-Source-Archive-MDB-Link-SL
    
- ms-Exch-Mailbox-Move-Source-MDB-Link-SL
    
- ms-Exch-Mailbox-Move-Storage-MDB-Link-SL
    
- ms-Exch-Mailbox-Move-Target-Archive-MDB-Link-SL
    
- ms-Exch-Mailbox-Move-Target-MDB-Link-SL
    
- ms-Exch-Mailflow-Policy-Countries
    
- ms-Exch-Mailflow-Policy-Keywords
    
- ms-Exch-Mailflow-Policy-Publisher-Name
    
- ms-Exch-Mailflow-Policy-Transport-Rules-Template-Xml
    
- ms-Exch-Mailflow-Policy-Version
    
- ms-Exch-Malware-Filter-Config-Alert-Text
    
- ms-Exch-Malware-Filter-Config-External-Body
    
- ms-Exch-Malware-Filter-Config-External-Sender-Admin-Address
    
- ms-Exch-Malware-Filter-Config-External-Subject
    
- ms-Exch-Malware-Filter-Config-Flags
    
- ms-Exch-Malware-Filter-Config-From-Address
    
- ms-Exch-Malware-Filter-Config-From-Name
    
- ms-Exch-Malware-Filter-Config-Internal-Body
    
- ms-Exch-Malware-Filter-Config-Internal-Sender-Admin-Address
    
- ms-Exch-Malware-Filter-Config-Internal-Subject
    
- ms-Exch-Malware-Filter-Config-Link
    
- ms-Exch-Malware-Filtering-Defer-Attempts
    
- ms-Exch-Malware-Filtering-Defer-Wait-Time
    
- ms-Exch-Malware-Filtering-Flags
    
- ms-Exch-Malware-Filtering-Primary-Update-Path
    
- ms-Exch-Malware-Filtering-Scan-Timeout
    
- ms-Exch-Malware-Filtering-Secondary-Update-Path
    
- ms-Exch-Malware-Filtering-Update-Frequency
    
- ms-Exch-Malware-Filtering-Update-Timeout
    
- ms-Exch-Management-Site-Link-SL
    
- ms-Exch-Multi-Mailbox-GUID
    
- ms-Exch-Multi-Mailbox-Locations-Link
    
- ms-Exch-OAB-Generating-Mailbox-BL
    
- ms-Exch-OAB-Generating-Mailbox-Link
    
- ms-Exch-OWA-Set-Photo-URL
    
- ms-Exch-OWA-Throttling-Policy-State-Ex
    
- ms-Exch-Off-Line-AB-Server-SL
    
- ms-Exch-Organization-Flags-2
    
- ms-Exch-Organization-Upgrade-Policy-BL
    
- ms-Exch-Organization-Upgrade-Policy-Date
    
- ms-Exch-Organization-Upgrade-Policy-Enabled
    
- ms-Exch-Organization-Upgrade-Policy-Link
    
- ms-Exch-Organization-Upgrade-Policy-Link-SL
    
- ms-Exch-Organization-Upgrade-Policy-MaxMailboxes
    
- ms-Exch-Organization-Upgrade-Policy-Priority
    
- ms-Exch-Organization-Upgrade-Policy-Source-Version
    
- ms-Exch-Organization-Upgrade-Policy-Status
    
- ms-Exch-Organization-Upgrade-Policy-Target-Version
    
- ms-Exch-POP-Throttling-Policy-State-Ex
    
- ms-Exch-Powershell-Throttling-Policy-State-Ex
    
- ms-Exch-Previous-Archive-Database
    
- ms-Exch-Previous-Archive-Database-SL
    
- ms-Exch-Previous-Home-MDB-SL
    
- ms-Exch-Public-Folder-EntryId
    
- ms-Exch-Public-Folder-Mailbox
    
- ms-Exch-Public-Folder-Smtp-Address
    
- ms-Exch-RCA-Throttling-Policy-State-Ex
    
- ms-Exch-RMS-Computer-Accounts-Link-SL
    
- ms-Exch-RMSOnline-Certification-Location-Url
    
- ms-Exch-RMSOnline-Key-Sharing-Location-Url
    
- ms-Exch-RMSOnline-Licensing-Location-Url
    
- ms-Exch-Recipient-SoftDeleted-Status
    
- ms-Exch-Relocate-Tenant-Completion-Target-Vector
    
- ms-Exch-Relocate-Tenant-Flags
    
- ms-Exch-Relocate-Tenant-Safe-Lockdown-Schedule
    
- ms-Exch-Relocate-Tenant-Source-Forest
    
- ms-Exch-Relocate-Tenant-Start-Lockdown
    
- ms-Exch-Relocate-Tenant-Start-Retired
    
- ms-Exch-Relocate-Tenant-Start-Sync
    
- ms-Exch-Relocate-Tenant-Status
    
- ms-Exch-Relocate-Tenant-Target-Forest
    
- ms-Exch-Relocate-Tenant-Transition-Counter
    
- ms-Exch-Resource-Type
    
- ms-Exch-RoleGroup-Type
    
- ms-Exch-Service-End-Point-URL
    
- ms-Exch-Shadow-When-Soft-Deleted-Time
    
- ms-Exch-Spam-Add-Header
    
- ms-Exch-Spam-Asf-Settings
    
- ms-Exch-Spam-Asf-Test-Bcc-Address
    
- ms-Exch-Spam-Country-Block-List
    
- ms-Exch-Spam-Digest-Frequency
    
- ms-Exch-Spam-False-Positive-Cc
    
- ms-Exch-Spam-Flags
    
- ms-Exch-Spam-Language-Block-List
    
- ms-Exch-Spam-Modify-Subject
    
- ms-Exch-Spam-Notify-Outbound-Recipients
    
- ms-Exch-Spam-Outbound-Spam-Cc
    
- ms-Exch-Spam-Quarantine-Retention
    
- ms-Exch-Spam-Redirect-Address
    
- ms-Exch-Sts-Refresh-Tokens-Valid-From
    
- ms-Exch-Sync-Cookie
    
- ms-Exch-Sync-Service-Instance-New-Tenant-Max-Version
    
- ms-Exch-Sync-Service-Instance-New-Tenant-Min-Version
    
- ms-Exch-Team-Mailbox-Expiration
    
- ms-Exch-Team-Mailbox-Expiry-Days
    
- ms-Exch-Team-Mailbox-Owners
    
- ms-Exch-Team-Mailbox-SharePoint-Linked-By
    
- ms-Exch-Team-Mailbox-SharePoint-Url
    
- ms-Exch-Team-Mailbox-Show-In-Client-List
    
- ms-Exch-Tenant-Country
    
- ms-Exch-Throttling-Policy-Flags
    
- ms-Exch-Transport-MaxRetriesForLocalSiteShadow
    
- ms-Exch-Transport-MaxRetriesForRemoteSiteShadow
    
- ms-Exch-Transport-Reseller-Settings-Link-SL
    
- ms-Exch-Transport-Rule-Immutable-Id
    
- ms-Exch-Trusted-Domain-BL
    
- ms-Exch-Trusted-Domain-Link
    
- ms-Exch-UG-Member-BL
    
- ms-Exch-UG-Member-Link
    
- ms-Exch-Urgent-Critical
    
- ms-Exch-Urgent-Overloaded
    
- ms-Exch-Urgent-Underloaded
    
- ms-Exch-WAC-Discovery-Endpoint
    
- ms-Exch-When-Soft-Deleted-Time
    
- ms-Exch-Workload-Classification
    
- ms-Exch-Workload-Management-Is-Enabled
    
- ms-Exch-Workload-Management-Policy
    
- ms-Exch-Workload-Management-Policy-BL
    
- ms-Exch-Workload-Management-Policy-Link
    
- ms-DS-External-Directory-Object-Id
    
- ms-Exch-Group-Security-Flags
    
- ms-Exch-Multi-Mailbox-Locations-BL
    
- ms-Exch-Multi-Mailbox-Databases-Link
    
- ms-Exch-Multi-Mailbox-Databases-BL
    
### Global catalog attributes added by Exchange 2016 RTM
<a name="GlobalCatRTM"> </a>

The following global catalog attributes are added by Exchange 2016 RTM:
  
- ms-Exch-Archive-Database-Link-SL
    
- ms-Exch-Correlation-Id
    
- ms-Exch-Default-Public-Folder-Mailbox
    
- ms-Exch-Device-Client-Type
    
- ms-Exch-Dirsync-Authority-Metadata
    
- ms-Exch-Dirsync-Status
    
- ms-Exch-Dirsync-Status-Ack
    
- ms-Exch-Disabled-Archive-Database-Link-SL
    
- ms-Exch-Edge-Sync-Config-Flags
    
- ms-Exch-EvictedMembers-Link
    
- ms-Exch-EvictedMemebers-BL
    
- ms-Exch-Extension-Custom-Attribute-1
    
- ms-Exch-Extension-Custom-Attribute-2
    
- ms-Exch-Extension-Custom-Attribute-3
    
- ms-Exch-Extension-Custom-Attribute-4
    
- ms-Exch-Extension-Custom-Attribute-5
    
- ms-Exch-Group-External-Member-Count
    
- ms-Exch-Group-Member-Count
    
- ms-Exch-HAB-Root-DepaPreviewent-Link
    
- ms-Exch-Home-MDB-SL
    
- ms-Exch-Home-MTA-SL
    
- ms-Exch-Is-Dirsync-Status-Pending
    
- ms-Exch-Localization-Flags
    
- ms-Exch-Mailbox-Container-Guid
    
- ms-Exch-Mailbox-Move-Source-Archive-MDB-Link-SL
    
- ms-Exch-Mailbox-Move-Source-MDB-Link-SL
    
- ms-Exch-Mailbox-Move-Storage-MDB-Link-SL
    
- ms-Exch-Mailbox-Move-Target-Archive-MDB-Link-SL
    
- ms-Exch-Mailbox-Move-Target-MDB-Link-SL
    
- ms-Exch-Offline-OrgId-Home-Realm-Record
    
- ms-Exch-Previous-Archive-Database
    
- ms-Exch-Previous-Archive-Database-SL
    
- ms-Exch-Previous-Home-MDB-SL
    
- ms-Exch-RMS-Computer-Accounts-Link-SL
    
- ms-Exch-Recipient-SoftDeleted-Status
    
- ms-Exch-Relocate-Tenant-Completion-Target-Vector,
    
- ms-Exch-Relocate-Tenant-Flags
    
- ms-Exch-Relocate-Tenant-Safe-Lockdown-Schedule
    
- ms-Exch-Relocate-Tenant-Source-Forest
    
- ms-Exch-Relocate-Tenant-Start-Lockdown
    
- ms-Exch-Relocate-Tenant-Start-Retired
    
- ms-Exch-Relocate-Tenant-Start-Sync
    
- ms-Exch-Relocate-Tenant-Status
    
- ms-Exch-Relocate-Tenant-Target-Forest
    
- ms-Exch-Relocate-Tenant-Transition-Counter
    
- ms-Exch-RoleGroup-Type
    
- ms-Exch-Sync-Cookie
    
- ms-Exch-Team-Mailbox-Expiration
    
- ms-Exch-Team-Mailbox-Expiry-Days
    
- ms-Exch-Team-Mailbox-Owners
    
- ms-Exch-Team-Mailbox-SharePoint-Linked-By
    
- ms-Exch-Team-Mailbox-SharePoint-Url
    
- ms-Exch-Team-Mailbox-Show-In-Client-List
    
- ms-Exch-Unified-Mailbox
    
- ms-Exch-When-Soft-Deleted-Time
    
### Attributes modified by Exchange 2016 RTM
<a name="AttribModRTM"> </a>

This section contains the attributes modified in Exchange 2016 RTM.
  
|**Attribute**|**Change**|**Value**|
|:-----|:-----|:-----|
|Exch-Configuration-Unit-Container  <br/> |rangeUpper  <br/> |15254  <br/> |
|Exch-Mailflow-Policy-Transport-Rules-Template-Xml  <br/> |rangeUpper  <br/> |256000  <br/> |
|Mail-Recipient  <br/> |Replace: mayContain  <br/> |msExchUGMemberLink  <br/> |
|Ms-exch-schema-version-pt  <br/> |rangeUpper  <br/> |15292  <br/> |
|Top  <br/> |Replace: mayContain  <br/> |msExchUGMemberBL  <br/> |
|ms-Exch-Accepted-Domain-Name  <br/> |replace: searchFlags  <br/> |9  <br/> |
|ms-Exch-Archive-GUID  <br/> |replace: searchFlags  <br/> |9  <br/> |
|ms-Exch-Bypass-Audit  <br/> |replace: searchFlags  <br/> |19  <br/> |
|ms-Exch-Coexistence-On-Premises-Smart-Host  <br/> |ntdsSchemaAdd  <br/> |attributeID: 1.2.840.113556.1.4.7000.102.51992 isMemberOfPartialAttributeSet: FALSE (not in global catalogue) searchFlags: 0 (no index)  <br/> |
|ms-Exch-Coexistence-Secure-Mail-Certificate-Thumbprint  <br/> |ntdsSchemaAdd  <br/> |attributeID: 1.2.840.113556.1.4.7000.102.51991 isMemberOfPartialAttributeSet: FALSE (not in global catalogue) searchFlags: 0 (no index)  <br/> |
|ms-Exch-Coexistence-Secure-Mail-Certificate-Thumbprintms-Exch-Sync-Cookie  <br/> |rangeUpper  <br/> |1024  <br/> |
|ms-Exch-Coexistence-Transport-Servers  <br/> |ntdsSchemaAdd  <br/> |attributeID: 1.2.840.113556.1.4.7000.102.51990 isMemberOfPartialAttributeSet: FALSE (not in global catalogue) searchFlags: 0 (no index)  <br/> |
|ms-Exch-ELC-Mailbox-Flags  <br/> |replace: attributeSecurityGuid  <br/> |F6SzsVXskUGzJ7cuM+OK8g==  <br/> |
|ms-Exch-Extension-Custom-Attribute-1  <br/> |isMemberOfPartialAttributeSet:  <br/> |TRUE  <br/> |
|ms-Exch-Extension-Custom-Attribute-2  <br/> |isMemberOfPartialAttributeSet:  <br/> |TRUE  <br/> |
|ms-Exch-Extension-Custom-Attribute-3  <br/> |isMemberOfPartialAttributeSet:  <br/> |TRUE  <br/> |
|ms-Exch-Extension-Custom-Attribute-4  <br/> |isMemberOfPartialAttributeSet:  <br/> |TRUE  <br/> |
|ms-Exch-Extension-Custom-Attribute-5  <br/> |isMemberOfPartialAttributeSet  <br/> |TRUE  <br/> |
|ms-Exch-Group-External-Member-Count  <br/> |ntdsSchemaModify  <br/> |isMemberOfPartialAttributeSet: TRUE MAPIID:36066  <br/> |
|ms-Exch-Group-Member-Count  <br/> |ntdsSchemaModify  <br/> |replace: isMemberOfPartialAttributeSetisMemberOfPartialAttributeSet: TRUE MAPIID: 36067  <br/> |
|ms-Exch-HAB-Root-DepaPreviewent-Link  <br/> |replace: isMemberOfPartialAttributeSet  <br/> |TRUE  <br/> |
|ms-Exch-MSO-Forward-Sync-Non-Recipient-Cookie  <br/> |rangeUpper  <br/> |20480  <br/> |
|ms-Exch-MSO-Forward-Sync-Recipient-Cookie  <br/> |rangeUpper  <br/> |20480  <br/> |
|ms-Exch-Mailbox-Audit-Enable  <br/> |replace: searchFlags  <br/> |19  <br/> |
|ms-Exch-Malware-Filtering-Update-Frequency  <br/> |rangeUpper  <br/> |38880  <br/> |
|ms-Exch-Role-Entries  <br/> |rangeUpper  <br/> |8192  <br/> |
|ms-Exch-Schema-Version-Pt  <br/> |rangeUpper  <br/> |15137  <br/> |
|ms-Exch-Schema-Version-Pt  <br/> |rangeUpper  <br/> |15281  <br/> |
|ms-Exch-Smtp-Receive-Tls-Certificate-Name  <br/> |Replace: rangeUpper  <br/> |1024  <br/> |
|ms-Exch-Smtp-TLS-Certificate  <br/> |replace: rangeUpper  <br/> |1024  <br/> |
|ms-Exch-Sync-Cookie  <br/> |rangeUpper  <br/> |262144  <br/> |
   
### Object IDs added by Exchange 2016 RTM
<a name="ObjIDsAddRTM"> </a>

The following class object IDs are added when you install Exchange 2016 RTM:
  
- 1.2.840.113556.1.5.7000.62.50161
    
- 1.2.840.113556.1.5.7000.62.50162
    
- 1.2.840.113556.1.5.7000.62.50163
    
- 1.2.840.113556.1.5.7000.62.50164
    
- 1.2.840.113556.1.5.7000.62.50165
    
- 1.2.840.113556.1.5.7000.62.50166
    
- 1.2.840.113556.1.5.7000.62.50167
    
- 1.2.840.113556.1.5.7000.62.50170
    
- 1.2.840.113556.1.5.7000.62.50171
    
- 1.2.840.113556.1.5.7000.62.50172
    
- 1.2.840.113556.1.5.7000.62.50173
    
- 1.2.840.113556.1.5.7000.62.50174
    
- 1.2.840.113556.1.5.7000.62.50176
    
- 1.2.840.113556.1.5.7000.62.50177
    
- 1.2.840.113556.1.5.7000.62.50178
    
- 1.2.840.113556.1.5.7000.62.50187
    
- 1.2.840.113556.1.5.7000.62.50188
    
- 1.2.840.113556.1.5.7000.62.50189
    
- 1.2.840.113556.1.5.7000.62.50190
    
- 1.2.840.113556.1.5.7000.62.50191
    
- 1.2.840.113556.1.5.7000.62.50192
    
- 1.2.840.113556.1.5.7000.62.50202
    
- 1.2.840.113556.1.5.7000.62.50203
    
- 1.2.840.113556.1.5.7000.62.50204
    
- 1.2.840.113556.1.5.7000.62.50205
    
The following attribute object IDs are added when you install Exchange 2016 RTM:
  
- 1.2.840.113556.1.4.2183
    
- 1.2.840.113556.1.4.2184
    
- 1.2.840.113556.1.4.2185
    
- 1.2.840.113556.1.4.7000.102.51773
    
- 1.2.840.113556.1.4.7000.102.51774
    
- 1.2.840.113556.1.4.7000.102.51775
    
- 1.2.840.113556.1.4.7000.102.51786
    
- 1.2.840.113556.1.4.7000.102.51787
    
- 1.2.840.113556.1.4.7000.102.51788
    
- 1.2.840.113556.1.4.7000.102.51789
    
- 1.2.840.113556.1.4.7000.102.51790
    
- 1.2.840.113556.1.4.7000.102.51791
    
- 1.2.840.113556.1.4.7000.102.51792
    
- 1.2.840.113556.1.4.7000.102.51794
    
- 1.2.840.113556.1.4.7000.102.51795
    
- 1.2.840.113556.1.4.7000.102.51796
    
- 1.2.840.113556.1.4.7000.102.51797
    
- 1.2.840.113556.1.4.7000.102.51798
    
- 1.2.840.113556.1.4.7000.102.51799
    
- 1.2.840.113556.1.4.7000.102.51800
    
- 1.2.840.113556.1.4.7000.102.51801
    
- 1.2.840.113556.1.4.7000.102.51805
    
- 1.2.840.113556.1.4.7000.102.51806
    
- 1.2.840.113556.1.4.7000.102.51807
    
- 1.2.840.113556.1.4.7000.102.51808
    
- 1.2.840.113556.1.4.7000.102.51809
    
- 1.2.840.113556.1.4.7000.102.51810
    
- 1.2.840.113556.1.4.7000.102.51811
    
- 1.2.840.113556.1.4.7000.102.51812
    
- 1.2.840.113556.1.4.7000.102.51813
    
- 1.2.840.113556.1.4.7000.102.51814
    
- 1.2.840.113556.1.4.7000.102.51815
    
- 1.2.840.113556.1.4.7000.102.51816
    
- 1.2.840.113556.1.4.7000.102.51818
    
- 1.2.840.113556.1.4.7000.102.51819
    
- 1.2.840.113556.1.4.7000.102.51820
    
- 1.2.840.113556.1.4.7000.102.51821
    
- 1.2.840.113556.1.4.7000.102.51822
    
- 1.2.840.113556.1.4.7000.102.51823
    
- 1.2.840.113556.1.4.7000.102.51824
    
- 1.2.840.113556.1.4.7000.102.51826
    
- 1.2.840.113556.1.4.7000.102.51827
    
- 1.2.840.113556.1.4.7000.102.51829
    
- 1.2.840.113556.1.4.7000.102.51830
    
- 1.2.840.113556.1.4.7000.102.51832
    
- 1.2.840.113556.1.4.7000.102.51833
    
- 1.2.840.113556.1.4.7000.102.51836
    
- 1.2.840.113556.1.4.7000.102.51837
    
- 1.2.840.113556.1.4.7000.102.51838
    
- 1.2.840.113556.1.4.7000.102.51839
    
- 1.2.840.113556.1.4.7000.102.51840
    
- 1.2.840.113556.1.4.7000.102.51851
    
- 1.2.840.113556.1.4.7000.102.51852
    
- 1.2.840.113556.1.4.7000.102.51859
    
- 1.2.840.113556.1.4.7000.102.51860
    
- 1.2.840.113556.1.4.7000.102.51861
    
- 1.2.840.113556.1.4.7000.102.51862
    
- 1.2.840.113556.1.4.7000.102.51863
    
- 1.2.840.113556.1.4.7000.102.51864
    
- 1.2.840.113556.1.4.7000.102.51865
    
- 1.2.840.113556.1.4.7000.102.51866
    
- 1.2.840.113556.1.4.7000.102.51867
    
- 1.2.840.113556.1.4.7000.102.51868
    
- 1.2.840.113556.1.4.7000.102.51869
    
- 1.2.840.113556.1.4.7000.102.51870
    
- 1.2.840.113556.1.4.7000.102.51871
    
- 1.2.840.113556.1.4.7000.102.51872
    
- 1.2.840.113556.1.4.7000.102.51873
    
- 1.2.840.113556.1.4.7000.102.51874
    
- 1.2.840.113556.1.4.7000.102.51875
    
- 1.2.840.113556.1.4.7000.102.51876
    
- 1.2.840.113556.1.4.7000.102.51877
    
- 1.2.840.113556.1.4.7000.102.51878
    
- 1.2.840.113556.1.4.7000.102.51879
    
- 1.2.840.113556.1.4.7000.102.51880
    
- 1.2.840.113556.1.4.7000.102.51881
    
- 1.2.840.113556.1.4.7000.102.51882
    
- 1.2.840.113556.1.4.7000.102.51883
    
- 1.2.840.113556.1.4.7000.102.51914
    
- 1.2.840.113556.1.4.7000.102.51915
    
- 1.2.840.113556.1.4.7000.102.51916
    
- 1.2.840.113556.1.4.7000.102.51917
    
- 1.2.840.113556.1.4.7000.102.51918
    
- 1.2.840.113556.1.4.7000.102.51919
    
- 1.2.840.113556.1.4.7000.102.51920
    
- 1.2.840.113556.1.4.7000.102.51921
    
- 1.2.840.113556.1.4.7000.102.51922
    
- 1.2.840.113556.1.4.7000.102.51923
    
- 1.2.840.113556.1.4.7000.102.51924
    
- 1.2.840.113556.1.4.7000.102.51925
    
- 1.2.840.113556.1.4.7000.102.51926
    
- 1.2.840.113556.1.4.7000.102.51927
    
- 1.2.840.113556.1.4.7000.102.51928
    
- 1.2.840.113556.1.4.7000.102.51929
    
- 1.2.840.113556.1.4.7000.102.51930
    
- 1.2.840.113556.1.4.7000.102.51931
    
- 1.2.840.113556.1.4.7000.102.51932
    
- 1.2.840.113556.1.4.7000.102.51933
    
- 1.2.840.113556.1.4.7000.102.51934
    
- 1.2.840.113556.1.4.7000.102.51935
    
- 1.2.840.113556.1.4.7000.102.51936
    
- 1.2.840.113556.1.4.7000.102.51937
    
- 1.2.840.113556.1.4.7000.102.51938
    
- 1.2.840.113556.1.4.7000.102.51939
    
- 1.2.840.113556.1.4.7000.102.51940
    
- 1.2.840.113556.1.4.7000.102.51941
    
- 1.2.840.113556.1.4.7000.102.51942
    
- 1.2.840.113556.1.4.7000.102.51943
    
- 1.2.840.113556.1.4.7000.102.51944
    
- 1.2.840.113556.1.4.7000.102.51945
    
- 1.2.840.113556.1.4.7000.102.51946
    
- 1.2.840.113556.1.4.7000.102.51947
    
- 1.2.840.113556.1.4.7000.102.51948
    
- 1.2.840.113556.1.4.7000.102.51949
    
- 1.2.840.113556.1.4.7000.102.51950
    
- 1.2.840.113556.1.4.7000.102.51951
    
- 1.2.840.113556.1.4.7000.102.51952
    
- 1.2.840.113556.1.4.7000.102.51953
    
- 1.2.840.113556.1.4.7000.102.51954
    
- 1.2.840.113556.1.4.7000.102.51955
    
- 1.2.840.113556.1.4.7000.102.51993
    
- 1.2.840.113556.1.4.7000.102.51994
    
- 1.2.840.113556.1.4.7000.102.51995
    
- 1.2.840.113556.1.4.7000.102.51996
    
- 1.2.840.113556.1.4.7000.102.51997
    
- 1.2.840.113556.1.4.7000.102.51998
    
- 1.2.840.113556.1.4.7000.102.52001
    
- 1.2.840.113556.1.4.7000.102.52002
    
- 1.2.840.113556.1.4.7000.102.52003
    
- 1.2.840.113556.1.4.7000.102.52004
    
- 1.2.840.113556.1.4.7000.102.52005
    
- 1.2.840.113556.1.4.7000.102.52006
    
- 1.2.840.113556.1.4.7000.102.52007
    
- 1.2.840.113556.1.4.7000.102.52008
    
- 1.2.840.113556.1.4.7000.102.52011
    
- 1.2.840.113556.1.4.7000.102.52012
    
- 1.2.840.113556.1.4.7000.102.52013
    
- 1.2.840.113556.1.4.7000.102.52014
    
- 1.2.840.113556.1.4.7000.102.52015
    
- 1.2.840.113556.1.4.7000.102.52016
    
- 1.2.840.113556.1.4.7000.102.52017
    
- 1.2.840.113556.1.4.7000.102.52018
    
- 1.2.840.113556.1.4.7000.102.52019
    
- 1.2.840.113556.1.4.7000.102.52020
    
- 1.2.840.113556.1.4.7000.102.52021
    
- 1.2.840.113556.1.4.7000.102.52022
    
- 1.2.840.113556.1.4.7000.102.52023
    
- 1.2.840.113556.1.4.7000.102.52024
    
- 1.2.840.113556.1.4.7000.102.52029
    
- 1.2.840.113556.1.4.7000.102.52030
    
- 1.2.840.113556.1.4.7000.102.52031
    
- 1.2.840.113556.1.4.7000.102.52032
    
- 1.2.840.113556.1.4.7000.102.52033
    
- 1.2.840.113556.1.4.7000.102.52034
    
- 1.2.840.113556.1.4.7000.102.52035
    
- 1.2.840.113556.1.4.7000.102.52036
    
- 1.2.840.113556.1.4.7000.102.52037
    
- 1.2.840.113556.1.4.7000.102.52039
    
- 1.2.840.113556.1.4.7000.102.52040
    
- 1.2.840.113556.1.4.7000.102.52041
    
- 1.2.840.113556.1.4.7000.102.52042
    
- 1.2.840.113556.1.4.7000.102.52043
    
- 1.2.840.113556.1.4.7000.102.52044
    
- 1.2.840.113556.1.4.7000.102.52045
    
- 1.2.840.113556.1.4.7000.102.52046
    
- 1.2.840.113556.1.4.7000.102.52047
    
- 1.2.840.113556.1.4.7000.102.52048
    
- 1.2.840.113556.1.4.7000.102.52049
    
- 1.2.840.113556.1.4.7000.102.52050
    
- 1.2.840.113556.1.4.7000.102.52051
    
- 1.2.840.113556.1.4.7000.102.52052
    
- 1.2.840.113556.1.4.7000.102.52053
    
- 1.2.840.113556.1.4.7000.102.52054
    
- 1.2.840.113556.1.4.7000.102.52055
    
- 1.2.840.113556.1.4.7000.102.52056
    
- 1.2.840.113556.1.4.7000.102.52057
    
- 1.2.840.113556.1.4.7000.102.52058
    
- 1.2.840.113556.1.4.7000.102.52059
    
- 1.2.840.113556.1.4.7000.102.52060
    
- 1.2.840.113556.1.4.7000.102.52061
    
- 1.2.840.113556.1.4.7000.102.52062
    
- 1.2.840.113556.1.4.7000.102.52063
    
- 1.2.840.113556.1.4.7000.102.52064
    
- 1.2.840.113556.1.4.7000.102.52065
    
- 1.2.840.113556.1.4.7000.102.52109
    
- 1.2.840.113556.1.4.7000.102.52110
    
- 1.2.840.113556.1.4.7000.102.52126
    
- 1.2.840.113556.1.4.7000.102.52127
    
- 1.2.840.113556.1.4.7000.102.52128
    
- 1.2.840.113556.1.4.7000.102.52129
    
- 1.2.840.113556.1.4.7000.102.52130
    
### Indexed attributes added by Exchange 2016 RTM
<a name="IndexAttRTM"> </a>

The following table lists the attributes that are added to the list of indexed attributes when you install Exchange 2016 RTM.
  
|**Attribute**|**Search flag value**|
|:-----|:-----|
|ms-DS-GeoCoordinates-Altitude  <br/> |1  <br/> |
|ms-DS-GeoCoordinates-Latitude  <br/> |1  <br/> |
|ms-DS-GeoCoordinates-Longitude  <br/> |1  <br/> |
|ms-Exch-Accepted-Domain-Name  <br/> |9  <br/> |
|ms-Exch-Archive-GUID  <br/> |9  <br/> |
|ms-Exch-Auth-Application-Identifier  <br/> |1  <br/> |
|ms-Exch-Auth-Issuer-Name  <br/> |1  <br/> |
|ms-Exch-Bypass-Audit  <br/> |9  <br/> |
|ms-Exch-Default-Public-Folder-Mailbox  <br/> |19  <br/> |
|ms-Exch-Device-Client-Type  <br/> |1  <br/> |
|ms-Exch-Extension-Custom-Attribute-1  <br/> |1  <br/> |
|ms-Exch-Extension-Custom-Attribute-2  <br/> |1  <br/> |
|ms-Exch-Extension-Custom-Attribute-3  <br/> |1  <br/> |
|ms-Exch-Extension-Custom-Attribute-4  <br/> |1  <br/> |
|ms-Exch-Extension-Custom-Attribute-5  <br/> |1  <br/> |
|ms-Exch-Home-MDB-SL  <br/> |1  <br/> |
|ms-Exch-Home-MTA-SL  <br/> |1  <br/> |
|ms-Exch-Is-Dirsync-Status-Pending  <br/> |1  <br/> |
|ms-Exch-Mailbox-Audit-Enable  <br/> |19  <br/> |
|ms-Exch-Mailbox-Database-Transport-Flags  <br/> |16  <br/> |
|ms-Exch-Mailbox-Move-Source-Archive-MDB-Link-SL  <br/> |1  <br/> |
|ms-Exch-Mailbox-Move-Source-MDB-Link-SL  <br/> |1  <br/> |
|ms-Exch-Mailbox-Move-Target-Archive-MDB-Link-SL  <br/> |1  <br/> |
|ms-Exch-OWA-Set-Photo-URL  <br/> |16  <br/> |
|ms-Exch-Organization-Upgrade-Policy-Link  <br/> |1  <br/> |
|ms-Exch-Organization-Upgrade-Policy-Link-SL  <br/> |1  <br/> |
|ms-Exch-Previous-Archive-Database-SL  <br/> |8  <br/> |
|ms-Exch-Previous-Home-MDB-SL  <br/> |8  <br/> |
|ms-Exch-Provisioning-Tags  <br/> |1  <br/> |
|ms-Exch-Public-Folder-EntryId  <br/> |24  <br/> |
|ms-Exch-Public-Folder-Mailbox  <br/> |24  <br/> |
|ms-Exch-Public-Folder-Smtp-Address  <br/> |24  <br/> |
|ms-Exch-Recipient-SoftDeleted-Status  <br/> |27  <br/> |
|ms-Exch-Relocate-Tenant-Completion-Target-Vector  <br/> |8  <br/> |
|ms-Exch-Relocate-Tenant-Flags  <br/> |8  <br/> |
|ms-Exch-Relocate-Tenant-Safe-Lockdown-Schedule  <br/> |8  <br/> |
|ms-Exch-Relocate-Tenant-Source-Forest  <br/> |9  <br/> |
|ms-Exch-Relocate-Tenant-Start-Lockdown  <br/> |8  <br/> |
|ms-Exch-Relocate-Tenant-Start-Retired  <br/> |8  <br/> |
|ms-Exch-Relocate-Tenant-Start-Sync  <br/> |8  <br/> |
|ms-Exch-Relocate-Tenant-Status,  <br/> |9  <br/> |
|ms-Exch-Relocate-Tenant-Target-Forest  <br/> |9  <br/> |
|ms-Exch-Relocate-Tenant-Transition-Counter  <br/> |8  <br/> |
|ms-Exch-Sync-Cookie  <br/> |8  <br/> |
|ms-Exch-Team-Mailbox-Expiration  <br/> |16  <br/> |
|ms-Exch-Team-Mailbox-Expiry-Days  <br/> |16  <br/> |
|ms-Exch-Team-Mailbox-Owners  <br/> |16  <br/> |
|ms-Exch-Team-Mailbox-SharePoint-Linked-By  <br/> |16  <br/> |
|ms-Exch-Team-Mailbox-SharePoint-Url  <br/> |16  <br/> |
|ms-Exch-Team-Mailbox-Show-In-Client-List  <br/> |16  <br/> |
|ms-Exch-Transport-Rule-Immutable-Id  <br/> |1  <br/> |
|ms-Exch-When-Soft-Deleted-Time  <br/> |17  <br/> |
   
### Property sets modified by Exchange 2016 RTM
<a name="PropSetsRTM"> </a>

The following property sets are modified when you install Exchange 2016 RTM:
  
- Exchange-Information
    
### MAPI IDs added by Exchange 2016 RTM
<a name="MAPIaddRTM"> </a>

The following MAPI IDs are added when you install Exchange 2016 RTM:
  
- 36066
    
- 36067
    
### Extended rights added by Exchange 2016 RTM
<a name="ExtendedAddRTM"> </a>

The following table lists the extended rights that are added when you install Exchange 2016 RTM. Installing Exchange 2016 RTM doesn't modify any existing extended rights.
  
|**Identifier**|**Values**|
|:-----|:-----|
|CN=ms-Exch-SMTP-Accept-XProxyFrom,CN=Extended-Rights,\<ConfigurationContainerDN\>  <br/> |changetype: ntdsSchemaAdd  <br/> displayName: Accept XProxyFrom  <br/> objectClass: controlAccessRight  <br/> rightsGuid: 5bee2b72-50d7-49c7-ba66-39a25daa1e92  <br/> validAccesses: 256  <br/> |
   

