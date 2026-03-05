---
title: "VBRGeneralUpdateOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrgeneralupdateoptions.html"
last_updated: "2/18/2026"
product_version: "13.0.1.1071"
---

# VBRGeneralUpdateOptions


Contains general update settings.

Properties

Properties

| Property | Type | Description |
| SourceRepositoryType | [VBRUpdateSourceRepositoryType](enums.md#VBRUpdateSourceRepositoryType) | Indicates the repository type. |
| AutoUpdatePeriod | Int32 | Compliance deadline for updates. |
| CustomRepositoryPath | String | Local mirror repository address. |
| ServerCertificate | X509Certificate2 | Server certificate. |
| MaintenanceWindow | [VBRMaintenanceWindowOptions](vbrmaintenancewindowoptions.md) | Maintenance window when updates are installed automatically. |
| UpdatesType | [VBRUpdateType](enums.md#VBRUpdateType) | Indicates the update type. |

Related Commands

[Get-VBRGeneralUpdateOptions](get-vbrgeneralupdateoptions.md)


