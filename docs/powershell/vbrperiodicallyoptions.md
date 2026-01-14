---
title: "VBRPeriodicallyOptions"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrperiodicallyoptions.html"
last_updated: "2/16/2024"
product_version: "13.0.1.1071"
---

# VBRPeriodicallyOptions

In this article

Contains periodically schedule settings for performing discovery operations in a protection group.

Properties

| Property | Type | Description |
| --- | --- | --- |
| PeriodicallyKind | VBRPeriodicallyKinds | Periodically schedule type:   * Hours * Minutes * Continuously |
| FullPeriod | int | The number of hours or minutes:   * Hours: 1, 2, 3, 4, 6, 8, 12, 24. * Minutes: 1-999. |
| PeriodicallySchedule | VBRBackupWindowOptions | The discovery window. |
| HourlyOffset | int | The exact time when the discovery window starts. |

Related Commands

* [New-VBRPeriodicallyOptions](new-vbrperiodicallyoptions.md)
* [New-VBRBackupWindowOptions](new-vbrbackupwindowoptions.md)

Page updated 2/16/2024

Page content applies to build 13.0.1.1071
