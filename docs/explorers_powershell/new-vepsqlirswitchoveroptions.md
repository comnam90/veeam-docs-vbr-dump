---
title: "New-VEPSQLIRSwitchOverOptions"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/new-vepsqlirswitchoveroptions.html"
last_updated: "3/12/2025"
product_version: "13.0.1.1071"
---


In this article

Short Description

Defines the switchover option that you can apply to the instant recovery session of a PostgreSQL instance.

Applies to

Veeam Backup & Replication

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Create a switchover option that starts the switchover immediately after database files are copied and synchronized.

|  |
| --- |
| New-VEPSQLIRSwitchOverOptions [-Auto] [<CommonParameters>] |

* Create a switchover option that allows you to start the switchover manually at any time after database files are copied and synchronized.

|  |
| --- |
| New-VEPSQLIRSwitchOverOptions [-Manual] [<CommonParameters>] |

* Create a switchover option that starts the switchover at a specified date and time.

|  |
| --- |
| New-VEPSQLIRSwitchOverOptions [-Scheduled] -SwitchingTimeUtc <DateTime> [<CommonParameters>] |

Detailed Description

This cmdlet creates a switchover option that you can use in the instant recovery session of a PostgreSQL instance. You can use it to create a switchover option and define a schedule for a scheduled switchover.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Auto | Defines that the switchover will be performed in the Auto mode. This option starts switchover immediately after database files are copied and synchronized. | SwitchParameter | True | Named | False |
| Manual | Defines that the switchover will be performed manually at a later time, using the [Switch-VEPSQLInstanceInstantRecovery](switch-vepsqlinstanceinstantrecovery.md) cmdlet. | SwitchParameter | True | Named | False |
| Scheduled | Defines that the switchover will be performed in the Scheduled mode. Switchover will be performed at the specified date and time. | SwitchParameter | True | Named | False |
| SwitchingTimeUtc | For the scheduled switchover option.  Specifies the date and time in UTC when the switchover must be started. | DateTime | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VEPSQLIRSwitchOverOptions](vepsqlirswitchoveroptions.md) object that contains a switchover option with the defined schedule.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Creating Scheduled Switchover Option

|  |  |
| --- | --- |
| This example shows how to create a scheduled switchover option.  |  | | --- | | $time = Get-Date -Date "2023-7-24 13:00:00"  $TimeUtc = $time.ToUniversalTime()  $ScheduledSwitch = New-VEPSQLIRSwitchOverOptions -Scheduled -SwitchingTimeUtc $TimeUtc |  Perform the following steps:   1. Run the [Get-Date](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/get-date?view=powershell-7.5) cmdlet and specify the date and time when the switchover must be performed. Save the result to the $time variable. 2. Convert the scheduled time to the UTC format using the ToUniversalTime() method. Save the result to the $TimeUtc variable. 3. Run the New-VEPSQLIRSwitchOverOptions cmdlet. Provide the Scheduled parameter. Set the $TimeUtc variable as the SwitchingTimeUtc parameter value. Save the result to the $ScheduledSwitch variable to use it with other cmdlets. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Defining Auto Switchover Option

|  |  |
| --- | --- |
| This command defines an auto switchover option. The switchover will run immediately after database files are copied and synchronized.  |  | | --- | | $AutoSwitch = New-VEPSQLIRSwitchOverOptions -Auto | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Defining Manual Switchover Option

|  |  |
| --- | --- |
| This command defines a manual switchover option. The switchover will start after you initiate this process manually with the [Switch-VEPSQLInstanceInstantRecovery](switch-vepsqlinstanceinstantrecovery.md) cmdlet.  |  | | --- | | $ManualSwitch = New-VEPSQLIRSwitchOverOptions -Manual | |

Related Commands

* [Set-VEPSQLInstanceInstantRecovery](set-vepsqlinstanceinstantrecovery.md)
* [Start-VEPSQLInstanceInstantRecovery](start-vepsqlinstanceinstantrecovery.md)
* [Switch-VEPSQLInstanceInstantRecovery](switch-vepsqlinstanceinstantrecovery.md)
* [Get-Date](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/get-date?view=powershell-7.5)

Page updated 3/12/2025

Page content applies to build 13.0.1.1071
