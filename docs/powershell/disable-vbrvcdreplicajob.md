---
title: "Disable-VBRvCDReplicaJob"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/disable-vbrvcdreplicajob.html"
last_updated: "12/19/2024"
product_version: "13.0.1.1071"
---

# Disable-VBRvCDReplicaJob


Short Description

Disables Cloud Director replication jobs.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Disable-VBRvCDReplicaJob -Job <VBRvCDReplicaJob[]>  [<CommonParameters>] |

Detailed Description

This cmdlet disables Cloud Director replication jobs.

Run the [Enable-VBRvCDReplicaJob](enable-vbrvcdreplicajob.md) cmdlet to enable Cloud Director replication jobs.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies an array of Cloud Director replication jobs. The cmdlet will disable these jobs. | Accepts the VBRvCDReplicaJob[]  object. To get this object, run the [Get-VBRvCDReplicaJob](get-vbrvcdreplicajob.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Disabling Cloud Director Replication Jobs

This example shows how to disable Cloud Director replication jobs.

|  |
| --- |
| $replicavCD = Get-VBRvCDReplicaJob  Disable-VBRvCDReplicaJob -Job $replicavCD |

Perform the following steps:

1. Run the [Get-VBRvCDReplicaJob](get-vbrvcdreplicajob.md) cmdlet. Save the result to the $replicavCD variable.
2. Run the Disable-VBRvCDReplicaJob cmdlet. Set the $replicavCD variable as the Job parameter value.

Related Commands

[Get-VBRvCDReplicaJob](get-vbrcdppolicy.md)


