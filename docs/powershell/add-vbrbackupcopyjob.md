---
title: "Add-VBRBackupCopyJob"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrbackupcopyjob.html"
last_updated: "12/19/2024"
product_version: "13.0.1.1071"
---

# Add-VBRBackupCopyJob

In this article

Short Description

Creates a backup copy job.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Create a backup copy job that will transfer data directly.

|  |
| --- |
| Add-VBRBackupCopyJob [-Name <String>] [-Description <String>] -Mode <VBRBackupCopyJobMode> [-Backup <VBRBackup[]>] [-BackupJob <CBackupJob[]>] [-SourceRepository <CBackupRepository[]>] [-TargetRepository <CBackupRepository>] [-DirectOperation] [-IgnoreLocation] [-NotificationOptions <VBRNotificationOptions>] [-StorageOptions <VBRBackupCopyJobStorageOptions>] [-BackupWindowOptions <VBRBackupWindowOptions>] [-ScheduleOptions <VBRServerScheduleOptions>] [-RPOWarningOptions <VBRRpoNotificationOption[]>] [-ScriptOptions <VBRJobScriptOptions>] [-HealthCheckOptions <VBRHealthCheckOptions>] [-EnableTransactionLogCopy] [-GFSOptions <VBRComputerGFSOptions>] [-RetentionType <VBRRetentionType>] [-RetentionNumber <Int32>] [-ProcessLatestAvailablePoint] [-TargetBackup <CBackup>]  [<CommonParameters>] |

* Create a backup copy job that will transfer data over WAN accelerators.

|  |
| --- |
| Add-VBRBackupCopyJob [-Name <String>] [-Description <String>] -Mode <VBRBackupCopyJobMode> [-Backup <VBRBackup[]>] [-BackupJob <CBackupJob[]>] [-SourceRepository <CBackupRepository[]>] [-TargetRepository <CBackupRepository>] -SourceAccelerator <CWanAccelerator> [-TargetAccelerator <CWanAccelerator>] [-IgnoreLocation] [-NotificationOptions <VBRNotificationOptions>] [-StorageOptions <VBRBackupCopyJobStorageOptions>] [-BackupWindowOptions <VBRBackupWindowOptions>] [-ScheduleOptions <VBRServerScheduleOptions>] [-RPOWarningOptions <VBRRpoNotificationOption[]>] [-ScriptOptions <VBRJobScriptOptions>] [-HealthCheckOptions <VBRHealthCheckOptions>] [-EnableTransactionLogCopy] [-GFSOptions <VBRComputerGFSOptions>] [-RetentionType <VBRRetentionType>] [-RetentionNumber <Int32>] [-ProcessLatestAvailablePoint] [-TargetBackup <CBackup>]  [<CommonParameters>] |

Detailed Description

This cmdlet creates a new backup copy job.

You can use backups, backup jobs, repositories or backup infrastructure as a source for the backup copy job.

You can transfer data in the following ways:

* Using WAN accelerators. This mode is recommended for off-site backups.

To create and run a backup copy job using WAN accelerators you need to have source and target WAN accelerators created. Run the [Add-VBRWANAccelerator](add-vbrwanaccelerator.md) cmdlet to create a WAN accelerator. WAN optimization is available only in Veeam Backup & Replication Enterprise Plus, Veeam Universal License Edition.

* Directly. With this method, the job sends the data directly to the target backup repository without performing data deduplication. This mode is recommended for on-site backups, or off-site backups using fast connections.

Use an appropriate parameter set for each way.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Backup | Specifies the array of backups. The cmdlet will add these backups as source to the backup copy job.  You can specify only the array of the following backups:   * EC2 instance backups. * Azure backups. * Google Cloud VM instance backups. | Accepts the VBRBackup[] object. To get this object, run the [Get-VBREC2Backup](get-vbrec2backup.md), [Get-VBRAzureComputeBackup](get-vbrazurecomputebackup.md) or [Get-VBRGoogleCloudBackup](get-vbrgooglecloudbackup.md) cmdlet. | False | Named | True (ByPropertyName) |
| BackupJob | Specifies an array of jobs. The cmdlet will add these jobs as source to the backup copy job. | Accepts the CBackupJob[] object. To get this object, run the [Get-VBRJob](get-vbrjob.md) cmdlet. | False | Named | True (ByPropertyName) |
| BackupWindowOption | Specifies a time interval within which a backup copy job can start. | Accepts the VBRBackupWindowOptions object. To get this object, run the [New-VBRBackupWindowOptions](new-vbrbackupwindowoptions.md) cmdlet. | False | Named | False |
| Description | Specifies a description for a backup copy job. | String | False | Named | False |
| DirectOperation | Defines that a backup copy job will send  the data directly to the target backup repository without performing data deduplication. | SwitchParameter | True | Named | False |
| EnableTransactionLogCopy | Defines that a backup copy job will process transaction logs of the source job. | SwitchParameter | False | Named | False |
| GFSOptions | Specifies a GFS retention. The cmdlet will create a backup copy job with the specified policy. | Accepts the VBRComputerGFSOptions object. To get this object, run the [New-VBRComputerGFSOptions](new-vbrcomputergfsoptions.md) cmdlet. | False | Named | False |
| HealthCheckOptions | Specifies the health check schedule. The cmdlet will create a file backup job with this health check schedule. | Accepts the VBRHealthCheckOptions object. To create this object, run the [New-VBRHealthCheckOptions](new-vbrhealthcheckoptions.md) cmdlet. | False | Named | False |
| IgnoreLocation | Defines that the job will be created even if original and target computer locations do not match.  If you do not specify this parameter and locations are different, the job will not start. | SwitchParameter | False | Named | False |
| Mode | Specifies a backup copy job mode: Periodic or Immediate. | VBRBackupCopyJobMode | True | Named | False |
| Name | Specifies the name you want to assign to the backup copy job. | String | False | Named | False |
| NotificationOptions | Specifies notification options of a backup copy job. | Accepts the VBRNotificationOptions object. To create this object, run the [New-VBRNotificationOptions](new-vbrnotificationoptions.md) cmdlet. | False | Named | False |
| ProcessLatestAvailablePoint | Defines that the most recent restore point will be processed instead of waiting for the most current backup file to become available. | SwitchParameter | False | Named | False |
| RPOWarningOptions | Specifies an array of the number of hours when data must be copied from the source repository to the target repository.  Default: 1. | Accepts the VBRRpoNotificationOption[] object. To create this object, run the [New-VBRRPONotificationOption](new-vbrrponotificationoption.md) cmdlet. | False | Named | False |
| RetentionNumber | For the RetentionType set to the RestoreDays property.  Specifies a number of days for which you want to store backup files in the target location.  Default: 7 days. | Int32 | False | Named | False |
| RetentionType | Specifies the retention type for a backup copy job managed by the Veeam Backup server. You can specify one of the following types:   * RestorePoints * RestoreDays | VBRRetentionType | False | Named | False |
| ScheduleOptions | Specifies schedule options. The cmdlet will create a backup job with these schedule options. | Accepts the VBRServerScheduleOptions object. To create this object, run the [New-VBRServerScheduleOptions](new-vbrserverscheduleoptions.md) cmdlet. | False | Named | False |
| ScriptOptions | Specifies pre-job and post-job script options for a backup copy job. The cmdlet will create the job with these settings. | Accepts the VBRJobScriptOptions object. To create this object, run the [New-VBRJobScriptOptions](new-vbrjobscriptoptions.md) cmdlet. | False | Named | False |
| SourceAccelerator | Specifies the WAN accelerator on the source side.  Remember to set the pair of source and target WAN accelerators. | Accepts the [CWanAccelerator](cwanaccelerator.md) object. To get this object, run the [Get-VBRWANAccelerator](get-vbrwanaccelerator.md) cmdlet. | True | Named | False |
| SourceRepository | Specifies an array of source backup repositories. | Accepts the CBackupRepository[] object. To create this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | False | Named | True (ByPropertyName) |
| StorageOptions | Specifies the storage settings of the backup repository. The cmdlet will create a backup copy job with these settings. | Accepts the VBRBackupCopyJobStorageOptions object. To create this object, run the [New-VBRBackupCopyJobStorageOptions](new-vbrbackupcopyjobstorageoptions.md) cmdlet. | False | Named | False |
| TargetAccelerator | Specifies the WAN accelerator on the target side.  Remember to set the pair of source and target WAN accelerators. | Accepts the [CWanAccelerator](cwanaccelerator.md) object. To get this object, run the [Get-VBRWANAccelerator](get-vbrwanaccelerator.md) cmdlet. | False | Named | False |
| TargetRepository | Specifies a target backup repository. The cmdlet will copy backups to this repository. | Accepts the CBackupRepository object. To get this object, run the | False | Named | False |
| TargetBackup | Specifies a target backup. The cmdlet will copy backups to this repository. | Accepts the CBackup object. To get this object, run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRBackupCopyJob object that contains settings of backup copy jobs.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Creating Backup Copy Job Which Transfers Data Directly

|  |  |
| --- | --- |
| This command creates a backup copy job that will transfer data directly.  |  | | --- | | Add-VBRBackupCopyJob -Mode Immediate -DirectOperation -Name CopyJob1 | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Creating Backup Copy Job Which Transfers Data Using WAN Accelerators

|  |  |
| --- | --- |
| This example shows how to create a backup copy job that will transfer data over WAN accelerators.  |  | | --- | | $wansource = Get-VBRWANAccelerator  $wantarget = Get-VBRWANAccelerator  Add-VBRBackupCopyJob -Mode Immediate -SourceAccelerator $wansource -TargetAccelerator $wantarget -Name CopyJob1 |  Perform the following steps:   1. Run the [Get-VBRWANAccelerator](get-vbrwanaccelerator.md) cmdlet. Save the result to the $wansource variable. 2. Run the [Get-VBRWANAccelerator](get-vbrwanaccelerator.md) cmdlet. Save the result to the $wantarget variable. 3. Run the Add-VBRBackupCopyJob cmdlet. Specify the following settings:  * Set the Immediate value as the Mode parameter value. * Set the $wansource variable as the SourceAccelerator parameter value. * Set the $wansource variable as the TargetAccelerator parameter value. * Specify the Name parameter value. |

Related Commands

[Get-VBRWANAccelerator](get-vbrwanaccelerator.md)

Page updated 12/19/2024

Page content applies to build 13.0.1.1071
