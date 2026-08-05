---
title: "VBRADForestReIpRule"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbradforestreiprule.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# VBRADForestReIpRule


Contains Microsoft Active Directory forest restore re-IP rule.

Properties

Properties

| Property | Type | Description |
| SourceIp | String | Source network IP. |
| SourceMask | String | Source subnet mask. |
| TargetIp | String | Target network IP. |
| TargetMask | String | Target subnet mask. |
| TargetGateway | String | Target network gateway address. |
| DNS | String[] | DNS servers addresses. |
| WINS | String[] | WINS servers addresses. |
| Description | String | Re-IP rule description. |
| VlanTag | Int32 | Target network VLAN ID.  Note: This property applies only when you restore domain controllers to a Microsoft Hyper-V host. For VMware vSphere, the VLAN is defined by the target network. |

Related Commands

[New-VBRADForestReIpRule](new-vbradforestreiprule.md)

Page updated 2026-06-12

