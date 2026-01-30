---
title: "Get-VBRCloudProviderNetworkAppliance"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrcloudprovidernetworkappliance.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# Get-VBRCloudProviderNetworkAppliance


Short Description

Returns network extension appliance configured on the user side.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRCloudProviderNetworkAppliance [-Name <string[]>] [-CloudProvider <VBRCloudProvider[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns network extension appliance created on the user side. This appliance is used in replica failover scenarios.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies the array of the appliance names. | String[] | False | Named | True (ByValue, |
| CloudProvider | Specifies the array of the service providers. The cmdlet will return appliances configured by these providers. | Accepts the [VBRCloudProvider[]](vbrcloudprovider.md) object. To get this object, run the [Get-VBRCloudProvider](get-vbrcloudprovider.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

* [VBRViCloudProviderNetworkAppliance](vbrvicloudprovidernetworkappliance.md)
* [VBRHvCloudProviderNetworkAppliance](vbrhvcloudprovidernetworkappliance.md)

Examples

Getting All Network Appliances by Cloud Service Provider IP Address

This example shows how to search for all network appliances configured by the cloud service provider with the 104.45.95.227 IP address.

|  |
| --- |
| $provider = Get-VBRCloudProvider –Name "104.45.95.227"  Get-VBRCloudProviderNetworkAppliance -CloudProvider $provider |

Perform the following steps:

1. Run the [Get-VBRCloudProvider](get-vbrcloudprovider.md) cmdlet. Specify the Name parameter value. Save the result to the $provider variable.
2. Run the Get-VBRCloudProviderNetworkAppliance cmdlet. Set the $provider variable as the CloudProvider parameter value.

Related Commands

[Get-VBRCloudProvider](get-vbrcloudprovider.md)


