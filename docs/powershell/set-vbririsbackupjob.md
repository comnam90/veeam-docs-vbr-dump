---
title: "Set-VBRIrisBackupJob"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbririsbackupjob.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Set-VBRIrisBackupJob


Short Description

Modifies InterSystems IRIS application backup policies.

Applies to

Product Edition: Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRIrisBackupJob -Job <VBRIrisBackupJob> [-Name <String>] [-Description <String>] [-BackupObject <Object[]>] [-ExcludedObject <VBRDiscoveredIris[]>] [-SourceBackup <VBRUnstructuredBackup>] [-BackupProxy <VBRNASProxyServer[]>] [-BackupRepository <CBackupRepository>] [-RetentionPolicy <Int32>] [-EnableSnapshotImmutability] [-EnableSnapshotRetention] [-SnapshotRetentionPeriod <Int32>] [-SnapshotImmutabilityPeriod <Int32>] [-StorageOptions <VBRStorageOptions>] [-ProcessingOptions <VBRIrisProcessingOptions[]>] [-HealthCheckOptions <VBRHealthCheckOptions>] [-NotificationOptions <VBRNotificationOptions>] [-ScriptOptions <VBRJobScriptOptions>] [-EnableSchedule] [-ScheduleOptions <VBRServerScheduleOptions>] [-GfsOptions <VBRComputerGFSOptions>] [-EnableGFSRetention]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies InterSystems IRIS application backup policies.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| Job | Specifies the InterSystems IRIS application backup policy that you want to modify. | Accepts the [VBRIrisBackupJob](vbririsbackupjob.md) object. To get this object, run the [Get-VBRApplicationBackupJob](get-vbrapplicationbackupjob.md) cmdlet. | True | Named | True (ByValue) |
| Name | Specifies a new name for the application backup policy. | String | False | Named | False |
| Description | Specifies a new description for the application backup policy. | String | False | Named | False |
| BackupObject | Specifies an array of discovered InterSystems IRIS instances and protection groups. The cmdlet will add these entities to the application backup policy. | Accepts the Object[] object. To get this object, run the [Get-VBRDiscoveredApplication](get-vbrdiscoveredapplication.md) cmdlet. | False | Named | False |
| ExcludedObject | Specifies an array of discovered InterSystems IRIS instances that you want to exclude from the application backup policy. | Accepts the VBRDiscoveredIris[] object. To get this object, run the [Get-VBRDiscoveredApplication](get-vbrdiscoveredapplication.md) cmdlet. | False | Named | False |
| SourceBackup | Specifies a backup that you want to map to the application backup policy. The cmdlet will use this backup as a seed for the policy. | Accepts the VBRUnstructuredBackup object. To get this object, run the [Get-VBRUnstructuredBackup](get-vbrunstructuredbackup.md) cmdlet. | False | Named | False |
| BackupProxy | Specifies an array of backup proxies that you want to use with the application backup policy. | Accepts the VBRNASProxyServer[] object. To get this object, run the [Get-VBRNASProxyServer](get-vbrnasproxyserver.md) cmdlet. | False | Named | False |
| BackupRepository | Specifies the target backup location for the application backup policy. | Accepts the CBackupRepository object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | False | Named | False |
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

The cmdlet returns the [VBRIrisBackupJob](vbririsbackupjob.md) object that contains the modified InterSystems IRIS application backup policy.

Examples

Modifying the Retention Policy of an InterSystems IRIS Backup Policy

This example shows how to change the retention policy of an existing InterSystems IRIS application backup policy.

|  |
| --- |
| $job = Get-VBRApplicationBackupJob -Name "IRIS Backup Job"  Set-VBRIrisBackupJob -Job $job -RetentionPolicy 14 |

Perform the following steps:

1. Run the [Get-VBRApplicationBackupJob](get-vbrapplicationbackupjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable.
2. Run the Set-VBRIrisBackupJob cmdlet. Set the $job variable as the Job parameter value. Specify the RetentionPolicy parameter value.

Related Commands

* [Get-VBRApplicationBackupJob](get-vbrapplicationbackupjob.md)

Page updated 2026-06-18

