---
title: "Stop-VBRAzureInstantRecovery"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/stop-vbrazureinstantrecovery.html"
last_updated: "7/30/2025"
product_version: "13.0.1.1071"
---

# Stop-VBRAzureInstantRecovery

In this article

Short Description

Stops the specified Instant Recovery to Microsoft Azure operation.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Stop-VBRAzureInstantRecovery [-InstantRecovery] <VBRAzureInstantRecovery[]> [-RunAsync] [<CommonParameters>] |

Detailed Description

This cmdlet stops the specified Instant Recovery to Microsoft Azure operation.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| InstantRecovery | Specifies an array of Instant Recovery to Microsoft Azure operations that you want to stop. | Accepts the VBRAzureInstantRecovery[] object. To create or get this object, run the [Start- VBRAzureInstantRecovery](start-vbrazureinstantrecovery.md), [Start-VBRAzureInstantRecoveryMigration](start-vbrazureinstantrecoverymigration.md) or [Get-VBRAzureInstantRecovery](get-vbrazureinstantrecovery.md) cmdlet. | True | 0 | True |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

This example shows how to stop the Instant Recovery to Microsoft Azure operation.

|  |
| --- |
| $session = Get-VBRAzureInstantRecovery -Id "d1d2a50e-8052-498f-826b-e5c86f30ed5a"  Stop-VBRAzureInstantRecovery -InstantRecovery $session |

Perform the following steps:

1. Run the [Get-VBRAzureInstantRecovery](get-vbrazureinstantrecovery.md) cmdlet. Specify the Id parameter value. Save the result to the $operation variable.
2. Run the Stop-VBRAzureInstantRecovery cmdlet. Set the $session variable as the InstantRecovery parameter value.

Related Commands

* [New-VBRAzureInstantRecoverySwitchingOptions](new-vbrazureinstantrecoveryswitchingoptions.md)
* [Get-VBRAzureInstantRecovery](get-vbrazureinstantrecovery.md)

Page updated 7/30/2025

Page content applies to build 13.0.1.1071
