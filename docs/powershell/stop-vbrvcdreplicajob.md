---
title: "Stop-VBRvCDReplicaJob"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/stop-vbrvcdreplicajob.html"
last_updated: "5/7/2024"
product_version: "13.0.1.1071"
---

# Stop-VBRvCDReplicaJob


Short Description

Stops Cloud Director replication jobs.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Stop-VBRvCDReplicaJob -Job <VBRvCDReplicaJob[]> [-Gracefully] [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet stops Cloud Director replication jobs.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies an array of Cloud Director replication jobs that you want to stop. | Accepts the VBRvCDReplicaJob[] object. To get this object, run the [Get-VBRvCDReplicaJob](get-vbrvcdreplicajob.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| Gracefully | Defines that the cmdlet will stop Cloud Director replication jobs gracefully. | SwitchParameter | False | Named | False |
| WhatIf | Defines that the cmdlet will write a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines that the cmdlet will display a prompt that asks if you want to continue running the command.  Note: Microsoft PowerShell enables the Confirm parameter for this cmdlet by default. To disable this option, set the parameter value to $false. That is, Confirm:$false. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Stopping Cloud Director Replication Jobs

This example shows how to stop all Cloud Director replication jobs that are added to the backup infrastructure.

|  |
| --- |
| $replicavCD = Get-VBRvCDReplicaJob  Stop-VBRvCDReplicaJob -Job $replicavCD |

Perform the following steps:

1. Run the [Get-VBRvCDReplicaJob](get-vbrvcdreplicajob.md) cmdlet. Save the result to the $replicavCD variable.
2. Run the Stop-VBRvCDReplicaJob cmdlet. Set the $replicavCD variable as the Job parameter value.

Related Commands

[Get-VBRvCDReplicaJob](get-vbrvcdreplicajob.md)


