---
title: "Disable-VBRComputerBackupCopyJob"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/disable-vbrcomputerbackupcopyjob.html"
last_updated: "3/1/2024"
product_version: "13.0.1.1071"
---

# Disable-VBRComputerBackupCopyJob

In this article

Short Description

Disables Veeam Agent backup copy jobs.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Disable-VBRComputerBackupCopyJob -Job <VBRComputerBackupCopyJob[]> [-PassThru]  [<CommonParameters>] |

Detailed Description

This cmdlet disables Veeam Agent backup copy jobs.

Run the [Enable-VBRComputerBackupCopyJob](enable-vbrcomputerbackupcopyjob.md) cmdlet to enable Veeam Agent backup copy jobs.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies an array of Veeam Agent backup copy jobs that you want to disable. | Accepts the VBRComputerBackupCopyJob[] object. To get this object, run the [Get-VBRComputerBackupCopyJob](get-vbrcomputerbackupcopyjob.md) cmdlet. | True | 0 | True (ByValue, ByPropertyName) |
| PassThru | Defines that the command returns the output object to the Windows PowerShell console. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Disabling Veeam Agent Backup Copy Jobs

This example shows how to disable Veeam Agent Backup copy jobs.

|  |
| --- |
| $jobs = Get-VBRComputerBackupCopyJob  Disable-VBRComputerBackupCopyJob -Job $jobs |

Perform the following steps:

1. Run the [Get-VBRComputerBackupCopyJob](get-vbrcomputerbackupcopyjob.md) cmdlet. Save the result to the $jobs variable.
2. Run the Disable-VBRComputerBackupCopyJob cmdlet. Set the $jobs variable as the Job parameter value.

Related Commands

[Get-VBRComputerBackupCopyJob](get-vbrcomputerbackupcopyjob.md)

Page updated 3/1/2024

Page content applies to build 13.0.1.1071
