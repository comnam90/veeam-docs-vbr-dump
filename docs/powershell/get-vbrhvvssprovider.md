---
title: "Get-VBRHvVssProvider"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrhvvssprovider.html"
last_updated: "3/1/2024"
product_version: "13.0.1.1071"
---

# Get-VBRHvVssProvider

In this article

Short Description

Returns VSS providers.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get all VSS providers on Microsoft Hyper-V host.

|  |
| --- |
| Get-VBRHvVssProvider -Server <CHost>  [<CommonParameters>] |

* Get VSS providers by the provider name.

|  |
| --- |
| Get-VBRHvVssProvider -Server <CHost> [-Name <string>]  [<CommonParameters>] |

* Get VSS providers by the provider ID.

|  |
| --- |
| Get-VBRHvVssProvider -Server <CHost> [-Id <guid>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns an array of VSS providers that are available on Microsoft Hyper-V hosts.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Server | Specifies a Microsoft Hyper-V host added to the backup infrastructure. The cmdlet will return VSS providers that are available on this Microsoft Hyper-V host. | Accepts the CHost object. To create this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| Name | Specifies a name of a VSS provider. The cmdlet will return the VSS provider with this name. | String | False | Named | True (ByValue, ByPropertyName) |
| Id | Specifies an ID of a VSS provider. The cmdlet will return the VSS provider with this ID. | Id | False | Named | True (ByValue, ByPropertyName) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRHvVssProvider object that contains an array of VSS providers that are available on a Microsoft Hyper-V host.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting all VSS Providers

|  |  |
| --- | --- |
| This example shows how to get all VSS providers that are available on the hyperv09.tech.local Microsoft Hyper-V host.  |  | | --- | | $server = Get-VBRServer -Name hyperv09.tech.local  Get-VBRHvVssProvider -Server $server |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 2. Run the Get-VBRHvVssProvider cmdlet. Set the $server variable as the Server parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting VSS Provider by Name

|  |  |
| --- | --- |
| This example shows how to get the Microsoft CSV Shadow Copy Helper Provider VSS provider that is available on the hyperv09.tech.local Microsoft Hyper-V host.  |  | | --- | | $server = Get-VBRServer -Name hyperv09.tech.local  Get-VBRHvVssProvider -Server $server -Name "Microsoft CSV Shadow Copy Helper Provider" |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 2. Run the Get-VBRHvVssProvider cmdlet. Set the $server variable as the Server parameter value. Specify the Name parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting VSS Provider by ID

|  |  |
| --- | --- |
| This example shows how to get the 6ca4d514-5f94-4913-800c-48fc0d87c75c VSS provider that is available on the hyperv09.tech.local Microsoft Hyper-V host.  |  | | --- | | $server = Get-VBRServer -Name hyperv09.tech.local  Get-VBRHvVssProvider -Server $server -Id "6ca4d514-5f94-4913-800c-48fc0d87c75c" |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 2. Run the Get-VBRHvVssProvider cmdlet. Set the $server variable as the Server parameter value. Specify the Id parameter value. |

Related Commands

[Get-VBRServer](get-vbrserver.md)

Page updated 3/1/2024

Page content applies to build 13.0.1.1071
