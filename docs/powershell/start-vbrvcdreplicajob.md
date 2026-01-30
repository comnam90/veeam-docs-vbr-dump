---
title: "Start-VBRvCDReplicaJob"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/start-vbrvcdreplicajob.html"
last_updated: "4/24/2024"
product_version: "13.0.1.1071"
---

# Start-VBRvCDReplicaJob


Short Description

Starts Cloud Director replication jobs.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Start-VBRvCDReplicaJob -Job <VBRvCDReplicaJob[]> [-RunAsync]  [<CommonParameters>] |

Detailed Description

This cmdlet starts Cloud Director replication jobs.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies an array of Cloud Director replication jobs that you want to start. | Accepts the VBRvCDReplicaJob[] object. To get this object, run the [Get-VBRvCDReplicaJob](get-vbrvcdreplicajob.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | True (ByValue, ByPropertyName) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Starting Cloud Director Replication Jobs

This example shows how to start all Cloud Director replication jobs that are added to the backup infrastructure.

|  |
| --- |
| $replicavCD = Get-VBRvCDReplicaJob  Start-VBRvCDReplicaJob -Job $replicavCD |

Perform the following steps:

1. Run the [Get-VBRvCDReplicaJob](get-vbrvcdreplicajob.md) cmdlet. Save the result to the $replicavCD variable.
2. Run the Start-VBRvCDReplicaJob cmdlet. Set the $replicavCD variable as the Job parameter value.

Related Commands

[Get-VBRvCDReplicaJob](get-vbrvcdreplicajob.md)


