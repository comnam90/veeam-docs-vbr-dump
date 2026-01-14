---
title: "Add-VBRMongoDBBackupJob"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrmongodbbackupjob.html"
last_updated: "7/30/2025"
product_version: "13.0.1.1071"
---

# Add-VBRMongoDBBackupJob

In this article

Short Description

Creates MongoDB backup policies.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Add-VBRMongoDBBackupJob [-Name <String>] [-Description <String>] -BackupObject <Object[]> [-SourceBackup <CBackup>] -BackupRepository <CBackupRepository> [-RetentionPolicy <Int32>] [-StorageOptions <VBRStorageOptions>] [-SyntheticFullOptions <VBRFullBackupOptions>] [-ActiveFullOptions <VBRFullBackupOptions>] [-HealthCheckOptions <VBRHealthCheckOptions>] [-CompactFullOptions <VBRFullBackupOptions>] [-NotificationOptions <VBRNotificationOptions>] [-ProcessingOptions <VBRMongoDBProcessingOptions[]>] [-OplogProcessingOptions <VBRMongoDBOplogProcessingOptions[]>] [-EnableSchedule] [-ScheduleOptions <VBRServerScheduleOptions>] [-GFSOptions <VBRComputerGFSOptions>] [-HighPriority]  [<CommonParameters>] |

Detailed Description

This cmdlet creates MongoDB Backup application backup policies.

For application backup policies, you must specify a container object with discovered application entities (protection groups, protection group child objects, replica sets) that you plan to back up and the target location for storing backups. To create application backup policies, do the following:

1. Run one of the following cmdlets:

1. Run the [Get-VBRProtectionGroup](get-vbrprotectiongroup.md) cmdlet to get the protection group.
2. Run the [Get-VBRDiscoveredApplication](get-vbrdiscoveredapplication.md) cmdlet to get the replica set.

1. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet to get the repository.
2. Run the Add-VBRMongoDBBackupJob cmdlet to create application backup policy.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies the name that you want to assign to the application backup policy. | String | False | Named | False |
| Description | Specifies the description of the application backup policy. | String | False | Named | False |
| BackupObject | Specifies an array of discovered application entities: protection groups and replica sets. The cmdlet will add these entities to the application backup policy. | Accepts the Object[] object. To get this object, run the [Get-VBRDiscoveredApplication](get-vbrdiscoveredapplication.md) cmdlet. | True | Named | False |
| SourceBackup | Specifies a backup file. The cmdlet will download metadata of this backup file from the long-term repository. | Accepts the CBackup object. To get this object, run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. | False | Named | False |
| BackupRepository | Specifies the target backup location for the application backup policy. | Accepts the CBackupRepository object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | True | Named | False |
| RetentionPolicy | Specifies the retention policy for backups created by MongoDB backup.  Note: The retention policy specifies only the number of days. | Int32 | False | Named | False |
| StorageOptions | Specifies storage options that you want to modify. | Accepts the VBRStorageOptions object. To create this object, run the [New-VBRStorageOptions](new-vbrstorageoptions.md) cmdlet. | False | Named | False |
| SyntheticFullOptions | Creates a synthetic full backup schedule for MongoDB backup policies. | Accepts the VBRFullBackupOptions object. To get this object, run the [New-VBRFullBackupOptions](new-vbrfullbackupoptions.md) cmdlet. | False | Named | False |
| ActiveFullOptions | Creates an active full backup schedule for MongoDB backup policies. | Accepts the VBRFullBackupOptions object. To get this object, run the [New-VBRFullBackupOptions](new-vbrfullbackupoptions.md) cmdlet. | False | Named | False |
| HealthCheckOptions | Defines the health check schedule options. | Accepts the VBRHealthCheckOption object. To get this object, run the [New-VBRHealthCheckOptions](new-vbrhealthcheckoptions.md) cmdlet. | False | Named | False |
| CompactFullOptions | Specifies the schedule for the compact operation of full backups created by the MongoDB backup policy.  Veeam Backup & Replication defragments and compacts a full backup per the schedule settings specified in the VBRFullBackupOptions object. | Accepts the VBRFullBackupOptions object. To get this object, run the [New-VBRFullBackupOptions](new-vbrfullbackupoptions.md) cmdlet. | False | Named | False |
| NotificationOptions | Specifies notification settings for the application backup policy. | Accepts the VBRNotificationOptions object. To define this object, run the [New-VBRNotificationOptions](new-vbrnotificationoptions.md) cmdlet. | False | Named | False |
| ProcessingOptions | Specifies processing settings for the application backup policy. | Accepts the [VBRMongoDBProcessingOptions](vbrmongodbprocessingoptions.md) object. To create this object, run the [New-VBRMongoDBProcessingOptions](new-vbrmongodbprocessingoptions.md) cmdlet. | False | Named | False |
| OplogProcessingOptions | Specifies oplog processing settings for the application backup policy. | Accepts the [VBRMongoDBOplogProcessingOptions[]](vbrmongodboplogprocessingoptions.md) object. To create this object, run the [New-VBRMongoDBOplogProcessingOptions](new-vbrmongodboplogprocessingoptions.md) cmdlet. | False | Named | False |
| EnableSchedule | Enables the option to schedule the application backup policy to run on a regular basis. | SwitchParameter | False | Named | False |
| ScheduleOptions | Specifies the settings for the application backup policy schedule. | Accepts the VBRServerScheduleOptions object. To create this object, run the [New-VBRServerScheduleOptions](new-vbrserverscheduleoptions.md) cmdlet. | False | Named | False |
| GFSOptions | Specifies GFS retention settings for MongoDB backup policy. | Accepts the VBRComputerGFSOptions object. To get this object, run the [New-VBRComputerGFSOptions](new-vbrcomputergfsoptions.md) cmdlet. | False | Named | False |
| HighPriority | Defines that Veeam Backup & Replication will prioritize this job higher than other similar jobs and will allocate resources to it first. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Creating a MongoDB Backup Policy for a Replica Set

|  |  |
| --- | --- |
| This example shows how to set up a MongoDB backup policy for a single replica set.  |  | | --- | | $rs = Get-VBRDiscoveredApplication -MongoDBEntityType ReplicaSet[0]  $backupRepo = Get-VBRBackupRepository -Name 'BackupRepo1'  Add-VBRMongoDBBackupJob -Name MongoDB\_Backup\_Job1 -BackupObject $rs -BackupRepository $backupRepo |  Perform the following steps:   1. Run the [Get-VBRDiscoveredApplication](get-vbrdiscoveredapplication.md) cmdlet. Specify the MongoDBEntityType parameter value. Save the result to the $rs variable.   The [Get-VBRDiscoveredApplication](get-vbrdiscoveredapplication.md) cmdlet will return an array of replica sets. Mind the ordinal number of the necessary replica set. An array starts with 0. In this example, it is the first replica set in the array.   1. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Save the result to the $backupRepo variable. 2. Run the Add-VBRMongoDBBackupJob cmdlet.  * Specify the Name parameter with the name of the backup policy. * Specify the BackupObject parameter value with the the $rs variable. * Specify the BackupRepository parameter value the $backupRepo variable. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Creating a MongoDB Backup Policy for a Protection Group

|  |  |
| --- | --- |
| This example shows how to set up a MongoDB backup policy for a protection group.  |  | | --- | | $pg = Get-VBRProtectionGroup -ContainerType MongoDB[0]  $backupRepo = Get-VBRBackupRepository -Name 'BackupRepo1'  Add-VBRMongoDBBackupJob -Name MongoDB\_Backup\_Job2 -BackupObject $pg -BackupRepository $backupRepo |  Perform the following steps:   1. Run the [Get-VBRProtectionGroup](get-vbrprotectiongroup.md) cmdlet. Specify the ContainerType parameter value. Save the result to the $pg variable.   The [Get-VBRProtectionGroup](get-vbrprotectiongroup.md) cmdlet will return an array of protection groups. Mind the ordinal number of the necessary protection group. An array starts with 0. In this example, it is the first protection group in the array.   1. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Save the result to the $backupRepo variable. 2. Run the Add-VBRMongoDBBackupJob cmdlet.  * Specify the Name parameter with the name of the backup policy. * Specify the BackupObject parameter value with the $pg variable. * Specify the BackupRepository parameter value with the $backupRepo variable. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Enable Oplog Processing in MongoDB Application Backup Policies

|  |  |
| --- | --- |
| This example shows how to enable the processing of oplogs and add them to an existing MongoDB oplog application backup policy.  |  | | --- | | $rs = Get-VBRDiscoveredApplication -MongoDBEntityType ReplicaSet  $oplogOptions = New-VBRMongoDBOplogProcessingOptions -BackupObject $rs[0] -EnableOplogProcessing -OplogBackupPeriod 30  $backupRepo = Get-VBRBackupRepository  Add-VBRMongoDBBackupJob -Name ps\_mongo\_job -BackupObject $rs -BackupRepository $backupRepo -OplogProcessingOptions $oplogOptions |  Perform the following steps:   1. Run the [Get-VBRDiscoveredApplication](get-vbrdiscoveredapplication.md) cmdlet to get the replica set. Specify the MongoDBEntityType parameter value. Save the result to the $rs variable. 2. Run the New-VBRMongoDBOplogProcessingOptions cmdlet.  * Specify the BackupObject parameter value with the $rs variable. * Set the switch parameter EnableOplogProcessing. * Specify the OplogBackupPeriod parameter with a number of minutes.  1. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Save the result to the $backupRepo variable. 2. Run the [Add-VBRMongoDBBackupJob](add-vbrmongodbbackupjob.md) cmdlet.  * Specify the Name parameter value with the name of the application backup policy. * Specify the BackupObject parameter value with the $rs variable. * Specify the BackupRepository parameter value with the $backupRepo variable. * Specify the OplogProcessingOptions parameter value with the $oplogOptions variable. |

Related Commands

* [Get-VBRProtectionGroup](get-vbrprotectiongroup.md)

* [Get-VBRComputerBackupJob](get-vbrcomputerbackupjob.md)

* [Get-VBRDiscoveredApplication](get-vbrdiscoveredapplication.md)

* [Get-VBRBackupRepository](get-vbrbackuprepository.md)
* [New-VBRFullBackupOptions](new-vbrfullbackupoptions.md)
* [New-VBRHealthCheckOptions](new-vbrhealthcheckoptions.md)
* [New-VBRStorageOptions](new-vbrstorageoptions.md)
* [New-VBRNotificationOptions](new-vbrnotificationoptions.md)
* [New-VBRDatabaseProcessingOptions](new-vbrdatabaseprocessingoptions.md)

Page updated 7/30/2025

Page content applies to build 13.0.1.1071
