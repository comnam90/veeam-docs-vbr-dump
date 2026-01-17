---
title: "Set-VESQLIRDatabase"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/set-vesqlirdatabase.html"
last_updated: "12/20/2024"
product_version: "13.0.1.1071"
---


In this article

Short Description

Modifies switchover settings for a specified Microsoft SQL Server database.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VESQLIRDatabase [-Database] <VESQLIRDatabase> [-SwitchOverOptions] <VESQLIRSwitchOverOptions> [<CommonParameters>] |

Detailed Description

This cmdlet allows you to modify the switchover settings for a specified Microsoft SQL Server database.

|  |
| --- |
| Important |
| You can only modify the switchover settings until the moment switchover is automatically triggered (if the Auto or Scheduled switchover options are selected). |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Database | Specifies a published Microsoft SQL Server database within an instant recovery session. | Accepts the [VESQLIRDatabase](vesqlirdatabase.md) object. To get this object, run the [Get-VESQLIRDatabase](get-vesqlirdatabase.md) cmdlet. | True | 0 | True (ByValue) |
| SwitchOverOptions | Specified a new switchover option for the specified Microsoft SQL Server database. | Accepts the [VESQLIRSwitchOverOptions](vesqlirswitchoveroptions.md) object. To create this object, run the [New-VESQLIRSwitchOverOptions](new-vesqlirswitchoveroptions.md) cmdlet. | True | 1 | True (ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

None.

Example

Setting Scheduled Switchover for Microsoft SQL Server Database

This example shows how to set scheduled switchover for the fiscal database. The switchover will be performed on 2023-12-4 at 13:00:00.

|  |
| --- |
| $time = Get-Date -Date "2023-12-4 13:00:00"  $TimeUtc = $time.ToUniversalTime()  $ScheduledSwitch = New-VESQLIRSwitchOverOptions -Scheduled -SwitchingTimeUtc $TimeUtc  $IRDatabase = Get-VESQLIRDatabase -DatabaseName "fiscal"  Set-VESQLIRDatabase -Database $IRDatabase -SwitchOverOptions $ScheduledSwitch |

Perform the following steps:

1. Run the [Get-Date](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/get-date?view=powershell-7.5) cmdlet and specify the date and time when the switchover must be performed. Save the result to the $time variable.
2. Use the ToUniversalTime() method to convert the date and time to the UTC format. Save the result to the $TimeUTC variable.
3. Run the [New-VESQLIRSwitchoverOptions](new-vesqlirswitchoveroptions.md) cmdlet. Provide the Scheduled parameter. Set the $TimeUTC variable as the SwitchingTimeUtc parameter value. Save the result to the $ScheduledSwitch variable.
4. Run the [Get-VESQLIRDatabase](get-vesqlirdatabase.md) cmdlet. Specify the DatabaseName parameter value. Save the result to the $IRDatabase variable.
5. Run the Set-VESQLIRDatabase cmdlet. Specify the following options:

* Set the $IRDatabase variable as the Database parameter value.
* Set the $ScheduledSwitch variable as the SwitchOverOptions parameter value.

Related Commands

* [New-VESQLIRSwitchOverOptions](new-vesqlirswitchoveroptions.md)
* [Get-VESQLIRDatabase](get-vesqlirdatabase.md)

Page updated 12/20/2024

Page content applies to build 13.0.1.1071
