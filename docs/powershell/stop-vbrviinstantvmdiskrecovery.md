---
title: "Stop-VBRViInstantVMDiskRecovery"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/stop-vbrviinstantvmdiskrecovery.html"
last_updated: "3/1/2024"
product_version: "13.0.1.1071"
---

# Stop-VBRViInstantVMDiskRecovery


Short Description

Stops restore of VM virtual disks.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Stop-VBRViInstantVMDiskRecovery -InstantRecovery <InstantRecovery> [-Force] [-RunAsync]  [<CommonParameters>] |

Detailed Description

This cmdlet stops restore of VM virtual disks.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| InstantRecovery | Specifies a session that is running to restore VM virtual disks. The cmdlet will stop this session. | Accepts the InstantRecovery object. To get this object, run the [Get-VBRInstantRecovery](get-vbrinstantrecovery.md) cmdlet. | True | 0 | True (ByValue, ByPropertyName) |
| Force | Defines that the cmdlet will run without warning. | SwitchParameter | False | Named | False |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

Stopping Restore of VM Virtual Disks

This example shows how to stop a session that is running to restore VM virtual disks.

|  |
| --- |
| $session = Get-VBRInstantRecovery  Stop-VBRViInstantVMDiskRecovery -InstantRecovery $session |

Perform the following steps:

1. Run the [Get-VBRInstantRecovery](get-vbrinstantrecovery.md) cmdlet. Save the result to the $session variable.
2. Run the Stop-VBRViInstantVMDiskRecovery cmdlet. Set the $session variable as the InstantRecovery parameter value.

Related Commands

[Get-VBRInstantRecovery](get-vbrinstantrecovery.md)


