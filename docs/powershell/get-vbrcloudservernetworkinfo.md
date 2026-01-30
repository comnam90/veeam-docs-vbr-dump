---
title: "Get-VBRCloudServerNetworkInfo"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrcloudservernetworkinfo.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# Get-VBRCloudServerNetworkInfo


Short Description

Returns networks available in your cloud resources.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get networks by name.

|  |
| --- |
| Get-VBRCloudServerNetworkInfo [-Name <string[]>]  [<CommonParameters>] |

* Get networks of a selected cloud service provider.

|  |
| --- |
| Get-VBRCloudServerNetworkInfo [-CloudServer <VBRCloudServer[]>] [-Name <string[]>]  [<CommonParameters>] |

* Get networks by ID.

|  |
| --- |
| Get-VBRCloudServerNetworkInfo [-Id <guid[]>] [-Name <string[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns networks that are allocated to you by your cloud resources.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies the name of the network you want to get. | String[] | False | Named | False |
| CloudServer | Specifies the cloud server. The cmdlet will return networks connected to this server. | Accepts the [VBRCloudServer[]](vbrcloudserver.md) object. To get this object, run the [Get-VBRCloudServer](get-vbrcloudserver.md) cmdlet. | False | Named | True (ByValue, |
| Id | Specifies the ID of the network you want to get. | Guid[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRCloudServerNetworkInfo](vbrcloudservernetworkinfo.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting Network by Name

|  |  |
| --- | --- |
| This command looks for a network by name.  |  | | --- | | Get-VBRCloudServerNetworkInfo -Name "Lab Isolated Network" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Networks Connected to Selected Cloud Server

|  |  |
| --- | --- |
| This example shows how to return networks connected to a selected cloud server.  |  | | --- | | $cloudServer = Get-VBRCloudServer -Name "Hyper-V Silver"  Get-VBRCloudServerNetworkInfo -CloudServer $cloudServer |  Perform the following steps:   1. Run the [Get-VBRCloudServer](get-vbrcloudserver.md) cmdlet. Specify the Name parameter value. Save the result to the $cloudServer variable. 2. Run the Get-VBRCloudServerNetworkInfo cmdlet. Set the $cloudServer variable as the CloudServer parameter value. |

Related Commands

[Get-VBRCloudServer](get-vbrcloudserver.md)


