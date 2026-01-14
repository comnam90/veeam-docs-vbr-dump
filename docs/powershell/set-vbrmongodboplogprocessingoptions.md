---
title: "Set-VBRMongoDBOplogProcessingOptions"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrmongodboplogprocessingoptions.html"
last_updated: "7/31/2025"
product_version: "13.0.1.1071"
---

# Set-VBRMongoDBOplogProcessingOptions

In this article

Short Description

Modifies operations log (oplog) processing options for MongoDB replica sets.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRMongoDBOplogProcessingOptions -Options <VBRMongoDBOplogProcessingOptions> [-BackupObject <Object>] [-EnableOplogProcessing] [-OplogBackupPeriod <Int32>] [-OplogRetentionPolicy <VBRMongoDBOplogRetentionPolicy>] [-OplogRetentionPeriod <Int32>]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies the parameters of existing oplog processing options for MongoDB Replica sets. Use this cmdlet and its parameters to update the oplog backup period, retention period and retention policy.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Options | Specifies the existing processing options for oplogs of MongoDB replica sets. | Accepts the [VBRMongoDBOplogProcessingOptions](vbrmongodboplogprocessingoptions.md) object. To get this object, run the [New-VBRMongoDBOplogProcessingOptions](new-vbrmongodboplogprocessingoptions.md) cmdlet. | True | Named | True (ByPropertyName, ByValue) |
| BackupObject | Specifies an array of MongoDB replica set and protection group objects. The cmdlet will add these entities to the application backup policy. | Accepts the Object object. To get this object, run the [Get-VBRDiscoveredApplication](get-vbrdiscoveredapplication.md) cmdlet. | True | Named | True (ByPropertyName, ByValue) |
| EnableOplogProcessing | Enables the processing of existing oplogs of MongoDB replica sets. | SwitchParameter | False | Named | True (ByPropertyName) |
| OplogBackupPeriod | Modifies the interval in minutes at which the system collects the oplog backup after an image-level backup operation.  Default: 15 minutes. | Int32 | False | Named | True (ByPropertyName) |
| OplogRetentionPeriod | Modifies the retention period of the oplog in the backup repository in days.  Default: 15 days | Int32 | False | Named | True (ByPropertyName) |
| OplogRetentionPolicy | Modifies the oplog retention policy settings:   * KeepLastDays: Retains oplog backup for a specified number of days, regardless of the state of the related full backup. * KeepWithBackup: Retains oplog backup simultaneously with the related full backup. | [VBRMongoDBOplogRetentionPolicy](enums.md#VBRMongoDBOplogRetentionPolicy) | False | Named | True (ByPropertyName) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the [VBRMongoDBOplogProcessingOptions](vbrmongodboplogprocessingoptions.md) object that configures processing settings for oplogs for MongoDB replica sets.

Examples

Change Existing Oplog Processing Options

This example shows how to change existing oplog processing and retention settings, and add them to an existing MongoDB oplog application backup policy.

|  |
| --- |
| $rs = Get-VBRDiscoveredApplication -MongoDBEntityType ReplicaSet  $oplogOptions = New-VBRMongoDBOplogProcessingOptions -BackupObject $rs[0] -EnableOplogProcessing  $newOplogOptions = Set-VBRMongoDBOplogProcessingOptions -Options $oplogOptions -BackupObject $rs[0] -OplogRetentionPolicy KeepLastDays -OplogRetentionPeriod 7  $backupRepo = Get-VBRBackupRepository  Add-VBRMongoDBBackupJob -Name ps\_mongo\_job -BackupObject $rs[0] -BackupRepository $backupRepo[0] -OplogProcessingOptions $newOplogOptions[0] |

Perform the following steps:

1. Run the [Get-VBRDiscoveredApplication](get-vbrdiscoveredapplication.md) cmdlet to get the replica set. Specify the MongoDBEntityType parameter value. Save the result to the $rs variable.
2. Run the [New-VBRMongoDBOplogProcessingOptions](new-vbrmongodboplogprocessingoptions.md) cmdlet. Specify the BackupObject and EnableOplogProcessing parameter values. Save the result to the $oplogOptions variable.
3. Run the Set-VBRMongoDBOplogProcessingOptions cmdlet.

* Specify the Options parameter value with the $oplogOptions variable.
* Specify the BackupObject parameter value with the $rs variable.
* Specify the OplogRetentionPolicy parameter value with the KeepLastDays variable.
* Specify the OplogRetentionPeriod parameter value with the number of days of retention.
* Save the result to the $newOplogOptions variable.

1. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Save the result to the $backupRepo variable.
2. Run the [Add-VBRMongoDBBackupJob](add-vbrmongodbbackupjob.md) cmdlet.

* Specify the Name parameter value with the name of the backup job.
* Specify the BackupObject parameter value with the $rs variable.
* Specify the BackupRepository parameter value with the $backupRepo variable.
* Specify the OplogProcessingOptions parameter value with the $newOplogOptions variable.

Related Commands

* [Get-VBRDiscoveredApplication](get-vbrdiscoveredapplication.md)
* [New-VBRMongoDBOplogProcessingOptions](new-vbrmongodboplogprocessingoptions.md)
* [Get-VBRBackupRepository](get-vbrbackuprepository.md)
* [Add-VBRMongoDBBackupJob](add-vbrmongodbbackupjob.md)

Page updated 7/31/2025

Page content applies to build 13.0.1.1071
