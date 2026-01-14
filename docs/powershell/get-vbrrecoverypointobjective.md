---
title: "Get-VBRRecoveryPointObjective"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrrecoverypointobjective.html"
last_updated: "1/8/2024"
product_version: "13.0.1.1071"
---

# Get-VBRRecoveryPointObjective

In this article

Short Description

Returns a schedule for a backup copy jobs that process backups stored on external repositories.

Applies to

Platform: VMware, Hyper-V

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRRecoveryPointObjective -Job <CBackupJob>  [<CommonParameters>] |

Detailed Description

Returns the VBRRecoveryPointObjective object. This object contains schedule settings backup copy jobs that process backups stored on external repositories.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies the backup copy job. The cmdlet will return schedule settings for the specified job. | Accepts the CBackupJob object. To get this object, run the [Get-VBRJob](get-vbrjob.md) cmdlet. | True | Named | True (ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRRecoveryPointObjective object that contains settings for backup copy interval of backup copy jobs.

Examples

Getting Schedule Settings for Backup Copy Job

This example shows how to get schedule settings for a backup copy job.

|  |
| --- |
| $job = Get-VBRJob -Name "EC2 BCJ 01"  Get-VBRRecoveryPointObjective -Job $job |

Perform the following steps:

1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable.
2. Run the Get-VBRRecoveryPointObjective cmdlet. Set the $job variable as the Job parameter value.

Related Commands

[Get-VBRJob](get-vbrjob.md)

Page updated 1/8/2024

Page content applies to build 13.0.1.1071
