---
title: "Set-VBRComputerBackupCopyJob"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrcomputerbackupcopyjob.html"
last_updated: "12/19/2024"
product_version: "13.0.1.1071"
---

# Set-VBRComputerBackupCopyJob

In this article

Short Description

Modifies Veeam Agent backup copy jobs.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRComputerBackupCopyJob -Job <VBRComputerBackupCopyJob> [-GFSOptions <VBRComputerGFSOptions>] [-AnyTime] [-EnableTransactionLogCopy] [-RPOWarningOptions <VBRRpoNotificationOption[]>] [-ScriptOptions <VBRJobScriptOptions>] [-HealthCheckOptions <VBRFullBackupOptions>] [-StorageOptions <VBRBackupCopyJobStorageOptions>] [-NotificationOptions <VBRNotificationOptions>] [-BackupWindowOptions <VBRBackupWindowOptions>] [-RetentionPolicy <VBRRetentionPolicy>] [-RecoveryPointObjective <VBRRecoveryPointObjective>] [-Force] [-TargetAccelerator <CWanAccelerator>] [-SourceAccelerator <CWanAccelerator>] [-DirectOperation] [-Repository <CBackupRepository>] [-SourceRepository <CBackupRepository[]>] [-BackupJob <VBRComputerBackupJob[]>] [-Backup <CBackup[]>] [-Description <String>] [-Name <String>] [-RetentionType <VBRRetentionType>] [-RetentionNumber <Int32>]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies Veeam Agent backup copy jobs.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies a Veeam Agent backup copy job that you want to modify. | Accepts the VBRComputerBackupCopyJob object. To create this object, run the [Get-VBRComputerBackupCopyJob](get-vbrcomputerbackupcopyjob.md) cmdlet. | True | Named | True (ByValue) |
| Name | Specifies a name that you want to assign to a Veeam Agent backup copy job. | String | False | Named | False |
| Description | Specifies a description of a Veeam Agent backup copy job. | String | False | Named | False |
| Backup | Specifies an array of backups. The cmdlet will add machines from these backups to a Veeam Agent backup copy.  Note: This parameter is available for a Veeam Agent backup copy job that is created with the periodic backup copy mode. | Accepts the CBackup[] object. To create this object, run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. | False | Named | True (ByValue, ByPropertyName) |
| BackupJob | Specifies an array of backup jobs. The cmdlet will add machines processed by these jobs to a Veeam Agent backup copy job. | Accepts the VBRComputerBackupJob[] object. To create this object, run the [Get-VBRComputerBackupJob](get-vbrcomputerbackupjob.md) cmdlet. | False | Named | True (ByPropertyName) |
| Repository | Specifies the backup repository. The cmdlet will copy the machine data to this repository.  Default: Default backup repository. | Accepts the CBackupRepository object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | False | Named | False |
| DirectOperation | Defines that the cmdlet will create a Veeam Agent backup copy job that will transfer data directly from the source backup repository to the target backup repository. | SwitchParameter | False | Named | False |
| SourceAccelerator | Specifies the WAN accelerator on the source side.  Remember to set the pair of source and target WAN accelerators. | Accepts the [CWanAccelerator](cwanaccelerator.md) object. To get this object, run the [Get-VBRWANAccelerator](get-vbrwanaccelerator.md)cmdlet. | False | Named | False |
| TargetAccelerator | Specifies the WAN accelerator on the target side.  Remember to set the pair of source and target WAN accelerators. | Accepts the [CWanAccelerator](cwanaccelerator.md) object. To get this object, run the [Get-VBRWANAccelerator](get-vbrwanaccelerator.md)cmdlet. | False | Named | False |
| GFSOptions | Specifies a GFS retention. The cmdlet will create Veeam Agent backup copy job with the specified policy.  Note: This option is not available for Veeam Agent policies. | Accepts the VBRComputerGFSOptions object. To get this object, run the [New-VBRComputerGFSOptions](new-vbrcomputergfsoptions.md) cmdlet. | False | Named | False |
| RecoveryPointObjective | Specifies a schedule for a Veeam Agent backup copy job with the periodic backup copy mode. The cmdlet will create the job with these settings. | Accepts the VBRRecoveryPointObjective object. To create this object, run the [Get-VBRRecoveryPointObjective](get-vbrrecoverypointobjective.md) cmdlet. | False | Named | False |
| RetentionPolicy | Specifies a retention policy for a Veeam Agent backup copy job. The cmdlet will create the job with these settings. You can specify the following types of retention policies:   * Simple retention policy: use this option for short-time archiving. To create a job with this type of the policy, provide the VBRSimpleRetentionPolicy object. Run the [New-VBRSimpleRetentionPolicy](new-vbrsimpleretentionpolicy.md) cmdlet to create this object. * GFS retention policy: use this option for long-term archiving. To create a job with this type of the policy, provide the VBRRetentionPolicy object. Run the [New-VBRGFSRetentionPolicy](new-vbrgfsretentionpolicy.md) cmdlet to create this object. | Accepts the following objects:   * VBRRetentionPolicy. Run the [New-VBRGFSRetentionPolicy](new-vbrgfsretentionpolicy.md) cmdlet to get this object. * VBRSimpleRetentionPolicy. Run the [New-VBRSimpleRetentionPolicy](new-vbrsimpleretentionpolicy.md) cmdlet to create this object. | False | Named | False |
| BackupWindowOptions | Specifies backup window settings for a Veeam Agent backup copy job. The cmdlet will create the job with these settings. | Accepts the VBRBackupWindowOptions object. To create this object, run the [New-VBRBackupWindowOptions](new-vbrbackupwindowoptions.md) cmdlet. | False | Named | False |
| NotificationOptions | Specifies notification settings for a Veeam Agent backup copy job. The cmdlet will create the job with these settings. | Accepts the VBRNotificationOptions object. To create this object, run the [New-VBRNotificationOptions](new-vbrnotificationoptions.md) cmdlet. | False | Named | False |
| StorageOptions | Specifies the storage settings of the backup repository. The cmdlet will create the Veeam Agent backup copy job with these settings. | Accepts the VBRBackupCopyJobStorageOptions object. To create this object, run the [New-VBRBackupCopyJobStorageOptions](new-vbrbackupcopyjobstorageoptions.md) cmdlet. | False | Named | False |
| HealthCheckOptions | Specifies the health check schedule for a Veeam Agent backup copy job. The cmdlet will create the job with these settings. | Accepts the VBRFullBackupOptions object. To create this object, run the [New-VBRFullBackupOptions](new-vbrfullbackupoptions.md) cmdlet. | False | Named | False |
| ScriptOptions | Specifies pre-job and post-job script options for a Veeam Agent backup copy job. The cmdlet will create the job with these settings. | Accepts the VBRJobScriptOptions object. To create this object, run the [New-VBRJobScriptOptions](new-vbrjobscriptoptions.md) cmdlet. | False | Named | False |
| RPOWarningOptions | Specifies an array of the number of hours when data must be copied from the source repository to the target repository.  Default: 1 hour. | Accepts the VBRRPONotificationOptions[] object. To create this object, run the [New-VBRRPONotificationOption](new-vbrrponotificationoption.md) cmdlet. | False | Named | False |
| EnableRPOWarning | Defines that the cmdlet will display a warning in case the job exceeds the period that is set for the job to copy data from the source repository to the target repository.  Use the RPOWarningOptions parameter to specify the limitation. | SwitchParameter | False | Named | False |
| EnableTransactionLogCopy | Defines that the Veeam Agent backup copy job will process transaction logs of the source job. | SwitchParameter | False | Named | False |
| SourceRepository | Specifies an array of source backup repositories. | Accepts the CBackupRepository[] object. To create this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | False | Named | False |
| RetentionType | Specifies retention type for Veeam Agent copy jobs managed by the Veeam Backup server. You can specify one of the following types:   * RestorePoints * RestoreDays | VBRRetentionType | False | Named | False |
| RetentionNumber | For the RetentionType set to the RestoreDays property.  Specifies a number of days for which you want to store backup files in the target location.  Default: 7 days. | Int32 | False | Named | False |
| AnyTime | Defines that Veeam Backup & Replication will run a Veeam Agent backup copy job at any time according to its schedule. | SwitchParameter | False | Named | False |
| Force | Defines that the cmdlet will modify Veeam Agent backup copy jobs without showing warnings in the PowerShell console. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRComputerBackupCopyJob object that contains settings of Veeam Agent backup copy jobs.

Examples

Modifying Backup Window Settings for Veeam Agent Backup Copy Job

The following example shows how to modify backup window settings for a Veeam Agent Backup Copy job.

|  |
| --- |
| $job = Get-VBRComputerBackupCopyJob -Name "Windows Copy Job05"  $windowoptions = New-VBRBackupWindowOptions -FromDay Monday -FromHour 08 -ToDay Friday -ToHour 20  Set-VBRComputerBackupCopyJob -Job $job -BackupWindowOptions $windowoptions |

Perform the following steps:

1. Run the [Get-VBRComputerBackupCopyJob](get-vbrcomputerbackupcopyjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable.
2. Run the [New-VBRBackupWindowOptions](new-vbrbackupwindowoptions.md) cmdlet. Specify the necessary parameters. Save the result to the $windowoptions variable.
3. Run the Set-VBRComputerBackupCopyJob cmdlet. Set the $job variable as the Job parameter value. Set the $windowoptions variable as the BackupWindowOptions parameter value.

Related Commands

* [Get-VBRComputerBackupCopyJob](get-vbrcomputerbackupcopyjob.md)
* [New-VBRBackupWindowOptions](new-vbrbackupwindowoptions.md)

Page updated 12/19/2024

Page content applies to build 13.0.1.1071
