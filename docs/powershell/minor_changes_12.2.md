---
title: "Minor Non-Breaking Changes"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/minor_changes_12.2.html"
last_updated: "12/19/2024"
product_version: "13.0.1.1071"
---

# Minor Non-Breaking Changes

In this article

The following minor non-breaking changes were introduced in Veeam PowerShell 12.2.

Object Storage Repositories

In this version, in the following cmdlets parameters were changed from obligatory to non-required:

| Cmdlet | Parameter |
| --- | --- |
| [Add-VBRAzureArchiveRepository](add-vbrazurearchiverepository.md) | AzureProxySpec |
| [Add-VBRAmazonS3GlacierRepository](add-vbramazons3glacierrepository.md) | AmazonProxySpec |

Replication

In this version, the following cmdlets can return new objects:

* The [Get-VBRViReplicaReIpRule](get-vbrvireplicareiprule.md) cmdlet can return the VBRViReplicaReIpIPv6Rule object that contains VMware vSphere replica re-IPv6 rule. You can use this object when you run the following cmdlets:

* The [Add-VBRCDPPolicy](add-vbrcdppolicy.md) or [Set-VBRCDPPolicy](set-vbrcdppolicy.md) cmdlets to create or modify CDP policies.
* The [Add-VBRViReplicaJob](add-vbrvireplicajob.md) or [Set-VBRViReplicaJob](set-vbrvireplicajob.md) cmdlets to create or modify VMware replication jobs.

* The [Get-VBRHvReplicaReIpRule](get-vbrhvreplicareiprule.md) cmdlet can return the VBRHvReplicaReIpIPv6Rule object that contains Hyper-V replica re-IPv6 rule. You can use this object when you run the [Add-VBRHvReplicaJob](add-vbrhvreplicajob.md) or the [Set-VBRHvReplicaJob](set-vbrhvreplicajob.md) cmdlets to create or modify Hyper-V replication jobs.

Page updated 12/19/2024

Page content applies to build 13.0.1.1071
