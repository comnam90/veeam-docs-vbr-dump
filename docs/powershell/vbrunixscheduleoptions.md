---
title: "VBRUnixScheduleOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrunixscheduleoptions.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# VBRUnixScheduleOptions


Contains schedule settings for a backup policy that the Veeam Agent backup job applies to Unix computers.

Properties

Properties

| Property | Type | Description |
| Type | VBRServerScheduleType | The schedule type configured for the backup policy. |
| DailyOptions | VBRDailyOptions | The daily schedule settings. |
| MonthlyOptions | VBRMonthlyOptions | The monthly schedule settings. |
| PeriodicallyOptions | VBRPeriodicallyOptions | The periodic schedule settings. |
| RetryEnabled | bool | Indicates whether the backup job is retried if it fails. |
| RetryCount | integer | The number of attempts to retry the failed backup job. |
| RetryTimeout | integer | The time interval between retry attempts, in minutes. |
| BackupTerminationWindowEnabled | bool | Indicates whether the backup job is stopped if it exceeds the backup window. |
| TerminationWindow | [VBRBackupWindowOptions](vbrbackupwindowoptions.md) | The backup window during which the backup job is allowed to run. |

Related Commands

* [New-VBRUnixScheduleOptions](new-vbrunixscheduleoptions.md)
* [Set-VBRUnixScheduleOptions](set-vbrunixscheduleoptions.md)

Page updated 2026-06-16

