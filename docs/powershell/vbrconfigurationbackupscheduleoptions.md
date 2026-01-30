---
title: "VBRConfigurationBackupScheduleOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrconfigurationbackupscheduleoptions.html"
last_updated: "11/6/2023"
product_version: "13.0.1.1071"
---

# VBRConfigurationBackupScheduleOptions


Contains configuration backup job schedule settings.

Properties

| Property | Type | Description |
| --- | --- | --- |
| DailyOptions | [VBRDailyOptions](vbrdailyoptions.md) | Job daily schedule settings. |
| MonthlyOptions | [VBRMonthlyOptions](vbrmonthlyoptions.md) | Job monthly schedule settings. |
| Enabled | bool | Indicates if the job schedule is enabled (TRUE) or not (FALSE). |
| Type | [VBRConfigurationBackupScheduleType](enums.md#VBRConfigurationBackupScheduleType) | Schedule type. |

Related Commands

[New-VBRConfigurationBackupScheduleOptions](new-vbrconfigurationbackupscheduleoptions.md)


