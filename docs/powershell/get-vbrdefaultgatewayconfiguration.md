---
title: "Get-VBRDefaultGatewayConfiguration"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrdefaultgatewayconfiguration.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# Get-VBRDefaultGatewayConfiguration

In this article

Short Description

Returns configuration of default gateways.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get default gateways of all cloud service providers.

|  |
| --- |
| Get-VBRDefaultGatewayConfiguration  [<CommonParameters>] |

* Get default gateways of a selected cloud service provider.

|  |
| --- |
| Get-VBRDefaultGatewayConfiguration [-CloudProvider <VBRCloudProvider[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns configuration information on service provider default gateways. You can get information about all gateways of all service providers, or look for a selected service provider.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| CloudProvider | Specifies the array of cloud providers. The cmdlet will return the default gateways of these cloud providers. | Accepts the [VBRCloudProvider[]](vbrcloudprovider.md) object. To get this object, run the [Get-VBRCloudProvider](get-vbrcloudprovider.md) cmdlet. | False | Named | True (ByValue, |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRDefaultGatewayConfiguration[]](vbrdefaultgatewayconfiguration.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting Configuration of Default Gateways of All Cloud Providers

|  |  |
| --- | --- |
| This command looks for configuration of default gateways of all cloud providers.  |  | | --- | | Get-VBRDefaultGatewayConfiguration | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Configuration of Default Gateway of Selected Cloud Provider

|  |  |
| --- | --- |
| This example shows how to look for configuration of default gateway of the cloud provider named Cloud provider01.  |  | | --- | | $cloudprovider = Get-VBRCloudprovider -Name "Cloud provider01"  Get-VBRDefaultGatewayConfiguration -CloudProvider $cloudprovider |  Perform the following steps:   1. Run the [Get-VBRCloudProvider](get-vbrcloudprovider.md) cmdlet. Specify the Name parameter value. Save the result to the $cloudprovider variable. 2. Run the Get-VBRDefaultGatewayConfiguration cmdlet. Set the $cloudprovider variable as the CloudProvider parameter value. |

Related Commands

[Get-VBRCloudProvider](get-vbrcloudprovider.md)

Page updated 10/7/2025

Page content applies to build 13.0.1.1071
