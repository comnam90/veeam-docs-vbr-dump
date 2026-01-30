---
title: "New-VBRMongoDBOplogProcessingOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrmongodboplogprocessingoptions.html"
last_updated: "7/31/2025"
product_version: "13.0.1.1071"
---

# New-VBRMongoDBOplogProcessingOptions


Short Description

Enables operations log (oplog) processing options for MongoDB replica sets.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRMongoDBOplogProcessingOptions -BackupObject <Object> [-EnableOplogProcessing] [-OplogBackupPeriod <Int32>] [-OplogRetentionPolicy <VBRMongoDBOplogRetentionPolicy>] [-OplogRetentionPeriod <Int32>]  [<CommonParameters>] |

Detailed Description

This cmdlet enables oplog processing options for MongoDB replica sets. Use this cmdlet to enable point-in-time restore and set oplog retention.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| BackupObject | Specifies an array of MongoDB replica set and protection group objects. The cmdlet will add these entities to the application backup policy. | Accepts the Object object. To get this object, run the [Get-VBRDiscoveredApplication](get-vbrdiscoveredapplication.md) cmdlet. | True | Named | True (ByPropertyName, ByValue) |
| EnableOplogProcessing | Enables the backup of oplogs of MongoDB replica sets. | SwitchParameter | False | Named | True (ByPropertyName) |
| OplogBackupPeriod | Specifies the interval in minutes at which the system collects the oplog backup after an image-level backup operation.  Default: 15 minutes. | Int32 | False | Named | True (ByPropertyName) |
| OplogRetentionPeriod | Specifies the retention period of the oplog in the backup repository in days.  Default: 15 days. | Int32 | False | Named | True (ByPropertyName) |
| OplogRetentionPolicy | Specifies the oplog retention policy settings:   * KeepLastDays: Retains oplog backup for a specified number of days, regardless of the state of the related full backup. * KeepWithBackup: Retains oplog backup simultaneously with the related full backup. | [VBRMongoDBOplogRetentionPolicy](enums.md#VBRMongoDBOplogRetentionPolicy) | False | Named | True (ByPropertyName) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the [VBRMongoDBOplogProcessingOptions](vbrmongodboplogprocessingoptions.md) object that configures processing settings for oplogs for MongoDB replica sets.

Examples

Enable Oplog Processing in MongoDB Application Backup Policies

This example shows how to enable the processing of oplogs and add them to an existing MongoDB oplog application backup policy.

|  |
| --- |
| $rs = Get-VBRDiscoveredApplication -MongoDBEntityType ReplicaSet  $oplogOptions = New-VBRMongoDBOplogProcessingOptions -BackupObject $rs[0] -EnableOplogProcessing -OplogBackupPeriod 30  $backupRepo = Get-VBRBackupRepository  Add-VBRMongoDBBackupJob -Name ps\_mongo\_job -BackupObject $rs -BackupRepository $backupRepo -OplogProcessingOptions $oplogOptions |

Perform the following steps:

1. Run the [Get-VBRDiscoveredApplication](get-vbrdiscoveredapplication.md) cmdlet to get the replica set. Specify the MongoDBEntityType parameter value. Save the result to the $rs variable.
2. Run the New-VBRMongoDBOplogProcessingOptions cmdlet.

* Specify the BackupObject parameter value with the $rs variable.

* Set the switch parameter EnableOplogProcessing.

* Specify the OplogBackupPeriod parameter with a number of minutes.

1. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Save the result to the $backupRepo variable.
2. Run the [Add-VBRMongoDBBackupJob](add-vbrmongodbbackupjob.md) cmdlet.

* Specify the Name parameter value with the name of the application backup policy.
* Specify the BackupObject parameter value with the $rs variable.
* Specify the BackupRepository parameter value with the $backupRepo variable.
* Specify the OplogProcessingOptions parameter value with the $oplogOptions variable.

Related Commands

* [Get-VBRDiscoveredApplication](get-vbrdiscoveredapplication.md)

* [Get-VBRBackupRepository](get-vbrbackuprepository.md)
* [Add-VBRMongoDBBackupJob](add-vbrmongodbbackupjob.md)


