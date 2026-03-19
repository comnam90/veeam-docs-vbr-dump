---
title: "VBRCloudFailoverPlanObject"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrcloudfailoverplanobject.html"
last_updated: "3/13/2026"
product_version: "13.0.1.2067"
---

# VBRCloudFailoverPlanObject


Contains cloud replica VMs added to cloud failover plan.

Properties

Properties

| Property | Type | Description |
| ProviderId | GUID | Service provider ID. |
| PublicIpRule | [VBRFailoverPlanPublicIPRule](vbrfailoverplanpubliciprule.md)[] | Public IP addresses mapping rules. |
| Item | IItem | Cloud replica VM added to a failover plan. |
| BootOrder | int | Order number by which the VM will boot during failover. |
| BootDelay | int | Delay time for the VM to boot during failover (seconds). |

Related Commands

* [New-VBRCloudFailoverPlanObject](new-vbrcloudfailoverplanobject.md)
* [Set-VBRCloudFailoverPlanObject](set-vbrcloudfailoverplanobject.md)


