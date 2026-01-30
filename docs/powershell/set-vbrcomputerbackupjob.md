---
title: "Set-VBRComputerBackupJob"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrcomputerbackupjob.html"
last_updated: "7/30/2025"
product_version: "13.0.1.1071"
---

# Set-VBRComputerBackupJob


Short Description

Modifies Veeam Agent backup jobs and Veeam Agent backup policies.

Applies to

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRComputerBackupJob -Job <VBRComputerBackupJob> [-Name <String>] [-Description <String>] [-BackupObject <Object[]>] [-BackupType <VBRComputerBackupJobBackupType>] [-SelectedFilesOptions <VBRSelectedFilesBackupOptions>] [-SelectedVolumes <IVBRSelectedVolume[]>] [-ExcludedVolumes <VBRWindowsSelectedVolume[]>] [-IncludeUsbDrives] [-DestinationOptions <VBRComputerDestinationOptions>] [-BackupRepository <CBackupRepository>] [-RetentionPolicy <Int32>] [-StorageOptions <VBRStorageOptions>] [-SyntheticFullOptions <VBRFullBackupOptions>] [-ActiveFullOptions <VBRFullBackupOptions>] [-HealthCheckOptions <VBRHealthCheckOptions>] [-CompactFullOptions <VBRFullBackupOptions>] [-NotificationOptions <VBRNotificationOptions>] [-ScriptOptions <VBRJobScriptOptions>] [-EnableDeletedComputerRetention] [-DeletedComputerRetentionPolicy <Int32>] [-EnableApplicationProcessing] [-ApplicationProcessingOptions <VBRApplicationProcessingOptions[]>] [-EnableIndexing] [-IndexingOptions <VBRComputerIndexingOptions[]>] [-EnableSchedule] [-ScheduleOptions <VBRObject>] [-UseSnapshotlessFileLevelBackup] [-BackupCacheOptions <VBRBackupCacheOptions>] [-RetentionType <VBRRetentionType>] [-GFSOptions <VBRComputerGFSOptions>] [-EnableGFSRetention] [-WarningOptions <VBRComputerWarningOptions>] [-SanIntegrationOptions <VBRSanIntegrationOptions>] [-HighPriority] [<CommonParameters>] |

Detailed Description

This cmdlet modifies settings of Veeam Agent backup jobs and Veeam Agent backup policies.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies the backup job or a backup policy that you want to modify. | Accepts the VBRComputerBackupJob object. To get this object, run the [Get-VBRComputerBackupJob](get-vbrcomputerbackupjob.md) cmdlet. | True | Named | True (ByValue) |
| Name | Specifies the name that you want to assign to a backup job or to a backup policy. | String | False | Named | False |
| Description | Specifies the description of a backup job or a backup policy. | String | False | Named | False |
| BackupObject | Specifies an array of protection groups and discovered computers that you want to add to a backup job or to a backup policy.  Important! The cmdlet will replace the protection groups that are currently added to the backup job with this array. | Accepts the VBRDiscoveredEntityType and [VBRProtectionGroup](vbrprotectiongroup.md)[] objects. To get this object, run the [Get-VBRProtectionGroup](get-vbrprotectiongroup.md) cmdlet. | False | Named | False |
| BackupType | Specifies the scope of data that you want to back up.   * EntireComputer: for entire computer image backups. * SelectedFiles: for file-level backups. Note:  This option is not available for the job that backs up failover clusters. If you select this option, you will not be able to switch to the EntireComputer or SelectedVolumes options.  * SelectedVolumes: for volume-level backups. * MacUserHome: for backups of the Users folder that contains the Home folders of all users. * UnixEntireFileSystem: for backups of Unix computers. | VBRComputerBackupJobBackupType | False | Named | False |
| SelectedFilesOptions | For file-level backups.  Specifies an array of the folders with the files that you want to back up. | Accepts the VBRSelectedFilesBackupOptions object. To create this object, run the [New-VBRSelectedFilesBackupOptions](new-vbrselectedfilesbackupoptions.md) cmdlet. | False | Named | False |
| SelectedVolumes | For volume-level backups.  Specifies an array of computer volumes that you want to back up. | Accepts the following objects:   * String[] Note: You can set this type for Windows-based computers only. To specify the OS volume, provide the "OS" value for this parameter. * VBRLinuxSelectedVolume Note: You can set this type for Linux-based computers only. | False | Named | False |
| ExcludedVolumes | For volume-level backups.  Specifies an array of computer volumes that you want to exclude from backup. | Accepts the VBRWindowsSelectedVolume[] object. | False | Named | False |
| IncludeUsbDrives | Defines that Veeam Backup & Replication will back up the periodically connected USB drives.  Note: You can set this parameter only for the following types of Veeam Agent jobs:   * Veeam Agent jobs that back up entire images of Windows computers. * Veeam Agent backup policies that back up the Users folder that contains the Home folders of all users. | SwitchParameter | False | Named | False |
| DestinationOptions | Specifies the target backup location for the protected computers that you want to add to the backup policy.  Note: This parameter is not available for backup jobs. | Accepts the VBRComputerDestinationOptions object. To get this object, run the [New-VBRComputerDestinationOptions](new-vbrcomputerdestinationoptions.md) cmdlet. | False | Named | False |
| BackupRepository | Specifies the target backup location for a backup job.  Note: This parameter is not available for backup policies. | Accepts the CBackupRepository object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | False | Named | False |
| RetentionPolicy | Specifies the retention policy for backups created by the Veeam Agent. | Int32 | False | Named | False |
| SyntheticFullOptions | Specifies the schedule for synthetic full backup. | Accepts the VBRFullBackupOptions object. To get this object, run the [New-VBRFullBackupOptions](new-vbrfullbackupoptions.md) cmdlet. | False | Named | False |
| ActiveFullOptions | Specifies the schedule for active full backup. | Accepts the VBRFullBackupOptions object. To get this object, run the [New-VBRFullBackupOptions](new-vbrfullbackupoptions.md) cmdlet. | False | Named | False |
| HealthCheckOptions | Specifies the health check schedule for the latest restore point.  Note: This parameter is not available for backup policies that Veeam Agent job applies to Linux computers. | Accepts the VBRHealthCheckOptions object. To get this object, run the [New-VBRHealthCheckOptions](new-vbrhealthcheckoptions.md) cmdlet. | False | Named | False |
| EnableDeletedComputerRetention | Enables the option to keep the backup data for machines that have not been backed up for a certain period of time. Veeam Backup & Replication will remove backup files of these computers in case Veeam Agent backup job will not be able to back up these computers for the specified period.  Use the DeletedComputerRetentionPolicy parameter to specify the number of days for keeping the backup files of machines that have not been backed up for a certain period of time. | SwitchParameter | False | Named | False |
| DeletedComputerRetentionPolicy | For the EnableDeletedComputerRetention option.  Specifies the period of time in days to keep backup files for machines that have not been backed up for a certain period of time. Veeam Backup & Replication will remove backup files of these computers in case Veeam Agent backup job will not be able to back up these computers when the specified period of time is over.  Default: 30 days. | Int32 | False | Named | False |
| CompactFullOptions | Specifies the schedule for the compact operation of full backups created by the Veeam Agent backup job.  Veeam Backup & Replication will defragment and compact a full backup per the schedule settings specified in the VBRFullBackupOptions object.  Note: This parameter is not available for backup policies that Veeam Agent job applies to Linux computers. | Accepts the VBRFullBackupOptions object. To get this object, run the [New-VBRFullBackupOptions](new-vbrfullbackupoptions.md) cmdlet. | False | Named | False |
| StorageOptions | Specifies the settings for compression and storage optimization of the target backup repository. | Accepts the VBRStorageOptions object. To get this object, run the [New-VBRStorageOptions](new-vbrstorageoptions.md) cmdlet. | False | Named | False |
| NotificationOptions | Specifies notification settings for the Veeam Agent backup job. | Accepts the [VBRNotificationOptions](vbrnotificationoptions.md) object. To get this object, run the [New-VBRNotificationOptions](new-vbrnotificationoptions.md) cmdlet. | False | Named | False |
| ScriptOptions | Specifies custom script settings. Veeam Backup & Replication will run pre-job and post-job scripts per these settings.  Note: This parameter is not available for backup policies that Veeam Agent job applies to Windows computers. | Accepts the [VBRJobScriptOptions](vbrjobscriptoptions.md) object. To get this object, run the [New-VBRJobScriptOptions](new-vbrjobscriptoptions.md) cmdlet. | False | Named | False |
| EnableApplicationProcessing | Enables application-aware processing for the Veeam Agent backup job. | SwitchParameter | False | Named | False |
| ApplicationProcessingOptions | Specifies the settings for application-aware processing. | Accepts the VBRApplicationProcessingOptions object. To get this object, run the [New-VBRApplicationProcessingOptions](new-vbrapplicationprocessingoptions.md) cmdlet. | False | Named | False |
| EnableIndexing | Enables the guest file system indexing. | SwitchParameter | False | Named | False |
| IndexingOptions | Specifies indexing scope settings. | Accepts the VBRComputerIndexingOptions object. To get this object, run the [New-VBRComputerIndexingOptions](new-vbrcomputerindexingoptions.md) cmdlet. | False | Named | False |
| EnableSchedule | Enables the Veeam Agent backup job to run on a regular basis. | SwitchParameter | False | Named | False |
| ScheduleOptions | Specifies the settings for Veeam Agent job schedule. | Accepts the objects returned by the following cmdlets:   * [New-VBRServerScheduleOptions](new-vbrserverscheduleoptions.md) * [New-VBRWindowsWorkstationScheduleOptions](new-vbrwindowsworkstationscheduleoptions.md) * [New-VBRLinuxScheduleOptions](new-vbrlinuxscheduleoptions.md) * [New-VBRMacScheduleOptions](new-vbrmacscheduleoptions.md) | False | Named | False |
| UseSnapshotlessFileLevelBackup | Defines that the cmdlet will create the crash-consistent file-level backup without a snapshot.  Note: Available for Linux machines with the file-level backup scope only. | SwitchParameter | False | Named | False |
| BackupCacheOptions | Specifies backup cache settings of a Veeam Agent backup job for Microsoft Windows.  Note: You can apply backup cache settings for Veeam Agent backup jobs that are targeted at the following types of backup location:   * Veeam backup repository * Veeam Cloud Connect repository | Accepts the VBRBackupCacheOptions object. To get this object, run the [New-VBRBackupCacheOptions](new-vbrbackupcacheoptions.md) cmdlet. | False | Named | False |
| RetentionType | Specifies retention type for Veeam Agent jobs managed by the Veeam Backup server. | VBRRetentionType | False | Named | False |
| EnableGFSRetention | Enables the GFS retention option for Veeam Agent jobs.  If you do not provide this parameter, Veeam Agent jobs will run without GFS retention policy.  Note: This options is not available for Veeam Agent policies.  Use the GFSOptions parameter to specify the GFS retention policy. | SwitchParameter | False | Named | False |
| GFSOptions | For the EnableGFSRetention option.  Specifies GFS retention. The cmdlet will create Veeam Agent job with the specified policy. | Accepts the VBRComputerGFSOptions object. To get this object, run the [New-VBRComputerGFSOptions](new-vbrcomputergfsoptions.md) cmdlet. | False | Named | False |
| WarningOptions | Specifies notifications settings for computers processed by Veeam Agent policies.  Note: This parameter is not available for computers processed by Veeam Agent backup jobs. | Accepts the VBRComputerWarningOptions object. To get this object, run the [New-VBRComputerWarningOptions](new-vbrcomputerwarningoptions.md) cmdlet. | False | Named | False |
| SanIntegrationOptions | Specifies storage integration settings for the Veeam Agent jobs. | Accepts the VBRSanIntegrationOptions object. To get this object, run the [New-VBRSanIntegrationOptions](new-vbrsanintegrationoptions.md) cmdlet. | False | Named | False |
| HighPriority | Defines that Veeam Backup & Replication will prioritize this job higher than other similar jobs and will allocate resources to it in the first place. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

This cmdlet returns the VBRComputerBackupJob[] object that contains settings of Veeam Agent backup jobs and Veeam Agent backup policies.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Applying New Storage Settings to Veeam Agent Backup Job

|  |  |
| --- | --- |
| This example shows how to apply new storage settings to an existing Veeam Agent backup job.  |  | | --- | | $job = Get-VBRComputerBackupJob -Name "ClusterJob"  $storage = New-VBRStorageOptions -CompressionLevel Optimal -StorageOptimizationType LocalTarget  Set-VBRComputerBackupJob -Job $job -StorageOptions $storage |  Perform the following steps:   1. Run the [Get-VBRComputerBackupJob](get-vbrcomputerbackupjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable. 2. Run the [New-VBRStorageOptions](new-vbrstorageoptions.md) cmdlet. Set the Optimal option for the CompressionLevel parameter. Set the LocalTarget option for the StorageOptimizationType parameter. Save the result to the $storage variable. 3. Run the Set-VBRComputerBackupJob cmdlet. Set the $job variable as the Job parameter value. Set the $storage variable as the StorageOptions parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Applying New Retention Policy to Veeam Agent Backup Job

|  |  |
| --- | --- |
| This example shows how to modify an existing Veeam Agent backup job. The job will run with the following settings:   * The job will create a full backup on a regular basis. * Veeam Backup & Replication will apply the retention policy for the backups created by the job.   |  | | --- | | $job = Get-VBRComputerBackupJob -Name "LinuxJob"  $fulloptions = New-VBRFullBackupOptions -Enable -ScheduleType Weekly -SelectedDays Sunday, Wednesday  Set-VBRComputerBackupJob -Job $job -ActiveFullOptions $fulloptions -RetentionPolicy 7 |  Perform the following steps:   1. Run the [Get-VBRComputerBackupJob](get-vbrcomputerbackupjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable. 2. Run the [New-VBRFullBackupOptions](new-vbrfullbackupoptions.md) cmdlet. Provide the Enable parameter. Specify the ScheduleType and SelectedDays parameter values. Save the result to the $fulloptions variable. 3. Run the Set-VBRComputerBackupJob cmdlet. Set the $job variable as the Job parameter value. Set the $fulloptions variable as the ActiveFullOptions parameter value. Specify the RetentionPolicy parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Adding Protection Group to Veeam Agent Backup Job

|  |  |
| --- | --- |
| This example shows how to add a protection group to an existing Veeam Agent backup job.  |  | | --- | | $job = Get-VBRComputerBackupJob -Name "BackupJob"  $objects = $job.BackupObject  $group = Get-VBRProtectionGroup -Name "Protection group"  $objects += $group  Set-VBRComputerBackupJob -Job $job -BackupObject $objects |  Perform the following steps:   1. Run the [Get-VBRComputerBackupJob](get-vbrcomputerbackupjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable. 2. Get the BackupObject property of the $job variable. Save the result to the $objects variable. 3. Run the [Get-VBRProtectionGroup](get-vbrprotectiongroup.md) cmdlet. Specify the Name parameter value. Save the result to the $group variable. 4. Add the protection group to the BackupObject array. Use the += operator. 5. Run the Set-VBRComputerBackupJob cmdlet. Set the $job variable as the Job parameter value. Set the $objects variable as the BackupObject parameter value. |

Related Commands

* [Get-VBRComputerBackupJob](get-vbrcomputerbackupjob.md)
* [New-VBRStorageOptions](new-vbrstorageoptions.md)
* [New-VBRFullBackupOptions](new-vbrfullbackupoptions.md)
* [Get-VBRProtectionGroup](get-vbrprotectiongroup.md)


