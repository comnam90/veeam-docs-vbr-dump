---
title: "VBRFileToTapeBackupPolicy"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrfiletotapebackuppolicy.html"
last_updated: "11/6/2023"
product_version: "13.0.1.1071"
---

# VBRFileToTapeBackupPolicy

In this article

Contains file to tape job schedule settings.

Properties

| Property | Type | Description |
| --- | --- | --- |
| Type | [VBRFileToTapeBackupPolicyType](enums.md#VBRFileToTapeBackupPolicyType) | Job schedule type. |
| DailyOptions | [VBRDailyOptions](vbrdailyoptions.md) | Job daily schedule settings. |
| MonthlyOptions | [VBRMonthlyOptions](vbrmonthlyoptions.md) | Job monthly schedule settings. |
| Enabled | bool | Indicates if the job schedule is enabled (TRUE) or disabled (FALSE). |

Related Commands

[New-VBRFileToTapeBackupPolicy](new-vbrfiletotapebackuppolicy.md)

Page updated 11/6/2023

Page content applies to build 13.0.1.1071
