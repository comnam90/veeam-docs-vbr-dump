---
title: "Add-VBRComputerBackupJob"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrcomputerbackupjob.html"
last_updated: "7/30/2025"
product_version: "13.0.1.1071"
---

# Add-VBRComputerBackupJob


Short Description

Creates Veeam Agent backup jobs and Veeam Agent backup policies.

Applies to

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Add-VBRComputerBackupJob -OSPlatform <VBRAgentType> -Type <VBRComputerBackupJobType> -Mode <VBRComputerBackupJobMode> [-Name <String>] [-Description <String>] -BackupObject <Object[]> -BackupType <VBRComputerBackupJobBackupType> [-SelectedFilesOptions <VBRSelectedFilesBackupOptions>] [-SelectedVolumes <IVBRSelectedVolume[]>] [-ExcludedVolumes <VBRWindowsSelectedVolume[]>] [-IncludeUsbDrives] [-DestinationOptions <VBRComputerDestinationOptions>] [-BackupRepository <CBackupRepository>] [-RetentionPolicy <Int32>] [-StorageOptions <VBRStorageOptions>] [-SyntheticFullOptions <VBRFullBackupOptions>] [-ActiveFullOptions <VBRFullBackupOptions>] [-HealthCheckOptions <VBRHealthCheckOptions>] [-CompactFullOptions <VBRFullBackupOptions>] [-NotificationOptions <VBRNotificationOptions>] [-ScriptOptions <VBRJobScriptOptions>] [-EnableDeletedComputerRetention] [-DeletedComputerRetentionPolicy <Int32>] [-EnableApplicationProcessing] [-ApplicationProcessingOptions <VBRApplicationProcessingOptions[]>] [-EnableIndexing] [-IndexingOptions <VBRComputerIndexingOptions[]>] [-EnableSchedule] [-ScheduleOptions <VBRObject>] [-UseSnapshotlessFileLevelBackup] [-BackupCacheOptions <VBRBackupCacheOptions>] [-RetentionType <VBRRetentionType>] [-GFSOptions <VBRComputerGFSOptions>] [-WarningOptions <VBRComputerWarningOptions>] [-SanIntegrationOptions <VBRSanIntegrationOptions>] [-HighPriority] [<CommonParameters>] |

Detailed Description

This cmdlet creates Veeam Agent backup jobs and Veeam Agent backup policies.

To create backup policies, you must specify the protection group with the protected computers that you plan to back up and the target location for storing backups.

To create Veeam Agent backup jobs, you must specify the protection group with the protected computers and the repository for storing backups.

* Run the [Get-VBRProtectionGroup](get-vbrprotectiongroup.md) cmdlet to get the protection group.
* Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet to get the repository.
* Run the [New-VBRComputerDestinationOptions](new-vbrcomputerdestinationoptions.md) cmdlet to specify the target location for storing backups.

To enable guest file indexing and application-aware processing, you must first specify the settings for these options.

* Run the [New-VBRApplicationProcessingOptions](new-vbrapplicationprocessingoptions.md) cmdlet to specify application-aware processing settings.
* Run the [New-VBRComputerIndexingOptions](new-vbrcomputerindexingoptions.md) cmdlet to specify guest file system indexing settings.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| OSPlatform | Specifies the OS of the protected computers:   * Windows: for Windows computers. * Linux: for Linux computers. * Mac: for macOS computers. * Unix: for Unix computers. | VBRAgentType | True | Named | False |
| Type | Specifies the type of the protected computers:   * Workstation: for remote workstations or laptops. Veeam Backup & Replication will apply the settings that are available in the Workstation edition of Veeam Agent. * Server: for standalone servers. Veeam Backup & Replication will apply the settings available for the Server edition of Veeam Agent. * FailoverCluster: for failover clusters. Note: The FailoverCluster type does not apply for Veeam Agent for Linux. | VBRComputerBackupJobType | True | Named | False |
| Mode | Specifies the Veeam Agent backup job mode:   * ManagedByAgent: use this option to create the backup policy. Note: This mode is the only available mode for jobs that back up workstations. * ManagedByBackupServer: use this option to create a backup job. Note: This mode is the only available mode for jobs that back up failover clusters. | VBRComputerBackupJobMode | True | Named | False |
| BackupObject | Specifies an array of protection groups and discovered computers that you want to add to the Veeam Agent backup job. | Accepts the VBRDiscoveredEntity[] and [VBRProtectionGroup](vbrprotectiongroup.md)[] objects. To get this object, run the [Get-VBRProtectionGroup](get-vbrprotectiongroup.md) cmdlet. | True | Named | False |
| BackupType | Specifies the scope of data that you want to back up.   * EntireComputer: for entire computer image backups. * SelectedFiles: for file-level backups. Note:  This option is not available for the job that backs up failover clusters. If you select this option, you will not be able to switch to the EntireComputer or SelectedVolumes options.  * SelectedVolumes: for volume-level backups. * MacUserHome: for backups of the Users folder that contains the Home folders of all users. * UnixEntireFileSystem: for backups of Unix computers. | VBRComputerBackupJobBackupType | True | Named | False |
| SelectedFilesOptions | For file-level backups.  Specifies an array of folders with files that you want to back up. | Accepts the VBRSelectedFilesBackupOptions object. To create this object, run the [New-VBRSelectedFilesBackupOptions](new-vbrselectedfilesbackupoptions.md) cmdlet. | False | Named | False |
| SelectedVolumes | For volume-level backups.  Specifies an array of computer volumes that you want to back up. | Accepts the following objects:   * String[] Note: You can set this type for Windows-based computers only. To specify the OS volume, provide the "OS" value for this parameter. * VBRLinuxSelectedVolume Note: You can set this type for Linux-based computers only. | False | Named | False |
| ExcludedVolumes | For volume-level backups.  Specifies an array of computer volumes that you want to exclude from backup. | Accepts the VBRWindowsSelectedVolume[] object. | False | Named | False |
| Name | Specifies the name that you want to assign to the Veeam Agent backup job. | String | False | Named | False |
| Description | Specifies the description of the Veeam Agent backup job. | String | False | Named | False |
| IncludeUsbDrives | Defines that Veeam Backup & Replication will back up the periodically connected USB drives.  Note: You can set this parameter only for the following types of Veeam Agent jobs:   * Veeam Agent jobs that back up entire images of Windows computers. * Veeam Agent backup policies that back up the Users folder that contains the Home folders of all users. | SwitchParameter | False | Named | False |
| DestinationOptions | Specifies the target backup location for the protected computers that you want to add to the backup policy.  Note: This parameter does not work for Veeam Agent backup jobs. | Accepts the VBRComputerDestinationOptions object. To get this object, run the [New-VBRComputerDestinationOptions](new-vbrcomputerdestinationoptions.md) cmdlet. | False | Named | False |
| BackupRepository | Specifies the target backup location for the Veeam Agent backup job.  Note: This parameter is not available for backup policies. | Accepts the CBackupRepository object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | False | Named | False |
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
| UseSnapshotlessFileLevelBackup | Defines that the cmdlet will create the crash-consistent file-level backup without a snapshot.  Note: This parameter is available for Linux machines with the file-level backup scope only. | SwitchParameter | False | Named | False |
| BackupCacheOptions | Specifies backup cache settings of a Veeam Agent backup job for Microsoft Windows.  Note: You can apply backup cache settings for Veeam Agent backup jobs that are targeted at the following types of backup location:   * Veeam backup repository * Veeam Cloud Connect repository | Accepts the VBRBackupCacheOptions object. To get this object, run the [New-VBRBackupCacheOptions](new-vbrbackupcacheoptions.md) cmdlet. | False | Named | False |
| RetentionType | Specifies a retention type for Veeam Agent jobs managed by the Veeam Backup server. | VBRRetentionType | False | Named | False |
| GFSOptions | Specifies a GFS retention. The cmdlet will create Veeam Agent job with the specified policy. | Accepts the VBRComputerGFSOptions object. To get this object, run the [New-VBRComputerGFSOptions](new-vbrcomputergfsoptions.md) cmdlet. | False | Named | False |
| WarningOptions | Specifies notifications settings for computers processed by Veeam Agent policies.  Note: This parameter is not available for computers processed by Veeam Agent backup jobs. | Accepts the VBRComputerWarningOptions object. To get this object, run the [New-VBRComputerWarningOptions](new-vbrcomputerwarningoptions.md) cmdlet. | False | Named | False |
| SanIntegrationOptions | Specifies storage integration settings for the Veeam Agent jobs. | Accepts the VBRSanIntegrationOptions object. To get this object, run the [New-VBRSanIntegrationOptions](new-vbrsanintegrationoptions.md) cmdlet. | False | Named | False |
| HighPriority | Defines that Veeam Backup & Replication will prioritize this job higher than other similar jobs and will allocate resources to it in the first place. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

This cmdlet returns the VBRComputerBackupJob[] object that contains settings of Veeam Agent backup jobs and Veeam Agent backup policies.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Creating Veeam Agent Backup Job for Windows Servers

|  |  |
| --- | --- |
| This example shows how to create the Veeam Agent backup job for Windows servers.  |  | | --- | | $group = Get-VBRProtectionGroup -Name "WindowsGroup"  $repository = Get-VBRBackupRepository -Name "Default Backup Repository"  Add-VBRComputerBackupJob -OSPlatform Windows -Type Server -Mode ManagedByBackupServer -Name "WindowsJob" -BackupObject $group -BackupType EntireComputer -BackupRepository $repository |  Perform the following steps:   1. Run the [Get-VBRProtectionGroup](get-vbrprotectiongroup.md) cmdlet. Specify the Name parameter value. Save the result to the $group variable. 2. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Save the result to the $repository variable. 3. Run the Add-VBRComputerBackupJob cmdlet. Specify the following settings:  * Set the Windows option for the OSPlatform parameter. * Set the Server option for the Type parameter. * Set the ManagedByBackupServer option for the Mode parameter.  * Specify the Name parameter value. * Set the $group variable as the BackupObject parameter value.  * Set the EntireComputer value for the BackupType parameter.  * Set the $repository variable as the BackupRepository parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Creating Veeam Agent Backup Job for Linux Workstation

|  |  |
| --- | --- |
| This example shows how to create the Veeam Agent backup policy for Linux workstation. A backup job will run on Fridays at 7:00 PM.  |  | | --- | | $group = Get-VBRProtectionGroup -Name "LinuxGroup"  $repository = Get-VBRBackupRepository -Name "Default Backup Repository"  $destination = New-VBRComputerDestinationOptions -OSPlatform Linux -BackupRepository $repository  $daily = New-VBRDailyOptions -DayOfWeek Friday -Period 19:00  $schedule = New-VBRLinuxScheduleOptions -Type Daily -DailyOptions $daily  Add-VBRComputerBackupJob -OSPlatform Linux -Type Workstation -Mode ManagedByAgent -Name "LinuxJob" -BackupObject $group -BackupType EntireComputer -DestinationOptions $destination -ScheduleOptions $schedule -EnableSchedule |  Perform the following steps:   1. Run the [Get-VBRProtectionGroup](get-vbrprotectiongroup.md) cmdlet. Specify the Name parameter value. Save the result to the $group variable. 2. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Save the result to the $repository variable. 3. Run the [New-VBRComputerDestinationOptions](new-vbrcomputerdestinationoptions.md) cmdlet. Set the Linux option for the OSPlatform parameter. Set the $repository variable as the BackupRepository parameter value. Save the result to the $destination variable. 4. Run the [New-VBRDailyOptions](new-vbrdailyoptions.md) cmdlet. Specify the DayOfWeek and Period parameter values. Save the result to the $daily variable. 5. Run the [New-VBRLinuxScheduleOptions](new-vbrlinuxscheduleoptions.md) cmdlet. Set the Daily value for the Type parameter. Set the $daily variable as the DailyOptions parameter value. Save the result to the $schedule variable. 6. Run the Add-VBRComputerBackupJob cmdlet. Specify the following settings:  * Set the Linux option for the OSPlatform parameter. * Set the Workstation option for the Type parameter.  * Set the ManagedByAgent option for the Mode parameter. * Specify the Name parameter value.  * Set the $group variable as the BackupObject parameter value.  * Set the EntireComputer option for the BackupType parameter.  * Set the $destination variable as the DestinationOptions parameter value.  * Set the $schedule variable as the ScheduleOptions parameter value. * Provide the EnableSchedule parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Creating Veeam Agent Backup Job for Failover Cluster

|  |  |
| --- | --- |
| This example shows how to create a Veeam Agent backup job for a failover cluster. The job will run with the following settings:   * Veeam Backup & Replication will run scripts located at the C:\script\ path before and after the backup job. * The Veeam Agent backup job will still run if scripts fail.   |  | | --- | | $group = Get-VBRProtectionGroup -Name "ClusterGroup"  $repository = Get-VBRBackupRepository -Name "Default Backup Repository"  $script = New-VBRScriptProcessingOptions -ProcessingAction IgnoreFailures -ScriptPrefreezeCommand C:\script\pre-script.bat -ScriptPostthawCommand C:\script\post-script.bat  $processoptions = New-VBRApplicationProcessingOptions -BackupObject $group -OSPlatform Windows -Enable -GeneralTransactionLogAction ProcessLogsWithJob -ScriptProcessingOptions $script  Add-VBRComputerBackupJob -OSPlatform Windows -Type FailoverCluster -Mode ManagedByBackupServer -Name "NewCluster" -BackupObject $group -BackupType SelectedVolumes -SelectedVolumes "D:\" -BackupRepository $repository -EnableApplicationProcessing -ApplicationProcessingOptions $processoptions |  Perform the following steps:   1. Run the [Get-VBRProtectionGroup](get-vbrprotectiongroup.md) cmdlet. Specify the Name parameter value. Save the result to the $group variable. 2. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Save the result to the $repository variable. 3. Run the [New-VBRScriptProcessingOptions](new-vbrscriptprocessingoptions.md) cmdlet. Specify the ProcessingAction, ScriptPrefreezeCommand and ScriptPostthawCommand parameter values. Save the result to the $script variable. 4. Run the [New-VBRApplicationProcessingOptions](new-vbrapplicationprocessingoptions.md) cmdlet. Set the the $group variable as the BackupObject parameter value. Specify the OSPlatform, Enable and GeneralTransactionLogAction parameter values. Set the $script variable as the ScriptProcessingOptions parameter value. Save the result to the $processoptions variable. 5. Run the Add-VBRComputerBackupJob cmdlet. Specify the following settings:  * Set the Windows option for the OSPlatform parameter.  * Set the FailoverCluster option for the Type parameter.  * Set the ManagedByBackupServer option for the Mode parameter.  * Specify the Name parameter value.  * Set the $group variable as the BackupObject parameter value. * Set the SelectedVolumes option for the BackupType parameter.  * Specify the SelectedVolumes parameter value.  * Set the $repository variable as the BackupRepository parameter value. * Provide the EnableApplicationProcessing parameter.  * Set the $processoptions variable as the ApplicationProcessingOptions parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Creating Veeam Agent Backup Policy for Linux Server

|  |  |
| --- | --- |
| This example shows how to create a Veeam Agent backup policy for Linux server. The backup job will create volume-level backups.  |  | | --- | | $group = Get-VBRProtectionGroup -Name "LinuxGroup"  $repository = Get-VBRBackupRepository -Name "Default Backup Repository"  $destination = New-VBRComputerDestinationOptions -OSPlatform Linux -BackupRepository $repository  $scope = New-VBRLinuxSelectedVolume -Type Device -Path "/dev/sda"  Add-VBRComputerBackupJob -OSPlatform Linux -Type Server -Mode ManagedByAgent -Name "LinuxServerJob" -BackupObject $group -BackupType SelectedVolumes -DestinationOptions $destination -SelectedVolumes $scope |  Perform the following steps:   1. Run the [Get-VBRProtectionGroup](get-vbrprotectiongroup.md) cmdlet. Specify the Name parameter value. Save the result to the $group variable. 2. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Save the result to the $repository variable. 3. Run the [New-VBRComputerDestinationOptions](new-vbrcomputerdestinationoptions.md) cmdlet. Set the Linux value for the OSPlatform parameter. Set the $repository variable as the BackupRepository parameter value. Save the result to the $destination variable. 4. Run the [New-VBRLinuxSelectedVolume](new-vbrlinuxselectedvolume.md) cmdlet. Set the Device value for the Type parameter. Specify the Path parameter value. Save the result to the $scope variable. 5. Run the Add-VBRComputerBackupJob cmdlet. Specify the following settings:  * Set the Linux option for the OSPlatform parameter.  * Set the Server option for the Type parameter.  * Set the ManagedByAgent option for the Mode parameter.  * Specify the Name parameter value.  * Set the $group variable as the BackupObject parameter value. * Set the SelectedVolumes option for the BackupType parameter.  * Set the $destination variable as the DestinationOptions parameter value.  * Set the $scope variable as the SelectedVolumes parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 5. Creating Veeam Agent Backup Job for Windows Servers (Volume-Level Backup)

|  |  |
| --- | --- |
| This example shows how to create the Veeam Agent backup job for Windows servers. The backup job will include OS volumes to volume-level backups.  |  | | --- | | $group = Get-VBRProtectionGroup -Name "WindowsGroup"  $repository = Get-VBRBackupRepository -Name "Default Backup Repository"  Add-VBRComputerBackupJob -OSPlatform Windows -Type Server -Mode ManagedByBackupServer -Name "WindowsJob" -BackupObject $group -BackupType SelectedVolumes -SelectedVolumes "OS" -BackupRepository $repository |  Perform the following steps:   1. Run the [Get-VBRProtectionGroup](get-vbrprotectiongroup.md) cmdlet. Specify the Name parameter value. Save the result to the $group variable. 2. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Save the result to the $repository variable. 3. Run the Add-VBRComputerBackupJob cmdlet. Specify the following settings:  * Set the Windows option for the OSPlatform parameter. * Set the Server option for the Type parameter. * Set the ManagedByBackupServer option for the Mode parameter.  * Specify the Name parameter value. * Set the $group variable as the BackupObject parameter value.  * Set the SelectedVolumes option for the BackupType parameter. * Specify the SelectedVolumes parameter value.  * Set the $repository variable as the BackupRepository parameter value. |

Related Commands

* [Get-VBRProtectionGroup](get-vbrprotectiongroup.md)
* [Get-VBRBackupRepository](get-vbrbackuprepository.md)
* [New-VBRComputerDestinationOptions](new-vbrcomputerdestinationoptions.md)
* [New-VBRDailyOptions](new-vbrdailyoptions.md)
* [New-VBRLinuxScheduleOptions](new-vbrlinuxscheduleoptions.md)
* [New-VBRScriptProcessingOptions](new-vbrscriptprocessingoptions.md)
* [New-VBRApplicationProcessingOptions](new-vbrapplicationprocessingoptions.md)
* [New-VBRLinuxSelectedVolume](new-vbrlinuxselectedvolume.md)


