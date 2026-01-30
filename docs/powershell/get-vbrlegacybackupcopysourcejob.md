---
title: "Get-VBRLegacyBackupCopySourceJob"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrlegacybackupcopysourcejob.html"
last_updated: "3/1/2024"
product_version: "13.0.1.1071"
---

# Get-VBRLegacyBackupCopySourceJob


Short Description

Returns legacy periodic backup copy job source objects.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRLegacyBackupCopySourceJob -Job <CBackupJob>  [<CommonParameters>] |

Detailed Description

This cmdlet returns legacy periodic backup copy job source objects.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies an array of jobs. The cmdlet will return source objects of these jobs. | Accepts the CBackupJob[] object. To get this object, run the [Get-VBRJob](get-vbrjob.md) cmdlet. | True | 0 | True (ByPropertyName, ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the CBackupJob object that contains legacy periodic backup copy job source objects.

Examples

Getting Source Objects of Legacy Periodic Backup Copy Job

This example shows how to get source objects of legacy periodic backup copy job named LegacyPeriodicJob.

|  |
| --- |
| $copyjob = Get-VBRJob -Name "LegacyPeriodicJob"  Get-VBRLegacyBackupCopySourceJob -Job $copyjob |

Perform the following steps:

1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. Save the result to the $copyjob variable.
2. Run the Get-VBRLegacyBackupCopySourceJob cmdlet. Set the $copyjob variable as the Job parameter value.

Related Commands

[Get-VBRJob](get-vbrjob.md)


