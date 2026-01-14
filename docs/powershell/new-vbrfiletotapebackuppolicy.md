---
title: "New-VBRFileToTapeBackupPolicy"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrfiletotapebackuppolicy.html"
last_updated: "5/12/2025"
product_version: "13.0.1.1071"
---

# New-VBRFileToTapeBackupPolicy

In this article

Short Description

Creates schedule settings for a file to tape job.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRFileToTapeBackupPolicy [-Type <VBRFileToTapeBackupPolicyType>] [-DailyOptions <VBRDailyOptions>] [-MonthlyOptions <VBRMonthlyOptions>] [-Enabled]  [<CommonParameters>] |

Detailed Description

This cmdlet creates the [VBRFileToTapeBackupPolicy](vbrfiletotapebackuppolicy.md) object. This object contains backup creation schedule settings for file to tape job and is used further to apply these settings to an existing file to tape job.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Type | Specifies the backup creation schedule type:   * Daily: the target files will be archived on selected days. Use the DailyOptions parameter to set the days. * Monthly: the target files will be archived on selected months. Use the MonthlyOptions parameter to set the months.   Default: Daily. | [VBRFileToTapeBackupPolicyType](enums.md#VBRBackupToTapePolicyType) | False | Named | False |
| DailyOptions | Used to set days for the Type parameter (Daily option).  Default:   * Type: SelectedDays * Period: 18:00 * DayOfWeek: Saturday | Accepts the [VBRDailyOptions](vbrdailyoptions.md) object. To create this object, run the [New-VBRDailyOptions](new-vbrdailyoptions.md) cmdlet. | False | Named | False |
| MonthlyOptions | Used to set months for the Type parameter (Monthly option).  Default:   * Period: 22:00 * DayNumberInMonth: Fourth * DayOfWeek: Saturday * Months: January, February, March, April, May, June, July, August, September, October, November, December | Accepts the [VBRMonthlyOptions](vbrmonthlyoptions.md) object. To create this object, run the [New-VBRMonthlyOptions](new-vbrmonthlyoptions.md) cmdlet. | False | Named | False |
| Enabled | Defines if this schedule is enabled.  Default: False. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRFileToTapeBackupPolicy](vbrfiletotapebackuppolicy.md)

Examples

Creating Monthly Job Schedule for File to Tape Jobs

This example shows how to create file to tape job schedule to run on last Sunday on 22:00 every month. The schedule is enabled.

|  |
| --- |
| $monthlyoptions = New-VBRMonthlyOptions -DayNumberInMonth Last -DayOfWeek Sunday -Period 22:00  New-VBRFileToTapeBackupPolicy -Type Monthly -MonthlyOptions $monthlyoptions -Enabled |

Perform the following steps:

1. Run the [New-VBRMonthlyOptions](new-vbrmonthlyoptions.md) cmdlet. Specify the DayNumberInMonth, DayOfWeek and the Period parameter values. Save the result to the $monthlyoptions variable.
2. Run the New-VBRFileToTapeBackupPolicy cmdlet. Set the Monthly option for the Type parameter. Set the $monthlyoptions variable as the MonthlyOptions parameter value. Provide the Enabled parameter.

Related Commands

* [New-VBRDailyOptions](new-vbrdailyoptions.md)
* [New-VBRMonthlyOptions](new-vbrmonthlyoptions.md)

Page updated 5/12/2025

Page content applies to build 13.0.1.1071
