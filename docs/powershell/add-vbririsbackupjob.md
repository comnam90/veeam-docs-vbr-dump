---
title: "Add-VBRIrisBackupJob"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbririsbackupjob.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Add-VBRIrisBackupJob


Short Description

Creates InterSystems IRIS application backup policies.

Applies to

Product Edition: Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Add-VBRIrisBackupJob [-Name <String>] [-Description <String>] -BackupObject <Object[]> [-ExcludedObject <VBRDiscoveredIris[]>] [-SourceBackup <VBRUnstructuredBackup>] [-BackupProxy <VBRNASProxyServer[]>] -BackupRepository <CBackupRepository> [-RetentionPolicy <Int32>] [-EnableSnapshotImmutability] [-EnableSnapshotRetention] [-SnapshotRetentionPeriod <Int32>] [-SnapshotImmutabilityPeriod <Int32>] [-StorageOptions <VBRStorageOptions>] [-ProcessingOptions <VBRIrisProcessingOptions[]>] [-HealthCheckOptions <VBRHealthCheckOptions>] [-NotificationOptions <VBRNotificationOptions>] [-ScriptOptions <VBRJobScriptOptions>] [-EnableSchedule] [-ScheduleOptions <VBRServerScheduleOptions>] [-GfsOptions <VBRComputerGFSOptions>] [-EnableGFSRetention]  [<CommonParameters>] |

Detailed Description

This cmdlet creates InterSystems IRIS application backup policies.

For application backup policies, you must specify the discovered InterSystems IRIS instances or a protection group that you plan to back up and the target location for storing backups. To create application backup policies, do the following:

1. Run one of the following cmdlets:

1. Run the [Get-VBRProtectionGroup](get-vbrprotectiongroup.md) cmdlet to get the protection group.
2. Run the [Get-VBRDiscoveredApplication](get-vbrdiscoveredapplication.md) cmdlet to get the discovered InterSystems IRIS instance.

1. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet to get the repository.
2. Run the Add-VBRIrisBackupJob cmdlet to create the application backup policy.

Parameters

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| BackupObject | Specifies an array of discovered InterSystems IRIS instances and protection groups. The cmdlet will add these entities to the application backup policy. | Accepts the Object[] object. To get this object, run the [Get-VBRDiscoveredApplication](get-vbrdiscoveredapplication.md) cmdlet. | True | Named | False |
| BackupRepository | Specifies the target backup location for the application backup policy.  Note: You can select a storage system as a repository to create a snap-only InterSystems IRIS backup job. Alternatively, you can select a Veeam Backup & Replication backup repository to create an InterSystems IRIS NAS backup job. | Accepts the CBackupRepository object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | True | Named | False |
| Name | Specifies the name that you want to assign to the application backup policy.  Note: If you do not specify this parameter, the cmdlet will assign a default name to the application backup policy. | String | False | Named | False |
| Description | Specifies the description of the application backup policy. | String | False | Named | False |
| ExcludedObject | Specifies an array of discovered InterSystems IRIS instances that you want to exclude from the application backup policy. | Accepts the VBRDiscoveredIris[] object. To get this object, run the [Get-VBRDiscoveredApplication](get-vbrdiscoveredapplication.md) cmdlet. | False | Named | False |
| SourceBackup | Specifies a backup that you want to map to the application backup policy. The cmdlet will use this backup as a seed for the new policy. | Accepts the VBRUnstructuredBackup object. To get this object, run the [Get-VBRUnstructuredBackup](get-vbrunstructuredbackup.md) cmdlet. | False | Named | False |
| BackupProxy | Specifies an array of backup proxies that you want to use with the application backup policy. If you do not specify this parameter, Veeam Backup & Replication will automatically select backup proxies. | Accepts the VBRNASProxyServer[] object. To get this object, run the [Get-VBRNASProxyServer](get-vbrnasproxyserver.md) cmdlet. | False | Named | False |
| RetentionPolicy | Specifies the number of restore points that you want to keep on the backup repository. | Int32 | False | Named | False |
| EnableSnapshotImmutability | Enables immutability for snapshots created by the application backup policy. Use the SnapshotImmutabilityPeriod parameter to specify the immutability period. | SwitchParameter | False | Named | False |
| EnableSnapshotRetention | Enables a separate retention policy for snapshots created by the application backup policy. Use the SnapshotRetentionPeriod parameter to specify the snapshot retention period. | SwitchParameter | False | Named | False |
| SnapshotRetentionPeriod | For the EnableSnapshotRetention parameter. Specifies the number of days during which Veeam Backup & Replication retains snapshots. | Int32 | False | Named | False |
| SnapshotImmutabilityPeriod | For the EnableSnapshotImmutability parameter. Specifies the number of days during which snapshots remain immutable. | Int32 | False | Named | False |
| StorageOptions | Specifies storage optimization settings for the application backup policy. | Accepts the VBRStorageOptions object. To create this object, run the [New-VBRStorageOptions](new-vbrstorageoptions.md) cmdlet. | False | Named | False |
| ProcessingOptions | Specifies processing settings for the discovered InterSystems IRIS instances added to the application backup policy. | Accepts the [VBRIrisProcessingOptions[]](vbririsprocessingoptions.md) object. To create this object, run the [New-VBRIrisProcessingOptions](new-vbririsprocessingoptions.md) cmdlet. | False | Named | False |
| HealthCheckOptions | Defines the health check schedule options for the application backup policy. | Accepts the VBRHealthCheckOptions object. To create this object, run the [New-VBRHealthCheckOptions](new-vbrhealthcheckoptions.md) cmdlet. | False | Named | False |
| NotificationOptions | Specifies notification settings for the application backup policy. | Accepts the VBRNotificationOptions object. To create this object, run the [New-VBRNotificationOptions](new-vbrnotificationoptions.md) cmdlet. | False | Named | False |
| ScriptOptions | Specifies pre-job and post-job script options for the application backup policy. | Accepts the VBRJobScriptOptions object. To create this object, run the [New-VBRJobScriptOptions](new-vbrjobscriptoptions.md) cmdlet. | False | Named | False |
| EnableSchedule | Enables the option to schedule the application backup policy to run on a regular basis. | SwitchParameter | False | Named | False |
| ScheduleOptions | Specifies the settings for the application backup policy schedule. | Accepts the VBRServerScheduleOptions object. To create this object, run the [New-VBRServerScheduleOptions](new-vbrserverscheduleoptions.md) cmdlet. | False | Named | False |
| GfsOptions | Specifies GFS (grandfather-father-son) retention policy settings for the application backup policy. | Accepts the VBRComputerGFSOptions object. To create this object, run the [New-VBRComputerGFSOptions](new-vbrcomputergfsoptions.md) cmdlet. | False | Named | False |
| EnableGFSRetention | Enables the GFS (grandfather-father-son) retention policy for the application backup policy. Use the GfsOptions parameter to specify the GFS retention policy. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the [VBRIrisBackupJob](vbririsbackupjob.md) object that contains the InterSystems IRIS application backup policy.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Creating an InterSystems IRIS Backup Policy for a Discovered Instance

|  |  |
| --- | --- |
| This example shows how to set up an InterSystems IRIS application backup policy for a single discovered instance.  |  | | --- | | $iris = Get-VBRDiscoveredApplication -Iris -IrisEntityType IrisInstance  $backupRepo = Get-VBRBackupRepository -Name 'BackupRepo1'  Add-VBRIrisBackupJob -Name "IRIS Backup Job" -BackupObject $iris[0] -BackupRepository $backupRepo |  Perform the following steps:   1. Run the [Get-VBRDiscoveredApplication](get-vbrdiscoveredapplication.md) cmdlet. Specify the Iris and IrisEntityType parameter values. Save the result to the $iris variable.   The [Get-VBRDiscoveredApplication](get-vbrdiscoveredapplication.md) cmdlet will return an array of discovered InterSystems IRIS instances. Mind the ordinal number of the necessary instance. An array starts with 0. In this example, it is the first instance in the array.   1. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Save the result to the $backupRepo variable. 2. Run the Add-VBRIrisBackupJob cmdlet.  * Specify the Name parameter with the name of the application backup policy. * Specify the BackupObject parameter value with the $iris variable. * Specify the BackupRepository parameter value with the $backupRepo variable. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Creating an InterSystems IRIS Backup Policy for a Protection Group

|  |  |
| --- | --- |
| This example shows how to set up an InterSystems IRIS application backup policy for a protection group.  |  | | --- | | $pg = Get-VBRProtectionGroup -Name "IRIS Servers"  $backupRepo = Get-VBRBackupRepository -Name 'BackupRepo1'  Add-VBRIrisBackupJob -Name "IRIS Backup Job" -BackupObject $pg -BackupRepository $backupRepo |  Perform the following steps:   1. Run the [Get-VBRProtectionGroup](get-vbrprotectiongroup.md) cmdlet. Specify the Name parameter value. Save the result to the $pg variable. 2. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Save the result to the $backupRepo variable. 3. Run the Add-VBRIrisBackupJob cmdlet.  * Specify the Name parameter with the name of the application backup policy. * Specify the BackupObject parameter value with the $pg variable. * Specify the BackupRepository parameter value with the $backupRepo variable. |

Related Commands

* [Get-VBRBackupRepository](get-vbrbackuprepository.md)
* [Get-VBRDiscoveredApplication](get-vbrdiscoveredapplication.md)
* [Get-VBRProtectionGroup](get-vbrprotectiongroup.md)

Page updated 2026-06-18

