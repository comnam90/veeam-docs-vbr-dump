---
title: "Set-VBRJobAdvancedHvOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrjobadvancedhvoptions.html"
last_updated: "11/18/2025"
product_version: "13.0.1.1071"
---

# Set-VBRJobAdvancedHvOptions


Short Description

Customizes Hyper-V job settings.

Applies to

Platform: Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRJobAdvancedHvOptions [-CanDoCrashConsistent <Boolean>] [-EnableHvQuiescence <Boolean>] [-ExcludeSwapFile <Boolean>] -Job <CBackupJob[]> [-UseChangeTracking <Boolean>]  [<CommonParameters>] |

Detailed Description

This cmdlet sets special options for the selected Hyper-V job.

In case you cannot use application-aware image processing, you can enable a Hyper-V quiescence mechanism to backup data that can be changed during the backup.

Read more about Hyper-V job settings in [Veeam Backup & Replication User Guide for Microsoft Hyper-V](https://helpcenter.veeam.com/docs/vbr/userguide/backup_job_advanced_hv_hv.html?ver=13).

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameters values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies the array of jobs. The cmdlet will modify advanced Hyper-V backup options of these jobs. | Accepts the CBackupJob[] object. To create this object, run the [Get-VBRJob](get-vbrjob.md) cmdlet. | True | Named | True (ByProperty Name, ByValue) |
| CanDoCrashConsistent | Defines whether the job will create crash consistent backup. | Bool | False | Named | False |
| EnableHvQuiescence | Defines whether the job will use the Hyper-V quiescence mechanism. | Bool | False | Named | False |
| UseChangeTracking | Defines whether the job will use the changed block tracking. | Bool | False | Named | False |
| ExcludeSwapFile | Defines whether the job will exclude the swap file from backup. | Bool | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Editing Advanced Job Settings to Specific Backup Job [Using Pipeline]

This example shows how to edit advanced job settings to backup job named Backup Job 01:

* The Hyper-V quiescence is enabled.
* The crash consistent backup is enabled.
* The changed block data is enabled.
* The swap file is excluded form backup.

|  |
| --- |
| Get-VBRJob -Name "Backup Job 01" | Set-VBRJobAdvancedHvOptions -EnableHvQuiescence $True -CanDoCrashConsistent $True -UseChangeTracking $True -ExcludeSwapFile $True |

Perform the following steps:

1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value.

1. Pipe the cmdlet output to the Set-VBRJobAdvancedHvOptions cmdlet. Specify the following settings:

* Provide the $True value for the EnableHVQuiescence parameter.
* Provide the $True value for the CanDoCrashConsistent parameter.
* Provide the $True value for the UseChangeTracking parameter.
* Provide the $True value for the ExcludeSwapFile parameter.

Related Commands

[Get-VBRJob](get-vbrjob.md)


