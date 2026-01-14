---
title: "Apply-VBRManagedByAgentPolicy"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/apply-vbrmanagedbyagentpolicy.html"
last_updated: "3/6/2024"
product_version: "13.0.1.1071"
---

# Apply-VBRManagedByAgentPolicy

In this article

Short Description

Assigns Veeam Agent backup policies to protected computers.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Apply-VBRManagedByAgentPolicy -Policy <VBRComputerBackupJob[]> [-RunAsync]  [<CommonParameters>] |

Detailed Description

This cmdlet assigns Veeam Agent backup policies to protected computers.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Policy | Specifies a Veeam Agent backup policy that you want to assign to protected computers. | Accepts the VBRComputerBackupJob[] object. To get this object, run the [Get-VBRComputerBackupJob](get-vbrcomputerbackupjob.md) cmdlet. | True | 0 | True (ByValue, ByPropertyName) |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRSession](vbrsession.md)

Examples

Assigning Veeam Agent Backup Policy to Protected Computers

This example shows how to assign a Veeam Agent backup policy to protected computers.

|  |
| --- |
| $job = Get-VBRComputerBackupJob -Name "WinSrv2049"  Apply-VBRManagedByAgentPolicy -Policy $job |

Perform the following steps:

1. Run the [Get-VBRComputerBackupJob](get-vbrcomputerbackupjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable.
2. Run the Apply-VBRManagedByAgentPolicy cmdlet. Set the $job variable as the Policy parameter value.

Related Commands

[Get-VBRComputerBackupJob](get-vbrcomputerbackupjob.md)

Page updated 3/6/2024

Page content applies to build 13.0.1.1071
