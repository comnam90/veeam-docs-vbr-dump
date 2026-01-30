---
title: "Set-VBREntraIDLogsBackupJob"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrentraidlogsbackupjob.html"
last_updated: "1/30/2025"
product_version: "13.0.1.1071"
---

# Set-VBREntraIDLogsBackupJob


Short Description

Modifies a Microsoft Entra ID log backup job.

Applies to

Product Edition: Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBREntraIDLogsBackupJob -Job <VBREntraIdLogsBackupJob> [-Tenant <VBREntraIDTenant>] [-ShortTermRetentionType <VBREntraIdLogsBackupShortTermRetentionType>] [-ShortTermRetentionPeriod <Int32>] [-Name <String>] [-Description <String>] [-ShortTermBackupRepository <CBackupRepository>] [-EnableSecondaryTarget] [-SecondaryTarget <VBRUnstructuredBackupSecondaryTarget[]>] [-StorageOptions <VBRStorageOptions>] [-HealthCheckOptions <VBRFullBackupOptions>] [-NotificationOptions <VBRNotificationOptions>] [-ScriptOptions <VBRJobScriptOptions>] [-EnableSchedule] [-ScheduleOptions <VBRServerScheduleOptions>] [-Force] [-HighPriority] [-TargetBackup <VBREntraIdLogsBackup>]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies a backup job that protect Entra ID audit and sign-in logs.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies the log backup job that you want to modify. | Accepts the VBREntraIdLogsBackupJob object. To get this object, run the [Get-VBREntraIDLogsBackupJob](get-vbrentraidlogsbackupjob.md) cmdlet. | True | Named | True (ByPropertyName, ByValue) |
| Tenant | Specifies the tenant whose logs you want to back up. | Accepts the VBREntraIDTenant object. To get this object, run the [Get-VBREntraIDTenant](get-vbrentraidtenant.md) cmdlet. | False | Named | False |
| ShortTermRetentionType | Specifies the type of the retention policy for the primary backup repository.  Use the ShortTermRetentionPeriod parameter to specify the number of days, months or years. | [VBREntraIdLogsBackupShortTermRetentionType](enums.md#VBREntraIdLogsBackupShortTermRetentionType) | False | Named | False |
| ShortTermRetentionPeriod | For the ShortTermRetentionType option.  Specifies the period of time to keep data in the primary backup repository. | Int32 | False | Named | False |
| Name | Specifies the name of the log backup job. | String | False | Named | False |
| Description | Specifies the description of the log backup job. | String | False | Named | False |
| ShortTermBackupRepository | Specifies the primary backup repository. The cmdlet will use this repository as a primary storage for storing log backups.  Note: You can change the primary backup repository only if there are no backups or they are detached from the job. | Accepts the CBackupRepository object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | False | Named | False |
| EnableSecondaryTarget | Enables copying log backups to the secondary backup repository. | SwitchParameter | False | Named | False |
| SecondaryTarget | Specifies the secondary backup repository. The cmdlet will use this repository as the secondary repository for the log backup job.  Note: The cmdlet will create a new backup chain in the new repository and detach backups stored in the old repository. | Accepts the VBRUnstructuredBackupSecondaryTarget[] object. To create this object, run the [New-VBRUnstructuredBackupSecondaryTarget](new-vbrunstructuredbackupsecondarytarget.md) cmdlet. | False | Named | False |
| StorageOptions | Specifies storage optimization settings. The cmdlet will create the log backup job with these settings. | Accepts the VBRStorageOptions object. To create this object, run the [New-VBRStorageOptions](new-vbrstorageoptions.md) cmdlet. | False | Named | False |
| HealthCheckOptions | Specifies the healthcheck schedule. The cmdlet will create the log backup job with this healthcheck schedule. | Accepts the VBRFullBackupOptions object. To create this object, run the [New-VBRFullBackupOptions](new-vbrfullbackupoptions.md) cmdlet. | False | Named | False |
| NotificationOptions | Specifies notification options. The cmdlet will create the log backup job with these notification options. | Accepts the VBRNotificationOptions object. To create this object, run the [New-VBRNotificationOptions](new-vbrnotificationoptions.md) cmdlet. | False | Named | False |
| ScriptOptions | Specifies pre-job and post-job script options. The cmdlet will create the log backup job with these script options. | Accepts the VBRJobScriptOptions object. To create this object, run the [New-VBRJobScriptOptions](new-vbrjobscriptoptions.md) cmdlet. | False | Named | False |
| EnableSchedule | Enables the job schedule. | SwitchParameter | False | Named | False |
| ScheduleOptions | Specifies schedule options. The cmdlet will create the log backup job with these schedule options. | Accepts the VBRServerScheduleOptions object. To create this object, run the [New-VBRServerScheduleOptions](new-vbrserverscheduleoptions.md) cmdlet. | False | Named | False |
| Force | Defines that the cmdlet will create a log backup job without showing warnings or errors in the PowerShell console. | SwichParameter | False | Named | False |
| HighPriority | Defines that Veeam Backup & Replication will prioritize this job higher than other similar jobs and will allocate resources to it in the first place. | SwichParameter | False | Named | False |
| TargetBackup | Used for mapping backups.  Specifies an Entra ID log backup. The cmdlet will use data of this backup to create a backup chain instead of creating the chain anew.  Note: The backup must be stored on the same repository as specified in ShortTermBackupRepository. | Accepts the VBREntraIdLogsBackup object. To get this object, run the [Get-VBREntraIDLogsBackup](get-vbrentraidlogsbackup.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the [VBREntraIdLogsBackupJob](vbrentraidlogsbackupjob.md) object that contains settings of the Entra ID log backup job.

Examples

Modifying Settings of Log Backup Job

This example shows how to change the settings of the Log Backup backup job and enable scheduling.

|  |
| --- |
| $backupJob = Get-VBREntraIDLogsBackupJob -Name "Log Backup"  $daily = New-VBRDailyOptions -DayOfWeek Friday -Period 7:00  $scheduleOptions = New-VBRServerScheduleOptions -Type Daily -DailyOptions $daily  Set-VBREntraIDLogsBackupJob -Job $backupJob -Description "Backup of Entra ID tenant logs" -EnableSchedule -ScheduleOptions $scheduleOptions |

Perform the following steps:

1. Run the [Get-VBREntraIDLogsBackupJob](get-vbrentraidlogsbackupjob.md) cmdlet. Specify the Name parameter value. Save the result to the $backupJob variable.
2. Run the [New-VBRDailyOptions](new-vbrdailyoptions.md) cmdlet. Specify the DayOfWeek and Period parameter values. Save the result to the $daily variable.
3. Run the [New-VBRServerScheduleOptions](new-vbrserverscheduleoptions.md) cmdlet. Specify the following settings:

* Set the Daily value as the Type parameter value.
* Set the $daily variable as the DailyOptions parameter value.
* Save the result to the $scheduleOptions variable.

1. Run the Set-VBREntraIDTenantBackupJob cmdlet. Specify the following settings:

* Set the $backupJob variable as the Job parameter value.
* Specify the Description parameter value.
* Provide the EnableSchedule parameter.
* Set the $scheduleOptions variable as the ScheduleOptions parameter value.

Related Commands

* [Get-VBREntraIDLogsBackupJob](get-vbrentraidlogsbackupjob.md)
* [New-VBRDailyOptions](new-vbrdailyoptions.md)
* [New-VBRServerScheduleOptions](new-vbrserverscheduleoptions.md)


