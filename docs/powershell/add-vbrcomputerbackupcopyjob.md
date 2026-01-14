---
title: "Add-VBRComputerBackupCopyJob (obsolete)"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrcomputerbackupcopyjob.html"
last_updated: "12/19/2024"
product_version: "13.0.1.1071"
---

# Add-VBRComputerBackupCopyJob (obsolete)

In this article

Short Description

Creates Veeam Agent backup copy jobs.

|  |
| --- |
| Note |
| This cmdlet is obsolete and only works for creating a simple mode backup copy job. It is recommended to create a new backup job using the [Add-VBRBackupCopyJob](add-vbrbackupcopyjob.md) cmdlet. |

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Create Veeam Agent backup copy jobs that will transfer data directly.

|  |
| --- |
| Add-VBRComputerBackupCopyJob -OSPlatform <VBRAgentType> -DirectOperation [-GFSOptions <VBRComputerGFSOptions>] [-EnableTransactionLogCopy] [-RPOWarningOptions <VBRRpoNotificationOption[]>] [-ScriptOptions <VBRJobScriptOptions>] [-HealthCheckOptions <VBRFullBackupOptions>] [-StorageOptions <VBRBackupCopyJobStorageOptions>] [-NotificationOptions <VBRNotificationOptions>] [-BackupWindowOptions <VBRBackupWindowOptions>] [-RetentionPolicy <VBRRetentionPolicy>] [-RecoveryPointObjective <VBRRecoveryPointObjective>] [-EnableImmediateCopy] [-Force] [-Repository <CBackupRepository>] [-SourceRepository <CBackupRepository[]>] [-BackupJob <VBRComputerBackupJob[]>] [-Backup <CBackup[]>] [-Description <String>] [-Name <String>] [-RetentionType <VBRRetentionType>] [-RetentionNumber <Int32>]  [<CommonParameters>] |

* Create Veeam Agent backup copy jobs that will transfer data over WAN accelerators.

|  |
| --- |
| Add-VBRComputerBackupCopyJob -OSPlatform <VBRAgentType> -SourceAccelerator <CWanAccelerator> [-GFSOptions <VBRComputerGFSOptions>] [-EnableTransactionLogCopy] [-RPOWarningOptions <VBRRpoNotificationOption[]>] [-ScriptOptions <VBRJobScriptOptions>] [-HealthCheckOptions <VBRFullBackupOptions>] [-StorageOptions <VBRBackupCopyJobStorageOptions>] [-NotificationOptions <VBRNotificationOptions>] [-BackupWindowOptions <VBRBackupWindowOptions>] [-RetentionPolicy <VBRRetentionPolicy>] [-RecoveryPointObjective <VBRRecoveryPointObjective>] [-EnableImmediateCopy] [-Force] [-TargetAccelerator <CWanAccelerator>] [-Repository <CBackupRepository>] [-SourceRepository <CBackupRepository[]>] [-BackupJob <VBRComputerBackupJob[]>] [-Backup <CBackup[]>] [-Description <String>] [-Name <String>] [-RetentionType <VBRRetentionType>] [-RetentionNumber <Int32>]  [<CommonParameters>] |

Detailed Description

This cmdlet creates Veeam Agent backup copy jobs.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| OSPlatform | Specifies the OS of the protected computers:   * Linux * Mac * Unix * Windows | VBRAgentType | True | Named | False |
| DirectOperation | Defines that the cmdlet will create a Veeam Agent backup copy job that will transfer data directly from the source backup repository to the target backup repository. | SwitchParameter | True | Named | False |
| SourceAccelerator | Specifies the WAN accelerator on the source side.  Remember to set the pair of source and target WAN accelerators. | Accepts the [CWanAccelerator](cwanaccelerator.md) object. To get this object, run the [Get-VBRWANAccelerator](get-vbrwanaccelerator.md) cmdlet. | True | Named | False |
| TargetAccelerator | Specifies the WAN accelerator on the target side.  Remember to set the pair of source and target WAN accelerators. | Accepts the [CWanAccelerator](cwanaccelerator.md) object. To get this object, run the [Get-VBRWANAccelerator](get-vbrwanaccelerator.md) cmdlet. | True | Named | False |
| GFSOptions | Specifies a GFS retention. The cmdlet will create Veeam Agent backup copy job with the specified policy.  Note: This option is not available for Veeam Agent policies. | Accepts the VBRComputerGFSOptions object. To get this object, run the [New-VBRComputerGFSOptions](new-vbrcomputergfsoptions.md) cmdlet. | False | Named | False |
| Name | Specifies a name that you want to assign to a Veeam Agent backup copy job. | String | False | Named | False |
| Description | Specifies a description of a Veeam Agent backup copy job. | String | False | Named | False |
| Backup | Specifies an array of backups. The cmdlet will add machines from these backups to a Veeam Agent backup copy job.  Note: This parameter is available for a Veeam Agent backup copy job that is created with the periodic backup copy mode. | Accepts the CBackup[] object. To create this object, run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. | False | Named | False |
| SourceRepository | Specifies an array of source backup repositories. | Accepts the CBackupRepository[] object. To create this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | False | Named | False |
| BackupJob | Specifies an array of backup jobs. The cmdlet will add machines processed by these jobs to a Veeam Agent backup copy job. | Accepts the VBRComputerBackupJob[] object. To create this object, run the [Get-VBRComputerBackupJob](get-vbrcomputerbackupjob.md) cmdlet. | False | Named | False |
| Repository | Specifies the target backup repository. The cmdlet will copy the machine data to this repository.  Default: Default backup repository. | Accepts the CBackupRepository object. To create this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | False | Named | False |
| EnableImmediateCopy | Defines that the cmdlet will enable the immediate copy mode.  If you specify this parameter, Veeam Backup & Replication will copy new restore points and transaction logs as soon as they appear.  Otherwise, Veeam Backup & Replication will copy data from backups once per backup copy interval.  Note:   * To run the script with the EnableImmediateCopy parameter, you must provide the BackupJob parameter. * To copy transaction logs you must provide the EnableTransactionLogCopy parameter. | SwitchParameter | False | Named | False |
| EnableTransactionLogCopy | Defines that the Veeam Agent backup copy job will process transaction logs of the source job. | SwitchParameter | False | Named | False |
| RecoveryPointObjective | Specifies a schedule for a Veeam Agent backup copy job with the periodic backup copy mode. The cmdlet will create the job with these settings. | Accepts the VBRRecoveryPointObjective object. To create this object, run the [Get-VBRRecoveryPointObjective](get-vbrrecoverypointobjective.md) cmdlet. | False | Named | False |
| RetentionPolicy | Specifies a retention policy for a Veeam Agent backup copy job. The cmdlet will create the job with these settings. You can specify the following types of retention policies:   * Simple retention policy: use this option for short-time archiving. To create a job with this type of the policy, provide the VBRSimpleRetentionPolicy object. Run the [New-VBRSimpleRetentionPolicy](new-vbrsimpleretentionpolicy.md) cmdlet to create this object. * GFS retention policy: use this option for long-term archiving. To create a job with this type of the policy, provide the VBRRetentionPolicy object. Run the [New-VBRGFSRetentionPolicy](new-vbrgfsretentionpolicy.md) cmdlet to create this object. | Accepts the following objects:   * VBRRetentionPolicy. Run the New-VBRGFSRetentionPolicy cmdlet to get this object. * VBRSimpleRetentionPolicy. Run the [New-VBRSimpleRetentionPolicy](new-vbrsimpleretentionpolicy.md) cmdlet to create this object. | False | Named | False |
| BackupWindowOptions | Specifies backup window settings for a Veeam Agent backup copy job. The cmdlet will create the job with these settings. | Accepts the VBRBackupWindowOptions object. To create this object, run the [New-VBRBackupWindowOptions](new-vbrbackupwindowoptions.md) cmdlet. | False | Named | False |
| NotificationOptions | Specifies notification settings for a Veeam Agent backup copy job. The cmdlet will create the job with these settings. | Accepts the VBRNotificationOptions object. To create this object, run the [New-VBRNotificationOptions](new-vbrnotificationoptions.md) cmdlet. | False | Named | False |
| StorageOptions | Specifies the storage settings of the backup repository. The cmdlet will create the Veeam Agent backup copy job with these settings. | Accepts the VBRBackupCopyJobStorageOptions object. To create this object, run the [New-VBRBackupCopyJobStorageOptions](new-vbrbackupcopyjobstorageoptions.md) cmdlet. | False | Named | False |
| HealthCheckOptions | Specifies the health check schedule for a Veeam Agent backup copy job. The cmdlet will create the job with these settings. | Accepts the VBRFullBackupOptions object. To create this object, run the [New-VBRFullBackupOptions](new-vbrfullbackupoptions.md) cmdlet. | False | Named | False |
| ScriptOptions | Specifies pre-job and post-job script options for a Veeam Agent backup copy job. The cmdlet will create the job with these settings. | Accepts the VBRJobScriptOptions object. To create this object, run the [New-VBRJobScriptOptions](new-vbrjobscriptoptions.md) cmdlet. | False | Named | False |
| RPOWarningOptions | Specifies a period of time when data must be copied from the source repository to the target repository.  Default: 1 hour. | Accepts the VBRRPONotificationOptions[] object. To create this object, run the [New-VBRRPONotificationOption](new-vbrrponotificationoption.md) cmdlet. | False | Named | False |
| RetentionType | Specifies retention type for Veeam Agent copy jobs managed by the Veeam Backup server. You can specify one of the following types:   * RestorePoints * RestoreDays | VBRRetentionType | False | Named | False |
| RetentionNumber | For the RetentionType set to the RestoreDays property.  Specifies a number of days for which you want to store backup files in the target location.  Default: 7 days. | Int32 | False | Named | False |
| Force | Defines that the cmdlet will ADD INFO without showing warnings in the PowerShell console. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRComputerBackupCopyJob object that contains settings of Veeam Agent backup copy jobs.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Creating Veeam Agent Backup Copy Job to Transfer Data Directly

|  |  |
| --- | --- |
| This example shows how to create a Veeam Agent backup copy job that will transfer data directly from the source backup repository to the target backup repository.  |  | | --- | | $repository = Get-VBRBackupRepository -Name Repository 05  $job = Get-VBRComputerBackupJob -Name "Agent backup job 05"  Add-VBRComputerBackupCopyJob -OSPlatform Windows -DirectOperation -Name "Agent Backup Copy 05" -BackupJob $job -Repository $repository |  Perform the following steps:   1. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Save the result to the $repository variable. 2. Run the [Get-VBRComputerBackupJob](get-vbrcomputerbackupjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable. 3. Run the Add-VBRComputerBackupCopyJob cmdlet. Specify the following settings:  * Specify the OSPlatform parameter value. * Provide the DirectOperation parameter. * Specify the Name parameter value. * Set the $job variable as the BackupJob parameter value. * Set the $repository variable as the Repository parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Creating Veeam Agent Backup Copy Job to Transfer Data over WAN Accelerators

|  |  |
| --- | --- |
| This example shows how to create a Veeam Agent backup copy job that will transfer data over WAN accelerators.  |  | | --- | | $wansource = Get-VBRWANAccelerator -Name "WAN Source"  $wantarget = Get-VBRWANAccelerator -Name "WAN02 Target"  $backup = Get-VBRBackup -Name "Windows Server Backup"  $repository = Get-VBRBackupRepository -Name Repository 05  Add-VBRComputerBackupCopyJob -OSPlatform Windows -SourceAccelerator $wansource -TargetAccelerator $wantarget -Backup $backup -Repository $repository |  Perform the following steps:   1. Run the [Get-VBRWANAccelerator](get-vbrwanaccelerator.md) cmdlet. Specify the Name parameter value. Save the result to the $wansource variable. 2. Run the [Get-VBRWANAccelerator](get-vbrwanaccelerator.md) cmdlet. Specify the Name parameter value. Save the result to the $wantarget variable. 3. Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable. 4. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Save the result to the $repository variable. 5. Run the Add-VBRComputerBackupCopyJob cmdlet. Specify the following settings:  * Specify the OSPlatform parameter value.  * Set the $wansource variable as the SourceAccelerator parameter value. * Set the $wantarget variable as the TargetAccelerator parameter value. * Set the $backup variable as the Backup parameter value. * Set the $repository variable as the Repository parameter value. |

Related Commands

* [Get-VBRComputerBackupJob](get-vbrcomputerbackupjob.md)
* [Get-VBRBackupRepository](get-vbrbackuprepository.md)
* [Get-VBRWANAccelerator](get-vbrwanaccelerator.md)
* [Get-VBRBackup](get-vbrbackup.md)

Page updated 12/19/2024

Page content applies to build 13.0.1.1071
