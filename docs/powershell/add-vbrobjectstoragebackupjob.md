---
title: "Add-VBRObjectStorageBackupJob"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrobjectstoragebackupjob.html"
last_updated: "11/5/2024"
product_version: "13.0.1.1071"
---

# Add-VBRObjectStorageBackupJob

In this article

Short Description

Creates object storage backup job.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Add-VBRObjectStorageBackupJob -BackupObject <VBRObjectStorageBackupJobObject[]> [-SkipTagTracking] [-Name <String>] [-Description <String>] -ShortTermBackupRepository <CBackupRepository> [-ShortTermRetentionType <VBRUnstructuredBackupShortTermRetentionType>] [-ShortTermRetentionPeriod <Int32>] [-LongTermRetentionType <VBRUnstructuredBackupLongTermRetentionType>] [-LongTermBackupRepository <IRepository>] [-LongTermRetentionPeriod <Int32>] [-LongTermArchivalOptions <VBRUnstructuredBackupArchivalOptions>] [-EnableLongTermRetention] [-EnableCopyMode] [-SecondaryTarget <VBRUnstructuredBackupSecondaryTarget[]>] [-VersionRetentionOptions <VBRUnstructuredBackupVersionRetentionOptions>] [-StorageOptions <VBRStorageOptions>] [-HealthCheckOptions <VBRFullBackupOptions>] [-NotificationOptions <VBRNotificationOptions>] [-ScriptOptions <VBRJobScriptOptions>] [-ScheduleOptions <VBRServerScheduleOptions>] [-HighPriority] [-TargetBackup <VBRUnstructuredBackup>] [-Force][<CommonParameters>] |

Detailed Description

This cmdlet creates object storage backup job.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| BackupObject | Specifies an array of objects. The cmdlet will add these objects to the object storage backup job. | Accepts the VBRObjectStorageBackupJobObject[] object. To define this object, run the [New-VBRObjectStorageBackupJobObject](new-vbrobjectstoragebackupjobobject.md) cmdlet. | True | Named | False |
| ShortTermBackupRepository | Specifies the backup repository. The cmdlet will add this repository as the short-term backup storage. | Accepts the CBackupRepository object. To create this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | True | Named | False |
| Name | Specifies a name of the object storage backup job. The cmdlet will create the object storage backup job with this name. | String | False | Named | False |
| Description | Specifies a description of the object storage backup job. The cmdlet will create the the object storage backup job with this description. | String | False | Named | False |
| ShortTermRetentionType | Specifies a retention policy for the short-term backup repository. You can set the retention policy to either of the following periods:   * Daily: use this option if you want Veeam Backup & Replication to apply retention policy daily. * Monthly: use this option if you want Veeam Backup & Replication to apply retention policy monthly.   Use the ShortTermRetentionPeriod to specify the number of days or months. | VBRUnstructuredBackupShortTermRetentionType | False | Named | False |
| ShortTermRetentionPeriod | For the ShortTermRetentionType option.  Specifies the period of time to keep data on the short-term backup repository. When this period is passed, Veeam Backup & Replication will move data to the long-term archive repository. | Int | False | Named | False |
| LongTermBackupRepository | Specifies the archive repository. The cmdlet will add this repository as the long-term archive storage. | Accepts the IRepository object. To get this object, run the following cmdlets:   * [Get-VBRBackupRepository](get-vbrbackuprepository.md): use this cmdlet to get backup repositories. * [Get-VBRObjectStorageRepository](get-vbrobjectstoragerepository.md): use this cmdlet to get object storage repositories. | False | Named | False |
| LongTermRetentionType | Specifies a retention policy for the long-term archive repository. You can set the retention policy to either of the following periods:   * Monthly: use this option if you want Veeam Backup & Replication to apply retention policy monthly. * Yearly: use this option if you want Veeam Backup & Replication to apply retention policy yearly.   Use the LongTermRetentionPeriod to specify the number of months or years. | VBRUnstructuredBackupLongTermRetentionType | False | Named | False |
| LongTermRetentionPeriod | For the LongTermRetentionType option.  Specifies the period of time to keep data on the long-term archive repository. When this period is passed, Veeam Backup & Replication will delete this data from the archive repository. | Int | False | Named | False |
| LongTermArchivalOptions | Specifies the retention policy for data versions that are located on the long-term archive repository. The cmdlet will create object storage backup jobs with the specified retention policy. | Accepts the VBRUnstructuredBackupArchivalOptions object. To create this object, run the [New-VBRUnstructuredBackupArchivalOptions](new-vbrunstructuredbackuparchivaloptions.md) cmdlet. | False | Named | False |
| EnableLongTermRetention | Defines that the cmdlet will keep objects on long-term archive repository. | SwitchParameter | False | Named | False |
| EnableCopyMode | Defines that the cmdlet will keep the copy of the data stored in the backup repository in the long-term archive repository. | SwitchParameter | False | Named | False |
| SecondaryTarget | Specifies the backup repository. The cmdlet will add this repository as the secondary repository to the object storage backup job. | Accepts the VBRUnstructuredBackupSecondaryTarget[] object. To create this object, run the [New-VBRUnstructuredBackupSecondaryTarget](new-vbrunstructuredbackupsecondarytarget.md) cmdlet. | False | Named | False |
| VersionRetentionOptions | Specifies the settings of version-based retention for backup and archive repositories. The cmdlet will apply these settings to the object storage backup job. | Accepts the VBRUnstructuredBackupVersionRetentionOptions object. To create this object, run the [New-VBRUnstructuredBackupVersionRetentionOptions](new-vbrunstructuredbackupversionretentionoptions.md) cmdlet. | False | Named | False |
| StorageOptions | Specifies storage optimization settings. The cmdlet will create the object storage backup with these settings. | Accepts the VBRStorageOptions object. To create this object, run the [New-VBRStorageOptions](new-vbrstorageoptions.md) cmdlet. | False | Named | False |
| HealthCheckOptions | Specifies the healthcheck schedule. The cmdlet will create the object storage backup with this healthcheck schedule. | Accepts the VBRFullBackupOptions object. To create this object, run the [New-VBRFullBackupOptions](new-vbrfullbackupoptions.md) cmdlet. | False | Named | False |
| NotificationOptions | Specifies notification options. The cmdlet will create the object storage backup job with these notification options. | Accepts the VBRNotificationOptions object. To create this object, run the [New-VBRFullBackupOptions](new-vbrfullbackupoptions.md) cmdlet. | False | Named | False |
| ScriptOptions | Specifies pre-job and post-job script options. The cmdlet will create the object storage backup job with these script options. | Accepts the VBRJobScriptOptions object. To create this object, run the [New-VBRJobScriptOptions](new-vbrjobscriptoptions.md) cmdlet. | False | Named | False |
| ScheduleOptions | Specifies schedule options. The cmdlet will create the object storage backup job with these schedule options. | Accepts the VBRJobScriptOptions object. To create this object, run the [New-VBRServerScheduleOptions](new-vbrserverscheduleoptions.md) cmdlet. | False | Named | False |
| Force | Defines that the cmdlet will add a file backup without showing warnings or errors in the PowerShell console. | SwitchParameter | False | Named | False |
| HighPriority | Defines that Veeam Backup & Replication will prioritize this job higher than other similar jobs and will allocate resources to it in the first place. | SwitchParameter | False | Named | False |
| SkipTagTracking | Defines that the cmdlet will enable tag tracking for an object storage backup job. If you provide this parameter, the cmdlet will skip tracking of tags for incremental backups in case the objects content is not changed when the job runs.  Note: The cmdlet skips this parameter if you define tag masks settings with the [New-VBRObjectStorageBackupTagMask](new-vbrobjectstoragebackuptagmask.md) cmdlet. | SwitchParameter | False | Named | False |
| TargetBackup | For backup job mapping.  Specifies a backup chain that you want to map to a job. | Accepts the VBRUnstructuredBackup object. To create this object, run the [Get-VBRUnstructuredBackup](get-vbrunstructuredbackup.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRObjectStorageBackupJob object that contains settings of object storage backup job.

Examples

Adding Object Storage Backup Job

This example shows how add the Azure OS Job object storage backup job.

|  |
| --- |
| $server = Get-VBRUnstructuredServer -Name "Azure 01"  $object = New-VBRObjectStorageBackupJobObject -Server $serv -Container "Monthly Backups" -Path "Reports"  $repository = Get-VBRBackupRepository -Name "WinSrv2017"  Add-VBRObjectStorageBackupJob -BackupObject $object -Name "Azure OS Job" -ShortTermBackupRepository $repository |

Perform the following steps:

1. Run the [Get-VBRUnstructuredServer](get-vbrunstructuredserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable.
2. Run the [New-VBRObjectStorageBackupJobObject](new-vbrobjectstoragebackupjobobject.md) cmdlet. Specify the Server, Container, Day and Path parameter values. Save the result to the $object variable.
3. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Save the result to the $repository variable.
4. Run the Add-VBRObjectStorageBackupJob cmdlet. Set the $object variable as the BackupObject parameter value. Specify the Name parameter value. Set the $repository variable as the ShortTermBackupRepository parameter value.

Related Commands

* [Get-VBRUnstructuredServer](get-vbrunstructuredserver.md)
* [New-VBRObjectStorageBackupJobObject](new-vbrobjectstoragebackupjobobject.md)
* [Get-VBRBackupRepository](get-vbrbackuprepository.md)

Page updated 11/5/2024

Page content applies to build 13.0.1.1071
