---
title: "Remove-VBRCloudGatewayPool"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/remove-vbrcloudgatewaypool.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# Remove-VBRCloudGatewayPool


Short Description

Removes cloud gateway pools.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Remove-VBRCloudGatewayPool -CloudGatewayPool <VBRCloudGatewayPool[]> [-Force] [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet removes selected cloud gateway pools from the backup infrastructure.

When you remove the cloud gateway pool, the cloud gateways are not removed from your cloud infrastructure. They will show up as the cloud gateways.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| CloudGatewayPool | Specifies an array of cloud gateways pools that you want to remove. | Accepts the [VBRCloudGatewayPool[]](vbrcloudgatewaypool.md) object. To get this object, run the [Get-VBRCloudGatewayPool](get-vbrcloudgatewaypool.md) cmdlet. | True | Named | True (ByValue, |
| WhatIf | Defines that the cmdlet will write a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines that the cmdlet will display a prompt that asks if you want to continue running the command.  Note: Microsoft PowerShell enables the Confirm parameter for this cmdlet by default. To disable this option, set the parameter value to $false. That is, Confirm:$false. | SwitchParameter | False | Named | False |
| Force | Defines that the cmdlet will remove cloud gateway pools without warning even if there are tenants assigned to that cloud gateway pool. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Removing Cloud Gateway Pool

This example shows how to remove a cloud gateway pool.

|  |
| --- |
| $pool = Get-VBRCloudGatewayPool -Name "New Cloud Pool"  Remove-VBRCloudGatewayPool -CloudGatewayPool $pool |

Perform the following steps:

1. Run the [Get-VBRCloudGatewayPool](get-vbrcloudgatewaypool.md) cmdlet. Specify the Name parameter value. Save the result to the $pool variable.
2. Run the Remove-VBRCloudGatewayPool cmdlet. Set the $pool variable as the CloudGatewayPool parameter value.

Related Commands

[Get-VBRCloudGatewayPool](get-vbrcloudgatewaypool.md)


