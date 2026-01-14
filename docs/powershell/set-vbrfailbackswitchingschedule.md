---
title: "Set-VBRFailbackSwitchingSchedule"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrfailbackswitchingschedule.html"
last_updated: "6/27/2024"
product_version: "13.0.1.1071"
---

# Set-VBRFailbackSwitchingSchedule

In this article

Short Description

Modifies the failback switching schedule.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRFailbackSwitchingSchedule -SwitchingSchedule <VBRFailbackSwitchingSchedule> -Replica <VBRvCDReplica>  [<CommonParameters>] |

Detailed Description

This cmdlet modifies the failback switching schedule.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| SwitchingSchedule | Specifies the failback switching schedule that you want to modify. | Accepts the VBRFailbackSwitchingSchedule object. To create this object, run the [Get-VBRFailbackSwitchingSchedule](get-vbrfailbackswitchingschedule.md) cmdlet. | True | Named | True (ByValue, ByPropertyName |
| Replica | Specifies a CDP replica that failback switching schedule you want to modify. | Accepts the VBRvCDReplica object. To create this object, run the [Get-VBRCDPReplica](get-vbrcdpreplica.md) cmdlet. | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

This cmdlet defines the VBRFailbackSwitchingSchedule object that defines the failback switching schedule settings.

Examples

Getting Failback Switching Schedule

This example shows how to get failback switching schedule of the CDP replica of the Win05 VM.

|  |
| --- |
| $replica = Get-VBRCDPReplica -Name "Win05"  $schedule = Get-VBRFailbackSwitchingSchedule -Replica $replica  Set-VBRFailbackSwitchingSchedule -SwitchingSchedule $schedule -Replica $replica |

Perform the following steps:

1. Run the [Get-VBRCDPReplica](get-vbrcdpreplica.md) cmdlet. Specify the Name parameter value. Save the result to the $replica variable.
2. Run the [Get-VBRFailbackSwitchingSchedule](get-vbrfailbackswitchingschedule.md) cmdlet. Set the $replica variable as the Replica parameter value. Save the result to the $schedule variable.
3. Run the Set-VBRFailbackSwitchingSchedule cmdlet. Set the $schedule variable as the SwitchingSchedule parameter value. Set the $replica variable as the Replica parameter value.

Related Commands

* [Get-VBRCDPReplica](get-vbrcdpreplica.md)
* [Get-VBRFailbackSwitchingSchedule](get-vbrfailbackswitchingschedule.md)

Page updated 6/27/2024

Page content applies to build 13.0.1.1071
