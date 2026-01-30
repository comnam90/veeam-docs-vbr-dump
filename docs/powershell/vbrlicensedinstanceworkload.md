---
title: "VBRLicensedInstanceWorkload"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrlicensedinstanceworkload.html"
last_updated: "11/6/2023"
product_version: "13.0.1.1071"
---

# VBRLicensedInstanceWorkload


Contains protected workloads for the per-instance license.

Properties

| Property | Type | Description |
| --- | --- | --- |
| ID | guid | Protected workload ID. |
| Name | string | Protected workload name. |
| UsedInstancesNumber | int | Number of used instances. |
| Type | [VBRinstanceLicenseObjectType](enums.md#VBRInstanceLicenseObjectType) | Types of instance licensed workloads. |

Related Commands

[Get-VBRLicensedInstanceWorkload](get-vbrlicensedinstanceworkload.md)


