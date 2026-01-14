---
title: "Disable-VBRHvProxy"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/disable-vbrhvproxy.html"
last_updated: "5/17/2024"
product_version: "13.0.1.1071"
---

# Disable-VBRHvProxy

In this article

Short Description

Disables the Hyper-V backup proxy.

Applies to

Platform: Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Disable-VBRHvProxy -Proxy <CHvProxy[]>  [<CommonParameters>] |

Detailed Description

This cmdlet allows you to disable the Hyper-V backup proxy. The disabled proxy is not used by any job.

Run the [Enable-VBRHvProxy](enable-vbrhvproxy.md) cmdlet to enable the Hyper-V backup proxy.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Proxy | Specifies an array of the Hyper-V proxies you want to disable. | Accepts the CHvProxy[] object. To get this object, run the [Get-VBRHvProxy](get-vbrhvproxy.md) cmdlet. | True | Named | True (ByValue, |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the CHvProxy[] that contains an array of Hyper-V backup proxy servers added to the backup infrastructure.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Disabling Hyper-V Backup Proxy [Using Variable]

|  |  |
| --- | --- |
| This example shows how to disable the Hyper-V backup proxy named Local Backup Proxy.  |  | | --- | | $proxy = Get-VBRHvProxy -Name "Local Backup Proxy"  Disable-VBRHvProxy -Proxy $proxy |  Perform the following steps:   1. Run the [Get-VBRHvProxy](get-vbrhvproxy.md)  cmdlet. Specify the Name parameter value. Save the result to the $proxy variable. 2. Run the Disable-VBRHvProxy cmdlet. Set the $proxy variable as the Proxy parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Disabling Hyper-V Backup Proxy [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to disable the Hyper-V backup proxy named Hyper-V Backup Proxy 01.  |  | | --- | | Get-VBRHvProxy -Name "Hyper-V Backup Proxy 01" | Disable-VBRHvProxy |  Perform the following steps:   1. Run the [Get-VBRHvProxy](get-vbrhvproxy.md)  cmdlet. Specify the Name parameter value. 2. Pipe the cmdlet output to the Disable-VBRHvProxy cmdlet. |

Related Commands

[Get-VBRHvProxy](get-vbrhvproxy.md)

Page updated 5/17/2024

Page content applies to build 13.0.1.1071
