---
title: "VBRTapeGFSScheduleQuarterlyOptions"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrtapegfsschedulequarterlyoptions.html"
last_updated: "5/17/2024"
product_version: "13.0.1.1071"
---

# VBRTapeGFSScheduleQuarterlyOptions

In this article

Contains GFS tape jobs quarterly schedule options.

Extends:

[VBRTapeGFSScheduleOptions](vbrtapegfsscheduleoptions.md)

Properties

| Property | Type | Description |
| --- | --- | --- |
| Kind | VBRGFSQuarterlyKind | The type of quarterly schedule:   * on a selected week day, for example, the first Sunday of a quarter (DayOfWeek) * on a selected date, for example, on the 1st of the first month of a quarter (DayOfQuarter) |
| DayOfWeekNumber | [VBRDayNumberInMonth](enums.md#VBRDayNumberInMonth) | Day in month in job schedule. |
| DayOfWeek | DayOfWeek | The day of week. |
| DayOfMonth | string | The day of month: 1-31/Last. |
| MonthOfQuarter | VBRGFSMonthOfQuarter | The number of month in quarter:   * First * Last |

Page updated 5/17/2024

Page content applies to build 13.0.1.1071
