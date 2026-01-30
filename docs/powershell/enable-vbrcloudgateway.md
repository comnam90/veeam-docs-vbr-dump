---
title: "Enable-VBRCloudGateway"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/enable-vbrcloudgateway.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# Enable-VBRCloudGateway


Short Description

Enables disabled cloud gateways.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Requires a cloud provider license.

Syntax

|  |
| --- |
| Enable-VBRCloudGateway -CloudGateway <VBRCloudGateway[]> [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet enables selected cloud gateways, that were previously disabled.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| CloudGateway | Specifies the array of cloud gateway you want to enable. | Accepts the [VBRCloudGateway[]](vbrcloudgateway.md) object. To get this object, run the [Get-VBRCloudGateway](get-vbrcloudgateway.md) cmdlet. | True | Named | True (ByValue, |
| WhatIf | Defines that the cmdlet will write a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines that the cmdlet will display a prompt that asks if you want to continue running the command. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRCloudGateway](vbrcloudgateway.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Enabling Cloud Gateway [Using Variable]

|  |  |
| --- | --- |
| This example shows how to enable the selected cloud gateway.  |  | | --- | | $cloudgateway = Get-VBRCloudGateway -Name "Cloud gateway"  Enable-VBRCloudGateway -CloudGateway $cloudgateway |  Perform the following steps:   1. Run the [Get-VBRCloudGateway](get-vbrcloudgateway.md) cmdlet. Specify the Name parameter value. Save the result to the $cloudgateway variable. 2. Run the Enable-VBRCloudGateway cmdlet. Set the $cloudgateway variable as the CloudGateway parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Enabling Cloud Gateway [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to enable two cloud gateways.  |  | | --- | | Get-VBRCloudGateway -Name "Cloud gateway", "Cloud gateway 01" | Enable-VBRCloudGateway |  Perform the following steps:   1. Run the [Get-VBRCloudGateway](get-vbrcloudgateway.md) cmdlet. Specify the Name parameter value. 2. Pipe the cmdlet output to the Enable-VBRCloudGateway cmdlet. |

Related Commands

[Get-VBRCloudGateway](get-vbrcloudgateway.md)


