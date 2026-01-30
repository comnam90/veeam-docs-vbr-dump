---
title: "Get-VBRInstantRecoveryMigration"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrinstantrecoverymigration.html"
last_updated: "4/4/2024"
product_version: "13.0.1.1071"
---

# Get-VBRInstantRecoveryMigration


Short Description

Returns running migration sessions launched during Instant Recovery.

Applies to

Platform: VMware

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRInstantRecoveryMigration [-Id <guid[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns migration sessions launched during Instant Recovery (including Instant Recovery for first class disks, file shares and so on) and running at the moment.

If you do not specify cmdlet parameters, the cmdlet will return all running migration sessions launched during Instant Recovery.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Id | Specifies IDs of migration sessions that you want to return.  Tip: You can find the session ID in an object returned by the cmdlet that launched the migration session. | Guid[] | False | Named | True (ByPropertyName) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the InstantRecoveryMigration[] object that defines settings of migration sessions.

Examples

Getting Migration Sessions for NAS Instant Recovery

This example shows how to get the migration session.

|  |
| --- |
| $nasInstantRecovery = Get-VBRNASInstantRecovery -Id "49664A5F-9C55-4A1F-8E6A-1CD5705A684B"  $session = Start-VBRNASInstantRecoveryMigration -InstantRecovery $nasInstantRecovery  $migrationsession = Get-VBRInstantRecoveryMigration -Id $session.Id |

Perform the following steps:

1. Run the [Get-VBRNASInstantRecovery](get-vbrnasinstantrecovery.md) cmdlet. Specify the Id parameter value. Save the result to the $nasInstantRecovery variable.
2. Run the [Start-VBRNASInstantRecoveryMigration](start-vbrnasinstantrecoverymigration.md) cmdlet. Set the $nasInstantRecovery variable as the InstantRecovery parameter value. Save the result to the $session variable.
3. Run the Get-VBRInstantRecoveryMigration cmdlet. Set the Id property of the $session variable as the Id parameter value. Save the result to the $migrationsession variable.


