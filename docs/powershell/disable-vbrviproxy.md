---
title: "Disable-VBRViProxy"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/disable-vbrviproxy.html"
last_updated: "4/18/2024"
product_version: "13.0.1.1071"
---

# Disable-VBRViProxy

In this article

Short Description

Disables a VMware backup proxy.

Applies to

Platform: VMware

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Disable-VBRViProxy -Proxy <CViProxy[]>  [<CommonParameters>] |

Detailed Description

This cmdlet allows you to temporarily disable a VMware backup proxy. The disabled proxy is not used by any job.

Run the [Enable-VBRViProxy](enable-vbrviproxy.md) cmdlet to enable a VMware backup proxy.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Proxy | Specifies an array of VMware proxies you want to disable. | Accepts the CViProxy[] object. To get this object, run the [Get-VBRViProxy](get-vbrviproxy.md) cmdlet. | True | Named | True (ByValue, |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the CViProxy[] that contains an array of VMware backup proxy servers added to the backup infrastructure.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Disabling VMware Backup Proxy [Using Variable]

|  |  |
| --- | --- |
| This example shows how to disable the VMware backup proxy named Local Backup Proxy.  |  | | --- | | $proxy = Get-VBRViProxy -Name "Local Backup Proxy"  Disable-VBRViProxy -Proxy $proxy |  Perform the following steps:   1. Run the [Get-VBRViProxy](get-vbrviproxy.md) cmdlet. Specify the Name parameter value. Save the result to the $proxy variable. 2. Run the Disable-VBRViProxy cmdlet. Set the $proxy variable as the Proxy parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Disabling VMware Backup Proxy [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to disable the VMware backup proxy named VMware Backup Proxy 01.  |  | | --- | | Get-VBRViProxy -Name "VMware Backup Proxy 01" | Disable-VBRViProxy |  Perform the following steps:   1. Run the [Get-VBRViProxy](get-vbrviproxy.md) cmdlet. Specify the Name parameter value. 2. Pipe the cmdlet output to the Disable-VBRViProxy cmdlet. |

Related Commands

[Get-VBRViProxy](get-vbrviproxy.md)

Page updated 4/18/2024

Page content applies to build 13.0.1.1071
