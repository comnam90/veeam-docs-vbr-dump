---
title: "Add-VBRCloudGatewayPool"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrcloudgatewaypool.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# Add-VBRCloudGatewayPool

In this article

Short Description

Creates cloud gateway pools.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Requires a cloud provider license.

Syntax

|  |
| --- |
| Add-VBRCloudGatewayPool -Name <String> -CloudGateway <VBRCloudGateway[]> [-Description <String>] [-Force]  [<CommonParameters>] |

Detailed Description

This cmdlet creates cloud gateway pools.

|  |
| --- |
| Important |
| If you add all available gateways to cloud gateway pools, the jobs will fail for tenants with the automatic gateway type. You will not be able to create new tenants with automatic selection type. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies the name of the cloud gateway pool. The cmdlet will add the cloud gateway pool with this name to the cloud infrastructure. | String | True | Named | True (ByValue) |
| CloudGateway | Specifies an array of gateways from the cloud infrastructure. The cmdlet will add these gateways to the cloud gateway pool. | Accepts the [VBRCloudGateway[]](vbrcloudgateway.md) object. To get this object, run the [Get-VBRCloudGateway](get-vbrcloudgateway.md) cmdlet. | True | Named | False |
| Description | Specifies the description of the cloud gateway pool. The cmdlet will add the cloud gateway pool with this description to the cloud infrastructure. | String | False | Named | False |
| Force | Defines that the cmdlet will add all available gateways to cloud gateway pools without warning. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRCloudGatewayPool](vbrcloudgatewaypool.md)

Examples

Creating Cloud Gateway Pool

This example shows how to create a cloud gateway pool.

|  |
| --- |
| $gateway = Get-VBRCloudGateway  Add-VBRCloudGatewayPool -Name "Silver Pool" -CloudGateway $gateway |

Perform the following steps:

1. Run the [Get-VBRCloudGateway](get-vbrcloudgateway.md) cmdlet to get the array of cloud gateways. Save the result to the $gateway variable.
2. Run the Add-VBRCloudGatewayPool cmdlet. Specify the Name parameter value. Set the $gateway variable as the CloudGateway parameter value.

Related Commands

[Get-VBRCloudGateway](get-vbrcloudgateway.md)

Page updated 10/7/2025

Page content applies to build 13.0.1.1071
