---
title: "Stop-VBRReplicaFailover"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/stop-vbrreplicafailover.html"
last_updated: "6/27/2024"
product_version: "13.0.1.1071"
---

# Stop-VBRReplicaFailover


Short Description

Undoes replica failover.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Stop-VBRReplicaFailover -RestorePoint <COib> [-RunAsync] [-Force] [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet undoes the replica failover. This cmdlet finalizes the replica failover started with the [Start-VBRViReplicaFailover](start-vbrvireplicafailover.md) cmdlet.

Run the [Start-VBRViReplicaFailback](start-vbrvireplicafailback.md) cmdlet to fail back to the VMware production VM.

Run the [Start-VBRHvReplicaFailback](start-vbrhvreplicafailback.md) cmdlet to fail back to the Hyper-V production VM.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| RestorePoint | Specifies the restore point of the production VM to recover to. | Accepts the COib object. To get this object, run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. | True | 1 | True (ByValue, |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |
| Force | Defines that the replica job starts running without waiting for the target host to power off. Otherwise the replica job will start only after the target host is powered off. | SwitchParameter | False | Named | False |
| WhatIf | Defines that the cmdlet writes a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines that the cmdlet displays a prompt that asks if the user is sure that they want to continue.  Note: Microsoft PowerShell enables the Confirm parameter for this cmdlet by default. To disable this option, set the parameter value to $false. That is, Confirm:$false. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Stopping Failover [Using Pipeline]

|  |  |
| --- | --- |
| This command stops failover process by reverting to the production VM.  |  | | --- | | Get-VBRRestorePoint -Name "WebServer\_replica" | Sort-Object $\_.creationtime -Descending | Select -First 1 | Stop-VBRReplicaFailover -Reason "Configuration recovery" -RunAsync -Force |  Perform the following steps:   1. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Specify the Name parameter value. Filter the restore points with the Sort-Object method by the creationtime property to get the most recent one. 2. Pipe the cmdlet output to the Stop-VBRReplicaFailover cmdlet. Specify the Reason parameter value. Provide the RunAsync and Force parameters. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Stopping Failover [Using Variable]

|  |  |
| --- | --- |
| This command stops failover process by reverting to the production VM.  |  | | --- | | $replica\_restorepoint = Get-VBRRestorePoint -Name "WebServer\_replica"  Stop-VBRReplicaFailover -RestorePoint $replica\_restorepoint[1] -Reason "Data recovery" -RunAsync |  Perform the following steps:   1. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Specify the Name parameter value. Save the result to the $replica\_restorepoint variable. 2. Run the Stop-VBRReplicaFailover cmdlet. Specify the following settings:  * Set the $replica\_restorepoint variable as the RestorePoint parameter value.   The Get-VBRRestorePoint cmdlet will return an array of restore points. Consider that the array numbering starts with 0. In our example, the second restore point is used.   * Specify the Reason parameter value. * Provide the RunAsync parameter. |

Related Commands

[Get-VBRRestorePoint](get-vbrrestorepoint.md)


