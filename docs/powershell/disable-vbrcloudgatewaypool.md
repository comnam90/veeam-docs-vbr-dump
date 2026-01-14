---
title: "Disable-VBRCloudGatewayPool"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/disable-vbrcloudgatewaypool.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# Disable-VBRCloudGatewayPool

In this article

Short Description

Disables cloud gateway pools.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Disable-VBRCloudGatewayPool -CloudGatewayPool <VBRCloudGatewayPool[]> [-Force] [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet disables selected cloud gateway pools. Disabling a cloud gateway pool temporarily suspends all operations on it.

Run the [Enable-VBRCloudGatewayPool](enable-vbrcloudgatewaypool.md) cmdlet to enable the disabled cloud gateway pools.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| CloudGatewayPool | Specifies an array of cloud gateway pools that you want to disable. | Accepts the [VBRCloudGatewayPool[]](vbrcloudgatewaypool.md) object. To get this object, run the [Get-VBRCloudGatewayPool](get-vbrcloudgatewaypool.md) cmdlet. | True | Named | True (ByValue, |
| Force | Defines that the cmdlet will not show the notification about the active sessions of tenants. | SwitchParameter | False | Named | False |
| WhatIf | Defines that the cmdlet will write a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines that the cmdlet will display a prompt that asks if you want to continue running the command.  Note: Microsoft PowerShell enables the Confirm parameter for this cmdlet by default. To disable this option, set the parameter value to $false. That is, Confirm:$false. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Disabling Cloud Gateway Pool

This example shows how to disable a cloud gateway pool.

|  |
| --- |
| $pool = Get-VBRCloudGatewayPool -Name "New Cloud Pool"  Disable-VBRCloudGatewayPool -CloudGatewayPool $pool |

Perform the following steps:

1. Run the [Get-VBRCloudGatewayPool](get-vbrcloudgatewaypool.md) cmdlet. Specify the Name parameter value. Save the result to the $pool variable.
2. Run the Disable-VBRCloudGatewayPool cmdlet. Set the $pool variable as the CloudGatewayPool parameter value.

Related Commands

[Get-VBRCloudGatewayPool](get-vbrcloudgatewaypool.md)

Page updated 10/7/2025

Page content applies to build 13.0.1.1071
