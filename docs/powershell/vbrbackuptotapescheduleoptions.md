---
title: "VBRBackupToTapeScheduleOptions"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrbackuptotapescheduleoptions.html"
last_updated: "11/6/2023"
product_version: "13.0.1.1071"
---

# VBRBackupToTapeScheduleOptions

In this article

Contains backup to tape job schedule settings.

Properties

"?" indicates that the property accepts zero values.

| Property | Type | Description |
| --- | --- | --- |
| Type | [VBRBackupToTapePolicyType](enums.md#VBRBackupToTapePolicyType) | Job schedule policy type. |
| DailyOptions | [VBRDailyOptions](vbrdailyoptions.md) | Job daily schedule settings. |
| MonthlyOptions | [VBRMonthlyOptions](vbrmonthlyoptions.md) | Job monthly schedule settings. |
| JobId | GUID? | ID of job after which this job must run. |
| Enabled | bool | Indicates if the job schedule is enabled (TRUE) or disabled (FALSE). |

Related Commands

[New-VBRBackupToTapeScheduleOptions](new-vbrbackuptotapescheduleoptions.md)

Page updated 11/6/2023

Page content applies to build 13.0.1.1071
