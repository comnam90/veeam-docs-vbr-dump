---
title: "Disable-VBRBackupCopyJob"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/disable-vbrbackupcopyjob.html"
last_updated: "4/24/2024"
product_version: "13.0.1.1071"
---

# Disable-VBRBackupCopyJob


Short Description

Disables backup copy jobs.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Disable-VBRBackupCopyJob -Job <VBRBackupCopyJob[]> [-PassThru]  [<CommonParameters>] |

Detailed Description

This cmdlet disables backup copy jobs.

Run the [Enable-VBRBackupCopyJob](enable-vbrbackupcopyjob.md) cmdlet to enable backup copy jobs.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies an array of backup copy jobs that you want to disable. | Accepts the VBRBackupCopyJob[] object. To create this object, run the [Get-VBRBackupCopyJob](get-vbrbackupcopyjob.md) cmdlet. | True | 0 | True(ByValue, ByPropertyName) |
| PassThru | Defines that the command returns the output object to the Windows PowerShell console. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Disabling Backup Copy Job

This example shows how to disable a backup copy job.

|  |
| --- |
| $job = Get-VBRBackupCopyJob  Disable-VBRBackupCopyJob -Job $job |

Perform the following steps:

1. Run the [Get-VBRBackupCopyJob](get-vbrbackupcopyjob.md) cmdlet. Save the result to the $job variable.
2. Run the Disable-VBRBackupCopyJob cmdlet. Set the $job variable as the Job parameter value.

Related Commands

[Get-VBRBackupCopyJob](get-vbrbackupcopyjob.md)


