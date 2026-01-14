---
title: "New-VBRComputerGFSOptions"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrcomputergfsoptions.html"
last_updated: "11/18/2025"
product_version: "13.0.1.1071"
---

# New-VBRComputerGFSOptions

In this article

Short Description

Defines settings of GFS retention for Veeam Agent backup jobs.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRComputerGFSOptions [-GFSWeeklyOptions <VBRComputerGFSWeeklyOptions>] [-GFSMonthlyOptions <VBRComputerGFSMonthlyOptions>] [-GFSYearlyOptions <VBRComputerGFSYearlyOptions>] [-ReadEntireRestorePoint]  [<CommonParameters>] |

Detailed Description

This cmdlet creates the VBRComputerGFSOptions object. This object contains GFS retention settings that you can apply to Veeam Agent backup jobs.

For more information on GFS retention, see the [GFS Retention Policy](https://helpcenter.veeam.com/docs/vbr/userguide/backup_copy_gfs.html?ver=13) section of the User Guide for VMware vSphere.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| GFSWeeklyOptions | Specifies settings of a weekly GFS retention. The cmdlet will define GFS retention with these settings. | Accepts the VBRComputerGFSWeeklyOptions object. To create this object, run the [New-VBRComputerGFSWeeklyOptions](new-vbrcomputergfsweeklyoptions.md) cmdlet. | False | Named | False |
| GFSMonthlyOptions | Specifies settings of a monthly GFS retention. The cmdlet will define GFS retention with these settings. | Accepts the VBRComputerGFSMonthlyOptions object. To create this object, run the [New-VBRComputerGFSMonthlyOptions](new-vbrcomputergfsmonthlyoptions.md) cmdlet. | False | Named | False |
| GFSYearlyOptions | Specifies settings of a yearly GFS retention. The cmdlet will define GFS retention with these settings. | Accepts the VBRComputerGFSYearlyOptions object. To create this object, run the [New-VBRComputerGFSYearlyOptions](new-vbrcomputergfsyearlyoptions.md) cmdlet. | False | Named | False |
| ReadEntireRestorePoint | Defines that the cmdlet will process the most recent restore point instead of waiting for the current backup file to become available. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

This cmdlet returns the VBRComputerGFSOptions object that contains settings of GFS retention for Veeam Agent backup jobs.

Examples

Defining GFS Retention Policy for Veeam Agent Backup Jobs

This example shows how to define GFS retention settings for Veeam Agent backup jobs. The cmdlet will define the GFS retention with the following weekly, monthly and yearly settings:

* Weekly: every Wednesday, keep backups for 3 weeks.
* Monthly: every first week of the month, keep backups for 3 months.
* Yearly: every November, keep backups for 2 years.

|  |
| --- |
| $weekly = New-VBRComputerGFSWeeklyOptions -RetentionPeriod 3 -SelectedDay Wednesday  $monthly = New-VBRComputerGFSMonthlyOptions -RetentionPeriod 3 -SelectedWeek First  $yearly = New-VBRComputerGFSYearlyOptions -RetentionPeriod 2 -SelectedMonth November  New-VBRComputerGFSOptions -GFSWeeklyOptions $weekly -GFSMonthlyOptions $monthly -GFSYearlyOptions $yearly |

Perform the following steps:

1. Run the [New-VBRComputerGFSWeeklyOptions](new-vbrcomputergfsweeklyoptions.md) cmdlet. Specify the RetentionPeriod and the SelectedDay parameter values. Save the result to the $weekly variable.
2. Run the [New-VBRComputerGFSMonthlyOptions](new-vbrcomputergfsmonthlyoptions.md) cmdlet. Specify the RetentionPeriod and the SelectedWeek parameter values. Save the result to the $monthly variable.
3. Run the [New-VBRComputerGFSYearlyOptions](new-vbrcomputergfsyearlyoptions.md) cmdlet. Specify the RetentionPeriod and the SelectedMonth parameter values. Save the result to the $yearly variable.
4. Run the New-VBRComputerGFSOptions cmdlet. Specify the following settings:

* Set the $weekly variable as the GFSWeeklyOptions parameter value.
* Set the $monthly variable as the GFSMonthlyOptions parameter value.
* Set the $yearly variable as the GFSYearlyOptions parameter value.

Related Commands

* [New-VBRComputerGFSWeeklyOptions](new-vbrcomputergfsweeklyoptions.md)
* [New-VBRComputerGFSMonthlyOptions](new-vbrcomputergfsmonthlyoptions.md)
* [New-VBRComputerGFSYearlyOptions](new-vbrcomputergfsyearlyoptions.md)

Page updated 11/18/2025

Page content applies to build 13.0.1.1071
