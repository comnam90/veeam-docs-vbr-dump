---
title: "Get-VBRHvServerNetworkInfo"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrhvservernetworkinfo.html"
last_updated: "6/17/2024"
product_version: "13.0.1.1071"
---

# Get-VBRHvServerNetworkInfo


Short Description

Returns virtual networks for a Hyper-V host.

Applies to

Platform: Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRHvServerNetworkInfo -Server <CHost>  [<CommonParameters>] |

Detailed Description

This cmdlet returns the list of all virtual networks to which a selected Hyper-V host is connected.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Server | Specifies the Hyper-V host. The cmdlet will return virtual networks connected to this host. | Accepts the CHost object or string (host name). To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | True | Named | True (ByValue, |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the [VBRHvServerNetworkInfo](vbrhvservernetworkinfo.md) object that defines Azure AD application settings.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting all Networks Connected to Specific Hyper-V Host

|  |  |
| --- | --- |
| This command gets all networks to which the srv01.tech.local host is connected.  |  | | --- | | Get-VBRHvServerNetworkInfo -Server "srv01.tech.local" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Networks Connected to Specific Hyper-V Host Using Host Name

|  |  |
| --- | --- |
| This example shows how to look for the networks to which the srv01.tech.local host is connected.  |  | | --- | | $server = Get-VBRServer -Type HvServer -Name "srv01.tech.local"  Get-VBRHvServerNetworkInfo -Server $server |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Type and Name parameter values. Save the result to the $server variable. 2. Run the Get-VBRHvServerNetworkInfo cmdlet. Set the $server variable as the Server parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting Specific Network Connected to Specific Hyper-V Host

|  |  |
| --- | --- |
| This example shows how get one network from the list of networks that are connected to the srv01.tech.local host.  |  | | --- | | $networks = Get-VBRHvServerNetworkInfo -Server "srv01.tech.local"  $targetnetwork = $networks[5] |  Perform the following steps:   1. Run the Get-VBRHvServerNetworkInfo cmdlet. Specify the Server parameter value. Save the result to the $networks variable. 2. The Get-VBRHvServerNetworkInfo cmdlet will return an array of networks. Specify the necessary network of the $networks variable using the square brackets. Save the result to the $targetnetwork variable. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Getting Specific Network Connected to Specific Hyper-V Host [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to get the Lab Isolated Network network that is connected to the srv01.tech.local host.  |  | | --- | | Get-VBRHvServerNetworkInfo -Server "srv01.tech.local" | Where-Object { $\_.NetworkName -eq "Lab Isolated Network" } |  Perform the following steps:   1. Run the Get-VBRHvServerNetworkInfo cmdlet. Specify the Server parameter value. 2. Pipe the cmdlet output to the [Where-Object](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/where-object?view=powershell-7.1) cmdlet. Specify the following settings:  * Provide the $\_. automatic variable. * Provide the NetworkName property. * Specify the eq comparison operator value. |

Related Commands

* [Get-VBRServer](get-vbrserver.md)
* [Where-Object](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/where-object?view=powershell-7.1)


