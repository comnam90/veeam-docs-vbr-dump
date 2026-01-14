---
title: "New-VBRPeriodicallyOptions"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrperiodicallyoptions.html"
last_updated: "5/3/2024"
product_version: "13.0.1.1071"
---

# New-VBRPeriodicallyOptions

In this article

Short Description

Creates periodical schedule settings.

Applies to

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRPeriodicallyOptions [-PeriodicallyKind <VBRPeriodicallyKinds> {Hours | Minutes | Continuously}] [-FullPeriod <int>] [-PeriodicallySchedule <VBRBackupWindowOptions>] [-HourlyOffset <int>]  [<CommonParameters>] |

Detailed Description

This cmdlet creates an object containing periodical schedule settings. You can use this object to create a discovery schedule for a protection group. Veeam Backup & Replication performs a discovery operation according to this schedule: connects to computers of a selected protection group and gathers information about them.

To create a discovery schedule, run the [New-VBRProtectionGroupScheduleOptions](new-vbrprotectiongroupscheduleoptions.md) cmdlet.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| PeriodicallyKind | Specifies the type of periodical schedule settings:   * Hours: Veeam Backup & Replication will perform discovery operations repeatedly in specified number of hours (for example, every 6 hours). * Minutes: Veeam Backup & Replication will perform discovery operations repeatedly in specified number of minutes (for example, every 30 minutes). * Continuously: Veeam Backup & Replication will discover new computers in a non-stop manner. | VBRPeriodicallyKinds | False | Named | True (ByValue, ByProperty Name) |
| FullPeriod | Specifies the number of hours or minutes for the PeriodicallyKind parameter.  Permitted values:   * For Hours: 1, 2, 3, 4, 6, 8, 12, 24. * For Minutes: 1-999. | Int | False | Named | True (ByProperty Name) |
| PeriodicallySchedule | Specifies the discovery window. The cmdlet sets the time period within which Veeam Backup & Replication is allowed to perform discovery operations for computers of a protection group. | Accepts the VBRBackupWindowOptions object. To get this object, run the [New-VBRBackupWindowOptions](new-vbrbackupwindowoptions.md) cmdlet. | False | Named | True (ByProperty Name) |
| HourlyOffset | Used for adjusting the discover window start time.  Specifies the number of minutes (1-59). Discovery operations will start at the hour set in the discovery window plus the indicated period (for example, at 8:30). | Int | False | Named | True (ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRPeriodicallyOptions](vbrperiodicallyoptions.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Creating Periodical Schedule Settings

|  |  |
| --- | --- |
| This command creates an object containing periodical schedule settings.  |  | | --- | | New-VBRPeriodicallyOptions -FullPeriod 12 -PeriodicallyKind Hours | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Creating Discovery Schedule for Protection Group

|  |  |
| --- | --- |
| This example shows how to create a discovery schedule for a protection group. Per this schedule, Veeam Backup & Replication will perform new computer discovery every 12 hours.  |  | | --- | | $periodically = New-VBRPeriodicallyOptions -FullPeriod 12 -PeriodicallyKind Hours  New-VBRProtectionGroupScheduleOptions -PolicyType Periodically -PeriodicallyOptions $periodically |  Perform the following steps:   1. Run the New-VBRPeriodicallyOptions cmdlet. Set the 12 value as the FullPeriod parameter value. Set the Hours value as the PeriodicallyKind parameter value. Save the result to the $periodically variable. 2. Run the [New-VBRProtectionGroupScheduleOptions](new-vbrprotectiongroupscheduleoptions.md) cmdlet. Set the Periodically option for the PolicyType parameter. Set the $periodically variable as the PeriodicallyOptions parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Applying Discovery Schedule to Protection Group

|  |  |
| --- | --- |
| This example shows how to apply a discovery schedule to a protection group. Per this schedule, Veeam Backup & Replication will perform new computer discovery every 12 hours.  |  | | --- | | $periodically = New-VBRPeriodicallyOptions -FullPeriod 12 -PeriodicallyKind Hours  $schedule = New-VBRProtectionGroupScheduleOptions -PolicyType Periodically -PeriodicallyOptions $periodically  $group = Get-VBRProtectionGroup -Name "East Computers"  Set-VBRProtectionGroup -ProtectionGroup $group -ScheduleOptions $schedule |  Perform the following steps:   1. Run the New-VBRPeriodicallyOptions cmdlet. Set the 12 value as the FullPeriod parameter value. Set the Hours value as the PeriodicallyKind parameter value. Save the result to the $periodically variable. 2. Run the [New-VBRProtectionGroupScheduleOptions](new-vbrprotectiongroupscheduleoptions.md) cmdlet. Set the Periodically option for the PolicyType parameter. Set the $periodically variable as the PeriodicallyOptions parameter value. Save the result to the $schedule variable. 3. Apply a discovery schedule to a protection group:  * Run the [Get-VBRProtectionGroup](get-vbrprotectiongroup.md) cmdlet. Specify the Name parameter value. Save the result to the $group variable. * Run the [Set-VBRProtectionGroup](set-vbrprotectiongroup.md) cmdlet. Set the $group variable as the ProtectionGroup parameter value. Set the $schedule variable as the ScheduleOptions parameter value. |

Related Commands

* [New-VBRProtectionGroupScheduleOptions](new-vbrprotectiongroupscheduleoptions.md)
* [Get-VBRProtectionGroup](get-vbrprotectiongroup.md)
* [Set-VBRProtectionGroup](set-vbrprotectiongroup.md)

Page updated 5/3/2024

Page content applies to build 13.0.1.1071
