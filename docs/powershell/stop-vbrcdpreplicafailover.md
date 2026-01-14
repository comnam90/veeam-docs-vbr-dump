---
title: "Stop-VBRCDPReplicaFailover"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/stop-vbrcdpreplicafailover.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# Stop-VBRCDPReplicaFailover

In this article

Short Description

Undoes a CDP replica failover.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Stop-VBRCDPReplicaFailover -Replica <VBRCDPReplica> [-Force] [-RunAsync] [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet undoes a CDP replica failover.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Replica | Specifies a CDP replica for which you want to undo a failover. The cmdlet will switch back from this  CDP replica to the original VM. | Accepts the VBRCDPReplica object. To create this object, run the [Get-VBRCDPReplica](get-vbrcdpreplica.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| ForceFailover | Defines that the cmdlet will force the undo failover operation. If you do not provide this parameter, the cmdlet will not be able to undo a failover in case the host on which the CDP replica resides is not avaialble. | SwitchParameter | False | Named | False |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |
| Force | Defines that the cmdlet will undo a failover for a CDP replica without showing warnings in the PowerShell console. | SwitchParameter | False | Named | False |
| WhatIf | Defines that the cmdlet will write a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines that the cmdlet will display a prompt that asks if you want to continue running the command.  Note: Microsoft PowerShell enables the Confirm parameter for this cmdlet by default. To disable this option, set the parameter value to $false. That is, Confirm:$false. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Undoing Failover

This example shows how to undo a failover of the CDP replica of the Win05 VM.

|  |
| --- |
| $replica = Get-VBRCDPReplica -Name "Win05"  Stop-VBRCDPReplicaFailover -Replica $replica -ForceFailover |

Perform the following steps:

1. Run the [Get-VBRCDPReplica](get-vbrcdpreplica.md) cmdlet. Specify the Name parameter value. Save the result to the $replica variable.
2. Run the Stop-VBRCDPReplicaFailover cmdlet. Set the $replica variable as the Replica parameter. Provide the ForceFailover parameter.

Related Commands

[Get-VBRCDPReplica](get-vbrcdpreplica.md)

Page updated 10/7/2025

Page content applies to build 13.0.1.1071
