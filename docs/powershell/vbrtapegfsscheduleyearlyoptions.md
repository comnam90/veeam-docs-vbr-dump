---
title: "VBRTapeGFSScheduleYearlyOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrtapegfsscheduleyearlyoptions.html"
last_updated: "5/17/2024"
product_version: "13.0.1.1071"
---

# VBRTapeGFSScheduleYearlyOptions


Contains GFS tape jobs yearly schedule options.

Extends:

[VBRTapeGFSScheduleOptions](vbrtapegfsscheduleoptions.md)

Properties

| Property | Type | Description |
| --- | --- | --- |
| Kind | VBRGFSYearlyKind | The type of yearly schedule:   * on a selected week day, for example, the first Sunday of a year (DayOfWeek) * on a selected date, for example, on the 1st January of a year (DayOfYear) |
| DayOfWeekNumber | [VBRDayNumberInMonth](enums.md#VBRDayNumberInMonth) | Day in month in job schedule. |
| DayOfWeek | DayOfWeek | The day of week. |
| DayOfMonth | string | The day of month: 1-31/Last. |
| MonthOfYear | VBRMonth | The month. |


