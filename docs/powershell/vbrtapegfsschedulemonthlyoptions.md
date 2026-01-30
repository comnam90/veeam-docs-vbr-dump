---
title: "VBRTapeGFSScheduleMonthlyOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrtapegfsschedulemonthlyoptions.html"
last_updated: "11/6/2023"
product_version: "13.0.1.1071"
---

# VBRTapeGFSScheduleMonthlyOptions


Contains GFS tape jobs monthly schedule options.

Extends:

[VBRTapeGFSScheduleOptions](vbrtapegfsscheduleoptions.md)

Properties

| Property | Type | Description |
| --- | --- | --- |
| Kind | [VBRGFSMonthlyKind](enums.md#VBRGFSMonthlyKind) | Monthly schedule type. |
| DayOfWeek | DayOfWeek | The day of week. |
| DayOfWeekNumber | [VBRDayNumberInMonth](enums.md#VBRDayNumberInMonth) | Day in month in job schedule. |
| DayOfMonth | string | The day in month: 1-31/Last. |


