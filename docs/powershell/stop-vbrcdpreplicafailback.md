---
title: "Stop-VBRCDPReplicaFailback"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/stop-vbrcdpreplicafailback.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# Stop-VBRCDPReplicaFailback

In this article

Short Description

Undoes a CDP replica failback.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Stop-VBRCDPReplicaFailback -Replica <VBRCDPReplica> [-PowerOn] [-Force] [-RunAsync] [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet undoes CDP replica failback.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Replica | Specifies a CDP replica for which you want to undo failback. | Accepts the VBRCDPReplica object. To create this object, run the [Get-VBRCDPReplica](get-vbrcdpreplica.md) cmdlet. | True | Named | False |
| PowerOn | Defines that the cmdlet will power on a CDP replica after failback stops.  If you do not provide this parameter, the cmdlet will not power on the replica.  Default: False. | SwitchParameter | False | Named | False |
| Force | Defines that the cmdlet will undo a failback for a CDP replica without showing warnings in the PowerShell console. | SwitchParameter | False | Named | False |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |
| WhatIf | Defines that the cmdlet will display a prompt that asks if you want to continue running the command. | SwitchParameter | False | Named | False |
| Confirm | Defines that the command returns the output object to the Windows PowerShell console.  Note: Microsoft PowerShell enables the Confirm parameter for this cmdlet by default. To disable this option, set the parameter value to $false. That is, Confirm:$false. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Undoing Failback

This example shows how to undo failback of the CDP replica of the Win05 VM.

|  |
| --- |
| $replica = Get-VBRCDPReplica -Name "Win05"  Stop-VBRCDPReplicaFailback -Replica $replica -RunAsync |

Perform the following steps:

1. Run the [Get-VBRCDPReplica](get-vbrcdpreplica.md) cmdlet. Specify the Name parameter value. Save the result to the $replica variable.
2. Run the Stop-VBRCDPReplicaFailback cmdlet. Set the $replica variable as the Replica parameter. Provide the RunAsync parameter.

Related Commands

[Get-VBRCDPReplica](get-vbrcdpreplica.md)

Page updated 10/7/2025

Page content applies to build 13.0.1.1071
