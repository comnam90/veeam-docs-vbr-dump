---
title: "VBRADForestDomain"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbradforestdomain.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# VBRADForestDomain


Contains a Microsoft Active Directory domain within the Microsoft Active Directory forest.

Properties

Properties

| Property | Type | Description |
| DnsName | String | DNS name of the Active Directory domain. |
| DistinguishedName | String | Distinguished name (DN) of the Active Directory domain. |
| IsRoot | Bool | Indicates whether the domain is the root domain of the forest. |
| Parent | [VBRADForestDomain](vbradforestdomain.md)? | Parent domain in the domain tree. Returns null for the root domain of the forest. |

Related Commands

[Get-VBRADForestDomain](get-vbradforestdomain.md)

Page updated 2026-04-01

