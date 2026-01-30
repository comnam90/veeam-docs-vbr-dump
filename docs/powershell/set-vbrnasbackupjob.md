---
title: "Set-VBRNASBackupJob"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrnasbackupjob.html"
last_updated: "10/2/2025"
product_version: "13.0.1.1071"
---

# Set-VBRNASBackupJob


Short Description

Modifies file backup jobs.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRNASBackupJob -Job <VBRNASBackupJob> [-Name <string>] [-Description <string>] [-BackupObject <VBRNASBackupJobObject[]>] [-ShortTermBackupRepository <CBackupRepository>] [-ShortTermRetentionType <VBRUnstructuredBackupShortTermRetentionType> {Daily | Monthly}] [-ShortTermRetentionPeriod <int>] [-EnableLongTermRetention] [-LongTermRetentionType <VBRUnstructuredBackupLongTermRetentionType> {Monthly | Yearly}] [-LongTermBackupRepository <CBackupRepository>] [-EnableCopyMode] [-LongTermRetentionPeriod <int>] [-LongTermArchivalOptions <VBRUnstructuredBackupArchivalOptions>] [-EnableSecondaryTarget] [-SecondaryTarget <VBRUnstructuredBackupSecondaryTarget[]>] [-VersionRetentionOptions <VBRUnstructuredBackupVersionRetentionOptions>] [-StorageOptions <VBRStorageOptions>] [-HealthCheckOptions <VBRFullBackupOptions>] [-NotificationOptions <VBRNotificationOptions>] [-ScriptOptions <VBRJobScriptOptions>] [-EnableFileACLChangeTracking] [-EnableSchedule][-ScheduleOptions <VBRServerScheduleOptions>] [-Force] [-HighPriority] [-TargetBackup <VBRUnstructuredBackup>] [<CommonParameters>] |

Detailed Description

This cmdlet modifies settings of existing file backup jobs.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies the file backup job. The cmdlet will modify settings of the specified job. | Accepts the VBRNASBackupJob object. To create this object, run the [Get-VBRUnstructuredBackupJob](get-vbrunstructuredbackupjob.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| Name | Specifies a name of the file backup job. The cmdlet will change the existing name of the file backup job with the specified name. | String | False | Named | False |
| Description | Specifies a description of the file backup job. The cmdlet will change the existing description of the file backup job with the specified description. | String | False | Named | False |
| BackupObject | Specifies folders and files. The cmdlet will add these folders and files to the file backup job. | Accepts the VBRNASBackupJobObject[] object. To create this object, run the [New-VBRNASBackupJobObject](new-vbrnasbackupjobobject.md) cmdlet. | False | Named | False |
| ShortTermBackupRepository | Specifies the backup repository. The cmdlet will add this backup repository as the short-term repository. | Accepts the CBackupRepository object. To create this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | False | Named | False |
| ShortTermRetentionType | Specifies a retention policy for the short-term repository. You can set the retention policy to either of the following periods:   * Daily: use this option if you want Veeam Backup & Replication to apply retention policy daily. * Monthly: use this option if you want Veeam Backup & Replication to apply retention policy monthly.   Use the ShortTermRetentionPeriod to specify the number of days or months. | VBRUnstructuredBackupShortTermRetentionType | False | Named | False |
| ShortTermRetentionPeriod | For the ShortTermRetentionType option.  Specifies the period of time to keep data on the short-term repository. When this period is passed, Veeam Backup & Replication will move data to the long-term repository. | Int32 | False | Named | False |
| EnableLongTermRetention | Defines that the cmdlet will enable custom retention policy for the long-term repository.  If you provide this parameter, Veeam Backup & Replication will apply custom retention policy for data that is stored on the long-term repository. Otherwise, Veeam Backup & Replication will keep data for three years on the long-term repository. | SwitchParamter | False | Named | False |
| LongTermRetentionType | Specifies a retention policy for the long-term repository. You can set the retention policy to either of the following periods:   * Daily: use this option if you want Veeam Backup & Replication to apply retention policy daily. * Monthly: use this option if you want Veeam Backup & Replication to apply retention policy monthly.   Use the LongTermRetentionPeriod to specify the number of days or months. | VBRUnstructuredBackupLongTermRetentionType | False | Named | False |
| LongTermBackupRepository | Specifies the backup repository. The cmdlet will add this backup repository as the long-term repository. | Accepts the CBackupRepository object. To create this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | False | Named | False |
| LongTermRetentionPeriod | For the LongTermRetentionType option.  Specifies the period of time to keep data on the short-term repository. When this period is passed, Veeam Backup & Replication will delete this data from the long-term repository. | Int32 | False | Named | False |
| LongTermArchivalOptions | Specifies the retention policy for file versions that are located on the long-term repository. The cmdlet will create file backup jobs with the specified retention policy. | Accepts the VBRUnstructuredBackupArchivalOptions object. To create this object, run the [New-VBRUnstructuredBackupArchivalOptions](new-vbrunstructuredbackuparchivaloptions.md) cmdlet. | False | Named | False |
| EnableCopyMode | Defines that the cmdlet will keep the copy of the data stored in the backup repository in the long-term archive repository. | SwitchParameter | False | Named | False |
| EnableSecondaryTarget | Defines that the cmdlet will enable a secondary backup repository for a file backup job.  If you provide this parameter, Veeam Backup & Replication will create copies of file backup jobs and will keep them on a secondary backup repository. Otherwise, copies of the file backup job will not be created. | SwitchParamter | False | Named | False |
| SecondaryTarget | Specifies the backup repository. The cmdlet will add this backup repository as the secondary repository to the file backup job. | Accepts the VBRUnstructuredBackupSecondaryTarget[] object. To create this object, run the [New-VBRUnstructuredBackupSecondaryTarget](new-vbrunstructuredbackupsecondarytarget.md) cmdlet. | False | Named | False |
| VersionRetentionOptions | Specifies the settings of version-based retention for backup and archive repositories. The cmdlet will apply these settings to the file backup job. | Accepts the VBRUnstructuredBackupVersionRetentionOptions object. To create this object, run the [New-VBRUnstructuredBackupVersionRetentionOptions](new-vbrunstructuredbackupversionretentionoptions.md) cmdlet. | False | Named | False |
| StorageOptions | Specifies storage optimization settings. The cmdlet will create the file backup job with these settings. | Accepts the VBRStorageOptions object. To create this object, run the [New-VBRStorageOptions](new-vbrstorageoptions.md) cmdlet. | False | Named | False |
| HealthCheckOptions | Specifies the healthcheck schedule. The cmdlet will create file backup jobs with this healthcheck schedule. | Accepts the VBRFullBackupOptions object. To create this object, run the [New-VBRFullBackupOptions](new-vbrfullbackupoptions.md) cmdlet. | False | Named | False |
| NotificationOptions | Specifies notification options. The cmdlet will create file backup jobs with these notification options. | Accepts the VBRNotificationOptions object. To create this object, run the [New-VBRFullBackupOptions](new-vbrfullbackupoptions.md) cmdlet. | False | Named | False |
| ScriptOptions | Specifies pre-job and post-job script options. The cmdlet will create file backup jobs with these script options. | Accepts the VBRJobScriptOptions object. To create this object, run the [New-VBRJobScriptOptions](new-vbrjobscriptoptions.md) cmdlet. | False | Named | False |
| EnableFileACLChangeTracking | Defines that Veeam Backup & Replication will process attributes and permissions for folders. Files that are added to these folders will inherit permissions of the folders.  If you enable this option, Veeam Backup & Replication will back up folder ACL attributes and permissions. Otherwise, they will not be backed up. | SwitchParamter | False | Named | False |
| EnableSchedule | Defines that the cmdlet will enable the custom schedule for a file backup job.  If you provide this parameter, the file backup job will run according to this schedule. Otherwise, to run the job, you will need to start it manually. | VBRJobScriptOptions | False | Named | False |
| ScheduleOptions | Specifies schedule options. The cmdlet will create file backup jobs with these schedule options. | Accepts the VBRJobScriptOptions object. To create this object, run the [New-VBRServerScheduleOptions](new-vbrserverscheduleoptions.md) cmdlet. | False | Named | False |
| Force | Defines that the cmdlet will create file backup without showing warnings in the PowerShell console. | SwitchParameter | False | Named | False |
| HighPriority | Defines that Veeam Backup & Replication will prioritize this job higher than other similar jobs and will allocate resources to it in the first place. | SwitchParameter | Named | False | False |
| TargetBackup | For backup job mapping.  Specifies a backup chain that you want to map to a job. | Accepts the VBRUnstructuredBackup object. To create this object, run the [Get-VBRUnstructuredBackup](get-vbrunstructuredbackup.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRNASBackupJob object that contains settings of file backup jobs.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Modifying Long-Term Repository

|  |  |
| --- | --- |
| This example shows how to modify a long-term repository for a file backup job. The file backup job will have the following settings:   * Veeam Backup & Replication will move data from the short-term repository to the Repository 09 backup repository. * Veeam Backup & Replication will keep file versions on the long-term repository for 3 years.     |  | | --- | | $job = Get-VBRUnstructuredBackupJob -Name "NFS Backup"  $repository = Get-VBRBackupRepository -Name "Repository 09"  Set-VBRNASBackupJob -Job $job -LongTermBackupRepository $repository -EnableLongTermRetention -LongTermRetentionType Yearly -LongTermRetentionPeriod 3 |  Perform the following steps:   1. Run the [Get-VBRUnstructuredBackupJob](get-vbrunstructuredbackupjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable. 2. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Save the result to the $repository variable. 3. Run the Set-VBRNASBackupJob cmdlet. Specify the following settings:  * Set the $Job variable as the Job parameter value. * Set the $repository variable as the LongTermBackupRepository parameter value. * Specify the EnableLongTermRetention parameter value. * Set the Yearly option for the LongTermRetentionType parameter value. * Specify the LongTermRetentionPeriod parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Modifying Notification Options

|  |  |
| --- | --- |
| This example shows how to modify notification options for a file backup job. Veeam Backup & Replication will send notifications about the job warnings and when the job completes successfully.  |  | | --- | | $options = New-VBRNotificationOptions -EnableAdditionalNotification -AdditionalAddress admin@domain.com -UseNotificationOptions -NotifyOnSuccess -NotifyOnWarning  $job = Get-VBRUnstructuredBackupJob -Name "NFS Backup"  Set-VBRNASBackupJob -Job $job -NotificationOptions $options |  Perform the following steps:   1. Run the [New-VBRNotificationOptions](new-vbrnotificationoptions.md) cmdlet. Specify the necessary parameters. Save the result to the $options variable.  1. Run the [Get-VBRUnstructuredBackupJob](get-vbrunstructuredbackupjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable. 2. Run the Set-VBRNASBackupJob cmdlet. Specify the following settings:  * Set the $Job variable as the Job parameter value. * Specify the LongTermBackupRepository parameter value. * Specify the EnableLongTermRetention parameter value. * Set the Yearly option for the LongTermRetentionType parameter value. * Specify the LongTermRetentionPeriod parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Enabling Secondary Target Repository

|  |  |
| --- | --- |
| This example shows how to enable the secondary repository for the file backup job. The secondary repository will be created with the following settings:   * Veeam Backup & Replication will apply a retention policy that is set to the file backup job. * Veeam Backup & Replication will apply an encryption key that is set to the file backup job. * Veeam Backup & Replication will copy data to the repository continuously.     |  | | --- | | $job = Get-VBRUnstructuredBackupJob -Name "NFS Backup"  $srepo = Get-VBRBackupRepository -Name "Repository 09"  $secondary = New-VBRUnstructuredBackupSecondaryTarget -BackupRepository $srepo  Set-VBRNASBackupJob -Job $job -EnableSecondaryTarget:$true -SecondaryTarget $secondary |  Perform the following steps:   1. Run the [Get-VBRUnstructuredBackupJob](get-vbrunstructuredbackupjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable. 2. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Save the result to the $srepo variable. 3. Run the [New-VBRUnstructuredBackupSecondaryTarget](new-vbrunstructuredbackupsecondarytarget.md) cmdlet. Set the $srepo variable as the BackupRepository parameter value. Save the result to the $secondary variable. 4. Run the Set-VBRNASBackupJob cmdlet. Specify the following settings:  * Set the $Job variable as the Job parameter value. * Set the EnableSecondaryTarget parameter to $true. * Set the $secondary variable as the SecondaryTarget parameter value. |

Related Commands

* [Get-VBRUnstructuredBackupJob](get-vbrunstructuredbackupjob.md)
* [Get-VBRBackupRepository](get-vbrbackuprepository.md)


