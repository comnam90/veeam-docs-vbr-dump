---
title: "New-VBRJobOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrjoboptions.html"
last_updated: "3/13/2024"
product_version: "13.0.1.1071"
---

# New-VBRJobOptions


Short Description

Creates new job options.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Edit all job options.

|  |
| --- |
| New-VBRJobOptions  [<CommonParameters>] |

* Edit backup jobs options.

|  |
| --- |
| New-VBRJobOptions [-ForBackupJob]  [<CommonParameters>] |

* Edit replication jobs options.

|  |
| --- |
| New-VBRJobOptions [-ForReplicaJob]  [<CommonParameters>] |

Detailed Description

This cmdlet returns the CJobOptions object. This object contains the default settings of the job you want to edit. You can customize any setting that you want to apply to a backup job, replication job or selected VMs.

Run the [Set-VBRJobOptions](set-vbrjoboptions.md) cmdlet to apply the modified options to a job.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| ForBackupJob | Defines that the cmdlet will return default settings for backup job. | SwitchParameter | Named | Named | False |
| ForReplicaJob | Defines that the cmdlet will return default settings for replication job. | SwitchParameter | Named | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

Defining Retention Policy for Backup Job

This example shows how to define the retention policy for a backup job.

|  |
| --- |
| $retention = New-VBRJobOptions -ForBackupJob  $retention.BackupStorageOptions.RetainCycles = 7  $job = Get-VBRJob -Name "ABC Backup"  Set-VBRJobOptions -Job $job -Options $retention |

Perform the following steps:

1. Run the New-VBRJobOptions cmdlet. Provide the ForBackupJob parameter. Save the result to the $retention variable.
2. Specify the RetainCycles parameter of the BackupStorageOptions object for the $retention variable.
3. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable.
4. Run the [Set-VBRJobOptions](set-vbrjoboptions.md) cmdlet. Set the $job variable as the Job parameter value. Set the $retention variable as the Options parameter value.

Related commands

* [Get-VBRJob](get-vbrjob.md)
* [Set-VBRJobOptions](set-vbrjoboptions.md)


