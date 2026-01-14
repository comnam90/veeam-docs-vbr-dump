---
title: "Set-VBRBackupCopyJob"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrbackupcopyjob.html"
last_updated: "12/19/2024"
product_version: "13.0.1.1071"
---

# Set-VBRBackupCopyJob

In this article

Short Description

Modifies backup copy jobs.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRBackupCopyJob -Job <VBRBackupCopyJob> [-Name <string>] [-Mode {Periodic | Immediate}] [-Description <string>] [-Backup <VBRBackup[]>] [-BackupJob <CBackupJob[]>] [-SourceRepository <CBackupRepository[]>] [-TargetRepository <CBackupRepository>] [-DirectOperation] [-SourceAccelerator <CWanAccelerator>] [-TargetAccelerator <CWanAccelerator>] [-IgnoreLocation] [-NotificationOptions <VBRNotificationOptions>] [-StorageOptions <VBRBackupCopyJobStorageOptions>] [-AnyTime] [-BackupWindowOptions <VBRBackupWindowOptions>] [-ScheduleOptions <VBRServerScheduleOptions>] [-RPOWarningOptions <VBRRpoNotificationOption[]>] [-ScriptOptions <VBRJobScriptOptions>] [-HealthCheckOptions <VBRHealthCheckOptions>] [-EnableTransactionLogCopy] [-GFSOptions <VBRComputerGFSOptions>] [-RetentionType {RestorePoints | RestoreDays}] [-RetentionNumber <int>] [-ProcessLatestAvailablePoint]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies Veeam Agent backup copy jobs.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| AnyTime | Defines that Veeam Backup & Replication will run a backup copy job at any time according to its schedule. | SwitchParameter | False | Named | False |
| Backup | Specifies an array of backups. The cmdlet will add these backups as source to the backup copy job.  You can specify only the array of the following backups:   * EC2 instance backups. * Azure backups. * Google Cloud VM instance backups. | Accepts the VBRBackup[] object. To get this object, run the [Get-VBREC2Backup](get-vbrec2backup.md), [Get-VBRAzureComputeBackup](get-vbrazurecomputebackup.md) or [Get-VBRGoogleCloudBackup](get-vbrgooglecloudbackup.md) cmdlet. | False | Named | True (ByPropertyName) |
| BackupJob | Specifies an array of backup jobs. The cmdlet will add backups processed by these jobs to this backup copy job. | Accepts the CBackupJob[] object. To get this object, run the [Get-VBRJob](get-vbrjob.md) cmdlet. | False | Named | True (ByPropertyName) |
| BackupWindowOptions | Specifies a time interval within which a backup copy job can start. | Accepts the VBRBackupWindowOptions object. To get this object, run the [New-VBRBackupWindowOptions](new-vbrbackupwindowoptions.md) cmdlet. | False | Named | False |
| Description | Specifies a description for a backup copy job. | String | False | Named | False |
| DirectOperation | Defines that a backup copy job will send  the data directly to the target backup repository without performing data deduplication. | SwitchParameter | False | Named | False |
| EnableTransactionLogCopy | Defines that a backup copy job will process transaction logs of the source job. | SwitchParameter | False | Named | False |
| GFSOptions | Specifies a GFS retention. The cmdlet will create a backup copy job with the specified policy. | Accepts the VBRComputerGFSOptions object. To get this object, run the [New-VBRComputerGFSOptions](new-vbrcomputergfsoptions.md) cmdlet. | False | Named | False |
| HealthCheckOptions | Specifies the health check schedule. The cmdlet will create a file backup job with this health check schedule. | Accepts the VBRHealthCheckOptions object. To create this object, run the [New-VBRHealthCheckOptions](new-vbrhealthcheckoptions.md) cmdlet. | False | Named | False |
| IgnoreLocation | Defines that the job will start even if original and target computer locations do not match. | SwitchParameter | False | Named | False |
| Job | Specifies an array of backup copy jobs that you want to modify. | Accepts the VBRBackupCopyJob[] object. To create this object, run the [Get-VBRBackupCopyJob](get-vbrbackupcopyjob.md) cmdlet. | True | Named | True(ByValue, ByPropertyName) |
| Mode | Specifies a backup copy job mode: Periodic or Immediate. | VBRBackupCopyJobMode | False | Named | False |
| Name | Specifies the name you want to assign to the backup copy job. | String | False | Named | False |
| NotificationOptions | Specifies notification options of a backup copy job. | Accepts the VBRNotificationOptions object. To create this object, run the [New-VBRNotificationOptions](new-vbrnotificationoptions.md) cmdlet. | False | Named | False |
| ProcessLatestAvailablePoint | Defines that the most recent restore point will be processed instead of waiting for the most current backup file to become available. | SwitchParameter | False | Named | False |
| RPOWarningOptions | Specifies an array of the number of hours when data must be copied from the source repository to the target repository.  Default: 1. | Accepts the VBRRpoNotificationOption[] object. To create this object, run the [New-VBRRPONotificationOption](new-vbrrponotificationoption.md) cmdlet. | False | Named | False |
| RetentionNumber | For the RetentionType set to the RestoreDays property.  Specifies a number of days for which you want to store backup files in the target location.  Default: 7 days. | Int32 | False | Named | False |
| RetentionType | Specifies the retention type for a backup copy job managed by the Veeam Backup server. You can specify one of the following types:   * RestorePoints * RestoreDays | VBRRetentionType | False | Named | False |
| ScheduleOptions | Specifies schedule options. The cmdlet will create a backup job with these schedule options. | Accepts the VBRServerScheduleOptions object. To create this object, run the [New-VBRServerScheduleOptions](new-vbrserverscheduleoptions.md) cmdlet. | False | Named | False |
| ScriptOptions | Specifies pre-job and post-job script options for a backup copy job. The cmdlet will create the job with these settings. | Accepts the VBRJobScriptOptions object. To create this object, run the [New-VBRJobScriptOptions](new-vbrjobscriptoptions.md) cmdlet. | False | Named | False |
| SourceAccelerator | Specifies the WAN accelerator on the source side.  Remember to set the pair of source and target WAN accelerators. | Accepts the [CWanAccelerator](cwanaccelerator.md) object. To get this object, run the [Get-VBRWANAccelerator](get-vbrwanaccelerator.md) cmdlet. | False | Named | False |
| SourceRepository | Specifies an array of source backup repositories. | Accepts the CBackupRepository[] object. To create this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | False | Named | True (ByPropertyName) |
| StorageOptions | Specifies the storage settings of the backup repository. The cmdlet will create a backup copy job with these settings. | Accepts the VBRBackupCopyJobStorageOptions object. To create this object, run the [New-VBRBackupCopyJobStorageOptions](new-vbrbackupcopyjobstorageoptions.md) cmdlet. | False | Named | False |
| TargetAccelerator | Specifies the WAN accelerator on the target side.  Remember to set the pair of source and target WAN accelerators. | Accepts the [CWanAccelerator](cwanaccelerator.md) object. To get this object, run the [Get-VBRWANAccelerator](get-vbrwanaccelerator.md) cmdlet. | False | Named | False |
| TargetRepository | Specifies a target backup repository. The cmdlet will copy backups to this repository. | Accepts the CBackupRepository object. To get this object, run the | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRBackupCopyJob object that contains settings of backup copy jobs.

Examples

Modifying Backup Window Settings for Backup Copy Job

This example shows how to modify backup window settings for a backup copy job named Copy Job05.

|  |
| --- |
| $job = Get-VBRBackupCopyJob -Name "Copy Job05"  $windowoptions = New-VBRBackupWindowOptions -FromDay Monday -FromHour 08 -ToDay Friday -ToHour 20  Set-VBRBackupCopyJob -Job $job -BackupWindowOptions $windowoptions |

Perform the following steps:

1. Run the [Get-VBRBackupCopyJob](get-vbrbackupcopyjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable.
2. Run the [New-VBRBackupWindowOptions](new-vbrbackupwindowoptions.md) cmdlet. Specify the FromDay, FromHour, ToDay and ToHour parameter values. Save the result to the $windowoptions variable.
3. Run the Set-VBRBackupCopyJob cmdlet. Set the $job variable as the Job parameter value. Set the $windowoptions variable as the BackupWindowOptions parameter value.

Related Commands

* [Get-VBRBackupCopyJob](get-vbrbackupcopyjob.md)
* [New-VBRBackupWindowOptions](new-vbrbackupwindowoptions.md)

Page updated 12/19/2024

Page content applies to build 13.0.1.1071
