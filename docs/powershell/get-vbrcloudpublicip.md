---
title: "Get-VBRCloudPublicIP"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrcloudpublicip.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# Get-VBRCloudPublicIP


Short Description

Returns existing public IP addresses.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Requires a VCP license.

Syntax

|  |
| --- |
| Get-VBRCloudPublicIP [-Tenant <VBRCloudTenant>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns public IP addresses that are configured by the service provider. You can get all configured IP addresses or the IP addresses allocated to a selected user.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Tenant | Specifies the cloud tenant. The cmdlet will return IP addresses assigned to this tenant. | Accepts the [VBRCloudTenant](vbrcloudtenant.md) object. To get this object, run the [Get-VBRCloudTenant](get-vbrcloudtenant.md) cmdlet. | False | Named | True (ByValue, |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRCloudIP](vbrcloudip.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All Configured Public IP Addresses

|  |  |
| --- | --- |
| This command returns all configured public IP addresses.  |  | | --- | | Get-VBRCloudPublicIP | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting All Configured Public IP Addresses

|  |  |
| --- | --- |
| This example shows how to return public IP addresses assigned to the ABC company cloud tenant.  |  | | --- | | $tenant = Get-VBRCloudTenant -Name "ABC Company"  Get-VBRCloudPublicIP -Tenant $tenant |  Perform the following steps:   1. Run the [Get-VBRCloudTenant](get-vbrcloudtenant.md) cmdlet. Specify the Name parameter value. Save the result to the $tenant variable. 2. Run the Get-VBRCloudPublicIP cmdlet. Set the $tenant variable as the Tenant parameter value. |

Related Commands

[Get-VBRCloudTenant](get-vbrcloudtenant.md)


