---
title: "Set-VBRJobOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrjoboptions.html"
last_updated: "8/14/2024"
product_version: "13.0.1.1071"
---

# Set-VBRJobOptions


Short Description

Modifies job settings.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRJobOptions -Job <CBackupJob[]> [-Options <CJobOptions>] [-HighPriority]  [<CommonParameters>] |

Detailed Description

This cmdlet applies customized settings to a selected job.

Run the [New-VBRJobOptions](new-vbrjoboptions.md) cmdlet to create the CJobOptions object. This object unifies all the options you want to apply to the job.

|  |
| --- |
| Important |
| Consider the following:   * The Set-VBRJobOptions cmdlet is deprecated for Veeam Agent jobs and policies. Run the [Set-VBRComputerBackupJob](set-vbrcomputerbackupjob.md) cmdlet instead. * The Set-VBRJobOptions cmdlet is deprecated for backup copy jobs. Run the [Set-VBRBackupCopyJob](set-vbrbackupcopyjob.md) cmdlet instead. |

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies the job you want to edit. | Accepts the CBackupJob object. To create this object, run the [Get-VBRJob](get-vbrjob.md) cmdlet. | True | 0 | True (ByProperty Name, ByValue) |
| Options | Specifies the set of parameters you want to apply to the job. | Accepts the CJobOptions object. To create this object, run the [New-VBRJobOptions](new-vbrjoboptions.md) cmdlet. | False | 1 | False |
| HighPriority | Defines that Veeam Backup & Replication will prioritize this job higher than other similar jobs and allocate resources to it first. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Applying Custom Settings to Specific Backup Job [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to apply custom settings to the backup job named Backup Job 01.  |  | | --- | | $options = New-VBRJobOptions  Get-VBRJob -Name "Backup Job 01" | Set-VBRJobOptions -Options $options |  Perform the following steps:   1. Run the [New-VBRJobOptions](new-vbrjoboptions.md) cmdlet. Save the result to the $options variable. 2. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. 3. Pipe the cmdlet output to the Set-VBRJobOptions cmdlet. Set the $options variable as the Options parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Applying Custom Settings to Backup Job [Using Variable]

|  |  |
| --- | --- |
| This example shows how to apply custom settings to the backup job represented by the $job variable.  |  | | --- | | $job = Get-VBRJob -Name "Backup Job 01"  $options = New-VBRJobOptions  Set-VBRJobOptions -Job $job -Options $options |  Perform the following steps:   1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable. 2. Run the [New-VBRJobOptions](new-vbrjoboptions.md) cmdlet. Save the result to the $options variable. 3. Run the Set-VBRJobOptions cmdlet. Set the $job variable as the Job parameter value. Set the $options variable as the Options parameter value. |

Related Commands

* [Get-VBRJob](get-vbrjob.md)
* [New-VBRJobOptions](new-vbrjoboptions.md)


