---
title: Use batch migration to migrate public folders to Exchange 2016 from previous versions
ms.prod: EXCHANGE
ms.assetid: da808e27-d2b7-4fbd-915c-a600751f526c
---


# Use batch migration to migrate public folders to Exchange 2016 from previous versions
 **Summary**: How to migrate Exchange 2010 public folders to Exchange 2016.
Migrate your public folders from Exchange Server 2010 SP3 RU8 to Microsoft Exchange Server 2016 within the same forest. If you're looking for the Exchange 2013 version of this article,  [go here](https://technet.microsoft.com/library/dn912663%28v=exchg.150%29.aspx).
  
    
    

We refer to the Exchange 2010 SP3 RU8 or later server as the legacy Exchange server.
> [!NOTE]
> The batch migration method described in this article is the only supported method for migrating legacy public folders to Exchange 2016. The old serial migration method for migrating public folders is being deprecated and is no longer supported by Microsoft. 
  
    
    

You'll perform the migration by using the ***MigrationBatch** cmdlets, and the ***PublicFolderMigrationRequest** cmdlets for troubleshooting. In addition, you will use the following PowerShell scripts:
-  `Export-PublicFolderStatistics.ps1` This script creates the folder name-to-folder size mapping file.
    
  
-  `Export-PublicFolderStatistics.psd1` This support file is used by the Export-PublicFolderStatistics.ps1 script and should be downloaded to the same location.
    
  
-  `PublicFolderToMailboxMapGenerator.ps1` This script creates the public folder-to-mailbox mapping file.
    
  
-  `PublicFolderToMailboxMapGenerator.strings.psd1` This support file is used by the PublicFolderToMailboxMapGenerator.ps1 script and should be downloaded to the same location.
    
  
-  `Create-PublicFolderMailboxesForMigration.ps1` This script creates the target public folder mailboxes for the migration. In addition, this script calculates the number of mailboxes necessary to handle the estimated user load, based on the guidelines for the number of user logons per public folder mailbox recommended in [Limits for public folders](limits-for-public-folders.md).
    
  
-  `Create-PublicFolderMailboxesForMigration.strings.psd1` This support file is used by the Create-PublicFolderMailboxesForMigration.ps1 script and should be downloaded to the same location.
    
  
 [Step 1: Download the migration scripts](use-batch-migration-to-migrate-public-folders-to-exchange-2016-from-previous-ver.md#Scripts) provides details about where to download these scripts. Make sure all scripts are downloaded to the same location.For additional management tasks related to public folders, see  [Public folder procedures](public-folder-procedures.md).
## What versions of Exchange are supported for migrating public folders to Exchange 2016?

Exchange supports moving your public folders from the following legacy versions of Exchange Server:
  
    
    

- Exchange 2010 SP3 RU8 or later
    
  
If you need to move your public folders to Exchange 2016 but your on-premises servers aren't running the minimum support versions of Exchange 2010, check out  [Use serial migration to migrate public folders to Exchange 2013 from previous versions](http://technet.microsoft.com/library/16773895-e9c3-4013-983f-683e5d14b221.aspx) (the steps for migrating to Exchange 2013 also apply to migrating to Exchange 2016). While serial migration is an option, we strongly recommend that you upgrade your on-premises servers and use batch migration. Batch migration is significantly faster and, more important, provides greater reliability.
  
    
    
You can't migrate public folders directly from Exchange 2003. If you're running Exchange 2003 in your organization, you need to move all public folder databases and replicas to Exchange 2010 SP3 RU8 or later. No public folder replicas can remain on Exchange 2003. Additionally, mail destined for an Exchange 2016 public folder can't be routed through an Exchange 2003 server.
  
    
    

## What do you need to know before you begin?


- Before you begin, we recommend that you read this topic in its entirety as downtime is required for some steps.
    
  
- The Exchange 2010 server needs to be running Exchange 2010 SP3 RU8 or later.
    
  
- The maximum number of public folders that can be migrated to Exchange 2016 in a single migration is 500,000.
    
  
- In Exchange 2016, you need to be a member of the Organization Management role group. For details about how to enable the Organization Management role group, see  [Manage role groups](manage-role-groups.md). 
    
  
- In Exchange 2010, you need to be a member of the Organization Management or Server Management RBAC role groups. For details, see  [Add Members to a Role Group](https://go.microsoft.com/fwlink/?LinkId=299212).
    
  
- Before you migrate, you should consider the  [Limits for public folders](limits-for-public-folders.md).
    
  
- Before you migrate, move all user mailboxes to Exchange 2016, because users with Exchange 2007 or Exchange 2010 mailboxes will not have access to public folders on Exchange 2016. For details, see  [Mailbox moves in Exchange 2016](mailbox-moves-in-exchange-2016.md).
    
  
- After the migration is complete, if you want external senders to send mail to the migrated mail-enabled public folders, the **Anonymous** user needs to be granted at least the **Create Items** permission. If you don't do this, external senders will receive a delivery failure notification and the messages won't be delivered to the migrated mail-enabled public folder. To read more about how to set permissions on the Anonymous user, see [Mail-enable or mail-disable a public folder](mail-enable-or-mail-disable-a-public-folder.md).
    
  
- For information about keyboard shortcuts that may apply to the procedures in this topic, see  [Keyboard shortcuts in the Exchange admin center](keyboard-shortcuts-in-the-exchange-admin-center.md).
    
  

> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at:  [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612),  [Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), or  [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351). 
  
    
    


## How do you do this?


### Step 1: Download the migration scripts
<a name="Scripts"> </a>


1. Download all scripts and supporting files from  [Public Folders Migration Scripts](https://go.microsoft.com/fwlink/?LinkId=299838).
    
  
2. Save the scripts to the local computer on which you'll be running PowerShell. For example, C:\\PFScripts. Make sure all scripts are saved in the same location.
    
  

### Step 2: Prepare for the migration
<a name="PrepareMigr"> </a>

Perform the following prerequisite steps before you begin the migration.
  
    
    
 **Prerequisite steps on the legacy Exchange server**
  
    
    

1. For verification purposes at the end of migration, we recommend that you first run the following commands on the legacy Exchange server to take snapshots of your current public folder deployment:
    
  - Run the following command to take a snapshot of the original source folder structure:
    
  ```
  
Get-PublicFolder -Recurse | Export-CliXML C:\\PFMigration\\Legacy_PFStructure.xml
  ```

  - Run the following command to take a snapshot of public folder statistics such as item count, size, and owner:
    
  ```
  Get-PublicFolderStatistics | Export-CliXML C:\\PFMigration\\Legacy_PFStatistics.xml
  ```

  - Run the following command to take a snapshot of the permissions:
    
  ```
  Get-PublicFolder -Recurse | Get-PublicFolderClientPermission | Select-Object Identity,User -ExpandProperty AccessRights | Export-CliXML C:\\PFMigration\\Legacy_PFPerms.xml
  ```


    Save the information from the preceding commands for comparison purposes after your migration is complete.
    
  
2. If the name of a public folder contains a backslash **\\**, the public folders will be created in the parent public folder when migration occurs. Before you migrate, we recommend that you rename any public folders that have a backslash in the name. 
    
1. In Exchange 2010, to locate public folders that have a backslash in the name, run the following command:
    
  ```
  Get-PublicFolderStatistics -ResultSize Unlimited | Where {($_.Name -like "*\\*") -or ($_.Name -like "*/*") } | Format-List Name, Identity

  ```

2. If any public folders are returned, you can rename them by running the following command:
    
  ```
  
Set-PublicFolder -Identity <public folder identity> -Name <new public folder name>
  ```

3. Make sure there isn't a previous record of a successful migration.
    
1. The following example checks the public folder migration status.
    
  ```
  Get-OrganizationConfig | Format-List PublicFoldersLockedforMigration, PublicFolderMigrationComplete
  ```


     If there has been a previous successful migration, the value of the _PublicFoldersLockedforMigration_ or _PublicFolderMigrationComplete_ properties is `$true`. Use the command in step 3b to set the value to  `$false`. If the value is set to  `$true`, your migration request will fail.
    
  
2. If the status of the  _PublicFoldersLockedforMigration_ or _PublicFolderMigrationComplete_ properties is `$true`, run the following command to set the value to  `$false`.
    
  ```
  Set-OrganizationConfig -PublicFoldersLockedforMigration:$false -PublicFolderMigrationComplete:$false
  ```


    > [!CAUTION]
      > After resetting these properties, you need to wait for Exchange to detect the new settings. This may take up to two hours to complete. 
For detailed syntax and parameter information, see the following topics:
  
    
    

-  [Get-PublicFolder](http://technet.microsoft.com/library/409711bc-6249-41d4-bf86-50e01240e69f.aspx)
    
  
-  [Get-PublicFolderDatabase](http://technet.microsoft.com/library/e2c9e769-ddfb-4981-906f-085834bc790f.aspx)
    
  
-  [Set-PublicFolder](http://technet.microsoft.com/library/657a8e15-2587-41b5-986c-2289b2772c89.aspx)
    
  
-  [Get-PublicFolderStatistics](http://technet.microsoft.com/library/6b435b2e-749f-47fd-9a20-9a7edaed96fb.aspx)
    
  
-  [Get-PublicFolderClientPermission](http://technet.microsoft.com/library/b991d477-e48c-4cf9-a4d0-6f1d5696991e.aspx)
    
  
-  [Get-OrganizationConfig](https://go.microsoft.com/fwlink/p/?linkid=183212)
    
  
-  [Set-OrganizationConfig](https://go.microsoft.com/fwlink/p/?linkid=183213)
    
  
 **Prerequisite steps on the Exchange 2016 server**
  
    
    

1. Make sure there are no existing public folder migration requests. If there are, clear them or your own migration request will fail. This step isn't required in all cases; it's only required if you think there may be an existing migration request in the pipeline.
    
    An existing migration request can be one of two types: batch migration or serial migration. The commands for detecting requests for each type and for removing requests of each type are as follows.
    
    > [!IMPORTANT]
      > Before removing a migration request, it is important to understand why there was an existing one. Running the following commands will determine when a previous request was made and help you diagnose any problems that may have occurred. You may need to communicate with other administrators in your organization to determine why the change was made. 

    The following example will discover any existing serial migration requests.
    


  ```
  Get-PublicFolderMigrationRequest | Get-PublicFolderMigrationRequestStatistics -IncludeReport | Format-List
  ```


    
    
    The following example removes any existing public folder serial migration requests.
    


  ```
  Get-PublicFolderMigrationRequest | Remove-PublicFolderMigrationRequest
  ```


    
    
    The following example will discover any existing batch migration requests.
    


  ```
  $batch = Get-MigrationBatch | ?{$_.MigrationType.ToString() -eq "PublicFolder"}
  ```


    
    
    The following example removes any existing public folder batch migration requests.
    


  ```
  $batch | Remove-MigrationBatch -Confirm:$false
  ```

2. Make sure no public folders or public folder mailboxes exist on the Exchange 2016 servers.
    
1. Run the following command to see if any public folders mailboxes exist.
    
  ```
  Get-Mailbox -PublicFolder 
  ```

2. If the command didn't return any public folder mailboxes, continue to  [Step 3: Generate the .csv files](use-batch-migration-to-migrate-public-folders-to-exchange-2016-from-previous-ver.md#CSVFiles). If the command returned any public folders, run the following command to see if any public folders exist:
    
  ```
  Get-PublicFolder
  ```

3. If you have any public folders, run the following PowerShell commands to remove them. Make sure you've saved any information that was in the public folders.
    
    > [!NOTE]
      > All information contained in the public folders will be permanently deleted when you remove them. 

  ```
  Get-Mailbox -PublicFolder | Where{$_.IsRootPublicFolderMailbox -eq $false} | Remove-Mailbox -PublicFolder -Force -Confirm:$false
  ```


  ```
  Get-Mailbox -PublicFolder | Remove-Mailbox -PublicFolder -Force -Confirm:$false
  ```

For detailed syntax and parameter information, see the following topics:
  
    
    

-  [Get-MigrationBatch](http://technet.microsoft.com/library/3a4d27c4-712b-40e8-b5a8-a4f1b8e5a3c6.aspx)
    
  
-  [Get-PublicFolderMigrationRequest](http://technet.microsoft.com/library/df474db6-7408-4aac-b703-424c9f36560e.aspx)
    
  
-  [Remove-PublicFolderMigrationRequest](http://technet.microsoft.com/library/2f884fb1-2b00-428c-994a-66b8d82deea4.aspx)
    
  
-  [Get-Mailbox](http://technet.microsoft.com/library/8a5a6eb9-4a75-47f9-ae3b-a3ba251cf9a8.aspx)
    
  
-  [Get-PublicFolder](http://technet.microsoft.com/library/409711bc-6249-41d4-bf86-50e01240e69f.aspx)
    
  
-  [Get-MailPublicFolder](http://technet.microsoft.com/library/da05e6cb-8ab1-4ba9-ae42-d0f631daec85.aspx)
    
  
-  [Disable-MailPublicFolder](http://technet.microsoft.com/library/92d6c890-a96a-469a-b864-99d9656b12e0.aspx)
    
  
-  [Remove-PublicFolder](http://technet.microsoft.com/library/dda460e0-2601-49ae-a43f-c75c69719196.aspx)
    
  
-  [Remove-Mailbox](http://technet.microsoft.com/library/0477708c-768c-4040-bad2-8f980606fcf4.aspx)
    
  

### Step 3: Generate the .csv files
<a name="CSVFiles"> </a>


1. On the legacy Exchange server, run the  `Export-PublicFolderStatistics.ps1` script to create the folder name-to-folder size mapping file. This script needs to be run by a local administrator. The file will contain two columns: **FolderName** and **FolderSize**. The values for the **FolderSize** column will be displayed in bytes. For example, **\\PublicFolder01,10000**.
    
  ```
  .\\Export-PublicFolderStatistics.ps1  <Folder to size map path> <FQDN of source server>
  ```


  -  _FQDN of source server_ equals the fully qualified domain name of the Mailbox server where the public folder hierarchy is hosted.
    
  
  -  _Folder to size map path_ equals the file name and path on a network shared folder where you want the .csv file saved. Later in this topic, you'll need to access this file from the Exchange 2016 server. If you specify only the file name, the file will be generated in the current PowerShell directory on the local computer.
    
  
2. Run the  `PublicFolderToMailboxMapGenerator.ps1` script to create the public folder-to-mailbox mapping file. This file is used to calculate the correct number of public folder mailboxes on the Exchange 2016 server.
    
    > [!NOTE]
      > If the name of a public folder contains a backslash **\\**, the public folders will be created in the parent public folder. We recommend that you review the .csv file and edit any names that contain a backslash. 

  ```
  .\\PublicFolderToMailboxMapGenerator.ps1 <Maximum mailbox size in bytes> <Folder to size map path> <Folder to mailbox map path>
  ```


  -  _Maximum mailbox size in bytes_ equals the maximum size you want to set for the new public folder mailboxes. When specifying this setting, be sure to allow for expansion so the public folder mailbox has room to grow.
    
  
  -  _Folder to size map path_ equals the file path of the .csv file you created when running the `Export-PublicFolderStatistics.ps1` script.
    
  
  -  _Folder to mailbox map path_ equals the file name and path of the folder-to-mailbox .csv file that you'll create with this step. If you specify only the file name, the file will be generated in the current PowerShell directory on the local computer.
    
  

### Step 4: Create the public folder mailboxes in Exchange 2016
<a name="CreatePFMbxs"> </a>


1. Run the following command to create the target public folder mailboxes. The script will create a target mailbox for each mailbox in the .csv file that you generated previously in Step 3, by running the PublicFoldertoMailboxMapGenerator.ps1 script.
    
  ```
  .\\Create-PublicFolderMailboxesForMigration.ps1 -FolderMappingCsv Mapping.csv -EstimatedNumberOfConcurrentUsers:<estimate>
  ```


     _Mapping.csv_ is the file generated by the PublicFoldertoMailboxMapGenerator.ps1 script in Step 3. The estimated number of simultaneous user connections browsing a public folder hierarchy is usually less than the total number of users in an organization.
    
  

### Step 5: Start the migration request
<a name="StartMigrRequest"> </a>

Once batch migration requests are created with the appropriate cmdlet, you can then view the requests and manage them in the EAC.
  
    
    
 **Migrate Exchange 2010 public folders**
  
    
    

1. On the Exchange 2016 server, run the following command.
    
  ```
  New-MigrationBatch -Name PFMigration -SourcePublicFolderDatabase (Get-PublicFolderDatabase -Server <Source server name>) -CSVData (Get-Content <Folder to mailbox map path> -Encoding Byte) -NotificationEmails <email addresses for migration notifications> 
  ```


    The  `NotificationEmails` parameter is optional.
    
  
2. Start the migration using the following command:
    
  ```
  Start-MigrationBatch PFMigration

  ```


    Or:
    
    You can start the migration in the EAC.
    
1. Log into Exchange Online and open the EAC.
    
  
2. Navigate to **Recipients** > **Migration**.
    
  
3. Select the migration batch you just created, and then click the start button.
    
  
The **Status** column will show the initial batch status as **Created**. The status changes to **Syncing** during migration. When the migration request is complete, the status will be **Synced**. You can double-click a batch to view the status of individual mailboxes within the batch. Mailbox jobs begin with a status of **Queued**. When the job begins the status is **Syncing**, and once  `InitialSync` is complete, the status will show **Synced**. 
  
    
    
The progress and completion of the migration can be viewed and managed in the EAC. Because the **New-MigrationBatch** cmdlet initiates a mailbox migration request for each public folder mailbox, you can view the status of these requests using the mailbox migration page. You can get to the mailbox migration page, and create migration reports that can be emailed to you, by doing the following:
  
    
    

1. Log into Exchange Online and open the EAC.
    
  
2. Navigate to **Mailbox** > **Migration**.
    
  
3. Select the migration request that was just created and then click **View Details** in the **Details** pane.
    
  
For detailed syntax and parameter information, see the following topics:
  
    
    

-  [New-PublicFolderMigrationRequest](http://technet.microsoft.com/library/4537bb70-8806-4e23-b596-6dbf9f85e84d.aspx)
    
  
-  [Get-PublicFolderDatabase](http://technet.microsoft.com/library/e2c9e769-ddfb-4981-906f-085834bc790f.aspx)
    
  
-  [Get-PublicFolderMigrationRequest](http://technet.microsoft.com/library/df474db6-7408-4aac-b703-424c9f36560e.aspx)
    
  
-  [Get-PublicFolderMigrationRequestStatistics](http://technet.microsoft.com/library/bfbcc746-b259-471b-97a4-0cf87f3cb2a6.aspx)
    
  

### Step 6: Lock down the public folders on the legacy Exchange server for final migration (downtime required)
<a name="LockDownPFs"> </a>

Until this point in the migration, users have been able to access public folders. The next steps will log users off from the legacy public folders and lock the folders while the migration completes its final synchronization. Users won't be able to access public folders during this process. Also, any mail sent to mail-enabled public folders will be queued and won't be delivered until the public folder migration is complete. 
  
    
    
Before you run the  `PublicFoldersLockedForMigration` command as described below, make sure that all jobs are in the **Synced** state. You can do this by running the `Get-PublicFolderMailboxMigrationRequest` command. Continue with this step only after you've verified that all jobs are in the **Synced** state.
  
    
    
On the legacy Exchange server, run the following command to lock the legacy public folders for finalization. 
  
    
    



```

Set-OrganizationConfig -PublicFoldersLockedForMigration:$true
```


> [!NOTE]
> If for any reason the migration batch file does not finalize ( **PublicFolderMigrationComplete** displays **False**), on the legacy server, restart the Information Store (IS). 
  
    
    

For detailed syntax and parameter information, see  [Set-OrganizationConfig](http://technet.microsoft.com/library/3b6df0fe-27c8-415f-ad0c-8b265f234c1a.aspx).
  
    
    
If your organization has multiple public folder databases, you'll need to wait until public folder replication is complete to confirm that all public folder databases have picked up the  `PublicFoldersLockedForMigration` flag and any pending changes users recently made to folders have converged across the organization. This may take several hours.
  
    
    

### Step 7: Finalize the public folder migration (downtime required)
<a name="Finalize"> </a>

First, run the following cmdlet to change the Exchange 2016 deployment type to **Remote**:
  
    
    

```
Set-OrganizationConfig -PublicFoldersEnabled Remote
```


  
    
    
Once that is done, you can complete the public folder migration by running the following command:
  
    
    



```
Complete-MigrationBatch PublicFolderMigration

```

Or, in EAC, you can complete the migration by clicking **Complete this migration batch**.
  
    
    
When you complete the migration, Exchange will perform a final synchronization between the legacy Exchange server and Exchange 2016. If the final synchronization is successful, the public folders on the Exchange 2016 server will be unlocked and the status of the migration batch will change to **Completing**, and then **Completed**. It is common for the migration batch to take a few hours before its status changes from **Synced** to **Completing**, at which point the final synchronization will begin.
  
    
    

### Step 8: Test and unlock the public folder migration
<a name="TestNUnlock"> </a>

After you finalize the public folder migration, you should run the following test to make sure that the migration was successful. This allows you to test the migrated public folder hierarchy before you switch to using Exchange 2016 public folders. 
  
    
    

1. In PowerShell, run the following command to assign some test mailboxes to use any newly migrated public folder mailbox as the default public folder mailbox. 
    
  ```
  
Set-Mailbox -Identity <Test User> -DefaultPublicFolderMailbox <Public Folder Mailbox Identity>
  ```

2. Log on to Outlook 2007 or later with the test user identified in the previous step, and then perform the following public folder tests: 
    
  - View the hierarchy.
    
  
  - Check permissions.
    
  
  - Create and delete public folders.
    
  
  - Post content to and delete content from a public folder.
    
  
3. If you run into any issues, see  [Roll back the migration](use-batch-migration-to-migrate-public-folders-to-exchange-2016-from-previous-ver.md#RollBack) later in this topic. If the public folder content and hierarchy is acceptable and functions as expected, run the following command to unlock the public folders for all other users.
    
  ```
  Get-Mailbox -PublicFolder | Set-Mailbox -PublicFolder -IsExcludedFromServingHierarchy $false
  ```


    > [!IMPORTANT]
      > Don't use the  _IsExcludedFromServingHierarchy_ parameter after initial migration validation is complete as this parameter is used by the automated storage management service for Exchange Online.
4. On the legacy Exchange server, run the following command to indicate that the public folder migration is complete:
    
  ```
  Set-OrganizationConfig -PublicFolderMigrationComplete:$true
  ```

5. After you've verified that the migration is complete, on the Exchange 2016 server, run the following command:
    
  ```
  Set-OrganizationConfig -PublicFoldersEnabled Local
  ```

6. Finally, if you want external senders to send mail to the migrated mail-enabled public folders, the **Anonymous** user needs to be granted at least the **Create Items** permission. If you don't do this, external senders will receive a delivery failure notification and the messages won't be delivered to the migrated mail-enabled public folder.
    
     You can use the Shell or Outlook to set the permissions on the Anonymous user. To read more about how to set permissions on the Anonymous user, see [Mail-enable or mail-disable a public folder](mail-enable-or-mail-disable-a-public-folder.md).
    
  

## How do I know this worked?
<a name="ItWorked"> </a>

In  [Step 2: Prepare for the migration](use-batch-migration-to-migrate-public-folders-to-exchange-2016-from-previous-ver.md#PrepareMigr), you were instructed to take snapshots of the public folder structure, statistics, and permissions before the migration began. The following steps will help verify that your public folder migration was successful by taking the same snapshots after the migration is complete. You can then compare the data in both files to verify success.
  
    
    

1. Run the following command to take a snapshot of the new folder structure.
    
  ```
  Get-PublicFolder -Recurse | Export-CliXML C:\\PFMigration\\Cloud_PFStructure.xml
  ```

2. Run the following command to take a snapshot of the public folder statistics such as item count, size, and owner.
    
  ```
  Get-PublicFolderStatistics -ResultSize Unlimited | Export-CliXML C:\\PFMigration\\Cloud_PFStatistics.xml
  ```

3. Run the following command to take a snapshot of the permissions.
    
  ```
  Get-PublicFolder -Recurse | Get-PublicFolderClientPermission | Select-Object Identity,User -ExpandProperty AccessRights | Export-CliXML  C:\\PFMigration\\Cloud_PFPerms.xml
  ```


## Remove public folder databases from the legacy Exchange servers
<a name="RemovePFDBs"> </a>

After the migration is complete, and you have verified that your Exchange 2016 public folders are working as expected, you should remove the public folder databases on the legacy Exchange servers. 
  
    
    

> [!IMPORTANT]
> Since all of your mailboxes have been migrated to Office 365 prior to the public folder migration, we strongly recommend that you route the traffic through Office 365 (decentralized mail flow) instead of centralized mail flow through your on-premises environment. If you choose to keep mail flow centralized, it could cause delivery issues to your public folders, since you've removed the public folder mailbox databases from your on-premises organization. 
  
    
    

For details about how to remove public folder databases from Exchange 2010 servers, see  [Remove Public Folder Databases](https://go.microsoft.com/fwlink/?LinkId=81409).
  
    
    

## Roll back the migration
<a name="RollBack"> </a>

If you run into issues with the migration and need to reactivate your legacy Exchange public folders, perform the following steps.
  
    
    

> [!CAUTION]
> If you roll your migration back to the legacy Exchange servers, you will lose any email that was sent to mail-enabled public folders or content that was posted to public folders in Exchange 2016 after the migration. To save this content, you need to export the public folder content to a .pst file and then import it to the legacy public folders when the rollback is complete. 
  
    
    


1. On the legacy Exchange server, run the following command to unlock the legacy Exchange public folders. This process may take several hours.
    
  ```
  Set-OrganizationConfig -PublicFoldersLockedForMigration:$False
  ```

2. On the Exchange 2016 server, run the following commands to remove the public folder mailboxes.
    
  ```
  Get-Mailbox -PublicFolder | Where{$_.IsRootPublicFolderMailbox -eq $false} | Remove-Mailbox -PublicFolder -Force -Confirm:$false
Get-Mailbox -PublicFolder | Remove-Mailbox -PublicFolder -Force -Confirm:$false
  ```

3. On the legacy Exchange server, run the following command to set the  `PublicFolderMigrationComplete` flag to `$false`.
    
  ```
  
Set-OrganizationConfig -PublicFolderMigrationComplete:$False
  ```


