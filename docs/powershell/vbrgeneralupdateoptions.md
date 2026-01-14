---
title: "VBRGeneralUpdateOptions"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrgeneralupdateoptions.html"
last_updated: "8/26/2025"
product_version: "13.0.1.1071"
---

# VBRGeneralUpdateOptions

In this article

Contains general update settings.

Properties

| Property | Type | Description |
| --- | --- | --- |
| SourceRepositoryType | [VBRUpdateSourceRepositoryType](enums.md#VBRUpdateSourceRepositoryType) | Indicates the repository type. |
| AutoUpdatePeriod | Int32 | Compliance deadline for updates. |
| CustomRepositoryPath | String | Local mirror repository address. |
| ServerCertificate | X509Certificate2 | Server certificate. |
| MaintenanceWindow | [VBRMaintenanceWindowOptions](vbrmaintenancewindowoptions.md) | Maintenance window when updates are installed automatically. |
| UpdatesType | [VBRUpdateType](enums.md#VBRUpdateType) | Indicates the update type. |

Related Commands

[Get-VBRGeneralUpdateOptions](get-vbrgeneralupdateoptions.md)

Page updated 8/26/2025

Page content applies to build 13.0.1.1071
