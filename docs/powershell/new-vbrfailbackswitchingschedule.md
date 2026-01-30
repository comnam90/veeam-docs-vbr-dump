---
title: "New-VBRFailbackSwitchingSchedule"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrfailbackswitchingschedule.html"
last_updated: "6/27/2024"
product_version: "13.0.1.1071"
---

# New-VBRFailbackSwitchingSchedule


Short Description

Defines the failback switching schedule.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRFailbackSwitchingSchedule [-Type <VBRFailbackSwitchingType> {Manual | Auto | Scheduled}] [-ScheduledTime <datetime>]  [<CommonParameters>] |

Detailed Description

This cmdlet defines the VBRFailbackSwitchingSchedule object. This object defines when the switch from replicas to production VMs must be performed.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Type | Specifies a type of the failback schedule. You can set one of the following types:   * Manual: Use this option if you want to switch CDP replica to production VMs manually once CDP replicas are ready. * Auto: Use this option if you want to switch CDP replica to production VMs automatically once CDP replicas are ready. * Scheduled: Use this option if you want to switch CDP replica to production VMs according to a specific schedule. | VBRFailbackSwitchingType | False | Named | False |
| ScheduledTime | For the scheduled type of the failback.  Specifies the date and time when Veeam Backup & Replication must perform failback from a CDP replica Vm to a production VM. | DateTime | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

This cmdlet defines the VBRFailbackSwitchingSchedule object that defines the failback schedule settings.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Defining Manual Failback Schedule

|  |  |
| --- | --- |
| This command defines the manual failback schedule.  |  | | --- | | New-VBRFailbackSwitchingSchedule -Type Manual | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Defining Auto Failback Schedule

|  |  |
| --- | --- |
| This command defines the auto failback schedule.  |  | | --- | | New-VBRFailbackSwitchingSchedule -Type Auto | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Defining Sheduled Failback

|  |  |
| --- | --- |
| This command schedules the failback to run at 9.05.54 AM.  |  | | --- | | $date = Get-Date  -Year 2021 -Month 6 -Day 2 -Hour 9 -Minute 05 -Second 54  New-VBRFailbackSwitchingSchedule -Type Scheduled -ScheduledTime $date |  Perform the following steps:   1. Run the [Get-Date](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/get-date?view=powershell-7.1) cmdlet. Specify the Year, Month, Day, Hour, Minute and Second parameter values. Save the result to the $date variable. 2. Run the New-VBRFailbackSwitchingSchedule cmdlet. Specify the Type parameter value. Set the $date variable as the ScheduledTime parameter value. |

Related Commands

[Get-Date](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/get-date?view=powershell-7.1)


