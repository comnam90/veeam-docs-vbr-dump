---
title: "Set-VBRTapeGFSScheduleOptions"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrtapegfsscheduleoptions.html"
last_updated: "5/12/2025"
product_version: "13.0.1.1071"
---

# Set-VBRTapeGFSScheduleOptions

In this article

Short Description

Modifies GFS scheduling options.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRTapeGFSScheduleOptions -Options <VBRTapeGFSScheduleOptions> [-DailyStartAt <TimeSpan>] -WeeklyDay <DayOfWeek> {Sunday | Monday | Tuesday | Wednesday | Thursday | Friday | Saturday}] [-WeeklyStartAt <timespan>] [-MonthlyKind <VBRGFSMonthlyKind> {DayOfWeek | DayOfMonth}] [-MonthlyDayOfWeek <DayOfWeek> {Sunday | Monday | Tuesday | Wednesday | Thursday | Friday | Saturday}] [-MonthlyDayOfWeekNumber <VBRDayNumberInMonth> {First | Second | Third | Fourth | Last | OnDay}] [-MonthlyDayOfMonth <string>] [-QuarterlyKind <VBRGFSQuarterlyKind> {DayOfWeek | DayOfQuarter}] [-QuarterlyDayOfWeekNumber <VBRDayNumberInMonth> {First | Second | Third | Fourth | Last | OnDay}] [-QuarterlyDayOfWeek <DayOfWeek> {Sunday | Monday | Tuesday | Wednesday | Thursday | Friday | Saturday}] [-QuarterlyDayOfMonth <string>] [-QuarterlyMonthOfQuarter <VBRGFSMonthOfQuarter> {First | Last}] [-YearlyKind <VBRGFSYearlyKind> {DayOfWeek | DayOfYear}] [-YearlyDayOfWeekNumber <VBRDayNumberInMonth> {First | Second | Third | Fourth | Last | OnDay}] [-YearlyDayOfWeek <DayOfWeek> {Sunday | Monday | Tuesday | Wednesday | Thursday | Friday | Saturday}] [-YearlyDayOfMonth <string>] [-MonthOfYear <VBRMonth> {January | February | March | April | May | June | July | August | September | October | November | December}]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies the [VBRTapeGFSScheduleOptions](vbrtapegfsscheduleoptions.md) object. This object contains GFS scheduling options and is used to set schedule to GFS jobs.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Options | Specifies the [VBRTapeGFSScheduleOptions](vbrtapegfsscheduleoptions.md) object you want to modify. | Accepts the [VBRTapeGFSScheduleOptions](vbrtapegfsscheduleoptions.md) object. To create this object, run the [New-VBRTapeGFSScheduleOptions](new-vbrtapegfsscheduleoptions.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |
| DailyStartAt | For daily backup.  Specifies the time of the day when the daily backup is archived. | TimeSpan | False | Named | False |
| WeeklyDay | For weekly backup.  Specifies the day of week when the weekly backup is archived. | DayOfWeek | False | Named | False |
| WeeklyStartAt | For weekly backup.  Specifies the time when the weekly backup is archived. | TimeSpan | False | Named | False |
| MonthlyKind | For monthly backup.  Specifies the type of monthly schedule:   * DayOfWeek: The monthly backup will be archived on a selected week day in month, for example, every first Sunday of month. Use the MonthlyDayOfWeek parameter to set the day of week and the MonthlyDayOfWeekNumber parameter to set the number of day, for example, "first" (Sunday). * DayOfMonth: The monthly backup will be archived on a selected day of month, for example, on the 1st. Use the MonthlyDayOfMonth parameter to set the day. | [VBRGFSMonthlyKind](enums.md#VBRGFSMonthlyKind) | False | Named | False |
| MonthlyDayOfWeek | For monthly backup.  Specifies the day of week for the MonthlyKind (DayOfWeek) parameter. | DayOfWeek | False | Named | False |
| MonthlyDayOfWeekNumber | For monthly backup.  Specifies the number of day in month (for example, Saturday):   * First: the job will create a full backup every first (Saturday) of month. * Second: the job will create a full backup every second (Saturday) of month. * Third: the job will create a full backup every third (Saturday) of month. * Fourth: the job will create a full backup every fourth (Saturday) of month. * Last: the job will create a full backup every last (Saturday) of month. | [VBRDayNumberInMonth](enums.md#VBRDayNumberInMonth) | False | Named | False |
| MonthlyDayOfMonth | For monthly backup.  Specifies the day in month for the MonthlyKind (DayOfMonth) parameter: 1-31/Last. | String | False | Named | False |
| QuarterlyKind | For quarterly backup.  Specifies the type of quarterly schedule:   * DayOfWeek: The quarterly backup will be archived on a selected week day, for example, the first Sunday of a quarter. Use the QuarterlyDayOfWeekNumber parameter to set the number of the week day and the QuarterlyDayOfWeek parameter to set the day of week. * DayOfQuarter: The quarterly backup will be archived on a selected day of month, for example, on the 1st of the first month of a quarter. Use the QuarterlyDayOfQuarter parameter to set the day of month and the QuartetlyMonthOfQuarter to set the month. | VBRGFSQuarterlyKind | False | Named | False |
| QuarterlyDayOfWeekNumber | For quarterly backup.  Specifies the number of the selected day, for example, "the first" (Sunday) for the QuarterlyKind (DayOfWeek) parameter: First/Second/Third/Fourth/Last. | [VBRDayNumberInMonth](enums.md#VBRDayNumberInMonth) | False | Named | False |
| QuarterlyDayOfWeek | For quarterly backup.  Specifies the day of week for the QuarterlyKind (DayOfWeek) parameter. | DayOfWeek | False | Named | False |
| QuarterlyDayOfMonth | For quarterly backup.  Specifies the day of month for the QuarterlyKind (DayOfQuarter) parameter: 1-31/Last. | String | False | Named | False |
| QuarterlyMonthOfQuarter | For quarterly backup.  Specifies the number of month in quarter for the QuarterlyKind (DayOfQuarter) parameter: First/Last. | VBRGFSMonthOfQuarter | False | Named | False |
| YearlyKind | For yearly backup.  Specifies the type of yearly schedule:   * DayOfWeek: The yearly backup will be archived on a selected week day in year, for example, every first Sunday of year. Use the YearlyDayOfWeek parameter to set the day of week and the YearlyDayOfWeekNumber parameter to set the number of day, for example, "first" (Sunday). * DayOfYear: The yearly backup will be archived on a selected day of month in year, for example, on the 1st of January. Use the YearlyDayOfMonth parameter to set the day in month and the MonthOfYear parameter to set the month. | VBRGFSYearlyKind | False | Named | False |
| YearlyDayOfWeekNumber | For yearly backup.  Specifies the number of the selected day, for example, "the first" (Sunday) for the YearlyKind (DayOfWeek) parameter: First/Second/Third/Fourth/Last. | [VBRDayNumberInMonth](enums.md#VBRDayNumberInMonth) | False | Named | False |
| YearlyDayOfWeek | For yearly backup.  Specifies the day of week for the YearlyKind (DayOfWeek) parameter. | DayOfWeek | False | Named | False |
| YearlyDayOfMonth | For yearly backup.  Specifies the day of month for the YearlyKind (DayOfYear) parameter: 1-31/Last. | String | False | Named | False |
| MonthOfYear | For yearly backup.  Specifies the month for the YearlyKind (MonthOfYear) parameter. | VBRMonth | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRTapeGFSScheduleOptions](vbrtapegfsscheduleoptions.md)

Examples

Changing Day and Time for Weekly Option of GFS Backup to Tape Job

This example shows how to change the day and time settings of the weekly schedule option of the GFS backup to tape job. The weekly job will run every Saturday at 10:00. The rest of the GFS schedule options remain the same.

|  |
| --- |
| $gfsschedule = New-VBRTapeGFSScheduleOptions -MonthlyKind DayOfMonth -MonthlyDayOfMonth 1  Set-VBRTapeGFSScheduleOptions -Options $gfsschedule -WeeklyDay Saturday -WeeklyStartAt 10:00 |

Perform the following steps:

1. Run the [New-VBRTapeGFSScheduleOptions](new-vbrtapegfsscheduleoptions.md) cmdlet. Set the DayOfMonth option for the MonthlyKind parameter. Specify the DayOfMonth parameter value. Save the result to the $gfsschedule variable to use with other cmdlets.
2. Run the Set-VBRTapeGFSScheduleOptions cmdlet. Set the $gfsschedule variable as the Options parameter value. Specify the WeeklyDay parameter value. Specify the WeeklyStartAt parameter value.

Related Commands

[New-VBRTapeGFSScheduleOptions](new-vbrtapegfsscheduleoptions.md)

Page updated 5/12/2025

Page content applies to build 13.0.1.1071
