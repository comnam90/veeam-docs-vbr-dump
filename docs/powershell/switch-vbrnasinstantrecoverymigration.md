---
title: "Switch-VBRNASInstantRecoveryMigration"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/switch-vbrnasinstantrecoverymigration.html"
last_updated: "9/4/2024"
product_version: "13.0.1.1071"
---

# Switch-VBRNASInstantRecoveryMigration


Short Description

Starts the manual switchover for completing the migration to production after you perform the instant file share recovery.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Switch-VBRNASInstantRecoveryMigration -InstantRecoveryMigration <VBRNASInstantRecoveryMigration>  [<CommonParameters>] |

Detailed Description

This cmdlet starts the manual switchover for completing the migration to production after you perform the instant file share recovery.

During migration to production, Veeam Backup & Replication moves to the production site not only content of the initial file share, but also incremental changes made by users in the mounted file share. When incremental changes are being moved, the mounted share is not available to users. This stage is called a switchover. The switchover may take some time, so ensure you properly plan when it is performed.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| InstantRecoveryMigration | Specifies an instant recovery migration session. | Accepts the VBRNASInstantRecoveryMigration object. To get this object, run the [Get-VBRNASInstantRecoveryMigration](get-vbrnasinstantrecoverymigration.md) cmdlet. | True | 0 | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Starting Manual Switchover

This example shows how to define settings for performing a switchover in the scheduled mode.

|  |
| --- |
| $nasInstantRecovery = Get-VBRNASInstantRecovery -Id "42696B53-6FEC-4148-9354-AA9E4B52DED9"  $migration = Get-VBRNASInstantRecoveryMigration -InstantRecovery $nasInstantRecovery  Write-Output "Start manual switchover for migration sessions of instant restore for file backups."  Switch-VBRNASInstantRecoveryMigration -InstantRecoveryMigration $migration |

Perform the following steps:

1. Run the [Get-VBRNASInstantRecovery](get-vbrnasinstantrecovery.md) cmdlet. Specify the Id parameter value. Save the result to the $nasInstantRecovery variable.
2. Run the [Get-VBRNASInstantRecoveryMigration](get-vbrnasinstantrecoverymigration.md) cmdlet. Set the $nasInstantRecovery variable as the InstantRecovery parameter value. Save the result to the $migration variable.
3. Run the Write-Output cmdlet. Specify the output wording.
4. Run the Switch-VBRNASInstantRecoveryMigration cmdlet. Set the $migration variable as the InstantRecoveryMigration parameter value.

Related Commands

[Get-VBRNASInstantRecoveryMigration](get-vbrnasinstantrecoverymigration.md)


