---
title: "Set-VEORIRDatabase"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/set-veorirdatabase.html"
last_updated: "1/28/2025"
product_version: "13.0.1.1071"
---


In this article

Short Description

Changes switchover settings of an instant recovery session for an Oracle database.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VEORIRDatabase [-Database] <VEORIRDatabase> [-SwitchOverOptions <VEORIRSchedule>] [<CommonParameters>] |

Detailed Description

This cmdlet allows you to change the switchover option for a specified Oracle database.

|  |
| --- |
| Important |
| You can only modify the switchover settings until the moment switchover is automatically triggered (if the Auto or Scheduled switchover options are selected). |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Database | Specifies an Oracle database published within an instant recovery session. | Accepts the [VEORIRDatabase](veorirdatabase.md) object. To get this object, run the [Get-VEORIRDatabase](get-veorirdatabase.md) cmdlet. | True | 0 | True (ByValue) |
| SwitchOverOptions | Specified a switchover option for the necessary Oracle database. | Accepts the [VEORIRSchedule](veorirschedule.md) object. To create this object, run the [New-VEORIRSwitchOverOptions](new-veorirswitchoveroptions.md) cmdlet. | True | 1 | True (ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

None.

Example

Setting Scheduled Switchover of Oracle Database

This example shows how to set the scheduled switchover for the orcl database. The cmdlet will perform the switchover at 13:00:00 on 2023-11-24.

|  |
| --- |
| $time = Get-Date -Date "2023-12-4 13:00:00"  $TimeUtc = $time.ToUniversalTime()  $ScheduledSwitch = New-VEORIRSwitchOverOptions -Scheduled -SwitchingTimeUtc $TimeUtc  $IRDatabase = Get-VEORIRDatabase -DatabaseName "orcl"  Set-VEORIRDatabase -Database $IRDatabase -SwitchOverOptions $ScheduledSwitch |

Perform the following steps:

1. Run the [Get-Date](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/get-date?view=powershell-7.5) cmdlet and specify the date and time when the switchover must be performed. Save the result to the $time variable.
2. Use the ToUniversalTime() method to convert the date and time to the UTC format.
3. Run the [New-VEORIRSwitchOverOptions](new-veorirswitchoveroptions.md) cmdlet. Provide the Scheduled parameter. Set the $TimeUtc variable as the SwitchingTimeUtc parameter value. Save the result to the $ScheduledSwitch variable.
4. Run the [Get-VEORIRDatabase](get-veorirdatabase.md) cmdlet. Specify the DatabaseName parameter value. Save the result to the $IRDatabase variable.
5. Run the Set-VEORIRDatabase cmdlet. Specify the following options:

* Set the $IRDatabase variable as the Database parameter value.
* Specify the $ScheduledSwitch variable as the SwitchOverOptions parameter value.

Related Commands

* [Get-Date](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/get-date?view=powershell-7.5)
* [New-VEORIRSwitchOverOptions](new-veorirswitchoveroptions.md)
* [Get-VEORIRDatabase](get-veorirdatabase.md)

Page updated 1/28/2025

Page content applies to build 13.0.1.1071
