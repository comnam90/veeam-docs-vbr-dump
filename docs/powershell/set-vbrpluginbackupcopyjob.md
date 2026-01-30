---
title: "Set-VBRPluginBackupCopyJob"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrpluginbackupcopyjob.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# Set-VBRPluginBackupCopyJob


Short Description

Modifies plug-in backup copy jobs.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRPluginBackupCopyJob -Job <VBRPluginBackupCopyJob> [-Name <string>] [-Description <string>] [-SourceRepository <CBackupRepository[]>] [-SourceJob <VBRPluginBackupJob[]>] [-ExcludedJob<VBRPluginBackupJob[]>] [-TargetRepository <CBackupRepository>] [-ApplicationDataRetention <int>] [-NotificationOptions <VBRNotificationOptions>] [-StorageOptions <VBRPluginCopyJobStorageOptions>] [-BackupWindowOptions <VBRBackupWindowOptions>] [-RPOWarningOptions <VBRRpoNotificationOption[]>] [-EnableRPOWarning] [-Force] [-AnyTime]  [<CommonParameters>] |

Detailed Description

This example modifies plug-in backup copy jobs.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies a plug-in backup copy job. The cmdlet will modify this job. | Accepts the VBRPluginBackupCopyJob object. To get this object, run the [Get-VBRPluginJob](get-vbrpluginjob.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| Name | Specifies a name of a plug-in backup copy job. The cmdlet will assign this name to the job. | String | False | Named | True (ByValue, ByPropertyName) |
| Description | Specifies a description of a plug-in backup copy job. The cmdlet will assign this description to the job. | String | False | Named | True (ByValue, ByPropertyName) |
| SourceRepository | Specifies a backup repository that contains backups of databases, created by a plug-in backup job. The cmdlet replace the existing source repository with the specified backup repository. | Accepts the CBackupRepository object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | False | Named | True (ByValue, ByPropertyName) |
| SourceJob | Specifies a plug-in backup job. The cmdlet will replace the existing source plug-in backup job with the specified plug-in backup job. | Accepts the VBRPluginBackupJob[] object. To get this object, run the [Get-VBRPluginJob](get-vbrpluginjob.md) cmdlet. | False | Named | True (ByValue, ByPropertyName) |
| ExcludedJob | Specifies an array of plug-in backup jobs that you do not want to process by a plug-in backup copy job. The cmdlet will replace an existing list of excluded plug-in backup jobs with the array of specified excluded plug-in backup jobs. | Accepts the VBRPluginBackupJob[] object. To get this object, run the [Get-VBRPluginJob](get-vbrpluginjob.md) cmdlet. | False | Named | True (ByValue, ByPropertyName) |
| TargetRepository | Specifies a target backup repository. The cmdlet will copy plug-in backups to this repository. | Accepts the CBackupRepository object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | False | Named | True (ByValue, ByPropertyName) |
| ApplicationDataRetention | Specifies the number of days. The cmdlet will create a plug-in backup copy job with the specified amount of days. | Int32 | False | Named | True (ByValue, ByPropertyName) |
| NotificationOptions | Specifies notification settings. The cmdlet will modify a plug-in backup job with these settings. | Accepts the VBRNotificationOptions object. To create this object, run the [New-VBRNotificationOptions](new-vbrnotificationoptions.md) cmdlet. | False | Named | True (ByValue, ByPropertyName) |
| StorageOptions | Specifies settings for compression and storage optimization of the target backup repository. The cmdlet will modify a plug-in backup job with these settings. | Accepts the VBRPluginCopyJobStorageOptions object. To create this object, run the [New-VBRPluginCopyJobStorageOptions](new-vbrplugincopyjobstorageoptions.md) cmdlet. | False | Named | True (ByValue, ByPropertyName) |
| BackupWindowOptions | Specifies backup window settings for a job. The cmdlet will modify the plug-in backup copy job with these settings. | Accepts the VBRBackupWindowOptions object. To create this object, run the [New-VBRBackupWindowOptions](new-vbrbackupwindowoptions.md) cmdlet | False | Named | True (ByValue, ByPropertyName) |
| EnableRPOWarning | Defines that the cmdlet will display a warning in case the job exceeds the period that is set for the job to copy data from the source repository to the target repository.  Use the RPOWarningOptions parameter to specify the time limitation. | SwitchParameter | False | Named | False |
| RPOWarningOptions | Specifies an array of the number of hours when data must be copied from the source repository to the target repository.  Default: 1. | Accepts the VBRRpoNotificationOption[] object. To create this object, run the [New-VBRRPONotificationOptions](new-vbrrponotificationoption.md) cmdlet. | False | Named | True (ByValue, ByPropertyName) |
| EnableDataDeduplication | Defines that the cmdlet will enable the data deduplication option.  If you do not provide this parameter, Veeam Backup & Replication will not decrease the size of the copied data. | SwitchParameter | False | Named | False |
| Force | Defines that the job will be created even if the source repository is located on the different from the target repository host. | SwitchParameter | False | Named | False |
| AnyTime | Defines that the job will run continuously. If you provide this parameter, the job will run at any time. Otherwise, the job will run only during permitted hours. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRPluginBackupCopyJob object that contains settings for plug-in backup copy jobs.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Modifying Target Repository of Plug-In Backup Copy Job

|  |  |
| --- | --- |
| This example shows how to change the target repository for a plug-in backup copy job.  |  | | --- | | $pluginjob = Get-VBRPluginJob -Name "Plug-in backup 04"  $targetrepository = Get-VBRBackupRepository -Name "TR08"  Set-VBRPluginBackupCopyJob -Job $pluginjob -TargetRepository $targetrepository |  Perform the following steps:   1. Run the [Get-VBRPluginJob](get-vbrpluginjob.md) cmdlet. Specify the Name parameter value. Save the result to the $pluginjob variable. 2. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Save the result to the $targetrepository variable. 3. Run the Set-VBRPluginBackupCopyJob cmdlet. Set the $pluginjob variable as the Job parameter value. Set the $targetrepository variable as the TargetRepository parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Excluding Jobs from Plug-In Backup Copy Job

|  |  |
| --- | --- |
| This example shows how to exclude the SAP backint backup 09 plug-in backup job from processing by the Plug-in backup 09 plug-in backup copy job.  |  | | --- | | $pluginjob = Get-VBRPluginJob -Name "Plug-in backup 09"  $excludedjob = Get-VBRPluginJob -Name "SAP backint backup 09"  Set-VBRPluginBackupCopyJob -Job $pluginjob -ExcludedJob $excludedjob |  Perform the following steps:   1. Run the [Get-VBRPluginJob](get-vbrpluginjob.md) cmdlet. Specify the Name parameter value. Save the result to the $pluginjob variable. 2. Run the [Get-VBRPluginJob](get-vbrpluginjob.md) cmdlet. Specify the Name parameter value. Save the result to the $excludedjob variable. 3. Run the Set-VBRPluginBackupCopyJob cmdlet. Set the $pluginjob variable as the Job parameter value. Set the $excludedjob variable as the ExcludedJob parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Modifying Storage Optimization Settings of Plug-In Backup Copy Job

|  |  |
| --- | --- |
| This example shows how to modify storage optimization settings for a plug-in backup copy job. The plug-in backup copy job will run with the following storage optimization settings:   * The compression level is set to optimal. * The backup target storage type is set to LocalTarget.   |  | | --- | | $pluginjob = Get-VBRPluginJob -Name "Plug-in backup 09"  $storage = New-VBRPluginCopyJobStorageOptions -CompressionLevel Optimal -StorageOptimizationType LocalTarget  Set-VBRPluginBackupCopyJob -Job $pluginjob -StorageOptions $storage |  Perform the following steps:   1. Run the [Get-VBRPluginJob](get-vbrpluginjob.md) cmdlet. Specify the Name parameter value. Save the result to the $pluginjob variable. 2. Run the [New-VBRPluginCopyJobStorageOptions](new-vbrplugincopyjobstorageoptions.md) cmdlet. Set the Optimal value for the CompressionLevel parameter. Set the LocalTarget option for the StorageOptimizationType parameter. 3. Run the Set-VBRPluginBackupCopyJob cmdlet. Set the $pluginjob variable as the Job parameter value. Set the $storage variable as the StorageOptions parameter value. |

Related Commands

* [Get-VBRPluginJob](get-vbrpluginjob.md)
* [New-VBRPluginCopyJobStorageOptions](new-vbrplugincopyjobstorageoptions.md)


