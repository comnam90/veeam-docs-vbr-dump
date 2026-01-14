---
title: "VBRFailoverPlanObject"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrfailoverplanobject.html"
last_updated: "1/25/2024"
product_version: "13.0.1.1071"
---

# VBRFailoverPlanObject

In this article

Contains VM in failover plan and VM processing settings.

Properties

| Property | Type | Description |
| --- | --- | --- |
| Item | IItem | VM added to a failover plan. Can contain only one VM. VM object must be CViVmItem or CHvVmItem. |
| BootOrder | int | Order number by which the VM will boot during failover. |
| BootDelay | int | Delay time for the VM to boot during failover (seconds). |

Related Commands

[Failover Plans](fplan_cmdlets.md)

Page updated 1/25/2024

Page content applies to build 13.0.1.1071
