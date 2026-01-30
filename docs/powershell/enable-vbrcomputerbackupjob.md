---
title: "Enable-VBRComputerBackupJob"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/enable-vbrcomputerbackupjob.html"
last_updated: "3/6/2024"
product_version: "13.0.1.1071"
---

# Enable-VBRComputerBackupJob


Short Description

Enables Veeam Agent backup jobs and Veeam Agent backup policies.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Enable-VBRComputerBackupJob -Job <VBRComputerBackupJob[]> [-PassThru]  [<CommonParameters>] |

Detailed Description

This cmdlet enables Veeam Agent backup jobs and Veeam Agent backup policies.

Run the [Disable-VBRComputerBackupJob](disable-vbrcomputerbackupjob.md) cmdlet to disable Veeam Agent backup jobs and Veeam Agent backup policies.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies a Veeam Agent backup job or a Veeam Agent backup policy that you want to enable. | Accepts the VBRComputerBackupJob[] object. To get this object, run the [Get-VBRComputerBackupJob](get-vbrcomputerbackupjob.md) cmdlet. | True | 0 | True (ByValue, ByPropertyName) |
| PassThru | Defines that the command returns the output object to the Windows PowerShell console. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

This cmdlet returns the VBRComputerBackupJob object that contains settings of enabled Veeam Agent backup jobs and Veeam Agent backup policies.

Examples

Enabling Veeam Agent Backup Job

This example shows how to enable the WinSrv2049 Veeam Agent Backup Job.

|  |
| --- |
| $job = Get-VBRComputerBackupJob -Name "WinSrv2049"  Enable-VBRComputerBackupJob -Job $job |

Perform the following steps:

1. Run the [Get-VBRComputerBackupJob](get-vbrcomputerbackupjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable.
2. Run the Enable-VBRComputerBackupJob cmdlet. Set the $job variable as the Job parameter value.

Related Commands

[Get-VBRComputerBackupJob](get-vbrcomputerbackupjob.md)


