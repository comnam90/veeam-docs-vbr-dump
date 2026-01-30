---
title: "VBRLicensedSocketWorkload"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrlicensedsocketworkload.html"
last_updated: "2/16/2024"
product_version: "13.0.1.1071"
---

# VBRLicensedSocketWorkload


Contains licensed hosts for the per-socket license.

Properties

| Property | Type | Description |
| --- | --- | --- |
| ID | guid | Licensed hosts ID. |
| Name | string | Licensed hosts name. |
| SocketsNumber | int | Number of sockets. |
| CoresNumber | int | Number of cores. |
| Type | [VBRinstanceLicenseObjectType](enums.md#VBRInstanceLicenseObjectType) | Types of instance licensed workloads. |

Related Commands

[Get-VBRLicensedSocketWorkload](get-vbrlicensedsocketworkload.md)


