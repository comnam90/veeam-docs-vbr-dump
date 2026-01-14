---
title: "Enable-VBRCloudGatewayPool"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/enable-vbrcloudgatewaypool.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# Enable-VBRCloudGatewayPool

In this article

Short Description

Enables disabled cloud gateway pools.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Enable-VBRCloudGatewayPool -CloudGatewayPool <VBRCloudGatewayPool[]> [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet enables cloud gateway pools that have been disabled.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| CloudGatewayPool | Specifies an array of cloud gateway pools you want to enable. | Accepts the [VBRCloudGatewayPool[]](vbrcloudgatewaypool.md) object. To get this object, run the [Get-VBRCloudGatewayPool](get-vbrcloudgatewaypool.md) cmdlet. | True | Named | True (ByValue, |
| WhatIf | Defines that the cmdlet will write a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines that the cmdlet will display a prompt that asks if you want to continue running the command. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Enabling Cloud Gateway Pool

This example shows how to enable a cloud gateway pool.

|  |
| --- |
| $pool = Get-VBRCloudGatewayPool -Name "New Cloud Pool"  Enable-VBRCloudGatewayPool -CloudGatewayPool $pool |

Perform the following steps:

1. Run the [Get-VBRCloudGatewayPool](get-vbrcloudgatewaypool.md) cmdlet. Specify the Name parameter value. Save the result to the $pool variable.
2. Run the Enable-VBRCloudGatewayPool cmdlet. Set the $pool variable as the CloudGatewayPool parameter value.

Related Commands

[Get-VBRCloudGatewayPool](get-vbrcloudgatewaypool.md)

Page updated 10/7/2025

Page content applies to build 13.0.1.1071
