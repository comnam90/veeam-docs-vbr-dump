---
title: "set-vepsqlinstanceinstantrecovery"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/set-vepsqlinstanceinstantrecovery.html"
last_updated: "4/4/2025"
product_version: "13.0.1.1071"
---


In this article

Short Description

Modifies switchover settings for a specified PostgreSQL instance.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VEPSQLInstanceInstantRecovery [-Instance] <VEPSQLInstanceInstantRecovery> [-SwitchOverOptions] <VEPSQLIRSwitchOverOptions> [<CommonParameters>] |

Detailed Description

This cmdlet allows you to modify the switchover settings for a specified PostgreSQL instance.

|  |
| --- |
| Important |
| You can only modify the switchover settings until the moment switchover is automatically triggered (if the Auto or Scheduled switchover options are selected). |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Instance | Specifies a published PostgreSQL instance within an instant recovery session. | Accepts the [VEPSQLInstanceInstantRecovery](vepsqlinstanceinstantrecovery.md) object. To get this object, run the [Get-VEPSQLInstanceInstantRecovery](get-vepsqlinstanceinstantrecovery.md) cmdlet. | True | 0 | True (ByValue) |
| SwitchOverOptions | Specifies a new switchover option for the specified PostgreSQL instance. | Accepts the [VEPSQLIRSwitchOverOptions](vepsqlirswitchoveroptions.md) object. To create this object, run the [New-VEPSQLIRSwitchOverOptions](new-vepsqlirswitchoveroptions.md) cmdlet. | True | 1 | True (ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

None.

Example

Setting Scheduled Switchover for PostgreSQL Instance

This example shows how to modify the scheduled switchover for the rhel01:5433 instance. The switchover will be performed in the Scheduled mode — on 2023-7-24 at 13:00:00 in the time zone of the backup server.

|  |
| --- |
| $time = Get-Date -Date "2023-7-24 13:00:00"  $TimeUtc = $time.ToUniversalTime()  $ScheduledSwitch = New-VEPSQLIRSwitchOverOptions -Scheduled -SwitchingTimeUtc $TimeUtc  $IRInstance = Get-VEPSQLInstanceInstantRecovery -InstanceName "rhel01:5433"  Set-VEPSQLInstanceInstantRecovery -Instance $IRInstance -SwitchOverOptions $ScheduledSwitch |

Perform the following steps:

1. Run the [Get-Date](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/get-date?view=powershell-7.5) cmdlet and specify the date and time when the switchover must be performed. Save the result to the $time variable.
2. Use the ToUniversalTime() method to convert the date and time to the UTC format. Save the result to the $TimeUtc variable.
3. Run the [New-VEPSQLIRSwitchoverOptions](new-vepsqlirswitchoveroptions.md) cmdlet. Provide the Scheduled parameter. Set the $TimeUtc variable as the SwitchingTimeUtc parameter value. Save the result to the $ScheduledSwitch variable.
4. Run the [Get-VEPSQLInstanceInstantRecovery](get-vepsqlinstanceinstantrecovery.md) cmdlet. Specify the InstanceName parameter value. Save the result to the $IRInstance variable.
5. Run the Set-VEPSQLInstanceInstantRecovery cmdlet. Set the $IRInstance as the Instance parameter value. Set the $ScheduledSwitch variable as the SwitchOverOptions parameter value.

Related Commands

* [New-VEPSQLIRSwitchOverOptions](new-vepsqlirswitchoveroptions.md)
* [Get-VEPSQLInstanceInstantRecovery](get-vepsqlinstanceinstantrecovery.md)
* [Get-Date](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/get-date?view=powershell-7.5)

Page updated 4/4/2025

Page content applies to build 13.0.1.1071
