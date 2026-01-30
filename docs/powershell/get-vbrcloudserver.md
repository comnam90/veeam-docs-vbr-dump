---
title: "Get-VBRCloudServer"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrcloudserver.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# Get-VBRCloudServer


Short Description

Returns cloud hosts allocated by a service provider.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* For looking for hosts by host name.

|  |
| --- |
| Get-VBRCloudServer [-Name <string[]>]  [<CommonParameters>] |

* For looking for hosts of a specific cloud service provider.

|  |
| --- |
| Get-VBRCloudServer [-CloudProvider <VBRCloudProvider[]>] [-Name <string[]>]  [<CommonParameters>] |

* For looking for hosts by host ID.

|  |
| --- |
| Get-VBRCloudServer [-Id <guid[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns cloud hosts that are allocated by a service provider.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies the array of the host names you want to get. | String[] | False | Named | False |
| CloudProvider | Specifies the array of the cloud providers. The cmdlet will return the hosts that are provided to you by these providers. | Accepts the [VBRCloudProvider[]](vbrcloudprovider.md) object. To get this object, run the [Get-VBRCloudProvider](get-vbrcloudprovider.md) cmdlet. | False | Named | True (ByValue, |
| Id | Specifies the array of the IDs of the host you want to get. The cmdlet will return the hosts with these IDs. | Guid[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRCloudServer](vbrcloudserver.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting Cloud Server by Name

|  |  |
| --- | --- |
| This command returns cloud server named Hyper-V Silver.  |  | | --- | | Get-VBRCloudServer -Name "Hyper-V Silver" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Cloud Servers of Selected Cloud Service Provider

|  |  |
| --- | --- |
| This example shows how to return cloud servers of the server provider with the 104.45.95.227 IP address.  |  | | --- | | $cloudProvider = Get-VBRCloudProvider -Name "104.45.95.227"  Get-VBRCloudServer -CloudProvider $cloudProvider |  Perform the following steps:   1. Run the [Get-VBRCloudProvider](get-vbrcloudprovider.md) cmdlet. Specify the Name parameter value. Save the result to the $cloudProvider variable. 2. Run the Get-VBRCloudServer cmdket. Set the $cloudProvider variable as the CloudProvider parameter value. |

Related Commands

[Get-VBRCloudProvider](get-vbrcloudprovider.md)


