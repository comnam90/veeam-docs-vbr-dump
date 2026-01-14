---
title: "New-VBRFullBackupToTapePolicy"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrfullbackuptotapepolicy.html"
last_updated: "5/12/2025"
product_version: "13.0.1.1071"
---

# New-VBRFullBackupToTapePolicy

In this article

Short Description

Creates schedule settings for creating virtual synthesized full backup for tape.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRFullBackupToTapePolicy [-Type <VBRFullBackupToTapePolicyType>] [-MonthlyOptions <VBRMonthlyOptions>] [-WeeklyOnDays <DayOfWeek[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet creates the [VBRFullBackupToTapePolicy](vbrfullbackuptotapepolicy.md) object. This object contains schedule settings for creating virtual synthesized full backup for tape and is used further to apply these settings to an existing backup to tape job.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Type | Specifies the virtual synthesized full backup creation type:   * Monthly: the virtual synthesized full backup is created on selected months. Use the MonthlyOptions parameter to set the months. * WeeklyOnDays: the virtual synthesized full backup is created on selected days of week. Use the WeeklyOnDays parameter to set the days.   Default: WeeklyOnDays. | [VBRFullBackupToTapePolicyType](enums.md#VBRFullBackupToTapePolicyType) | False | Named | False |
| MonthlyOptions | Used to set months for the Type parameter (Monthly option).  Default:   * Period: 22:00 * DayNumberInMonth: Fourth * DayOfWeek: Saturday * Months: January, February, March, April, May, June, July, August, September, October, November, December. | Accepts the [VBRMonthlyOptions](vbrmonthlyoptions.md) object. To create this object, run the [New-VBRMonthlyOptions](new-vbrmonthlyoptions.md) cmdlet. | False | Named | False |
| WeeklyOnDays | Used to set days of week for the Type parameter (WeeklyOnDays option). | DayOfWeek[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRFullBackupToTapePolicy](vbrfullbackuptotapepolicy.md)

Examples

Creating Schedule Settings for Weekly Virtual Full Backup

This example shows how to create schedule settings for weekly virtual full backup scheduled to run on Saturdays.

|  |
| --- |
| New-VBRFullBackupToTapePolicy -Type WeeklyOnDays -WeeklyOnDays Saturday |

Related Commands

[New-VBRMonthlyOptions](new-vbrmonthlyoptions.md)

Page updated 5/12/2025

Page content applies to build 13.0.1.1071
