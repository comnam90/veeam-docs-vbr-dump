---
title: "VBRFailoverPlanPublicIPRule"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrfailoverplanpubliciprule.html"
last_updated: "11/6/2023"
product_version: "13.0.1.1071"
---

# VBRFailoverPlanPublicIPRule


Contains IP addresses and ports mapping rule.

Properties

| Property | Type | Description |
| --- | --- | --- |
| SourceIp | string | Replica IP address. |
| SourcePort | UInt16 | Replica port. |
| TargetIp | string | Replica public IP address. |
| TargetPort | UInt16 | Replica public port. |
| Description | string | Description of the rule. |

Related Commands

[New-VBRFailoverPlanPublicIPRule](new-vbrfailoverplanpubliciprule.md)


