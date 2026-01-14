---
title: "Set-VBRDefaultGatewayConfiguration"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrdefaultgatewayconfiguration.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# Set-VBRDefaultGatewayConfiguration

In this article

Short Description

Modifies default gateway configuration.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRDefaultGatewayConfiguration -Configuration <VBRDefaultGatewayConfiguration> [-EnableRouting] [-PassThru]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies settings of the default gateway.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Configuration | Specifies the default gateway configuration that you want to modify. | Accepts the [VBRDefaultGatewayConfiguration](vbrdefaultgatewayconfiguration.md) object. To get this object, run the [Get-VBRDefaultGatewayConfiguration](get-vbrdefaultgatewayconfiguration.md) cmdlet. | True | Named | True (ByValue, |
| EnableRouting | Enables routing option for the gateway. | SwitchParameter | False | Named | False |
| PassThru | Defines that the command returns the output object to the Windows PowerShell console. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRDefaultGatewayConfiguration[]](vbrdefaultgatewayconfiguration.md)

Examples

Enabling Routing for Selected Default Gateway Configuration

This example shows how to enable routing for a selected default gateway configuration.

|  |
| --- |
| $c = Get-VBRDefaultGatewayConfiguration  Set-VBRDefaultGatewayConfiguration -Configuration $c -EnableRouting |

Perform the following steps:

1. Run the [Get-VBRDefaultGatewayConfiguration](get-vbrdefaultgatewayconfiguration.md) cmdlet. Save the result to $c variable.
2. Run the Set-VBRDefaultGatewayConfiguration cmdlet. Set the $c variable as the Configuration parameter value. Provide the EnableRouting parameter.

Related Commands

[Get-VBRDefaultGatewayConfiguration](get-vbrdefaultgatewayconfiguration.md)

Page updated 10/7/2025

Page content applies to build 13.0.1.1071
