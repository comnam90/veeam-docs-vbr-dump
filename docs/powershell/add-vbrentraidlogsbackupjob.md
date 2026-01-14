---
title: "Add-VBREntraIDLogsBackupJob"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrentraidlogsbackupjob.html"
last_updated: "1/30/2025"
product_version: "13.0.1.1071"
---

# Add-VBREntraIDLogsBackupJob

In this article

Short Description

Creates a Microsoft Entra ID log backup job.

Applies to

Product Edition: Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Add-VBREntraIDLogsBackupJob -Tenant <VBREntraIDTenant> [-ShortTermRetentionType <VBREntraIdLogsBackupShortTermRetentionType>] [-ShortTermRetentionPeriod <Int32>] [-TargetBackup <VBREntraIdLogsBackup>] [-Name <String>] [-Description <String>] -ShortTermBackupRepository <CBackupRepository> [-SecondaryTarget <VBRUnstructuredBackupSecondaryTarget[]>] [-StorageOptions <VBRStorageOptions>] [-HealthCheckOptions <VBRFullBackupOptions>] [-NotificationOptions <VBRNotificationOptions>] [-ScriptOptions <VBRJobScriptOptions>] [-ScheduleOptions <VBRServerScheduleOptions>] [-Force] [-HighPriority]  [<CommonParameters>] |

Detailed Description

This cmdlet creates a backup job for Entra ID audit and sign-in logs.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Tenant | Specifies the tenant whose logs you want to back up. | Accepts the VBREntraIDTenant object. To get this object, run the [Get-VBREntraIDTenant](get-vbrentraidtenant.md) cmdlet. | True | Named | False |
| ShortTermBackupRepository | Specifies the primary backup repository. The cmdlet will use this repository as a primary storage for storing log backups. | Accepts the CBackupRepository object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | True | Named | False |
| ShortTermRetentionType | Specifies the type of the retention policy for the primary backup repository.  Use the ShortTermRetentionPeriod parameter to specify the number of days, months or years. | [VBREntraIdLogsBackupShortTermRetentionType](enums.md#VBREntraIdLogsBackupShortTermRetentionType) | False | Named | False |
| ShortTermRetentionPeriod | For the ShortTermRetentionType option.  Specifies the period of time to keep data in the primary backup repository. | Int32 | False | Named | False |
| TargetBackup | Used for mapping backups.  Specifies an Entra ID log backup. The cmdlet will use data of this backup to create a backup chain instead of creating the chain anew.  Note: The backup must be stored in the same repository as specified in ShortTermBackupRepository. | Accepts the VBREntraIdLogsBackup object. To get this object, run the [Get-VBREntraIDLogsBackup](get-vbrentraidlogsbackup.md) cmdlet. | False | Named | False |
| Name | Specifies the name of the log backup job. | String | False | Named | False |
| Description | Specifies the description of the log backup job. | String | False | Named | False |
| SecondaryTarget | Specifies the secondary backup repository. The cmdlet will use this repository as the secondary repository for the log backup job. | Accepts the VBRUnstructuredBackupSecondaryTarget[] object. To create this object, run the [New-VBRUnstructuredBackupSecondaryTarget](new-vbrunstructuredbackupsecondarytarget.md) cmdlet. | False | Named | False |
| StorageOptions | Specifies storage optimization settings. The cmdlet will create the log backup job with these settings. | Accepts the VBRStorageOptions object. To create this object, run the [New-VBRStorageOptions](new-vbrstorageoptions.md) cmdlet. | False | Named | False |
| HealthCheckOptions | Specifies the healthcheck schedule. The cmdlet will create the log backup job with this healthcheck schedule. | Accepts the VBRFullBackupOptions object. To create this object, run the [New-VBRFullBackupOptions](new-vbrfullbackupoptions.md) cmdlet. | False | Named | False |
| NotificationOptions | Specifies notification options. The cmdlet will create the log backup job with these notification options. | Accepts the VBRNotificationOptions object. To create this object, run the [New-VBRNotificationOptions](new-vbrnotificationoptions.md) cmdlet. | False | Named | False |
| ScriptOptions | Specifies pre-job and post-job script options. The cmdlet will create the log backup job with these script options. | Accepts the VBRJobScriptOptions object. To create this object, run the [New-VBRJobScriptOptions](new-vbrjobscriptoptions.md) cmdlet. | False | Named | False |
| ScheduleOptions | Specifies schedule options. The cmdlet will create the log backup job with these schedule options. | Accepts the VBRServerScheduleOptions object. To create this object, run the [New-VBRServerScheduleOptions](new-vbrserverscheduleoptions.md) cmdlet. | False | Named | False |
| Force | Defines that the cmdlet will create a log backup job without showing warnings or errors in the PowerShell console. | SwichParameter | False | Named | False |
| HighPriority | Defines that Veeam Backup & Replication will prioritize this job higher than other similar jobs and will allocate resources to it in the first place. | SwichParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the [VBREntraIdLogsBackupJob](vbrentraidlogsbackupjob.md) object that contains settings of the Entra ID log backup job.

Examples

Adding Entra ID Log Backup Job

This example shows how to add an Entra ID log backup job with the 14 day retention period. The backups will also be copied to a secondary repository. From the secondary repository, the backups will be deleted after 2 months.

|  |
| --- |
| $tenant = Get-VBREntraIdTenant -AzureTenantId "xxxx"  $shortRepo = Get-VBRBackupRepository -Name "Default Backup Repository"  $repository = Get-VBRBackupRepository -Name "Secondary Backup Repository"  $secondaryRepo = New-VBRUnstructuredBackupSecondaryTarget -BackupRepository $repository -CustomRetentionType Monthly -CustomRetentionPeriod 2  $logBackupJob = Add-VBREntraIDLogsBackupJob -Tenant $tenant -ShortTermRetentionType 0 -ShortTermRetentionPeriod 14 -Name "Log Backup" -ShortTermBackupRepository $shortRepo -SecondaryTarget $secondaryRepo |

Perform the following steps:

1. Run the [Get-VBREntraIdTenant](get-vbrentraidtenant.md) cmdlet. Specify the AzureTenantId parameter value. Save the result to the $tenant variable.
2. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Save the result to the $shortRepo variable.
3. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Save the result to the $repository variable.
4. Run the [New-VBRUnstructuredBackupSecondaryTarget](new-vbrunstructuredbackupsecondarytarget.md) cmdlet. Specify the following settings:

* Set the $repository variable as the BackupRepository parameter value.

* Specify the CustomRetentionType and CustomRetentionPeriod parameter values.

* Save the result to the $secondaryRepo variable.

1. Run the Add-VBREntraIDLogsBackupJob cmdlet. Specify the following settings:

* Set the $tenant variable as the Tenant parameter value.
* Specify the ShortTermRetentionType and ShortTermRetentionPeriod parameter values.
* Specify the Name parameter value.
* Set the $shortRepo variable as the ShortTermBackupRepository parameter value.
* Set the $secondaryRepo variable as the SecondaryTarget parameter value.
* Save the result to the $logBackupJob variable.

Related Commands

* [Get-VBREntraIdTenant](get-vbrentraidtenant.md)
* [Get-VBRBackupRepository](get-vbrbackuprepository.md)
* [New-VBRUnstructuredBackupSecondaryTarget](new-vbrunstructuredbackupsecondarytarget.md)

Page updated 1/30/2025

Page content applies to build 13.0.1.1071
