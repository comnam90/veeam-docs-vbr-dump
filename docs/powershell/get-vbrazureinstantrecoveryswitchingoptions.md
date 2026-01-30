---
title: "Get-VBRAzureInstantRecoverySwitchingOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrazureinstantrecoveryswitchingoptions.html"
last_updated: "7/31/2025"
product_version: "13.0.1.1071"
---

# Get-VBRAzureInstantRecoverySwitchingOptions


Short Description

Returns the switchover options.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRAzureInstantRecoverySwitchingOptions -InstantRecovery <VBRAzureInstantRecovery> [<CommonParameters>] |

Detailed Description

This cmdlet returns the switchover options.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| InstantRecovery | Specifies the operation for which you want to get the switchover options. | Accepts the VBRAzureInstantRecovery object. To create or get this object, run the [Start-VBRAzureInstantRecovery](start-vbrazureinstantrecovery.md) or [Get-VBRAzureInstantRecovery](get-vbrazureinstantrecovery.md) cmdlet. | True | Named | True |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRAzureInstantRecoverySwitchingOptions](vbrazureinstantrecoveryswitchingoptions.md)

Examples

This command shows how to get switchover options for the Instant Recovery operation with the d1d2a50e-8052-498f-826b-e5c86f30ed5a ID.

|  |
| --- |
| $recovery = Get-VBRAzureInstantRecovery -Id "d1d2a50e-8052-498f-826b-e5c86f30ed5a"  $options = Get-VBRAzureInstantRecoverySwitchingOptions -InstantRecovery $recovery |

Perform the following steps:

1. Run the [Get-VBRAzureInstantRecovery](get-vbrazureinstantrecovery.md) cmdlet. Specify the Id parameter value. Save the result to the $recovery variable.
2. Run the Get-VBRAzureInstantRecoverySwitchingOptions cmdlet. Set the $recovery variable as the InstantRecovery parameter value.

Related Commands

[Get-VBRAzureInstantRecovery](get-vbrazureinstantrecovery.md)


