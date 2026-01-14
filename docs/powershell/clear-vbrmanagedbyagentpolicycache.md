---
title: "Clear-VBRManagedByAgentPolicyCache"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/clear-vbrmanagedbyagentpolicycache.html"
last_updated: "5/7/2024"
product_version: "13.0.1.1071"
---

# Clear-VBRManagedByAgentPolicyCache

In this article

Short Description

Removes cache from the protected computers.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Clear-VBRManagedByAgentPolicyCache -Policy <VBRComputerBackupJob[]> [-RunAsync] [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet removes backup cache from protected computers.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Policy | Specifies a Veeam Agent backup policy. The cmdlet will remove backup cache from computers that are processed by this policy. | Accepts the VBRComputerBackupJob[] object. To get this object, run the [Get-VBRComputerBackupJob](get-vbrcomputerbackupjob.md) cmdlet. | True | 0 | True (ByValue, ByPropertyName) |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |
| WhatIf | Defines whether the cmdlet writes a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines whether the cmdlet displays a prompt that asks if the user is sure that they want to continue.  Note: Microsoft PowerShell enables the Confirm parameter for this cmdlet by default. To disable this option, set the parameter value to $false. That is, Confirm:$false. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRSession](vbrsession.md)

Examples

Removing Backup Cache from Protected Computers

This example shows how to remove backup cache from protected computers that are processed by the WinSrv2049 Veeam Agent backup policy.

|  |
| --- |
| $policy = Get-VBRComputerBackupJob -Name "WinSrv2049"  Clear-VBRManagedByAgentPolicyCache -Policy $policy |

Perform the following steps:

1. Run the [Get-VBRComputerBackupJob](get-vbrcomputerbackupjob.md) cmdlet. Specify the Name parameter value. Save the result to the $policy variable.
2. Run the Clear-VBRManagedByAgentPolicyCache cmdlet. Set the $policy variable as the Policy parameter value.

Related Commands

[Get-VBRComputerBackupJob](get-vbrcomputerbackupjob.md)

Page updated 5/7/2024

Page content applies to build 13.0.1.1071
