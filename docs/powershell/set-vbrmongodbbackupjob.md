---
title: "Set-VBRMongoDBBackupJob"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrmongodbbackupjob.html"
last_updated: "7/30/2025"
product_version: "13.0.1.1071"
---

# Set-VBRMongoDBBackupJob

In this article

Short Description

Modifies MongoDB backup policies.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRMongoDBBackupJob -Job <VBRMongoDBBackupJob> [-Name <String>] [-Description <String>] [-BackupObject <Object[]>] [-SourceBackup <CBackup>] [-BackupRepository <CBackupRepository>] [-RetentionPolicy <Int32>] [-ActiveFullOptions <VBRFullBackupOptions>] [-SyntheticFullOptions <VBRFullBackupOptions>] [-StorageOptions <VBRStorageOptions>] [-ProcessingOptions <VBRMongoDBProcessingOptions[]>] [-OplogProcessingOptions <VBRMongoDBOplogProcessingOptions[]>] [-CompactFullOptions <VBRFullBackupOptions>] [-HealthCheckOptions <VBRHealthCheckOptions>] [-EnableSchedule] [-ScheduleOptions <VBRServerScheduleOptions>] [-GFSOptions <VBRComputerGFSOptions>] [-EnableGFSRetention] [-HighPriority] [-NotificationOptions <VBRNotificationOptions>] [<CommonParameters>] |

Detailed Description

This cmdlet modifies MongoDB Backup application backup policies.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies the MongoDB backup policy that you want to modify. | Accepts the [VBRMongoDBBackupJob](vbrmongodbbackupjob.md) object. To get this object, run the [Get-VBRApplicationBackupJob](get-vbrapplicationbackupjob.md) cmdlet. | True | Named | True (ByPropertyName, ByValue) |
| Name | Specifies the name that you want to assign to the application backup policy. | String | False | Named | False |
| Description | Specifies the description of the application backup policy. | String | False | Named | False |
| BackupObject | Specifies an array of discovered application entities: protection groups and replica sets. The cmdlet will add these entities to the application backup policy. | Accepts the Object[] object. To get this object, run the [Get-VBRDiscoveredApplication](get-vbrdiscoveredapplication.md) cmdlet. | False | Named | False |
| SourceBackup | Specifies a backup file. The cmdlet will download metadata of this backup file from the long-term repository. | Accepts the CBackup object. To get this object, run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. | False | Named | False |
| BackupRepository | Specifies the target backup location for the application backup policy. | Accepts the CBackupRepository object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | False | Named | False |
| RetentionPolicy | Specifies the retention policy for backups created by MongoDB Backup.  Note: The retention policy specifies only the number of days. | Int32 | False | Named | False |
| ActiveFullOptions | Creates an active full backup schedule for MongoDB backup policies. | Accepts the VBRFullBackupOptions object. To get this object, run the [New-VBRFullBackupOptions](new-vbrfullbackupoptions.md) cmdlet. | False | Named | False |
| SyntheticFullOptions | Creates a synthetic full backup schedule for MongoDB backup policies. | Accepts the VBRFullBackupOptions object. To get this object, run the [New-VBRFullBackupOptions](new-vbrfullbackupoptions.md) cmdlet. | False | Named | False |
| StorageOptions | Specifies storage options that you want to modify. | Accepts the VBRStorageOptions object. To create this object, run the [New-VBRStorageOptions](new-vbrstorageoptions.md) cmdlet. | False | Named | False |
| ProcessingOptions | Specifies processing settings for the application backup policy. | Accepts the [VBRMongoDBProcessingOptions](vbrmongodbprocessingoptions.md) object. To create this object, run the [New-VBRMongoDBProcessingOptions](new-vbrmongodbprocessingoptions.md) cmdlet. | False | Named | False |
| OplogProcessingOptions | Specifies oplog processing settings for the application backup policy. | Accepts the [VBRMongoDBOplogProcessingOptions[]](vbrmongodboplogprocessingoptions.md) object. To create this object, run the [New-VBRMongoDBOplogProcessingOptions](new-vbrmongodboplogprocessingoptions.md) cmdlet. | False | Named | False |
| CompactFullOptions | Specifies the schedule for the compact operation of full backups created by the MongoDB backup policy.  Veeam Backup & Replication defragments and compacts a full backup per the schedule settings specified in the VBRFullBackupOptions object. | Accepts the VBRFullBackupOptions object. To get this object, run the [New-VBRFullBackupOptions](new-vbrfullbackupoptions.md) cmdlet. | False | Named | False |
| HealthCheckOptions | Defines the health check schedule options. | Accepts the VBRHealthCheckOption object. To get this object, run the [New-VBRHealthCheckOptions](new-vbrhealthcheckoptions.md) cmdlet. | False | Named | False |
| EnableSchedule | Enables the option to schedule the application backup policy to run on a regular basis. | SwitchParameter | False | Named | False |
| ScheduleOptions | Specifies the schedule for the configuration backup policy. | Accepts the VBRServerScheduleOptions object. To create this object, run the [New-VBRServerScheduleOptions](new-vbrserverscheduleoptions.md) cmdlet. | False | Named | False |
| GFSOptions | Specifies GFS retention settings for MongoDB backup policies. | Accepts the VBRComputerGFSOptions object. To get this object, run the [New-VBRComputerGFSOptions](new-vbrcomputergfsoptions.md) cmdlet. | False | Named | False |
| EnableGFSRetention | Enables GFS retention for MongoDB backup policies. | SwitchParameter | False | Named | False |
| HighPriority | Defines that Veeam Backup & Replication will prioritize this job higher than other similar jobs and will allocate resources to it first. | SwitchParameter | False | Named | False |
| NotificationOptions | Specifies notification settings for the application backup policy. | Accepts the VBRNotificationOptions object. To define this object, run the [New-VBRNotificationOptions](new-vbrnotificationoptions.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRMongoDBBackupJob object that contains settings of backup copy jobs.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Applying New Storage Settings to MongoDB Backup Policy

|  |  |
| --- | --- |
| This example shows how to apply new storage settings to an existing MongoDB backup policy.  |  | | --- | | $job = Get-VBRApplicationBackupJob -Name "MongoDBBackupPolicy"  $storage = New-VBRStorageOptions -CompressionLevel Optimal -StorageOptimizationType LocalTarget  Set-VBRMongoDBBackupJob -Job $job -StorageOptions $storage |  Perform the following steps:   1. Run the [Get-VBRApplicationBackupJob](get-vbrapplicationbackupjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable. 2. Run the [New-VBRStorageOptions](new-vbrstorageoptions.md) cmdlet. Set the Optimal option for the CompressionLevel parameter. Set the LocalTarget option for the StorageOptimizationType parameter. Save the result to the $storage variable. 3. Run the Set-VBRMongoDBBackupJob cmdlet. Specify the Job parameter value with the $job variable. Specify the StorageOptions parameter value with the $storage variable. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Applying New Retention Policy to MongoDB Backup Policy

|  |  |
| --- | --- |
| This example shows how to modify an existing MongoDB backup policy. The policy will run with the following settings:   * The policy will create a full backup on a regular basis. * Veeam Backup & Replication will apply the retention policy for the backups created by this policy.   |  | | --- | | $job = Get-VBRApplicationBackupJob -Name "MongoDBBackupJob"  $fulloptions = New-VBRFullBackupOptions -Enable -ScheduleType Weekly -SelectedDays Sunday, Wednesday  Set-VBRMongoDBBackupJob -Job $job -ActiveFullOptions $fulloptions -RetentionPolicy 7 |  Perform the following steps:   1. Run the [Get-VBRApplicationBackupJob](get-vbrapplicationbackupjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable. 2. Run the [New-VBRFullBackupOptions](new-vbrfullbackupoptions.md) cmdlet. Provide the Enable parameter. Specify the ScheduleType and SelectedDays parameter values. Save the result to the $fulloptions variable. 3. Run the Set-VBRMongoDBBackupJob cmdlet.  * Specify the Job parameter value with the $job variable. * Specify the ActiveFullOptions parameter value with the $fulloptions variable. * Specify the RetentionPolicy parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Change Existing Oplog Processing Options

|  |  |
| --- | --- |
| This example shows how to change existing oplog processing and retention settings, and add them to an existing MongoDB oplog application backup policy.  |  | | --- | | $rs = Get-VBRDiscoveredApplication -MongoDBEntityType ReplicaSet  $oplogOptions = New-VBRMongoDBOplogProcessingOptions -BackupObject $rs[0] -EnableOplogProcessing  $newOplogOptions = Set-VBRMongoDBOplogProcessingOptions -Options $oplogOptions -BackupObject $rs[0] -OplogRetentionPolicy KeepLastDays -OplogRetentionPeriod 7  $backupRepo = Get-VBRBackupRepository  Add-VBRMongoDBBackupJob -Name ps\_mongo\_job -BackupObject $rs[0] -BackupRepository $backupRepo[0] -OplogProcessingOptions $newOplogOptions[0] |  Perform the following steps:   1. Run the [Get-VBRDiscoveredApplication](get-vbrdiscoveredapplication.md) cmdlet to get the replica set. Specify the MongoDBEntityType parameter value. Save the result to the $rs variable. 2. Run the [New-VBRMongoDBOplogProcessingOptions](new-vbrmongodboplogprocessingoptions.md) cmdlet.  * Specify the BackupObject parameter value with the $rs variable. * Set the switch parameter EnableOplogProcessing. * Save the result to the $oplogOptions variable.  1. Run the [Set-VBRMongoDBOplogProcessingOptions](set-vbrmongodboplogprocessingoptions.md) cmdlet.  * Specify the Options parameter value with the $oplogOptions variable. * Specify the BackupObject parameter value with the $rs variable. * Specify the OplogRetentionPolicy parameter value with the KeepLastDays variable. * Specify the OplogRetentionPeriod parameter value with the number of days of retention. * Save the result to the $newOplogOptions variable.  1. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Save the result to the $backupRepo variable. 2. Run the [Add-VBRMongoDBBackupJob](add-vbrmongodbbackupjob.md) cmdlet.  * Specify the Name parameter value with the name of the backup job. * Specify the BackupObject parameter value with the $rs variable. * Specify the BackupRepository parameter value with the $backupRepo variable. * Specify the OplogProcessingOptions parameter value with the $newOplogOptions variable. |

Related Commands

* [Get-VBRProtectionGroup](get-vbrprotectiongroup.md)

* [Get-VBRApplicationBackupJob](get-vbrapplicationbackupjob.md)

* [Get-VBRDiscoveredApplication](get-vbrdiscoveredapplication.md)

* [Get-VBRBackupRepository](get-vbrbackuprepository.md)
* [New-VBRFullBackupOptions](new-vbrfullbackupoptions.md)
* [New-VBRHealthCheckOptions](new-vbrhealthcheckoptions.md)
* [New-VBRStorageOptions](new-vbrstorageoptions.md)
* [New-VBRNotificationOptions](new-vbrnotificationoptions.md)
* [New-VBRDatabaseProcessingOptions](new-vbrdatabaseprocessingoptions.md)
* [New-VBRMongoDBOplogProcessingOptions](new-vbrmongodboplogprocessingoptions.md)
* [Set-VBRMongoDBOplogProcessingOptions](set-vbrmongodboplogprocessingoptions.md)

Page updated 7/30/2025

Page content applies to build 13.0.1.1071
