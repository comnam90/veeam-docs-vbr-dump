---
title: "Find-VBRViResourcePool"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/find-vbrviresourcepool.html"
last_updated: "5/20/2024"
product_version: "13.0.1.1071"
---

# Find-VBRViResourcePool

In this article

Short Description

Returns VMware resource pools.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Find-VBRViResourcePool -Server <CHost> [-Name <String[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns resource pools on a selected ESXi host.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Server | Specifies the ESXi host. The cmdlet will return resource pools created on this host. | Accepts the CHost object or string. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | True | Named | True (ByValue, |
| Name | Specifies the array of resource pool names. The cmdlet will return resource pools with these names. | String[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

This cmdlet returns the CViResourcePoolItem object that contains information on VMware resource pools on a selected ESXi host.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Looking for all Resource Pools on Specific ESXi Host

|  |  |
| --- | --- |
| This example shows how to get a list of resource pools on the esx05.tech.local ESXi hosts.  |  | | --- | | $server = Get-VBRServer -Type ESXi -Name "esx05.tech.local"  Find-VBRViResourcePool -Server $server |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Type and Name parameter values. Save the result to the $server variable. 2. Run the Find-VBRViResourcePool cmdlet. Set the $server variable as the Server parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Looking for Specific Resource Pool on Specific ESXi Host

|  |  |
| --- | --- |
| This example shows how to get the RP\_05 resource pool on the esx05.tech.local ESXi hosts.  |  | | --- | | $server = Get-VBRServer -Type ESXi -Name "esx05.tech.local"  Find-VBRViResourcePool -Server $server -Name "ResourcePool\_05" |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Type and Name parameter values. Save the result to the $server variable. 2. Run the Find-VBRViResourcePool cmdlet. Set the $server variable as the Server parameter value. Specify the Name parameter value. |

Related Commands

[Get-VBRServer](get-vbrserver.md)

Page updated 5/20/2024

Page content applies to build 13.0.1.1071
