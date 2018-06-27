---
title: "Use batch migration to migrate Exchange 2013 public folders to Exchange Online"
ms.author: dmaguire
author: msdmaguire
ms.date: 3/26/2018
ms.audience: ITPro
ms.topic: article
ms.service: exchange-online
localization_priority: Normal
ms.collection: Strat_EX_EXOBlocker
ms.assetid: 25a5234c-dd2c-487b-8541-3655fbeb030a
description: "Summary: This article tells you how to move modern public folders from Exchange 2013 to Office 365."
---

# Use batch migration to migrate Exchange 2013 public folders to Exchange Online

 **Summary**: This article tells you how to move modern public folders from Exchange 2013 to Office 365.
  
Migrating your Exchange 2013 public folders to Exchange Online requires Exchange Server 2013 CU15 or later running in your on-premises environment.
  
> [!NOTE]
> If you have both Exchange 2013 and Exchange 2016 public folders in your organization, and you want to move them all to Exchange Online, use [the Exchange 2016 version of this article](https://go.microsoft.com/fwlink/p/?linkid=845314) to plan and execute your migration. Your Exchange 2013 servers will still need to have CU15 or later installed. 
  
## What do you need to know before you begin?

- When you upgrade to Exchange Server 2013 CU15 or later, you must also prepare Active Directory or your public folder migration will fail. This Active Directory preparation ensures that all relevant PowerShell cmdlets and parameters are available to you for preparing and running the migration. See [Prepare Active Directory and Domains](http://technet.microsoft.com/library/f895e1ce-d766-4352-ac46-ec959c9954a9.aspx) for more information. 
    
- In Exchange Online, you need to be a member of the Organization Management role group. This role group is different from the permissions assigned to you when you subscribe to Office 365 or Exchange Online. For details about how to enable the Organization Management role group, see [Manage Role Groups](http://technet.microsoft.com/library/ab9b7a3b-bf67-4ba1-bde5-8e6ac174b82c.aspx).
    
- In Exchange Server 2013, you need to be a member of the Organization Management or Server Management RBAC role groups. For details, see [Add Members to a Role Group](https://go.microsoft.com/fwlink/?LinkId=299212). 
    
- Before you begin the public folder migration, if any single public folder in your organization is larger than 25 GB, we recommend that you delete content from that folder to make it smaller, or divide the public folder's content into multiple, smaller public folders. Note that the 25 GB limit cited here only applies to the public folder and not to any child or sub-folders the folder in question may have. If neither option is feasible, we recommend that you do not move your public folders to Exchange Online. See [Exchange Online Limits](https://go.microsoft.com/fwlink/p/?LinkID=391188) for more information. 
    
    > [!NOTE]
    > If your current public folder quotas in Exchange Online are less than 25 GB, you can use the [Set-OrganizationConfig cmdlet](https://go.microsoft.com/fwlink/p/?linkid=844062) to increase them with the DefaultPublicFolderIssueWarningQuota and DefaultPublicFolderProhibitPostQuota parameters. 
  
- In Office 365 and Exchange Online, you can create a maximum of 1000 public folder mailboxes.
    
- If you intend to migrate users to Office 365, you should complete your user migration prior to migrating your public folders. For more information, see [Ways to migrate multiple email accounts to Office 365](https://go.microsoft.com/fwlink/p/?linkid=842798).
    
- MRS Proxy needs to be enabled on at least one Exchange server, a server that is also hosting public folder mailboxes. See [Enable the MRS Proxy Endpoint for Remote Moves](http://technet.microsoft.com/library/9840f712-127e-4c2d-bfe5-1b35cdb2a31b.aspx) for details. 
    
- To perform the migration procedures in this article, you can't use the Exchange Admin Center (EAC). Instead, you need to use the Exchange Management Shell on your Exchange 2013 servers. In Exchange Online, you need to use Exchange Online PowerShell. For more information, see [Connect to Exchange Online PowerShell](https://go.microsoft.com/fwlink/p/?linkid=842801).
    
- Migrating deleted items and deleted folders from Exchange 2013 to Exchange Online is supported. Before you begin your migration, we recommend that you review all deleted folders and folder items and permanently delete anything you won't need in Exchange Online. Note that once something is permanently deleted, it can't be recovered.
    
    You can use the following commands to list deleted public folders present in the Exchange dumpster (in your Exchange on-premises environment):
    
  ```
  Get-PublicFolder \NON_IPM_SUBTREE\DUMPSTER_ROOT -Recurse | ?{$_.FolderClass -ne "$null"} | ft name,foldersize
  ```

    To permanently delete a specific folder, use the following command (this example uses a folder named 'Calendar2'):
    
  ```
  Get-PublicFolder \NON_IPM_SUBTREE\DUMPSTER_ROOT -Recurse | ?{$_.FolderClass -ne "$null" -and $_.Name -eq "Calendar2"} | Remove-PublicFolder
  ```

- You must use a single migration batch to migrate all of your public folder data. Exchange allows creating only one migration batch at a time. If you attempt to create more than one migration batch simultaneously, the result will be an error.
    
- Before you begin, please read this article in its entirety. For some steps there is downtime required. During this downtime, public folders will not be accessible by anyone.
    
> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612),[Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351). 
  
## Step 1: Download the migration scripts

1. Download all scripts and supporting files from [Exchange 2013/2016 Public Folders Migration Scripts](https://go.microsoft.com/fwlink/p/?linkid=844893).
    
2. Save the scripts to the local computer on which you'll be running PowerShell. For example, C:\PFScripts. Make sure all scripts are saved in the same location.
    
The scripts and files you're downloading are:
  
-  `Sync-ModernMailPublicFolders.ps1` This script synchronizes mail-enabled public folder objects between your Exchange on-premises environment and Office 365. You'll run this script on an Exchange 2013 server. 
    
-  `SyncModernMailPublicFolders.strings.psd1` This support file is used by the Sync-ModernMailPublicFolders.ps1 script and should be downloaded to the same location. 
    
-  `Export-ModernPublicFolderStatistics.ps1` This script creates the folder name-to-folder size and deleted item size mapping file. You'll run this script on the Exchange 2013 server. 
    
-  `Export-ModernPublicFolderStatistics.strings.psd1` This support file is used by the Export-ModernPublicFolderStatistics.ps1 script and should be downloaded to the same location. 
    
-  `ModernPublicFolderToMailboxMapGenerator.ps1` This script creates the public folder-to-mailbox mapping file by using the output from the Export-ModernPublicFolderStatistics.ps1 script. You'll run this script on an Exchange 2013 server. 
    
-  `ModernPublicFolderToMailboxMapGenerator.strings.psd1` This support file is used by the ModernPublicFolderToMailboxMapGenerator.ps1 script and should be downloaded to the same location. 
    
-  `SetMailPublicFolderExternalAddress.ps1` This script updates  `ExternalEmailAddress` of mail-enabled public folders in your on-premises environment to that of their Exchange Online counterparts. This ensures that, post-migration, emails addressed to mail-enabled public folders are properly routed to Exchange Online. You need to run this script on an Exchange 2013 server. 
    
-  `SetMailPublicFolderExternalAddress.strings.psd1` This support file is used by the SetMailPublicFolderExternalAddress.ps1 script and should be downloaded to the same location. 
    
## Step 2: Prepare for the migration
<a name="Prepareformigration"> </a>

Perform all prerequisite steps in the following sections before you begin the public folder migration.
  
 **General prerequisite steps**
  
For your migration to be successful, you should:
  
- Make sure that there are no orphaned public folder mail objects in Active Directory. These are objects in Active Directory without a corresponding Exchange object.
    
- Confirm that the SMTP email addresses configured for public folders in Active Directory match the SMTP email addresses on the Exchange objects.
    
- Confirm that there are no duplicate public folder objects in Active Directory. This is necessary to avoid having two or more Active Directory objects that are pointing to the same mail-enabled public folder.
    
 **Prerequisite steps in the on-premises Exchange 2013 server environment**
  
In Exchange Management Shell (on-premises) perform the following steps:
  
1. Once your migration is complete, it will take some time for DNS caches across the Internet to direct messages to your mail-enabled public folders in their new location in Exchange Online. You can ensure that your newly migrated mail-enabled public folders receive messages during this DNS transition period by creating an accepted domain with a well-known name. To do this, run the following command in your Exchange on-premises environment. In this example,  `target domain` is your Office 365 or Exchange Online domain, for which a send connector has already been configured by the Hybrid Configuration Wizard. 
    
  ```
  New-AcceptedDomain -Name PublicFolderDestination_78c0b207_5ad2_4fee_8cb9_f373175b3f99 -DomainName <target domain> -DomainType InternalRelay
  ```

    **Example**:
    
  ```
  New-AcceptedDomain -Name PublicFolderDestination_78c0b207_5ad2_4fee_8cb9_f373175b3f99 -DomainName "contoso.mail.onmicrosoft.com" -DomainType InternalRelay
  ```

    If the accepted domain already exists in your on-premises environment, rename it to  `PublicFolderDestination_78c0b207_5ad2_4fee_8cb9_f373175b3f99` and leave the other attributes intact. 
    
    To check if the accepted domain is already present in your on-premises environment:
    
  ```
  Get-AcceptedDomain | Where { $_.DomainName -eq "<target domain>" }
  ```

    To rename the accepted domain to  `PublicFolderDestination_78c0b207_5ad2_4fee_8cb9_f373175b3f99`, run the following:
    
  ```
  Get-AcceptedDomain | Where { $_.DomainName -eq "<target domain>" } | Set-AcceptedDomain -Name PublicFolderDestination_78c0b207_5ad2_4fee_8cb9_f373175b3f99
  ```

    > [!NOTE]
    > If you're expecting your mail-enabled public folders in Exchange Online to receive external emails from the Internet, you have to disable Directory Based Edge Blocking (DBEB) in Exchange Online and Exchange Online Protection (EOP). See [Use Directory Based Edge Blocking to reject messages sent to invalid recipients](../../mail-flow-best-practices/use-directory-based-edge-blocking.md) for more information. 
  
2. If the name of a public folder contains a backslash **\** or a forward slash **/**, it may not get migrated to its designated mailbox during the migration process. Before you migrate, rename any such folders to remove these characters
    
1. To locate public folders that have a backslash in the name, run the following command:
    
  ```
  Get-PublicFolder -Recurse -ResultSize Unlimited | Where {$_.Name -like "*\*" -or $_.Name -like "*/*"} | Format-List Name, Identity, EntryId
  ```

2. If any public folders are returned, you can rename them by running the following command:
    
  ```
  Set-PublicFolder -Identity "<public folder EntryId>" -Name "<new public folder name>"
  ```

3. Take the following steps to confirm there isn't a record of a previous, successful migration in your organization. If there is, you need to set that value to  `$false`.
    
    Before changing the values, please confirm that the previous migration attempt can be discarded so that you don't accidentally perform a second migration.
    
1. Run the following command to check for any previous migrations, and the status of those migrations:
    
  ```
  Get-OrganizationConfig | Format-List PublicFoldersLockedforMigration, PublicFolderMigrationComplete, PublicFolderMailboxesLockedForNewConnections, PublicFolderMailboxesMigrationComplete
  ```

    > [!NOTE]
    > If either the  `PublicFoldersLockedforMigration` or  `PublicFolderMigrationComplete` parameters are  `$true`, it means you have migrated legacy public folders at some point. Make sure any legacy public folder databases have been decommissioned before you continue to step 3b. 
  
2. If any of the above is returned with a value set to  `$true`, make them  `$false` by running: 
    
  ```
  Set-OrganizationConfig -PublicFoldersLockedforMigration:$false -PublicFolderMigrationComplete:$false -PublicFolderMailboxesLockedForNewConnections:$false -PublicFolderMailboxesMigrationComplete:$false
  ```

4. For the purpose of verifying the success of the migration upon its completion, we recommend that you run the following commands on all appropriate Exchange 2013 servers. This will take snapshots of your current public folder deployment that you can later use to compare with your newly migrated public folders.
    
    > [!NOTE]
    > Depending on the size of your Exchange organization, it could take some time for these commands to run. 
  
  - Run the following command to take a snapshot of the original source folder structure.
    
  ```
  Get-PublicFolder -Recurse -ResultSize Unlimited | Export-CliXML OnPrem_PFStructure.xml
  ```

  - Run the following command to take a snapshot of public folder statistics such as item count, size, and owner.
    
  ```
  Get-PublicFolderStatistics -ResultSize Unlimited | Export-CliXML OnPrem_PFStatistics.xml
  ```

  - Run the following command to take a snapshot of public folder permissions.
    
  ```
  Get-PublicFolder -Recurse -ResultSize Unlimited | Get-PublicFolderClientPermission | Select-Object Identity,User -ExpandProperty AccessRights | Export-CliXML OnPrem_PFPerms.xml
  ```

  - Run the following command to take a snapshot of your mail-enabled public folders:
    
  ```
  Get-MailPublicFolder -ResultSize Unlimited | Export-CliXML OnPrem_MEPF.xml
  ```

  - Save the files generated from the preceding commands in a safe place in order to make a comparison at the end of the migration.
    
5. If you are using Microsoft Azure Active Directory Connect (Azure AD Connect) to synchronize your on-premises directories with Azure Active Directory, you must take the following actions (if you are not using Azure AD Connect, you can skip this step):
    
1. On an on-premises computer, open Microsoft Azure Active Directory Connect, and then select **Configure**.
    
2. On the **Additional tasks** screen, select **Customize synchronization options**, and then click **Next**.
    
3. On the **Connect to Azure AD** screen, enter the appropriate credentials, and then click **Next**. Once connected, keep clicking **Next** until you are on the **Optional Features** screen. 
    
4. Make sure that **Exchange Mail Public Folders** is not selected. If it isn't selected, you can continue to the next section,  *Prerequisite steps in Exchange Online*  . If it is selected, click to clear the check box, and then click **Next**.
    
    > [!NOTE]
    > If you don't see **Exchange Mail Public Folders** as an option on the **Optional Features** screen, you can exit Microsoft Azure Active Directory Connect and proceed to the next section,  *Prerequisite steps in Exchange Online*  . 
  
5. After you have cleared the **Exchange Mail Public Folders** selection, keep clicking **Next** until you are on the **Ready to configure** screen, and then click **Configure**.
    
 **Prerequisite steps in Exchange Online**
  
In Exchange Online PowerShell, do the following:
  
1. Make sure there are no existing public folder migration requests. If there are, clear them or your own migration request will fail. This step is only required if you think there may be an existing migration request in the pipeline (one that has failed or that you wish to abort).
    
    An existing migration request can be one of two types: batch migration or serial migration. The commands for detecting, and removing, each type of request are as follows.
    
    The following example will discover any existing serial migration requests:
    
  ```
  Get-PublicFolderMigrationRequest | Get-PublicFolderMigrationRequestStatistics 
  ```

    The following example removes any existing public folder serial migration requests:
    
  ```
  Get-PublicFolderMigrationRequest | Remove-PublicFolderMigrationRequest
  ```

    The following example will discover any existing batch migration requests:
    
  ```
  Get-MigrationBatch | ?{$_.MigrationType.ToString() -eq "PublicFolder"}
  ```

    The following example removes any existing public folder batch migration requests:
    
  ```
  Remove-MigrationBatch <name of migration batch> -Confirm:$false
  ```

2.  You need to have the migration feature **PAW** enabled for your Office 365 tenant. You can check this by running the following command in Exchange Online PowerShell: 
    
  ```
  Get-MigrationConfig
  ```

    If the output under **Features** has **PAW**, then the feature is enabled and you can continue to the next step.
    
    If PAW is not yet enabled for your tenant, it could be because you have some existing migration batches, either public folder batches or user batches. These batches could be in any state, including Completed. If this is the case, please complete and remove any migration batches until no records are returned when you run  `Get-MigrationBatch`. Once all the existing batches are removed, PAW should get enabled automatically. Note that the change may not reflect in  `Get-MigrationConfig` immediately, but that is okay. In the case of user migrations, you can continue creating new batches once this step is completed. 
    
3. Make sure there aren't any existing public folders or public folder mailboxes in Exchange Online. If you do discover public folders in Exchange Online after following the steps below, it's important to determine why they are there and who in your organization started a public folder hierarchy before you begin removing any public folders and public folder mailboxes. 
    
1. In Office 365 or Exchange Online PowerShell, run the following command to see if any public folders mailboxes exist.
    
  ```
  Get-Mailbox -PublicFolder
  ```

2. If the command doesn't return any public folder mailboxes, continue to [Step 3: Generate the .csv files](batch-migration-of-exchange-2013-public-folders.md#Generatecsv). If the command does return any public folders mailboxes, run the following command to see if any public folders exist:
    
  ```
  Get-PublicFolder -Recurse
  ```

3. If you do have any public folders in Office 365 or Exchange Online, run the following PowerShell command to remove them (after confirming that they are not needed). Make sure that you've saved any information within these public folders before deleting them, because all information will be permanently deleted when you remove the public folders.
    
  ```
  Get-MailPublicFolder -ResultSize Unlimited | where {$_.EntryId -ne $null}| Disable-MailPublicFolder -Confirm:$false 
  Get-PublicFolder -GetChildren \ -ResultSize Unlimited | Remove-PublicFolder -Recurse -Confirm:$false
  
  ```

4. After the public folders are removed, run the following commands to remove all public folder mailboxes:
    
  ```
  $hierarchyMailboxGuid = $(Get-OrganizationConfig).RootPublicFolderMailbox.HierarchyMailboxGuid
  Get-Mailbox -PublicFolder | Where-Object {$_.ExchangeGuid -ne $hierarchyMailboxGuid} | Remove-Mailbox -PublicFolder -Confirm:$false -Force
  Get-Mailbox -PublicFolder | Where-Object {$_.ExchangeGuid -eq $hierarchyMailboxGuid} | Remove-Mailbox -PublicFolder -Confirm:$false -Force
  Get-Mailbox -PublicFolder -SoftDeletedMailbox | Remove-Mailbox -PublicFolder -PermanentlyDelete:$true 
  
  ```

## Step 3: Generate the .csv files
<a name="Generatecsv"> </a>

Use the previously downloaded scripts to generate the .csv files that will be used in the migration.
  
1. From the Exchange Management Shell (on premises), run the  `Export-ModernPublicFolderStatistics.ps1` script to create the folder name-to-folder size mapping file. You must have local administrator permissions to run this script. The resulting file will contain three columns: **FolderName**, **FolderSize**, and **DeletedItemSize**. The values for the **FolderSize** and **DeletedItemSize** columns will be displayed in bytes. For example, **\PublicFolder01,10240, 100** means the public folder in the root of your hierarchy named PublicFolder01 is 10240 bytes, or 10.240 MB, in size, and there are 100 bytes of recoverable items in it. 
    
  ```
  .\Export-ModernPublicFolderStatistics.ps1 <Folder-to-size map path>
  ```

    **Example**:
    
  ```
  .\Export-ModernPublicFolderStatistics.ps1 stats.csv
  ```

2. Run the  `ModernPublicFolderToMailboxMapGenerator.ps1` script to create a .csv file that maps source public folders to public folder mailboxes in your Exchange Online destination. This file is used to calculate the correct number of public folder mailboxes in Exchange Online. 
    
    > [!NOTE]
    > The file generated by  `ModernPublicFolderToMailboxMapGenerator.ps1` will not contain the name of every public folder in your organization. It will contain references to the parent folders of larger folder trees, or the names of folders which themselves are significantly large. You can think of this file as an "exception" file used to make sure certain folder trees and larger folders get placed into specific public folder mailboxes. It is normal to not see every one of your public folders in this file. Child folders of any folder listed in this mapping file will also be migrated to the same public folder mailbox as their parent folder (unless explicitly mentioned on another line within the mapping file that directs them to a different public folder mailbox). 
  
  ```
  .\ModernPublicFolderToMailboxMapGenerator.ps1 <Maximum mailbox size in bytes><Maximum mailbox recoverable item size in bytes><Folder-to-size map path><Folder-to-mailbox map path>
  ```

  -  `Maximum mailbox size in bytes` is the maximum amount of data you want to migrate into any single public folder mailbox in Exchange Online. The maximum size of this field is currently 50 GB, but we recommend you use a smaller size, such as 50% of maximum size, to allow for future growth. 
    
  -  `Maximum mailbox recoverable items size in bytes` is the recoverable items quota on your Exchange Online mailboxes. The maximum size of public folder mailboxes In Exchange Online is currently 50 GB. We recommend setting  ` RecoverableItemsQuota ` to 15 GB or less. 
    
  -  `Folder-to-size map path` is the file path of the .csv file you created when you ran the  `Export-ModernPublicFolderStatistics.ps1` script. 
    
  -  `Folder-to-mailbox map path` is the file path of the folder-to-mailbox .csv file that you are creating in this step. If you only specify a file name, the file will be generated in the current PowerShell directory on the local computer. 
    
 **Example**:
  
```
.\ModernPublicFolderToMailboxMapGenerator.ps1 -MailboxSize 25GB -MailboxRecoverableItemSize 1GB -ImportFile .\stats.csv -ExportFile map.csv
```

> [!NOTE]
> We don't support migrating public folders to Exchange Online if the number of unique public folder mailboxes in Exchange Online is more than 100. 
  
## Step 4: Create the public folder mailboxes in Exchange Online
<a name="Generatecsv"> </a>

Next, in Exchange Online PowerShell, create the target public folder mailboxes that will contain your migrated public folders.
  
1. Run the following script to create the target public folder mailboxes. The script will create a target mailbox for each mailbox in the .csv file that you generated previously in  *Step 3: Generate the .csv files*  , when you ran the  `ModernPublicFoldertoMailboxMapGenerator.ps1` script. 
    
  ```
  $mappings = Import-Csv <Folder-to-mailbox map path>
  $primaryMailboxName = ($mappings | Where-Object FolderPath -eq "\" ).TargetMailbox
  New-Mailbox -HoldForMigration:$true -PublicFolder -IsExcludedFromServingHierarchy:$false $primaryMailboxName 
  ($mappings | Where-Object TargetMailbox -ne $primaryMailboxName).TargetMailbox | Sort-Object -unique | ForEach-Object { New-Mailbox -PublicFolder -IsExcludedFromServingHierarchy:$false $_ }
  
  ```

  -  `Folder-to-mailbox map path` is the file path of the folder-to-mailbox .csv file that was generated by the  `ModernPublicFoldertoMailboxMapGenerator.ps1` script in  *Step 3: Generate the .csv files*  . 
    
## Step 5: Start the migration request
<a name="Generatecsv"> </a>

A number of commands now need to be run in your Exchange 2013 on-premises environment and in Exchange Online.
  
1. From any of your Exchange 2013 servers hosting public folder mailboxes, execute the following script. This script will synchronize mail-enabled public folders from your local Active Directory to Exchange Online. Make sure that you have downloaded the latest version of this script and that you are running it from Exchange Management Shell.
    
  ```
  .\Sync-ModernMailPublicFolders.ps1 -Credential (Get-Credential) -CsvSummaryFile:sync_summary.csv
  ```

  -  `Credential` is your Exchange Online administrative user name and password. 
    
  -  `CsvSummaryFile` is the file path to where you want your log file of synchronization operations and errors located. The log will be in .csv format. 
    
2. On the Exchange 2013 server, find the MRS proxy endpoint server and make note of it. You will need this information to run the migration request. Save this information for step 3b below.
    
3. In Exchange Online PowerShell, run the following commands to pass credential information and the MRS information from the previous step to cmdlet variables that will be used in the migration request.
    
1. Pass the credential of a user who has administrator permissions in the Exchange 2013 on-premises environment into the variable  `$Source_Credential`. The migration request that you run in Exchange Online will use this credential to gain access to your on-premises Exchange 2013 servers to copy the public folder content over to Exchange Online.
    
  ```
  $Source_Credential = Get-Credential <source_domain>\<PublicFolder_Administrator_Account>
  ```

2. Take the MRS Proxy Server information from the Exchange 2013 environment that you found in step 2 above and pass it into the variable:
    
  ```
  $Source_RemoteServer = "<paste the value here>"
  
  ```

4. In Exchange Online PowerShell, run the following commands to create the public folder migration endpoint and the public folder migration request:
    
  ```
  $PfEndpoint = New-MigrationEndpoint -PublicFolder -Name PublicFolderEndpoint -RemoteServer $Source_RemoteServer -Credentials $Source_Credential
   
  [byte[]]$bytes = Get-Content -Encoding Byte <folder_mapping.csv>
  New-MigrationBatch -Name PublicFolderMigration -CSVData $bytes -SourceEndpoint $PfEndpoint.Identity -NotificationEmails <email addresses for migration notifications>
  ```

    > [!NOTE]
    > Separate multiple email addresses with commas. 
  
    Where  `folder_mapping.csv` is the map file that was generated in  *Step 3: Create the .csv files*  . Be sure to provide the full file path. If the map file was moved for any reason, be sure to use the new location. 
    
5. Finally, start the migration using the following command in Exchange Online PowerShell:
    
  ```
  Start-MigrationBatch PublicFolderMigration
  ```

While batch migrations need to be created using the New-MigrationBatch cmdlet in Exchange Online PowerShell, the progress and completion of the migration can be viewed and managed in the EAC or by running the Get-MigrationBatch cmdlet. The New-MigrationBatch cmdlet initiates a mailbox migration request for each public folder mailbox, and you can view the status of these requests using the mailbox migration page. 
  
To go to the mailbox migration page:
  
1. Log on to Exchange Online and open the EAC.
    
2. Navigate to **Recipients**, and then select **Migration**.
    
3. Select the migration request that was just created and then, on the **Details** pane, select **View Details**.
    
Before moving on to  *Step 6: Lock down the public folders on the Exchange 2013 server*  , verify that all data has been copied and that there are no errors in the migration. Once you have confirmed that the batch has moved to the state of **Synced**, run the commands mentioned in  *Step 2: Prepare for the migration*  , in the final step under **Prerequisite steps in the on-premises Exchange 2013 server environment**, to take a snapshot of the public folders on-premises. Once these commands have run, you can proceed to the next step. Note that these commands could take a while to complete depending on the number of folders you have. 
  
## Step 6: Lock down the public folders in the Exchange 2013 environment for final migration (public folder downtime required)
<a name="Generatecsv"> </a>

Until this point in the migration process, users have been able to access your on-premises public folders. The following steps will now log off users off from Exchange 2013 public folders and then lock the folders as the migration process completes its final synchronization. Users won't be able to access public folders during this time, and any messages sent to these mail-enabled public folders will be queued and remain undelivered until the public folder migration is complete. 
  
Before you run the  `PublicFolderMailboxesLockedForNewConnections` command as described below, make sure that all jobs are in the **Synced** state. You can do this by running the  `Get-PublicFolderMailboxMigrationRequest` command. Continue with this step only after you've verified that all jobs are in the **Synced** state. 
  
In your on-premises environment, run the following command to lock the Exchange 2013 public folders for finalization.
  
```
Set-OrganizationConfig -PublicFolderMailboxesLockedForNewConnections $true
```

> [!NOTE]
> If you are not able to access the  `-PublicFolderMailboxesLockedForNewConnections` parameter, it could be because your Active Directory was not prepared during the CU upgrade, as we advised above in  *What do you need to know before you begin?*  See [Prepare Active Directory and Domains](http://technet.microsoft.com/library/f895e1ce-d766-4352-ac46-ec959c9954a9.aspx) for more information. > Also note that any users who need access to public folders should be migrated first, **before** you migrate the public folders themselves. 
  
If your organization has public folder mailboxes on multiple Exchange 2013 servers, you'll need to wait until AD replication is complete. Once complete, you can confirm that all public folder mailboxes have picked up the  `PublicFolderMailboxesLockedForNewConnections` flag, and that any pending changes users recently made to their public folders have converged across the organization. All of this could take several hours. 
  
## Step 7: Finalize the public folder migration (public folder downtime required)
<a name="Generatecsv"> </a>

Before you can complete your public folder migration, you need to confirm that there are no other public folder mailbox moves or public folder moves going on in your on-premises Exchange environment. To do this, use the  `Get-MoveRequest` and  `Get-PublicFolderMoveRequest` cmdlets to list any existing public folder moves. If there are any moves in progress, or in the **Completed** state, remove them. 
  
Next, to complete the public folder migration, run the following command in Exchange Online PowerShell:
  
```
Complete-MigrationBatch PublicFolderMigration
```

When you run this command, Exchange will do a final synchronization between your Exchange on-premises organization and Exchange Online. During this period, the status of the migration batch will change from **Synced** to **Completing**, and then finally to **Completed**. If the final synchronization is successful, the public folders in Exchange Online will be unlocked.
  
It is common for the migration batch to take a few hours before its status changes from **Synced** to **Completing**, at which point the final synchronization will begin.
  
## Step 8: Test and unlock public folders in Exchange Online
<a name="Generatecsv"> </a>

Once the public folder migration is complete, take the following steps to test the success of the migration, and to officially verify its completion. These final tasks allow you to test the migrated public folder hierarchy before you permanently switch your organization to Exchange Online public folders.
  
1. In Exchange Online PowerShell, assign some test user mailboxes to use one of your newly migrated public folder mailbox as their default public folder mailbox.:
    
  ```
  Set-Mailbox -Identity <test user> -DefaultPublicFolderMailbox <public folder mailbox identity>
  ```

    Make sure that your test users have necessary permissions to create public folders.
    
2. Log on to Outlook with the test user you designated in the previous step, and then take the following public folder tests. Note that it may take 15 to 30 minutes for changes to take effect. Once Outlook is aware of the changes, it might prompt you to restart a couple of times.
    
1. View the hierarchy.
    
2. Check permissions.
    
3. Create some public folders and then delete them.
    
4. Post content to, and delete content from, a public folder.
    
    If you run into any issues and determine that you're not ready to switch your organization's public folders entirely to Exchange Online, see [Roll back a public folder migration from Exchange 2013 to Exchange Online](roll-back-exchange-2013-public-folder-migration.md).
    
3. Run the following command in Exchange Online PowerShell to unlock your public folders in Exchange Online. After you run the command, it may take approximately 15 to 30 minutes for the changes to take effect. After Outlook becomes aware of the changes, it might prompt your users to restart the program several times.
    
  ```
  Set-OrganizationConfig -RemotePublicFolderMailboxes $Null -PublicFoldersEnabled Local
  ```

## Step 9: Finalize the migration on-premises
<a name="Generatecsv"> </a>

To enable emails to mail-enabled public folders on-premises, follow these steps:
  
1. In your on-premises environment, run the following script to make sure all emails to mail-enabled public folders are correctly routed to Exchange Online. The script will stamp mail-enabled public folders with an  `ExternalEmailAddress` that points them to their Exchange Online counterparts: 
    
  ```
  .\SetMailPublicFolderExternalAddress.ps1 -ExecutionSummaryFile:mepf_summary.csv
  ```

2. If your testing is successful, in your on-premises environment, run the following command to indicate that the public folder migration is complete:
    
  ```
  Set-OrganizationConfig -PublicFolderMailboxesMigrationComplete:$true -PublicFoldersEnabled Remote
  ```

## How do I know this worked?
<a name="Generatecsv"> </a>

In [Step 2: Prepare for the migration](batch-migration-of-exchange-2013-public-folders.md#Prepareformigration), you took snapshots of your on-premises public folder structure, statistics, and permissions. The following steps will help you verify your public folder migration was successful by taking the same snapshots in Exchange Online post-migration. Compare the data in both files to verify success.
  
1. In Exchange Online PowerShell, run the following command to take a snapshot of the new folder structure:
    
  ```
  Get-PublicFolder -Recurse -ResultSize Unlimited | Export-CliXML Cloud_PFStructure.xml
  ```

2. In Exchange Online PowerShell, run the following command to take a snapshot of the public folder statistics, including item count, size, and owner:
    
  ```
  Get-PublicFolder -Recurse -ResultSize Unlimited | Get-PublicFolderStatistics | Export-CliXML Cloud_PFStatistics.xml
  ```

3. In Exchange Online PowerShell, run the following command to take a snapshot of the permissions:
    
  ```
  Get-PublicFolder -Recurse -ResultSize Unlimited | Get-PublicFolderClientPermission | Select-Object Identity,User, AccessRights | Export-CliXML Cloud_PFPerms.xml
  ```

4. In Exchange Online PowerShell, run the following command to take a snapshot of the mail-enabled public folders:
    
  ```
  Get-MailPublicFolder -ResultSize Unlimited | Export-CliXML Cloud_MEPF.xml
  ```

## Known issues
<a name="Generatecsv"> </a>

The following are common public folder migration issues that you may experience in your organization.
  
- We don't support migrating public folders to Exchange Online if the number of unique public folder mailboxes in Exchange Online is more than 100.
    
- Permissions for the root public folder and the EFORMS REGISTRY folder will not be migrated to Exchange Online, and you will have to manually apply them in Exchange Online. To do this, run the following command in your Exchange Online PowerShell. Run the command once for each permission entry that is present on-premises but missing in Exchange Online:
    
  ```
  Add-PublicFolderClientPermission "\" -User <user> -AccessRights <access rights>
  Add-PublicFolderClientPermission "\NON_IPM_SUBTREE\EFORMS REGISTRY" -User <user> -AccessRights <access rights>
  ```

- Some public folder migrations will fail if some public folder mailboxes are not serving the public folder hierarchy. This means that the  `IsExcludedFromServingHierarchy` parameter on one or more mailboxes is set to  `$true`. To avoid this, set all mailboxes in Exchange Online to serve the hierarchy.
    
- **Send As** and **Send on Behalf** permissions don't get migrated to Exchange Online. If this happens with your migration, use the following commands in your on-premises environment to note who has these permissions. 
    
    To see which public folders have Send As permissions on-premises:
    
  ```
  Get-MailPublicFolder | Get-ADPermission | ?{$_.ExtendedRights -like "*Send-As*"}
  ```

    To see which public folders have Send on Behalf permissions on-premises:
    
  ```
  Get-MailPublicFolder | ?{$_.GrantSendOnBehalfTo -ne "$null"} | ft name,GrantSendOnBehalfTo
  ```

    To add Send As permission to a mail-enabled public folder in Exchange Online, in Exchange Online PowerShell type:
    
  ```
  Add-RecipientPermission -Identity <mail-enabled public folder primary SMTP address> -Trustee <name of user to be assigned permission> -AccessRights SendAs
  ```

    **Example**:
    
  ```
  Add-RecipientPermission -Identity send1 -Trustee Exo1 -AccessRights SendAs
  ```

    To add Send on Behalf permission to a mail-enabled public folder in Exchange Online, in Exchange Online PowerShell type:
    
  ```
  Set-MailPublicFolder -Identity <name of public folder> -GrantSendOnBehalfTo <user or comma-separated list of users>
  ```

    **Example**:
    
  ```
  Set-MailPublicFolder send2 -GrantSendOnBehalfTo exo1,exo2
  ```

- Having more than 10,000 folders under the "\NON_IPM_SUBTREE\DUMPSTER_ROOT" folder can cause the migration to fail. Therefore, check the "\NON_IPM_SUBTREE\DUMPSTER_ROOT" folder to see if there are more than 10,000 folders directly under it (immediate children). You can use the following command to find the number of public folders in this location:
    
  ```
  (Get-PublicFolder -GetChildren "\NON_IPM_SUBTREE\DUMPSTER_ROOT").Count 
  ```

    Exchange Online does not support more than 10,000 subfolders, which is why migrations of more than 10,000 folders will fail. We are currently developing a script to unblock such configurations. In the meantime, we suggest waiting to migrate your public folders.
    
- Migration jobs are not making progress or are stalled. This can happen if there are too many jobs running in parallel, causing jobs to fail with intermittent errors. You can reduce the number of concurrent jobs by modifying  `MaxConcurrentMigrations` and  `MaxConcurrentIncrementalSyncs` to a smaller number. Use the following example to set these values: 
    
  ```
  Set-MigrationEndpoint <PublicFolderEndpoint> -MaxConcurrentMigrations 30 -MaxConcurrentIncrementalSyncs 20  -SkipVerification 
  ```

- Migration jobs fail with the error "Error: Dumpster of the Dumpster folder." If you see this error, it should be resolved if you stop the batch and then restart it.
    
- Migration jobs fail and generate a "Request was quarantined because of the following error: The given key was not present in the dictionary" error message. This happens when a corrupted item is present in a folder that migration jobs cannot copy. To work around this issue:
    
1. Stop the migration batch.
    
2. Identify the folder containing the bad item. The migration report should include references to the folder that was being copied when the error occurred.
    
3. In your on-premises environment, move the affected folder to the primary public folder mailbox. You can use the  `New-PublicFolderMoveRequest` cmdlet to move folders. 
    
4. Wait for the folder move to complete. After it is completed, remove the move request. Then, restart the migration batch.
    
## Remove public folder mailboxes from your Exchange on-premises environment
<a name="Generatecsv"> </a>

After the migration is complete and you have verified that your public folders in Exchange Online are working as expected and contain all expected data, you can remove your on-premises public folder mailboxes. 
  
Be aware that this step is irreversible, because once public folder mailboxes are deleted, they cannot be recovered. Therefore, we strongly recommend that, in addition to verifying the success of your migration, you also monitor your Exchange Online public folders for a few weeks before you remove the on-premises public folder mailboxes.
  

