---
title: "Remove-VBRDefaultGateway"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/remove-vbrdefaultgateway.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# Remove-VBRDefaultGateway

In this article

Short Description

Removes default cloud gateways.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Remove-VBRDefaultGateway -Gateway <VBRDefaultGateway> [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet removes a selected cloud default gateway.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Gateway | Specifies the default cloud gateway you want to remove. | Accepts the [VBRDefaultGateway](vbrdefaultgateway.md) object. To get this object, run the [Get-VBRDefaultGatewayConfiguration](get-vbrdefaultgatewayconfiguration.md) cmdlet. | True | Named | True (ByValue, |
| WhatIf | Defines that the cmdlet will write a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines that the cmdlet will display a prompt that asks if you want to continue running the command.  Note: Microsoft PowerShell enables the Confirm parameter for this cmdlet by default. To disable this option, set the parameter value to $false. That is, Confirm:$false. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRDefaultGateway](vbrdefaultgateway.md)

Examples

Removing Default Gateway [Using Pipeline]

This example shows how to remove a default gateway.

|  |
| --- |
| $configuration = Get-VBRDefaultGatewayConfiguration  $configuration.DefaultGateway | Remove-VBRDefaultGateway |

Perform the following steps:

1. Run the [Get-VBRDefaultGatewayConfiguration](get-vbrdefaultgatewayconfiguration.md) cmdlet. Save it to $configuration variable.
2. Get the default gateway using the DefaultGateway property of the $configuration variable. Pipe the result to the Remove-VBRDefaultGateway cmdlet.

Related Commands

[Get-VBRDefaultGatewayConfiguration](get-vbrdefaultgatewayconfiguration.md)

Page updated 10/7/2025

Page content applies to build 13.0.1.1071
