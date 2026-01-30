---
title: "Get-VBRVCDOrgVdcNetworkInfo"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrvcdorgvdcnetworkinfo.html"
last_updated: "4/24/2024"
product_version: "13.0.1.1071"
---

# Get-VBRVCDOrgVdcNetworkInfo


Short Description

Returns target networks for Cloud Director replica mapping.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRVCDOrgVdcNetworkInfo [-Name <string[]>] [-Server <CHost[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns target networks for Cloud Director replica mapping.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies an array of names for Cloud Director networks. The cmdlet will return these networks. | String[] | True | Named | True (ByValue, ByPropertyName) |
| Server | Specifies an array of Cloud Director hosts. The cmdlet will return networks that are available on these Cloud Director hosts. | Accepts the CHost[] object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRVCDOrgVdcNetworkInfo object that networks for Cloud Director replica mapping.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting all Cloud Director Replica Mapping Networks

|  |  |
| --- | --- |
| This example shows how to get all mapping networks that are available on the Cloud Director host.  |  | | --- | | $server = Get-VBRServer -Name vCloud  Get-VBRVCDOrgVdcNetworkInfo -Server $server |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 2. Run the Get-VBRVCDOrgVdcNetworkInfo cmdlet. Set the $server variable as the Server parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Cloud Director Replica Mapping Networks by Name

|  |  |
| --- | --- |
| This example shows how to get the Net06, Net10, Net21 mapping networks that are available on the Cloud Director host.  |  | | --- | | $server = Get-VBRServer -Name vCloud  Get-VBRVCDOrgVdcNetworkInfo -Server $server -Name "Net06", "Net10", "Net21" |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 2. Run the Get-VBRVCDOrgVdcNetworkInfo cmdlet. Set the $server variable as the Server parameter value. Specify the Name parameter value. |

Related Commands

[Get-VBRServer](get-vbrserver.md)


