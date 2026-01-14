---
title: "VBRMonthlyOptions"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrmonthlyoptions.html"
last_updated: "11/6/2023"
product_version: "13.0.1.1071"
---

# VBRMonthlyOptions

In this article

Contains job monthly schedule settings.

Properties

| Property | Type | Description |
| --- | --- | --- |
| Period | Timespan | The time when the job runs. |
| DayOfWeek | DayOfWeek | The days of week when the job runs. |
| DayNumberInMonth | [VBRDayNumberInMonth](enums.md#VBRDayNumberInMonth) | Day in month in job schedule. |
| Months | VBRMonth[] | The months when the job runs. |

Related Commands

[New-VBRMonthlyOptions](new-vbrmonthlyoptions.md)

Page updated 11/6/2023

Page content applies to build 13.0.1.1071
