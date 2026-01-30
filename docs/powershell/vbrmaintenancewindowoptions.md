---
title: "VBRMaintenanceWindowOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrmaintenancewindowoptions.html"
last_updated: "8/4/2025"
product_version: "13.0.1.1071"
---

# VBRMaintenanceWindowOptions


Contains maintenance window settings.

Properties

| Property | Type | Description |
| --- | --- | --- |
| DailyOptions | [VBRDailyOptions](vbrdailyoptions.md) | The day of the week when updates are installed automatically. |
| Enable | Boolean | Indicates if there is a maintenance window when updates are installed automatically. |
| MonthlyOptions | [VBRMonthlyOptions](vbrmonthlyoptions.md) | The day of the month when updates are installed automatically. |

Related Commands

* [New-VBRMaintenanceWindowOptions](new-vbrmaintenancewindowoptions.md)
* [New-VBRDailyOptions](new-vbrdailyoptions.md)
* [New-VBRMonthlyOptions](new-vbrmonthlyoptions.md)


