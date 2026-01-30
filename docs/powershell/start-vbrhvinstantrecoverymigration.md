---
title: "Start-VBRHvInstantRecoveryMigration"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/start-vbrhvinstantrecoverymigration.html"
last_updated: "5/7/2024"
product_version: "13.0.1.1071"
---

# Start-VBRHvInstantRecoveryMigration


Short Description

Performs migration of instantly recovered VMs to a Hyper-V host.

Applies to

Platform: Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Start-VBRHvInstantRecoveryMigration -InstantRecovery <InstantRecovery[]>  [<CommonParameters>] |

Detailed Description

This cmdlet migrates a recovered VM to the production host. You finalize the instant recovery of the VM initiated with the [Start-VBRHvInstantRecovery](start-vbrhvinstantrecovery.md) cmdlet by migrating the VM to production.

Run the [Stop-VBRInstantRecovery](stop-vbrinstantrecovery.md) cmdelt to terminate the recovery session by unpublishing the VM.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| InstantRecovery | Specifies the array of instant recovery sessions. The cmdlet will migrate the VMs recovered with these sessions to the Hyper-V host. | Accepts the InstantRecovery[] object. To create this object, run the [Get-VBRInstantRecovery](get-vbrinstantrecovery.md) cmdlet. | True | 1 | True (ByValue, ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the CBackupSession object that contains setting of a VMs quick migration session.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Finalizing Current Instant Recovery Session [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to finalize the current instant recovery session.  |  | | --- | | Get-VBRInstantRecovery | Start-VBRHvInstantRecoveryMigration |  Perform the following steps:   1. Run the [Get-VBRInstantRecovery](get-vbrinstantrecovery.md) cmdlet. 2. Pipe the cmdlet output to the Start-VBRHvInstantRecoveryMigration cmdlet. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Finalizing Current Instant Recovery Session [Using Variable]

|  |  |
| --- | --- |
| This example shows how to finalize the current instant recovery session.  |  | | --- | | $HvInstantRecovery = Get-VBRInstantRecovery  Start-VBRHvInstantRecoveryMigration -InstantRecovery $HvInstantRecovery |  Perform the following steps:   1. Run the [Get-VBRInstantRecovery](get-vbrinstantrecovery.md) cmdlet. Save the result to the $HvInstantRecovery variable. 2. Run the Start-VBRHvInstantRecoveryMigration cmdlet. Set the $HvInstantRecovery variable as the InstantRecovery parameter value. |

Related Commands

[Get-VBRInstantRecovery](get-vbrinstantrecovery.md)


