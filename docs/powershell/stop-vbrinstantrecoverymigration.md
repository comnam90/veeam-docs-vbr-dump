---
title: "Stop-VBRInstantRecoveryMigration"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/stop-vbrinstantrecoverymigration.html"
last_updated: "4/4/2024"
product_version: "13.0.1.1071"
---

# Stop-VBRInstantRecoveryMigration


Short Description

Stops running migration sessions launched during Instant Recovery.

Applies to

Platform: VMware

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Stop-VBRInstantRecoveryMigration -Migration <InstantRecoveryMigration[]> [-RunAsync]  [<CommonParameters>] |

Detailed Description

This cmdlet stops migration sessions launched during Instant Recovery (including Instant Recovery for first class disks, file shares and so on).

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Migration | Specifies an array of IDs of the migration sessions that you want to stop. | Accepts the InstantRecoveryMigration[] object. To create this object, run the [Get-VBRInstantRecoveryMigration](get-vbrinstantrecoverymigration.md) cmdlet. | True | 0 | True (ByValue, ByPropertyName) |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Stopping Migration Sessions Launched During Instant Recovery

This example shows how to stop a running migration session launched during Instant Recovery.

|  |
| --- |
| $session = Get-VBRInstantRecoveryMigration  Stop-VBRInstantRecoveryMigration -Migration $session[3] |

Perform the following steps:

1. Run the [Get-VBRInstantRecoveryMigration](get-vbrinstantrecoverymigration.md) cmdlet. Save the result to the $session variable.

The [Get-VBRInstantRecoveryMigration](get-vbrinstantrecoverymigration.md) cmdlet will return an array of migration sessions. Mind the ordinal number of the necessary migration session (in our example, it is the fourth migration session in the array).

1. Run the Stop-VBRInstantRecoveryMigration cmdlet. Set the $session[3] variable as the Migration parameter value.

Related Commands

[Get-VBRInstantRecoveryMigration](get-vbrinstantrecoverymigration.md)


