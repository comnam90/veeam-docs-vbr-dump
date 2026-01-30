---
title: "Enable-VBRvCDReplicaJob"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/enable-vbrvcdreplicajob.html"
last_updated: "4/24/2024"
product_version: "13.0.1.1071"
---

# Enable-VBRvCDReplicaJob


Short Description

Enables Cloud Director replication jobs.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Enable-VBRvCDReplicaJob -Job <VBRvCDReplicaJob[]>  [<CommonParameters>] |

Detailed Description

This cmdlet enables Cloud Director replication jobs that were previously disabled.

Run the [Disable-VBRvCDReplicaJob](disable-vbrvcdreplicajob.md) cmdlet to disable Cloud Director replication jobs.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies an array of Cloud Director replication jobs.The cmdlet will enable these jobs. | Accepts the VBRvCDReplicaJob[] object. To get this object, run the [Get-VBRvCDReplicaJob](get-vbrvcdreplicajob.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Enabling Cloud Director Replication Jobs

This example shows how to enable Cloud Director replication jobs.

|  |
| --- |
| $replicavCD = Get-VBRvCDReplicaJob  Enable-VBRvCDReplicaJob -Job $replicavCD |

Perform the following steps:

1. Run the [Get-VBRvCDReplicaJob](get-vbrvcdreplicajob.md) cmdlet. Save the result to the $replicavCD variable.
2. Run the Enable-VBRvCDReplicaJob cmdlet. Set the $replicavCD variable as the Job parameter value.

Related Commands

[Get-VBRvCDReplicaJob](get-vbrvcdreplicajob.md)


