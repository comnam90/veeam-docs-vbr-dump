---
title: "Get-VBRRetentionPolicy"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrretentionpolicy_azure.html"
last_updated: "1/25/2024"
product_version: "13.0.1.1071"
---

# Get-VBRRetentionPolicy


Short Description

Returns a retention policy for backup copy jobs.

Applies to

Platform: VMware, Hyper-V

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRRetentionPolicy -Job <CBackupJob>  [<CommonParameters>] |

Detailed Description

This cmdlet returns a retention policy for backup copy jobs of the following types:

* Backup copy jobs that process backups stored on external repositories.
* Veeam Agent backup copy jobs.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies a backup copy job. The cmdlet will return a retention policy for the specified job. | Accepts the CBackupJob object. To get this object, run the [Get-VBRJob](get-vbrjob.md) cmdlet. | True | Named | True (ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRRetentionPolicy object that contains a retention policy for backup copy jobs.

Examples

Getting Retention Policy for Backup Copy Job

This example shows how to get a retention policy for a backup copy job.

|  |
| --- |
| $job = Get-VBRJob -Name "EC2 BCJ 01"  Get-VBRRetentionPolicy -Job $job |

Perform the following steps:

1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable.
2. Run the Get-VBRRetentionPolicy cmdlet. Set the $job variable as the Job parameter value.

Related Commands

[Get-VBRJob](get-vbrjob.md)


