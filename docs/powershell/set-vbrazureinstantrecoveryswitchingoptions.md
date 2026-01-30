---
title: "Set-VBRAzureInstantRecoverySwitchingOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrazureinstantrecoveryswitchingoptions.html"
last_updated: "8/1/2025"
product_version: "13.0.1.1071"
---

# Set-VBRAzureInstantRecoverySwitchingOptions


Short Description

Sets the switchover options for an Instant Recovery operation.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRAzureInstantRecoverySwitchingOptions -InstantRecovery <VBRAzureInstantRecovery> -SwitchingOptions <VBRAzureInstantRecoverySwitchingOptions> [<CommonParameters>] |

Detailed Description

This cmdlet sets the switchover options for an Instant Recovery operation.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| InstantRecovery | Specifies the Instant Recovery operation for which you want to change the switchover options. | Accepts the VBRAzureInstantRecovery object. To create or get this object, run the [Start-VBRAzureInstantRecovery](start-vbrazureinstantrecovery.md) or [Get-VBRAzureInstantRecovery](get-vbrazureinstantrecovery.md) cmdlet. | True | Named | True |
| SwitchingOptions | Specifies the switchover options that you want to change for the Instant Recovery operation. | Accepts the VBRAzureInstantRecoverySwitchingOptions object. To create or get this object, run the [New-VBRAzureInstantRecoverySwitchingOptions](new-vbrazureinstantrecoveryswitchingoptions.md) or [Get-VBRAzureInstantRecoverySwitchingOptions](get-vbrazureinstantrecoveryswitchingoptions.md) cmdlet. | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

This command shows how to set switchover options for the Instant Recovery operation with the d1d2a50e-8052-498f-826b-e5c86f30ed5a ID.

|  |
| --- |
| $recovery = Get-VBRAzureInstantRecovery -Id "d1d2a50e-8052-498f-826b-e5c86f30ed5a"  $switchingOptions = New-VBRAzureInstantRecoverySwitchingOptions -SwitchingType Manual -PowerOnVm  Set-VBRAzureInstantRecoverySwitchingOptions -InstantRecovery $recovery -SwitchingOptions $switchingOptions |

Perform the following steps:

1. Run the [Get-VBRAzureInstantRecovery](get-vbrazureinstantrecovery.md) cmdlet. Specify the Id parameter value. Save the result to the $recovery variable.
2. Run the [New-VBRAzureInstantRecoverySwitchingOptions](new-vbrazureinstantrecoveryswitchingoptions.md) cmdlet. Specify the SwitchingType and PowerOnVm parameter values. Save the result to the $switchingOptions variable.
3. Run the Set-VBRAzureInstantRecoverySwitchingOptions cmdlet. Set the $recovery variable as the InstantRecovery parameter value. Set the $switchingOptions variable as the SwitchingOptions parameter value.

Related Commands

* [Get-VBRAzureInstantRecovery](get-vbrazureinstantrecovery.md)
* [New-VBRAzureInstantRecoverySwitchingOptions](new-vbrazureinstantrecoveryswitchingoptions.md)


