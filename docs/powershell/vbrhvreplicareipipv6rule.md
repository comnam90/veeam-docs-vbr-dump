---
title: "VBRHvReplicaReIpIPv6Rule"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrhvreplicareipipv6rule.html"
last_updated: "6/25/2024"
product_version: "13.0.1.1071"
---

# VBRHvReplicaReIpIPv6Rule

In this article

Contains Hyper-V replica re-IPv6 rule.

Properties

| Property | Type | Description |
| --- | --- | --- |
| SourceIp | string | Source network IPv6. |
| SourcePrefix | string | Prefix length of the source subnet. |
| TargetIp | string | Target network IPv6. |
| TargetPrefix | string | Prefix length of the target subnet. |
| TargetGateway | string | Target network gateway address. |
| PreferredDNS | string | Preferred DNS server address. |
| AlternateDNS | string | Alternate DNS server address. |
| Description | string | Re-IP rule description. |

Related Commands

* [Get-VBRHvReplicaReIpRule](get-vbrhvreplicareiprule.md)
* [New-VBRHvReplicaReIpIPv6Rule](new-vbrhvreplicareipipv6rule.md)

Page updated 6/25/2024

Page content applies to build 13.0.1.1071
