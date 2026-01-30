---
title: "Remove-VBRCloudGateway"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/remove-vbrcloudgateway.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# Remove-VBRCloudGateway


Short Description

Removes cloud gateways.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Requires a cloud provider license.

Syntax

|  |
| --- |
| Remove-VBRCloudGateway -CloudGateway <VBRCloudGateway[]> [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet removes selected cloud gateways from Veeam Backup & Replication console.

When you remove a cloud gateway, Veeam Backup & Replication unassigns the gateway role from the server, so it is no longer used as a cloud gateway. The actual server remains connected to Veeam Backup & Replication.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| CloudGateway | Specifies the array of cloud gateways you want to remove. | Accepts the [VBRCloudGateway[]](vbrcloudgateway.md) object. To get this object, run the [Get-VBRCloudGateway](get-vbrcloudgateway.md) cmdlet. | True | Named | True (ByValue, |
| WhatIf | Defines that the cmdlet will write a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines that the cmdlet will display a prompt that asks if you want to continue running the command.  Note: Microsoft PowerShell enables the Confirm parameter for this cmdlet by default. To disable this option, set the parameter value to $false. That is, Confirm:$false. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Removing Cloud Gateway [Using Variable]

|  |  |
| --- | --- |
| This example shows how to remove the selected cloud gateway.  |  | | --- | | $cloudgateway = Get-VBRCloudGateway -Name "Cloud gateway"  Remove-VBRCloudGateway -CloudGateway $cloudgateway |  Perform the following steps:   1. Run the [Get-VBRCloudGateway](get-vbrcloudgateway.md) cmdlet. Specify the Name parameter value. Save the result to the $cloudgateway variable. 2. Run the Remove-VBRCloudGateway cmdlet. Set the $cloudgateway variable as the CloudGateway parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Removing Cloud Gateway [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to remove the selected cloud gateway.  |  | | --- | | Get-VBRCloudGateway -Name "Cloud gateway" | Remove-VBRCloudGateway |  Perform the following steps:   1. Run the [Get-VBRCloudGateway](get-vbrcloudgateway.md) cmdlet. Specify the Name parameter value. 2. Pipe the cmdlet output to the Remove-VBRCloudGateway cmdlet. |

Related Commands

[Get-VBRCloudGateway](get-vbrcloudgateway.md)


