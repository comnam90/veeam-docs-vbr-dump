---
title: "Add-VBRHvSimpleVirtualLab"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrhvsimplevirtuallab.html"
last_updated: "4/30/2024"
product_version: "13.0.1.1071"
---

# Add-VBRHvSimpleVirtualLab

In this article

Short Description

Creates a Hyper-V basic virtual lab.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Add-VBRHvSimpleVirtualLab -Server <CHost> [-Name <string>] [-Description <string>] [-Path <string>] [-ProxyAppliance <VBRHvVirtualLabProxyAppliance>]  [<CommonParameters>] |

Detailed Description

This cmdlet creates a Hyper-V basic virtual lab.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Server | Specifies a Microsoft Hyper-V host. The cmdlet will create a virtual lab on this host. | Accepts the CHost object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | True | Named | False |
| Name | Specifies a name. The cmdlet will create a virtual lab with this name. | String | False | Named | False |
| Description | Specifies a description. The cmdlet will create a virtual lab with this description. | String | False | Named | False |
| Path | Specifies the path to the folder where virtual lab will be stored. | String | False | Named | False |
| ProxyAppliance | Specifies a proxy appliance. The cmdlet will add this proxy appliance to a virtual lab. | Accepts the VBRHvVirtualLabProxyAppliance object. To get this object, run the [New-VBRHvVirtualLabProxyAppliance](new-vbrhvvirtuallabproxyappliance.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRVirtualLab object that contains settings of basic Hyper-V virtual labs.

Examples

Creating Basic Virtual Lab

|  |  |
| --- | --- |
| This example shows how to create a basic virtual lab with default settings. The cmdlet will create the virtual lab on the esx09 host.  |  | | --- | | $host = Get-VBRServer -Name "esx09"  Add-VBRHvSimpleVirtualLab -Server $host -Name "Exchange Lab" -Description "Virtual Lab for Exchange VMs" |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $host variable. 2. Run the Add-VBRHvSimpleVirtualLab cmdlet. Set the $host variable as the Server parameter value. Specify the Name parameter value. Specify the Description parameter value. |

Related Commands

[Get-VBRServer](get-vbrserver.md)

Page updated 4/30/2024

Page content applies to build 13.0.1.1071
