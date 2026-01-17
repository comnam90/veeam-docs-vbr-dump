---
title: "New-VESQLIRSwitchOverOptions"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/new-vesqlirswitchoveroptions.html"
last_updated: "3/12/2025"
product_version: "13.0.1.1071"
---


In this article

Short Description

Defines the switchover option that you can apply to the instant recovery session of a Microsoft SQL Server database.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Create a switchover option that starts the switchover immediately after database files are copied and synchronized.

|  |
| --- |
| New-VESQLIRSwitchOverOptions [-Auto] [<CommonParameters>] |

* Create a switchover option that allows you to start the switchover manually at any time after database files are copied and synchronized.

|  |
| --- |
| New-VESQLIRSwitchOverOptions [-Manual] [<CommonParameters>] |

* Create a switchover option that starts the switchover at a specified date and time.

|  |
| --- |
| New-VESQLIRSwitchOverOptions [-Scheduled] -SwitchingTimeUtc <DateTime> [<CommonParameters>] |

Detailed Description

This cmdlet creates the [VESQLIRSwitchOverOptions](vesqlirswitchoveroptions.md) object that defines a switchover option that you can apply to the instant recovery session of Microsoft SQL Server databases. You can use this option to create a switchover option and define a schedule for a scheduled switchover.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Auto | Defines that the switchover will be performed in the Auto mode. This option starts switchover immediately after database files are copied and synchronized. | SwitchParameter | True | Named | False |
| Manual | Defines that the switchover will be performed manually at a later time, using the Switch-VESQLIRDatabase cmdlet. | SwitchParameter | True | Named | False |
| Scheduled | Defines that the switchover will be performed in the Scheduled mode. Switchover will be performed at the specified date and time. | SwitchParameter | True | Named | False |
| SwitchingTimeUtc | For the scheduled switchover option.  Specifies the date and time in UTC when the switchover must be started. | DateTime | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VESQLIRSwitchOverOptions](vesqlirswitchoveroptions.md) object that contains a switchover option with the defined schedule.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Defining Scheduled Switchover Option

|  |  |
| --- | --- |
| This example shows how to define a scheduled switchover option. The switchover schedule is set to 2023-11-24 13:00:00.  |  | | --- | | $time = Get-Date -Date "2023-11-24 13:00:00"  $TimeUtc = $time.ToUniversalTime()  $ScheduledSwitch = New-VESQLIRSwitchOverOptions -Scheduled -SwitchingTimeUtc $TimeUtc |  Perform the following steps:   1. Run the [Get-Date](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/get-date?view=powershell-7.5) cmdlet and specify the date and time when the switchover must be performed. Save the result to the $time variable. 2. Convert the scheduled time to the UTC format using the ToUniversalTime() method. Save the result to the $TimeUtc variable. 3. Run the New-VESQLIRSwitchOverOptions cmdlet. Provide the Scheduled parameter. Set the $TimeUtc variable as the SwitchingTimeUtc parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Defining Automatic Switchover Option

|  |  |
| --- | --- |
| This command defines the auto switchover option. The switchover will run immediately after database files are copied and synchronized.  |  | | --- | | $AutomaticSwitch = New-VESQLIRSwitchOverOptions -Auto | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Defining Manual Switchover Option

|  |  |
| --- | --- |
| This command defines a manual switchover option. The switchover will run at any time after database files are copied and synchronized.  |  | | --- | | $ManualSwitch = New-VESQLIRSwitchOverOptions -Manual | |

Related Commands

* [Set-VESQLIRDatabase](set-vesqlirdatabase.md)
* [Restore-VESQLIRDatabase](restore-vesqlirdatabase.md)
* [Switch-VESQLIRDatabase](switch-vesqlirdatabase.md)

Page updated 3/12/2025

Page content applies to build 13.0.1.1071
