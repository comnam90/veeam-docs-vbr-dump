---
title: "Stop-VBRHvReplicaFailback"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/stop-vbrhvreplicafailback.html"
last_updated: "6/27/2024"
product_version: "13.0.1.1071"
---

# Stop-VBRHvReplicaFailback

In this article

Short Description

Undoes Hyper-V replica failback.

Applies to

Platform: Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Stop-VBRHvReplicaFailback -RestorePoint <COib> [-RunAsync] [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet undoes the Hyper-V replica failback started with the [Start-VBRHvReplicaFailback](start-vbrhvreplicafailback.md) cmdlet.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| RestorePoint | Specifies the restore point of the replica VM. The cmdlet will undo failback of this VM. | Accepts the COib object. To get this object, run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. | True | Named | True (ByValue, |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |
| WhatIf | Defines whether the cmdlet writes a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines whether the cmdlet displays a prompt that asks if the user is sure that they want to continue.  Note: Microsoft PowerShell enables the Confirm parameter for this cmdlet by default. To disable this option, set the parameter value to $false. That is, Confirm:$false. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Undoing Replica Failback [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to stop failback using pipeline.  |  | | --- | | Get-VBRRestorePoint -Name "WebServer\_replica" | Sort-Object $\_.creationtime -Descending | Select -First 1 | Stop-VBRHvReplicaFailback -RunAsync |  Perform the following steps:   1. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Specify the Name parameter value. Filter the restore points of the VM with the Sort-Object method by the creationtime property to get the most recent one. 2. Pipe the cmdlet output to the Stop-VBRHvReplicaFailback cmdlet. Provide the RunAsync parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Undoing Replica Failback [Using Variable]

|  |  |
| --- | --- |
| This example shows how to stop failback using a variable.  |  | | --- | | $replica\_restorepoint = Get-VBRRestorePoint -Name "WebServer\_replica" | Sort-Object $\_.creationtime -Descending | Select -First 1  Stop-VBRHvReplicaFailback -RestorePoint $replica\_restorepoint -RunAsync |  Perform the following steps:   1. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Specify the Name parameter value. Filter the restore points of the VM with the Sort-Object method by the creationtime property to get the most recent one. Save it to the $replica\_restorepoint variable. 2. Run the Stop-VBRHvReplicaFailback cmdlet. Set the $replica\_restorepoint variable as the RestorePoint parameter value. Provide the RunAsync parameter. |

Related Commands

[Get-VBRRestorePoint](get-vbrrestorepoint.md)

Page updated 6/27/2024

Page content applies to build 13.0.1.1071
