---
title: "Set-VBRNASInstantRecoveryMigration"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrnasinstantrecoverymigration.html"
last_updated: "9/4/2024"
product_version: "13.0.1.1071"
---

# Set-VBRNASInstantRecoveryMigration


Short Description

Modifies switchover parameters for the specified session of migration to production during the instant file share recovery.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRNASInstantRecoveryMigration -InstantRecoveryMigration <VBRNASInstantRecoveryMigration> -SwitchOverOptions <VBRNASInstantRecoveryMigrationSwitchOverOptions>  [<CommonParameters>] |

Detailed Description

This cmdlet modifies switchover parameters for the specified session of migration to production during the instant file share recovery.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| InstantRecoveryMigration | Specifies an active session of migration to production during the instant file share recovery. | Accepts the VBRNASInstantRecoveryMigration object. To get this object, run the [Get-VBRNASInstantRecoveryMigration](get-vbrnasinstantrecoverymigration.md) cmdlet. | True | 0 | False |
| SwitchOverOptions | Defines new switchover options for the specified session of migration to production during the instant file share recovery. | Accepts the VBRNASInstantRecoveryMigrationSwitchOverOptions object. To create this object, run the [New-VBRNASInstantRecoveryMigrationSwitchOverOptions](new-vbrnasinstantrecoverymigrationswitchoveroptions.md) cmdlet. | True | 1 | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Setting New Switchover Options for Migration Session Instant Restore for File Backups

This example shows how to set new switchover options for migration session Instant Restore for file backups.

|  |
| --- |
| $nasInstantRecovery = Get-VBRNASInstantRecovery -Id "42696B53-6FEC-4148-9354-AA9E4B52DED9"  $migration = Get-VBRNASInstantRecoveryMigration -InstantRecovery $nasInstantRecovery  $switchover = New-VBRNASInstantRecoveryMigrationSwitchOverOptions -Scheduled -SwitchingTimeUtc "2020-11-24 13:00:00"  Set-VBRNASInstantRecoveryMigration -InstantRecoveryMigration $migration -SwitchOverOptions $switchover  Write-Output "Set new switchover for migration sessions of instant restore for file backups." |

Perform the following steps:

1. Run the [Get-VBRNASInstantRecovery](get-vbrnasinstantrecovery.md) cmdlet. Specify the Id parameter value. Save the result to the $nasInstantRecovery variable.
2. Run the [Get-VBRNASInstantRecoveryMigration](get-vbrnasinstantrecoverymigration.md) cmdlet. Set the $nasInstantRecovery variable as the InstantRecovery parameter value. Save the result to the $migration variable.
3. Run the [New-VBRNASInstantRecoveryMigrationSwitchOverOptions](new-vbrnasinstantrecoverymigrationswitchoveroptions.md) cmdlet. Provide the Scheduled parameter. Specify the SwitchingTimeUtc parameter value. Save the result to the $switchover variable.
4. Run the Set-VBRNASInstantRecoveryMigration cmdlet. Set the $migration variable as the InstantRecoveryMigration parameter value. Set the $switchover variable as the SwitchOverOptions parameter value.

Related Commands

* [Get-VBRNASInstantRecovery](get-vbrnasinstantrecovery.md)
* [Get-VBRNASInstantRecoveryMigration](get-vbrnasinstantrecoverymigration.md)
* [New-VBRNASInstantRecoveryMigrationSwitchOverOptions](new-vbrnasinstantrecoverymigrationswitchoveroptions.md)


