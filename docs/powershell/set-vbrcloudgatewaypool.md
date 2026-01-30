---
title: "Set-VBRCloudGatewayPool"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrcloudgatewaypool.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# Set-VBRCloudGatewayPool


Short Description

Modifies cloud gateway pools.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRCloudGatewayPool -CloudGatewayPool <VBRCloudGatewayPool> [-Name <String>] [-Description <String>] [-CloudGateway <VBRCloudGateway[]>] [-Force]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies cloud gateway pools.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| CloudGatewayPool | Specifies the cloud gateway pool that you want to modify. | Accepts the [VBRCloudGatewayPool](vbrcloudgatewaypool.md) object. To get this object, run the [Get-VBRCloudGatewayPool](get-vbrcloudgatewaypool.md) cmdlet. | True | Named | True (ByValue) |
| Name | Specifies the name that you want to assign to the existing cloud gateway pool. The cmdlet will change the name of the selected cloud gateway pool. | String | False | Named | False |
| Description | Specifies the description that you want to add to the existing cloud gateway pool. The cmdlet will change the description of the selected cloud gateway pool. | String | False | Named | False |
| CloudGateway | Specifies cloud gateways. The cmdlet will add these cloud gateways to the cloud gateway pool.  Note: The cmdlet will overwrite the existing cloud gateway pools with the new ones. | Accepts the [VBRCloudGateway[]](vbrcloudgateway.md) object. To get this object, run the [Get-VBRCloudGateway](get-vbrcloudgateway.md) cmdlet. | False | Named | False |
| Force | Defines that the cmdlet will add all available gateways to cloud gateway pools without warning. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRCloudGatewayPool](vbrcloudgatewaypool.md)

Examples

Modifying Name of Cloud Gateway Pool

This example shows how to modify the name of a cloud gateway pool.

|  |
| --- |
| $pool = Get-VBRCloudGatewayPool -Name "New Cloud Pool"  Set-VBRCloudGatewayPool -CloudGatewayPool $pool -Name "Silver Cloud Pool" |

Perform the following steps:

1. Run the [Get-VBRCloudGatewayPool](get-vbrcloudgatewaypool.md) cmdlet. Specify the Name parameter value. Save the result to the $pool variable.
2. Run the Set-VBRCloudGatewayPool cmdlet. Set the $pool variable as the CloudGatewayPool parameter value. Specify the Name parameter value.

Related Commands

[Get-VBRCloudGatewayPool](get-vbrcloudgatewaypool.md)


