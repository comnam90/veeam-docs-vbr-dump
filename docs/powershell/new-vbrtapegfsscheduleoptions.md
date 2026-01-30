---
title: "New-VBRTapeGFSScheduleOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrtapegfsscheduleoptions.html"
last_updated: "12/18/2025"
product_version: "13.0.1.1071"
---

# New-VBRTapeGFSScheduleOptions


Short Description

Creates new GFS schedule settings.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRTapeGFSScheduleOptions [-DailyStartAt <TimeSpan>] [-MonthlyDayOfMonth <String>] [-MonthlyDayOfWeek {Sunday| Monday | Tuesday | Wednesday | Thursday | Friday | Saturday}] [-MonthlyDayOfWeekNumber {First | Second | Third | Fourth | Last | OnDay}] [-MonthlyKind {DayOfWeek | DayOfMonth}] [-MonthOfYear {January | February | March | April | May | June | July | August | September | October | November | December}] [-QuarterlyDayOfMonth <String>] [-QuarterlyDayOfWeek {Sunday | Monday | Tuesday | Wednesday | Thursday | Friday | Saturday}] [-QuarterlyDayOfWeekNumber {First | Second | Third | Fourth | Last | OnDay}] [-QuarterlyKind {DayOfWeek | DayOfQuarter}] [-QuarterlyMonthOfQuarter {First | Last}] [-WeeklyDay {Sunday | Monday | Tuesday | Wednesday | Thursday | Friday | Saturday}] [-WeeklyStartAt <TimeSpan>] [-YearlyDayOfMonth <String>] [-YearlyDayOfWeek {Sunday | Monday | Tuesday | Wednesday | Thursday | Friday | Saturday}] [-YearlyDayOfWeekNumber {First | Second | Third | Fourth | Last | OnDay}] [-YearlyKind {DayOfWeek | DayOfYear}]  [<CommonParameters>] |

Detailed Description

This cmdlet creates a new [VBRTapeGFSScheduleOptions](vbrtapegfsscheduleoptions.md) object. This object contains GFS schedule and is used to apply the schedule to a tape job.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| DailyStartAt | For daily backup.  Specifies the time of the day when the daily backup is archived. | TimeSpan | False | Named | False |
| WeeklyDay | For weekly backup.  Specifies the day of week when the weekly backup is archived. | DayOfWeek | False | Named | False |
| WeeklyStartAt | For weekly backup.  Specifies the time when the weekly backup is archived. | TimeSpan | False | Named | False |
| MonthlyKind | For monthly backup.  Specifies the type of monthly schedule:   * DayOfWeek: The monthly backup will be archived on a selected week day in month, for example, every first Sunday of month. Use the MonthlyDayOfWeek parameter to set the day of week and the MonthlyDayOfWeekNumber parameter to set the number of day, for example, "first" (Sunday). * DayOfMonth: The monthly backup will be archived on a selected day of month, for example, on the 1st. Use the MonthlyDayOfMonth parameter to set the day. | [VBRGFSMonthlyKind](enums.md#VBRGFSMonthlyKind) | False | Named | False |
| MonthlyDayOfWeek | For monthly backup.  Specifies the day of week for the MonthlyKind (DayOfWeek) parameter. | DayOfWeek | False | Named | False |
| MonthlyDayOfWeekNumber | For monthly backup.  Specifies the number of day in month (for example, Saturday):   * First: the job will create a full backup every first (Saturday) of month. * Second: the job will create a full backup every second (Saturday) of month. * Third: the job will create a full backup every third (Saturday) of month. * Fourth: the job will create a full backup every forth (Saturday) of month. * Last: the job will create a full backup every last (Saturday) of month. | [VBRDayNumberInMonth](enums.md#VBRDayNumberInMonth) | False | Named | False |
| Monthly DayOfMonth | For monthly backup.  Specifies the day in month for the MonthlyKind (DayOfMonth) parameter: 1-31/Last. | String | False | Named | False |
| QuarterlyKind | For quarterly backup.  Specifies the type of quarterly schedule:   * DayOfWeek: The quarterly backup will be archived on a selected week day, for example, the first Sunday of a quarter. Use the QuarterlyDayOfWeekNumber parameter to set the number of the week day and the QuarterlyDayOfWeek parameter to set the day of week. * DayOfQuarter: The quarterly backup will be archived on a selected day of month, for example, on the 1st of the first month of a quarter. Use the QuarterlyDayOfQuarter parameter to set the day of month and the QuartetlyMonthOfQuarter to set the month. | VBRGFSQuarterlyKind | False | Named | False |
| Quarterly DayOfWeek Number | For quarterly backup.  Specifies the number of the selected day, for example, "the first" (Sunday) for the QuarterlyKind (DayOfWeek) parameter: First/Second/Third/Fourth/Last. | [VBRDayNumberInMonth](enums.md#VBRDayNumberInMonth) | False | Named | False |
| Quarterly DayOfWeek | For quarterly backup.  Specifies the day of week for the QuarterlyKind (DayOfWeek) parameter. | DayOfWeek | False | Named | False |
| Quarterly DayOfMonth | For quarterly backup.  Specifies the day of month for the QuarterlyKind (DayOfQuarter) parameter: 1-31/Last. | String | False | Named | False |
| Quarterly MonthOfQuarter | For quarterly backup.  Specifies the number of month in quarter for the QuarterlyKind (DayOfQuarter) parameter: First/Last. | VBRGFSMonthOfQuarter | False | Named | False |
| YearlyKind | For yearly backup.  Specifies the type of yearly schedule:   * DayOfWeek: The yearly backup will be archived on a selected week day in year, for example, every first Sunday of year. Use the YearlyDayOfWeek parameter to set the day of week and the YearlyDayOfWeekNumber parameter to set the number of day, for example, "first" (Sunday). * DayOfYear: The yearly backup will be archived on a selected day of month in year, for example, on the 1st of January. Use the YearlyDayOfMonth parameter to set the day in month and the MonthOfYear parameter to set the month. | VBRGFSYearlyKind | False | Named | False |
| Yearly DayOfWeek Number | For yearly backup.  Specifies the number of the selected day, for example, "the first" (Sunday) for the YearlyKind (DayOfWeek) parameter: First/Second/Third/Fourth/Last. | [VBRDayNumberInMonth](enums.md#VBRDayNumberInMonth) | False | Named | False |
| Yearly DayOfWeek | For yearly backup.  Specifies the day of week for the YearlyKind (DayOfWeek) parameter. | DayOfWeek | False | Named | False |
| YearlyDayOfMonth | For yearly backup.  Specifies the day of month for the YearlyKind (DayOfYear) parameter: 1-31/Last. | String | False | Named | False |
| MonthOfYear | For yearly backup.  Specifies the month for the YearlyKind (DayOfYear) parameter. | VBRMonth | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRTapeGFSScheduleOptions](vbrtapegfsscheduleoptions.md)

Examples

Creating GFS Backup to Tape Schedule

This command creates a new GFS schedule with the following settings:

* Weekly backup: Tuesday 18:00:00
* Monthly backup: First Sunday of the month (default)
* Quarterly backup: First Sunday of the quarter (default)
* Yearly backup: First Sunday of the year (default)
* Daily backup: 0:00:00 (default)

|  |
| --- |
| $sch = New-VBRTapeGFSScheduleOptions -WeeklyDay Tuesday -WeeklyStartAt 18:00 |


