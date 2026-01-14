---
title: "Get-VBRViReplicaReIpRule"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrvireplicareiprule.html"
last_updated: "5/12/2025"
product_version: "13.0.1.1071"
---

# Get-VBRViReplicaReIpRule

In this article

Short Description

Returns VMware job re-IP rules.

Applies to

Platform: VMware

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRViReplicaReIpRule -Job <CBackupJob>  [<CommonParameters>] |

Detailed Description

This cmdlet returns the list of re-IP rules configured for a selected VMware replication job.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies the replication job for which you want to get the list of the re-IP rules. | Accepts the CBackupJob object. To get this object, run the [Get-VBRJob](get-vbrjob.md) cmdlet. | True | Named | True (ByValue, |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRViReplicaReIpRule](vbrvireplicareiprule.md)

[VBRViReplicaReIpIPv6Rule](vbrvireplicareipipv6rule.md)

Examples

Getting Re-IP Rules for Replication Job

This example gets re-IP rules set for a replication job.

|  |
| --- |
| $job = Get-VBRJob -Name "Backup Copy Job"  Get-VBRViReplicaReIpRule -Job $job |

Perform the following steps:

1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Save the result to the $job variable.
2. Run the Get-VBRViReplicaReIpRule cmdlet. Set the $job variable as the Job parameter value.

Related Commands

[Get-VBRJob](get-vbrjob.md)

Page updated 5/12/2025

Page content applies to build 13.0.1.1071
