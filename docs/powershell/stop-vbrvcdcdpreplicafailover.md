---
title: "Stop-VBRvCDCDPReplicaFailover"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/stop-vbrvcdcdpreplicafailover.html"
last_updated: "5/7/2024"
product_version: "13.0.1.1071"
---

# Stop-VBRvCDCDPReplicaFailover

In this article

Short Description

Stops Cloud Director CDP replica failover.

Applies to

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Stop-VBRvCDCDPReplicaFailover -Replica <VBRvCDCDPReplica> [-ForceFailover] [-RunAsync] [-Force] [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet stops Cloud Director CDP replica failover, that is, performs failover undo.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Replica | Specifies the replica of the vApp for which you want to undo failover. | Accepts the VBRvCDCDPReplica object. To get this object, run the [Get-VBRCDPReplica](get-vbrcdpreplicavcd.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| ForceFailover | Defines that the cmdlet will force the undo failover operation. If you do not provide this parameter, the cmdlet will not be able to undo failover in case the host on which the replica resides is not available. | SwitchParameter | False | Named | False |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |
| Force | Defines that the cmdlet will undo a failover without showing warnings in the PowerShell console. | SwitchParameter | False | Named | False |
| WhatIf | Defines that the cmdlet will write a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines that the cmdlet will display a prompt that asks if you want to continue running the command.  Note: Microsoft PowerShell enables the Confirm parameter for this cmdlet by default. To disable this option, set the parameter value to $false. That is, Confirm:$false. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Performing Failover Undo of Cloud Director CDP Replica

This example shows how to perform failover to a specific long-term restore point of a Cloud Director CDP replica.

|  |
| --- |
| $replica = Get-VBRCDPReplica -Name "Win07"  Stop-VBRvCDCDPReplicaFailover -Replica $replica |

Perform the following steps:

1. Run the [Get-VBRCDPReplica](get-vbrcdpreplica.md) cmdlet.  Specify the Name parameter value. Save the result to the $replica variable.
2. Run the Stop-VBRvCDCDPReplicaFailover cmdlet. Set the $replica variable as the Replica parameter value.

Related Commands

[Get-VBRCDPReplica](get-vbrcdpreplica.md)

Page updated 5/7/2024

Page content applies to build 13.0.1.1071
