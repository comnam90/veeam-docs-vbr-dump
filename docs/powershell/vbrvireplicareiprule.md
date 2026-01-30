---
title: "VBRViReplicaReIpRule"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrvireplicareiprule.html"
last_updated: "2/16/2024"
product_version: "13.0.1.1071"
---

# VBRViReplicaReIpRule


Contains VMware replica re-IP rule.

Properties

| Property | Type | Description |
| --- | --- | --- |
| SourceIp | string | Source network IP. |
| SourceMask | string | Source subnet mask. |
| TargetIp | string | Target network IP. |
| TargetMask | string | Target subnet mask. |
| TargetGateway | string | Target network gateway address. |
| DNS | string[] | DNS servers addresses. |
| WINS | string[] | WINS servers addresses. |
| Description | string | Re-IP rule description. |

Related Commands

* [Get-VBRViReplicaReIpRule](get-vbrvireplicareiprule.md)
* [New-VBRViReplicaReIpRule](new-vbrvireplicareiprule.md)


