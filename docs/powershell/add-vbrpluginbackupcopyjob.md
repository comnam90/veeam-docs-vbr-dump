---
title: "Add-VBRPluginBackupCopyJob"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrpluginbackupcopyjob.html"
last_updated: "12/19/2024"
product_version: "13.0.1.1071"
---

# Add-VBRPluginBackupCopyJob

In this article

Short Description

Creates plug-in backup copy jobs.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Add-VBRPluginBackupCopyJob -TargetRepository <CBackupRepository> [-Name <String>] [-Description <String>] [-SourceJob <VBRPluginBackupJob[]>] [-ExcludedJob <VBRPluginBackupJob[]>] [-SourceRepository <CBackupRepository[]>] [-ApplicationDataRetention <Int32>] [-NotificationOptions <VBRNotificationOptions>] [-StorageOptions <VBRPluginCopyJobStorageOptions>] [-BackupWindowOptions <VBRBackupWindowOptions>] [-RPOWarningOptions <VBRRpoNotificationOption[]>] [-Force]  [<CommonParameters>] |

Detailed Description

This cmdlet creates plug-in backup copy jobs. To create plug-in backup copy jobs, you must specify at least one source that contains the data you want to add to the copy job. Plug-in backup copy jobs use one of the following sources:

* The existing plug-in backup job created to back up Oracle RMAN or SAP HANA. Run the [Get-VBRPluginJob](get-vbrpluginjob.md) cmdlet to get the plug-in backup job.
* Backup files that are stored in the source repositories. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet to get the source repository.

|  |
| --- |
| Note |
| The backup copy job is created in the disabled state. Run the [Enable-VBRPluginJob](enable-vbrpluginjob.md) cmdlet to run the job manually. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| TargetRepository | Specifies a target backup repository. The cmdlet will copy plug-in backups to this repository. | Accepts the CBackupRepository object. To get this object, run the | True | Named | True (ByValue, ByPropertyName) |
| Name | Specifies a name of a plug-in backup copy job. The cmdlet will create the job with this name. | String | False | Named | True (ByValue, ByPropertyName) |
| Description | Specifies a description of a plug-in backup copy job. The cmdlet will create the job with this description. | String | False | Named | True (ByValue, ByPropertyName) |
| SourceJob | Specifies a plug-in backup job. The cmdlet will add databases processed by this job to the plug-in backup copy job. | Accepts the VBRPluginBackupJob[] object. To get this object, run the [Get-VBRPluginJob](get-vbrpluginjob.md) cmdlet. | False | Named | True (ByValue, ByPropertyName) |
| ExcludedJob | Specifies a plug-in backup job that you do not want to process by a plug-in backup copy job. The cmdlet will not add databases processed by this job to the plug-in backup copy job. | Accepts the VBRPluginBackupJob[] object. To get this object, run the [Get-VBRPluginJob](get-vbrpluginjob.md) cmdlet. | False | Named | True (ByValue, ByPropertyName) |
| SourceRepository | Specifies a backup repository that contains backups of databases, created by a plug-in backup job. The cmdlet will add backups located on this repository to the plug-in backup copy job. | Accepts the CBackupRepository object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | False | Named | True (ByValue, ByPropertyName) |
| ApplicationDataRetention | Specifies the number of days. The cmdlet will create a plug-in backup copy job with the specified amount of days. | Int32 | False | Named | True (ByValue, ByPropertyName) |
| NotificationOptions | Specifies notification settings. The cmdlet will create the plug-in backup copy job with these settings. | Accepts the VBRNotificationOptions object. To create this object, run the [New-VBRNotificationOptions](new-vbrnotificationoptions.md) cmdlet. | False | Named | True (ByValue, ByPropertyName) |
| StorageOptions | Specifies settings for compression and storage optimization of the target backup repository. The cmdlet will create the plug-in backup copy job with these settings. | Accepts the VBRPluginCopyJobStorageOptions object. To create this object, run the [New-VBRPluginCopyJobStorageOptions](new-vbrplugincopyjobstorageoptions.md) cmdlet. | False | Named | True (ByValue, ByPropertyName) |
| BackupWindowOptions | Specifies backup window settings for a job. The cmdlet will create the plug-in backup copy job with these settings. | Accepts the VBRBackupWindowOptions object. To create this object, run the [New-VBRBackupWindowOptions](new-vbrbackupwindowoptions.md) cmdlet. | False | Named | True (ByValue, ByPropertyName) |
| RPOWarningOptions | Specifies an array of the number of hours when data must be copied from the source repository to the target repository.  Default: 1. | Accepts the VBRRpoNotificationOption[] object. To create this object, run the [New-VBRRPONotificationOption](new-vbrrponotificationoption.md) cmdlet. | False | Named | True (ByValue, ByPropertyName) |
| Force | Defines that the job will be created even if the source repository is located in the different geographic location than the target repository. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRPluginBackupCopyJob object that contains settings for plug-in backup copy jobs.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Creating Plug-In Backup Copy Job Using Existing Plug-In Backup Job

|  |  |
| --- | --- |
| This example shows how to create a plug-in backup copy job using the existing plug-in backup job.  |  | | --- | | $pluginjob = Get-VBRPluginJob -Name "SAP backint backup 07"  $targetrepository = Get-VBRBackupRepository -Name "TR05"  Add-VBRPluginBackupCopyJob -SourceJob $pluginjob -Name "Plug-in backup 03" -TargetRepository $targetrepository |  Perform the following steps:   1. Run the [Get-VBRPluginJob](get-vbrpluginjob.md) cmdlet. Specify the Name parameter value. Save the result to the $pluginjob variable. 2. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Save the result to the $targetrepository variable. 3. Run the Add-VBRPluginBackupCopyJob cmdlet. Specify the following settings:  * Set the $pluginjob variable as the SourceJob parameter value. * Specify the Name parameter value. * Set the $targetrepository as the TargetRepository parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Creating Plug-In Backup Copy Job Using Source Repository

|  |  |
| --- | --- |
| This example shows how to create a plug-in backup copy job using the source repository.  |  | | --- | | $sourcerepository = Get-VBRBackupRepository -Name "SR09"  $targetrepository = Get-VBRBackupRepository -Name "TR07"  Add-VBRPluginBackupCopyJob -Name "Plug-in backup 05" -SourceRepository $sourcerepository -TargetRepository $targetrepository |  Perform the following steps:   1. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Save the result to the $sourcerepository variable. 2. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Save the result to the $targetrepository variable. 3. Run the Add-VBRPluginBackupCopyJob cmdlet. Specify the following settings:  * Specify the Name parameter value. * Set the $sourcerepository variable as the SourceRepository parameter value. * Set the $targetrepository as the TargetRepository parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Creating Plug-In Backup Copy Job Using Job and Source Repository

|  |  |
| --- | --- |
| This example shows how to create a plug-in backup copy job using the existing backup copy job and a source repository.  |  | | --- | | $pluginjob = Get-VBRPluginJob -Name "SAP backint backup 11"  $sourcerepository = Get-VBRBackupRepository -Name "SR013"  $targetrepository = Get-VBRBackupRepository -Name "TR015"  Add-VBRPluginBackupCopyJob -SourceJob $pluginjob -Name "Plug-in backup 17" -SourceRepository $sourcerepository -TargetRepository $targetrepository |  Perform the following steps:   1. Run the [Get-VBRPluginJob](get-vbrpluginjob.md) cmdlet. Specify the Name parameter value. Save the result to the $pluginjob variable. 2. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Save the result to the $sourcerepository variable. 3. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Save the result to the $targetrepository variable. 4. Run the Add-VBRPluginBackupCopyJob cmdlet. Specify the following settings:  * Set the $pluginjob variable as the SourceJob parameter value. * Specify the Name parameter value. * Set the $sourcerepository variable as the SourceRepository parameter value. * Set the $targetrepository variable as the TargetRepository parameter value. |

Related Commands

* [Get-VBRPluginJob](get-vbrpluginjob.md)
* [Get-VBRBackupRepository](get-vbrbackuprepository.md)

Page updated 12/19/2024

Page content applies to build 13.0.1.1071
