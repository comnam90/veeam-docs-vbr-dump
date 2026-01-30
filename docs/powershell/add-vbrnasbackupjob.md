---
title: "Add-VBRNASBackupJob"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrnasbackupjob.html"
last_updated: "11/5/2024"
product_version: "13.0.1.1071"
---

# Add-VBRNASBackupJob


Short Description

Creates file backup jobs.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Add-VBRNASBackupJob -BackupObject <VBRNASBackupObject[]> -ShortTermBackupRepository <CBackupRepository> [-Name <string>] [-Description <string>] [-ShortTermRetentionType {Daily | Monthly}] [-ShortTermRetentionPeriod <int>] [-LongTermRetentionType {Monthly | Yearly}] [-LongTermBackupRepository <IRepository>] [-LongTermRetentionPeriod <int>] [-LongTermArchivalOptions <VBRUnstructuredBackupArchivalOptions>] [-EnableLongTermRetention] [-EnableCopyMode] [-SecondaryTarget <VBRUnstructuredBackupSecondaryTarget[]>] [-VersionRetentionOptions <VBRUnstructuredBackupVersionRetentionOptions>] [-StorageOptions <VBRStorageOptions>] [-HealthCheckOptions <VBRFullBackupOptions>] [-NotificationOptions <VBRNotificationOptions>] [-ScriptOptions <VBRJobScriptOptions>] [-EnableFileACLChangeTracking] [-ScheduleOptions <VBRServerScheduleOptions>] [-Force] [-HighPriority] [-TargetBackup <VBRUnstructuredBackup>] [<CommonParameters>] |

Detailed Description

This cmdlet creates file backup jobs.

Run the [Start-VBRJob](start-vbrjob.md) cmdlet to start a created job.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| BackupObject | Specifies folders and files. The cmdlet will add these folders and files to the file backup job. | Accepts the VBRNASBackupJobObject[] object. To create this object, run the [New-VBRNASBackupJobObject](new-vbrnasbackupjobobject.md) cmdlet. | True | Named | False |
| ShortTermBackupRepository | Specifies the backup repository. The cmdlet will add this repository as the short-term backup storage. | Accepts the CBackupRepository object. To create this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | True | Named | False |
| Name | Specifies a name of the file backup job. The cmdlet will create the file backup job with the specified name. | String | False | Named | False |
| Description | Specifies a description of the file backup job. The cmdlet will create the file backup job with the specified description. | String | False | Named | False |
| ShortTermRetentionType | Specifies a retention policy for the short-term backup repository. You can set the retention policy to either of the following periods:   * Daily: use this option if you want Veeam Backup & Replication to apply retention policy daily. * Monthly: use this option if you want Veeam Backup & Replication to apply retention policy monthly.   Use the ShortTermRetentionPeriod to specify the number of days or months. | VBRUnstructuredBackupShortTermRetentionType | False | Named | False |
| ShortTermRetentionPeriod | For the ShortTermRetentionType option.  Specifies the period of time to keep data on the short-term backup repository. When this period is passed, Veeam Backup & Replication will move data to the long-term archive repository. | Int32 | False | Named | False |
| LongTermBackupRepository | Specifies the archive repository. The cmdlet will add this repository as the long-term archive storage. | Accepts the CBackupRepository object. To get this object, run the following cmdlets:   * [Get-VBRBackupRepository](get-vbrbackuprepository.md): use this cmdlet to get backup repositories. * [Get-VBRObjectStorageRepository](get-vbrobjectstoragerepository.md): use this cmdlet to get object storage repositories. | False | Named | False |
| LongTermRetentionType | Specifies a retention policy for the long-term archive repository. You can set the retention policy to either of the following periods:   * Monthly: use this option if you want Veeam Backup & Replication to apply retention policy monthly. * Yearly: use this option if you want Veeam Backup & Replication to apply retention policy yearly.   Use the LongTermRetentionPeriod to specify the number of months or years. | VBRUnstructuredBackupLongTermRetentionType | False | Named | False |
| LongTermRetentionPeriod | For the LongTermRetentionType option.  Specifies the period of time to keep data on the long-term archive repository. When this period is passed, Veeam Backup & Replication will delete this data from the archive repository. | Int32 | False | Named | False |
| LongTermArchivalOptions | Specifies the retention policy for file versions that are located on the long-term archive repository. The cmdlet will create file backup jobs with the specified retention policy. | Accepts the VBRUnstructuredBackupArchivalOptions object. To create this object, run the [New-VBRUnstructuredBackupArchivalOptions](new-vbrunstructuredbackuparchivaloptions.md) cmdlet. | False | Named | False |
| EnableLongTermRetention | Defines that the cmdlet will keep files on long-term archive repository. | SwitchParameter | False | Named | False |
| EnableCopyMode | Defines that the cmdlet will keep the copy of the data stored in the backup repository in the long-term archive repository. | SwitchParameter | False | Named | False |
| SecondaryTarget | Specifies the backup repository. The cmdlet will add this repository as the secondary repository to a file backup job. | Accepts the VBRUnstructuredBackupSecondaryTarget[] object. To create this object, run the [New-VBRUnstructuredBackupSecondaryTarget](new-vbrunstructuredbackupsecondarytarget.md) cmdlet. | False | Named | False |
| VersionRetentionOptions | Specifies the settings of version-based retention for backup and archive repositories. The cmdlet will apply these settings to the file backup job. | Accepts the VBRUnstructuredBackupVersionRetentionOptions object. To create this object, run the [New-VBRUnstructuredBackupVersionRetentionOptions](new-vbrunstructuredbackupversionretentionoptions.md) cmdlet. | False | Named | False |
| StorageOptions | Specifies storage optimization settings. The cmdlet will create a file backup job with these settings. | Accepts the VBRStorageOptions object. To create this object, run the [New-VBRStorageOptions](new-vbrstorageoptions.md) cmdlet. | False | Named | False |
| HealthCheckOptions | Specifies the healthcheck schedule. The cmdlet will create a file backup job with this healthcheck schedule. | Accepts the VBRFullBackupOptions object. To create this object, run the [New-VBRFullBackupOptions](new-vbrfullbackupoptions.md) cmdlet. | False | Named | False |
| NotificationOptions | Specifies notification options. The cmdlet will create file backup jobs with these notification options. | Accepts the VBRNotificationOptions object. To create this object, run the [New-VBRFullBackupOptions](new-vbrfullbackupoptions.md) cmdlet. | False | Named | False |
| ScriptOptions | Specifies pre-job and post-job script options. The cmdlet will create file backup jobs with these script options. | Accepts the VBRJobScriptOptions object. To create this object, run the [New-VBRJobScriptOptions](new-vbrjobscriptoptions.md) cmdlet. | False | Named | False |
| EnableFileACLChangeTracking | Defines that Veeam Backup & Replication will process attributes and permissions for folders. Files that are added to these folders will inherit permissions of the folders.  If you enable this option, Veeam Backup & Replication will back up folder ACL attributes and permissions. Otherwise, they will not be backed up. | SwitchParameter | False | Named | False |
| ScheduleOptions | Specifies schedule options. The cmdlet will create file backup jobs with these schedule options. | Accepts the VBRServerScheduleOptions object. To create this object, run the [New-VBRServerScheduleOptions](new-vbrserverscheduleoptions.md) cmdlet. | False | Named | False |
| Force | Defines that the cmdlet will add a file backup without showing warnings or errors in the PowerShell console. | SwitchParameter | False | Named | False |
| HighPriority | Defines that Veeam Backup & Replication will prioritize this job higher than other similar jobs and will allocate resources to it in the first place. | SwitchParameter | Named | False | False |
| TargetBackup | For backup job mapping.  Specifies a backup chain that you want to map to a job. | Accepts the VBRUnstructuredBackup object. To create this object, run the [Get-VBRUnstructuredBackup](get-vbrunstructuredbackup.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRNASBackupJob object that contains settings of fileshare backup jobs.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Creating File Backup Job

|  |  |
| --- | --- |
| This example shows how to create a file backup job with the following settings:   * The file backup job will process files that are located on the \WinSRV2049 server in the \\WinSRV2049\Documents\January folder. * The backup files will be stored on the Repository05 short-term repository.     |  | | --- | | $server = Get-VBRUnstructuredServer -Name "\\WinSRV2049\Documents"  $object = New-VBRNASBackupJobObject -Server $server -Path "\\WinSRV2049\Documents\January"  $repository = Get-VBRBackupRepository -Name "Repository05"  Add-VBRNASBackupJob -BackupObject $object -ShortTermBackupRepository $repository |  Perform the following steps:   1. Run the [Get-VBRUnstructuredServer](get-vbrunstructuredserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 2. Run the [New-VBRNASBackupJobObject](new-vbrnasbackupjobobject.md) cmdlet. Set the $server variable as the Server parameter value. Specify the Path parameter value. Save the result to the $object variable. 3. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Save the result to the $repository variable. 4. Run the Add-VBRNASBackupJob cmdlet. Set the $object variable as the BackupObject parameter value. Set the $repository variable as the ShortTermBackupRepository parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Creating File Backup Job with Long-Term Repository

|  |  |
| --- | --- |
| This example shows how to create a file backup job. The job will be created with the following settings:   * The file backup job will process files that are located on the \WinSRV2027 server in the \\WinSRV2027\Documents\Reports folder. * The backup files will be stored on the Repository07 short-term repository until the retention period is passed. * After retention period is passed, the backup files will be moved to the Repository10 long-term repository.     |  | | --- | | $server = Get-VBRUnstructuredServer -Name "\\WinSRV2049\Documents"  $object = New-VBRNASBackupJobObject -Server $server -Path "\\WinSRV2027\Documents\Reports"  $shortrepository = Get-VBRBackupRepository -Name "Repository07"  $archiverepository = Get-VBRBackupRepository -Name "Repository10"  Add-VBRNASBackupJob -BackupObject $object -ShortTermBackupRepository $repository -LongTermBackupRepository $archiverepository |  Perform the following steps:   1. Run the [Get-VBRUnstructuredServer](get-vbrunstructuredserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 2. Run the [New-VBRNASBackupJobObject](new-vbrnasbackupjobobject.md) cmdlet. Set the $server variable as the Server parameter value. Specify the Path parameter value. Save the result to the $object variable. 3. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Save the result to the $shortrepository variable. 4. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Save the result to the $archiverepository variable. 5. Run the Add-VBRNASBackupJob cmdlet. Specify the following settings:  * Set the $object variable as the BackupObject parameter value. * Set the $shortrepository variable as the ShortTermBackupRepository parameter value. * Set the $archiverepository variable as the LongTermBackupRepository parameter value. |

Related Commands

* [Get-VBRUnstructuredServer](get-vbrunstructuredserver.md)
* [New-VBRNASBackupJobObject](new-vbrnasbackupjobobject.md)
* [Get-VBRBackupRepository](get-vbrbackuprepository.md)
* [Start-VBRJob](start-vbrjob.md)


