---
title: "Switch-VBRAzureInstantRecoveryMigration"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/switch-vbrazureinstantrecoverymigration.html"
last_updated: "8/1/2025"
product_version: "13.0.1.1071"
---

# Switch-VBRAzureInstantRecoveryMigration


Short Description

Starts the manual switchover for finalizing the migration to production process after you perform the Instant Recovery to Microsoft Azure.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Switch-VBRAzureInstantRecoveryMigration -InstantRecovery <VBRAzureInstantRecovery> [-RunAsync] [<CommonParameters>] |

Detailed Description

This cmdlet starts the manual switchover for finalizing the migration to production process after you perform the Instant Recovery to Microsoft Azure.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| InstantRecovery | Specifies the Instant Recovery operation for which the migration was started. | Accepts the VBRAzureInstantRecovery object. To get this object, run the [Start-VBRAzureInstantRecoveryMigration](start-vbrazureinstantrecoverymigration.md) cmdlet. | True | Named | True |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRAzureInstantRecovery](vbrazureinstantrecovery.md)

Examples

This example shows how to start the second phase of migration (switchover).

|  |
| --- |
| $switchingOptions = New-VBRAzureInstantRecoverySwitchingOptions -SwitchingType Manual  $session = Get-VBRAzureInstantRecovery -Id "d1d2a50e-8052-498f-826b-e5c86f30ed5a"  $migration = Start-VBRAzureInstantRecoveryMigration -InstantRecovery $session -SwitchingOptions $switchingOptions  Switch-VBRAzureInstantRecoveryMigration -InstantRecovery $migration |

Perform the following steps:

1. Run the [New-VBRAzureInstantRecoverySwitchingOptions](new-vbrazureinstantrecoveryswitchingoptions.md) cmdlet. Specify the SwitchingType parameter value. Save the result to the $switchingOptions variable.
2. Run the [Get-VBRAzureInstantRecovery](get-vbrazureinstantrecovery.md) cmdlet. Specify the Id parameter value. Save the result to the $session variable.
3. Run the [Start-VBRAzureInstantRecoveryMigration](start-vbrazureinstantrecoverymigration.md) cmdlet. Set the $session variable as the InstantRecovery parameter value. Set the $switchingOptions variable as the SwitchingOptions parameter value. Save the result to the $migration variable.
4. Run the Switch-VBRAzureInstantRecoveryMigration cmdlet. Set the $migration variable as the InstantRecovery parameter value.

Related Commands

* [New-VBRAzureInstantRecoverySwitchingOptions](new-vbrazureinstantrecoveryswitchingoptions.md)
* [Get-VBRAzureInstantRecovery](get-vbrazureinstantrecovery.md)
* [Start-VBRAzureInstantRecoveryMigration](start-vbrazureinstantrecoverymigration.md)


