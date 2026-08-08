---
title: "VBRApplicationBackupRepositoryScheduleOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrapplicationbackuprepositoryscheduleoptions.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# VBRApplicationBackupRepositoryScheduleOptions


Contains schedule settings for the application backup repository snapshots.

Properties

Properties

| Property | Type | Description |
| ScheduleEnabled | Boolean | Defines whether the snapshot schedule for the application backup repository is enabled. |
| Type | VBRServerScheduleType | Schedule type:   * Daily * Monthly * Periodically |
| DailyOptions | [VBRDailyOptions](vbrdailyoptions.md) | Daily schedule settings. |
| MonthlyOptions | [VBRMonthlyOptions](vbrmonthlyoptions.md) | Monthly schedule settings. |
| PeriodicallyOptions | [VBRPeriodicallyOptions](vbrperiodicallyoptions.md) | Periodically schedule settings. |

Related Commands

[New-VBRApplicationBackupRepositoryScheduleOptions](new-vbrapplicationbackuprepositoryscheduleoptions.md)

Page updated 2026-05-29

