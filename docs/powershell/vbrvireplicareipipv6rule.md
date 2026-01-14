---
title: "VBRViReplicaReIpIPv6Rule"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrvireplicareipipv6rule.html"
last_updated: "7/5/2024"
product_version: "13.0.1.1071"
---

# VBRViReplicaReIpIPv6Rule

In this article

Contains VMware vSphere replica re-IPv6 rule.

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

* [Get-VBRViReplicaReIpRule](get-vbrvireplicareiprule.md)
* [New-VBRViReplicaReIpIPv6Rule](new-vbrvireplicareipipv6rule.md)

Page updated 7/5/2024

Page content applies to build 13.0.1.1071
