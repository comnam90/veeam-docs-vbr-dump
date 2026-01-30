---
title: "VBRInstanceLicenseSummaryObject"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrinstancelicensesummaryobject.html"
last_updated: "11/6/2023"
product_version: "13.0.1.1071"
---

# VBRInstanceLicenseSummaryObject


Contains details on the protected workloads.

Properties

| Property | Type | Description |
| --- | --- | --- |
| Type | [VBRinstanceLicenseObjectType](enums.md#VBRInstanceLicenseObjectType) | Type of a protected workload. |
| Count | int | Number of protected workloads. |
| Multiplier | int | Consumed instance multiplier. |
| UsedInstancesNumber | int | Number of consumed instance. |

Related Commands

[Get-VBRInstalledLicense](get-vbrinstalledlicense.md)


