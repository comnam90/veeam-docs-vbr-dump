---
title: "New-VBRAzureInstantRecoverySwitchingOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrazureinstantrecoveryswitchingoptions.html"
last_updated: "7/31/2025"
product_version: "13.0.1.1071"
---

# New-VBRAzureInstantRecoverySwitchingOptions


Short Description

Defines the switchover options.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRAzureInstantRecoverySwitchingOptions -SwitchingType {Auto | Manual | Scheduled} [-ScheduleTime <datetime>] [-VerifyVMBoot] [-PowerOnVm] [<CommonParameters>] |

Detailed Description

This cmdlet defines the switchover options. Switchover can be performed automatically, manually or at the specified date and time.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| SwitchingType | Specifies the type of switchover:   * Auto: use this option to start the switchover process (the second phase of migration) automatically right after the first phase of migration finishes. * Manual: use this option to start the switchover process manually.   To start the switchover manually, use the [Switch-VBRAzureInstantRecoveryMigration](switch-vbrazureinstantrecoverymigration.md) cmdlet.   * Scheduled: use this option to start the switchover process at the specified date and time. To specify the time, use the ScheduleTime parameter. | VBRAzureInstantRecoverySwitchingType | True | Named | True |
| ScheduleTime | For the SwitchingType parameter set to Scheduled.  Specifies the date and time when you want to perform the switchover. | DateTime | False | Named | False |
| VerifyVMBoot | Defines that Veeam Backup & Replication checks if the recovered workload boots successfully.  Default: False. | SwitchParameter | False | Named | False |
| PowerOnVm | Defines that the cmdlet powers on the recovered workload after the switchover.  Default: True. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRAzureInstantRecoverySwitchingOptions](vbrazureinstantrecoveryswitchingoptions.md)

Examples

This command shows how to create switchover options. The switchover will be performed manually, after the switchover the VM will be powered on.

|  |
| --- |
| $switchingOptions = New-VBRAzureInstantRecoverySwitchingOptions -SwitchingType Manual -PowerOnVm |


