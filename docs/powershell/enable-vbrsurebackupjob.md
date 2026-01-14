---
title: "Enable-VBRSureBackupJob"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/enable-vbrsurebackupjob.html"
last_updated: "3/1/2024"
product_version: "13.0.1.1071"
---

# Enable-VBRSureBackupJob

In this article

Short Description

Enables stopped SureBackup jobs.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Enable-VBRSureBackupJob -Job <VBRSureBackupJobBase>  [<CommonParameters>] |

Detailed Description

This cmdlet disables running SureBackup jobs.

Run the [Disable-VBRSureBackupJob](disable-vbrsurebackupjob.md) cmdlet to disable SureBackup jobs.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies a SureBackup job. The cmdlet will enable this job. | Accepts the VBRSureBackupJobBase object. To create this object, run the [Get-VBRSureBackupJob](get-vbrsurebackupjob.md) cmdlet. | True | Named | True (ByValue, |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

Enabling SureBackup Job

This example shows how to enable the Job01 SureBackup job.

|  |
| --- |
| $surejob = Get-VBRSureBackupJob -Name "Job01"  Enable-VBRSureBackupJob -Job $surejob |

Perform the following steps:

1. Run the [Get-VBRSureBackupJob](get-vbrsurebackupjob.md) cmdlet. Specify the Name parameter value. Save the result to the $surejob variable.
2. Run the Enable-VBRSureBackupJob cmdlet. Set the $surejob variable as the Job parameter value.

Related Commands

[Get-VBRSureBackupJob](get-vbrsurebackupjob.md)

Page updated 3/1/2024

Page content applies to build 13.0.1.1071
