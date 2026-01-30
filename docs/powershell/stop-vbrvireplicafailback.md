---
title: "Stop-VBRViReplicaFailback"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/stop-vbrvireplicafailback.html"
last_updated: "6/27/2024"
product_version: "13.0.1.1071"
---

# Stop-VBRViReplicaFailback


Short Description

Undoes VMware replica failback.

Applies to

Platform: VMware

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Stop-VBRViReplicaFailback -RestorePoint <COib> [-PowerOn] [-RunAsync] [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet undoes the VMware replica failback started with the [Start-VBRViReplicaFailback](start-vbrvireplicafailback.md) cmdlet.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| RestorePoint | Specifies the restore point of the replica VM. The cmdlet will undo failback of this VM. | Accepts the COib object. To get this object, run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. | True | 1 | True (ByValue, |
| PowerOn | Defines that the cmdlet will power on the replica VM after the failback stops.  By default this parameter is set to True. If you want to power on replica VM manually, set this parameter to False. | SwitchParameter | False | Named | False |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |
| WhatIf | Defines that the cmdlet writes a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines that the cmdlet displays a prompt that asks if the user is sure that they want to continue.  Note: Microsoft PowerShell enables the Confirm parameter for this cmdlet by default. To disable this option, set the parameter value to $false. That is, Confirm:$false. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Stopping Replica Failback

This example shows how to stop replica failback.

|  |
| --- |
| $replica\_restorepoint = Get-VBRRestorePoint -Name "WebServer\_replica" | Sort-Object $\_.creationtime -Descending | Select -First 1  Stop-VBRViReplicaFailback -RestorePoint $replica\_restorepoint -PowerOn:$False -RunAsync |

Perform the following steps:

1. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Specify the Name parameter value. Filter the restore points of the VM with the Sort-Object method by the creationtime property to get the most recent one. Save the result to the $replica\_restorepoint variable.
2. Run the Stop-VBRViReplicaFailback cmdlet. Set the $replica\_restorepoint variable as the RestorePoint parameter value. Set the PowerOn parameter to False if you want to power on replica VM manually. Provide the RunAsync parameter.

Related Commands

[Get-VBRRestorePoint](get-vbrrestorepoint.md)


