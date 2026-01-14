---
title: "Disable-VBRCloudGateway"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/disable-vbrcloudgateway.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# Disable-VBRCloudGateway

In this article

Short Description

Disables cloud gateways.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Requires a cloud provider license.

Syntax

|  |
| --- |
| Disable-VBRCloudGateway -CloudGateway <VBRCloudGateway[]> [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet disables a selected cloud gateway. Disabling a gateway temporarily suspends all operations on it. Run the [Enable-VBRCloudGateway](enable-vbrcloudgateway.md) cmdlet to enable a disabled cloud gateway.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| CloudGateway | Specifies the array of cloud gateways you want to disable. | Accepts the [VBRCloudGateway[]](vbrcloudgateway.md) object. To get this object, run the [Get-VBRCloudGateway](get-vbrcloudgateway.md) cmdlet. | True | Named | True (ByValue, |
| WhatIf | Defines that the cmdlet will write a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines that the cmdlet will display a prompt that asks if you want to continue running the command.  Note: Microsoft PowerShell enables the Confirm parameter for this cmdlet by default. To disable this option, set the parameter value to $false. That is, Confirm:$false. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRCloudGateway](vbrcloudgateway.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Disabling Cloud Gateway [Using Variable]

|  |  |
| --- | --- |
| This example shows how to disable the selected cloud gateway.  |  | | --- | | $cloudgateway = Get-VBRCloudGateway -Name "Cloud gateway"  Disable-VBRCloudGateway -CloudGateway $cloudgateway |  Perform the following steps:   1. Run the [Get-VBRCloudGateway](get-vbrcloudgateway.md) cmdlet. Specify the Name parameter value. Save the result to the $cloudgateway variable. 2. Run the Disable-VBRCloudGateway cmdlet. Set the $cloudgateway variable as the CloudGateway parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Disabling Cloud Gateway [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to disable the selected cloud gateway.  |  | | --- | | Get-VBRCloudGateway -Name "Cloud gateway" | Disable-VBRCloudGateway |  Perform the following steps:   1. Run the [Get-VBRCloudGateway](get-vbrcloudgateway.md) cmdlet. Specify the Name parameter value. 2. Pipe the cmdlet output to the Disable-VBRCloudGateway cmdlet. |

Related Commands

[Get-VBRCloudGateway](get-vbrcloudgateway.md)

Page updated 10/7/2025

Page content applies to build 13.0.1.1071
