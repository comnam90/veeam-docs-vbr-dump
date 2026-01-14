---
title: "New-VBRProtectionGroupScheduleOptions"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrprotectiongroupscheduleoptions.html"
last_updated: "5/3/2024"
product_version: "13.0.1.1071"
---

# New-VBRProtectionGroupScheduleOptions

In this article

Short Description

Creates a discovery schedule.

Applies to

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRProtectionGroupScheduleOptions [-PolicyType <VBRProtectionGroupPolicyType> {Daily | Periodically}] [-DailyOptions <VBRDailyOptions>] [-PeriodicallyOptions <VBRPeriodicallyOptions>]  [<CommonParameters>] |

Detailed Description

This cmdlet creates the [VBRProtectionGroupScheduleOptions](vbrprotectiongroupscheduleoptions.md) object representing a discovery schedule for a protection group. Per this schedule, Veeam Backup & Replication performs a discovery operation: connects to computers of a selected protection group and gathers information about them. After the discovery operation is complete, processed computers are recognized by Veeam Backup & Replication as discovered.

Run the [Set-VBRProtectionGroup](set-vbrprotectiongroup.md) cmdlet to apply a discovery schedule to a protection group.

Run the [Rescan-VBREntity](rescan-vbrentity.md) cmdlet to discover computers manually.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| PolicyType | Specifies the type of the discovery schedule:   * Daily * Periodically   The cmdlet will create the discovery schedule of this type. | VBRProtectionGroupPolicyType | False | Named | True (ByValue, ByProperty Name) |
| DailyOptions | For daily schedule.  Specifies daily schedule settings. The cmdlet will create the discovery schedule with these settings. | Accepts the [VBRDailyOptions](vbrdailyoptions.md) object. To create this object, run the [New-VBRDailyOptions](new-vbrdailyoptions.md) cmdlet. | False | Named | True (ByProperty Name) |
| PeriodicallyOptions | For periodical schedule.  Specifies periodical schedule settings. The cmdlet will create the discovery schedule with these settings. | Accepts the [VBRPeriodicallyOptions](vbrperiodicallyoptions.md) object. To create this object, run the [New-VBRPeriodicallyOptions](new-vbrperiodicallyoptions.md) cmdlet. | False | Named | True (ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRProtectionGroupScheduleOptions](vbrprotectiongroupscheduleoptions.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Creating Discovery Schedule for Protection Group

|  |  |
| --- | --- |
| This example shows how to create a discovery schedule for a protection group. Per this schedule, Veeam Backup & Replication will perform discovery operations every Friday at 5 PM.  |  | | --- | | $daily = New-VBRDailyOptions -DayofWeek Friday -Period 17:00  New-VBRProtectionGroupScheduleOptions -PolicyType Daily -DailyOptions $daily |  Perform the following steps:   1. Run the [New-VBRDailyOptions](new-vbrdailyoptions.md) cmdlet. Set the Friday option for the DayofWeek parameter. Specify the Period parameter value. Save the result to the $daily variable. 2. Run the New-VBRProtectionGroupScheduleOptions cmdlet. Set the Daily option for the PolicyType parameter. Set the $daily variable as the DailyOptions parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Applying Discovery Schedule to Protection Group

|  |  |
| --- | --- |
| This example shows how to apply a discovery schedule to a protection group. Per this schedule, Veeam Backup & Replication will perform discovery operations every Friday at 5 PM.  |  | | --- | | $daily = New-VBRDailyOptions -DayOfWeek Friday -Period 17:00  $schedule = New-VBRProtectionGroupScheduleOptions -PolicyType Daily -DailyOptions $daily  $group = Get-VBRProtectionGroup -Name "North Computers"  Set-VBRProtectionGroup -ProtectionGroup $group -ScheduleOptions $schedule |  Perform the following steps:   1. Run the [New-VBRDailyOptions](new-vbrdailyoptions.md) cmdlet. Set the Friday option for the DayofWeek parameter. Specify the Period parameter value. Save the result to the $daily variable. 2. Run the New-VBRProtectionGroupScheduleOptions cmdlet. Set the Daily option for the PolicyType parameter. Set the $daily variable as the DailyOptions parameter value. Save the result to the $schedule variable. 3. Run the [Get-VBRProtectionGroup](get-vbrprotectiongroup.md) cmdlet. Specify the Name parameter value. Save the result to the $group variable. 4. Run the [Set-VBRProtectionGroup](set-vbrprotectiongroup.md) cmdlet. Set the $group variable as the ProtectionGroup parameter value. Set the $schedule variable as the ScheduleOptions parameter value. |

Related Commands

* [New-VBRDailyOptions](new-vbrdailyoptions.md)
* [Get-VBRProtectionGroup](get-vbrprotectiongroup.md)
* [Set-VBRProtectionGroup](set-vbrprotectiongroup.md)

Page updated 5/3/2024

Page content applies to build 13.0.1.1071
