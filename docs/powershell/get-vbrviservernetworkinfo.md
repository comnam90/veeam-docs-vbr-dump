---
title: "Get-VBRViServerNetworkInfo"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrviservernetworkinfo.html"
last_updated: "3/4/2024"
product_version: "13.0.1.1071"
---

# Get-VBRViServerNetworkInfo


Short Description

Returns virtual networks for a VMware host.

Applies to

Platform: VMware

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRViServerNetworkInfo -Server <CHost>  [<CommonParameters>] |

Detailed Description

This cmdlet returns the list of all virtual networks to which a selected VMware host is connected.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Server | Specifies the VMware host. The cmdlet will return virtual networks connected to this host. | Accepts the CHost object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | True | Named | True (ByValue, |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the following objects:

* [VBRViNetworkInfo](vbrvinetworkinfo.md)[]
* [VBRViDVSNetworkInfo](vbrvidvsnetworkinfo.md)[]

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting Networks Connected to Specific VMware Host

|  |  |
| --- | --- |
| This example shows how to get the networks to which the srv01.tech.local host is connected.  |  | | --- | | $server = Get-VBRServer -Type ESXi -Name "srv01.tech.local"  Get-VBRViServerNetworkInfo -Server $server |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Type and Name parameter values. Save the result to the $server variable. 2. Run the Get-VBRViServerNetworkInfo cmdlet. Set the $server variable as the Server parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Networks Connected to Specific VMware Host Using Host Name

|  |  |
| --- | --- |
| This command shows how to look get the networks to which the srv01.tech.local host is connected.  |  | | --- | | Get-VBRViServerNetworkInfo -Server "srv01.tech.local" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting Specific Network Connected to Specific VMware Host

|  |  |
| --- | --- |
| This example shows how to get one network from the list of networks that are connected to the srv01.tech.local host.  |  | | --- | | $networks = Get-VBRViServerNetworkInfo -Server "srv01.tech.local"  $targetnetwork = $networks[5] |  Perform the following steps:   1. Run the Get-VBRViServerNetworkInfo cmdlet. Specify the Server parameter value. Save the result to the $networks variable. 2. The Get-VBRViServerNetworkInfo cmdlet will return an array of networks. Specify the necessary network of the $networks variable using the square brackets. Save the result to the $targetnetwork variable. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Getting Specific Network Connected to Specific VMware Host [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to get the NW01 network that is connected to the srv01.tech.local host.  |  | | --- | | Get-VBRViServerNetworkInfo -Server "srv01.tech.local" | Where-Object { $\_.NetworkName -eq "NW01" } |  Perform the following steps:   1. Run the Get-VBRViServerNetworkInfo cmdlet. Specify the Server parameter value. 2. Pipe the cmdlet output to the [Where-Object](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/where-object?view=powershell-7.1) cmdlet. Specify the following settings:  * Provide the $\_. automatic variable. * Provide the NetworkName property. * Specify the eq comparison operator value. |

Related Commands

* [Get-VBRServer](get-vbrserver.md)
* [Where-Object](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/where-object?view=powershell-7.1)


