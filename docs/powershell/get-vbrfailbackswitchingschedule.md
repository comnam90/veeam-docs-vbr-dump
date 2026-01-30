---
title: "Get-VBRFailbackSwitchingSchedule"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrfailbackswitchingschedule.html"
last_updated: "6/27/2024"
product_version: "13.0.1.1071"
---

# Get-VBRFailbackSwitchingSchedule


Short Description

Returns the failback switching schedule.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRFailbackSwitchingSchedule -Replica <VBRvCDReplica>  [<CommonParameters>] |

Detailed Description

This cmdlet returns the failback switching schedule.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Replica | Specifies a CDP replica for which you want to get failback switching schedule. | Accepts the VBRvCDReplica object. To create this object, run the [Get-VBRCDPReplica](get-vbrcdpreplica.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

This cmdlet defines the VBRFailbackSwitchingSchedule object that defines the failback switching schedule settings.

Examples

Getting Failback Switching Schedule

This example shows how to get failback switching replica schedule of the CDP replica of the Win05 VM.

|  |
| --- |
| $replica = Get-VBRCDPReplica -Name "Win05"  Get-VBRFailbackSwitchingSchedule -Replica $replica |

Perform the following steps:

1. Run the [Get-VBRCDPReplica](get-vbrcdpreplica.md) cmdlet. Specify the Name parameter value. Save the result to the $replica variable.
2. Run the Get-VBRFailbackSwitchingSchedule cmdlet. Set the $replica variable as the Replica parameter.

Related Commands

[Get-VBRCDPReplica](get-vbrcdpreplica.md)


