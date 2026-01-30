---
title: "Enable-VBRViProxy"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/enable-vbrviproxy.html"
last_updated: "5/17/2024"
product_version: "13.0.1.1071"
---

# Enable-VBRViProxy


Short Description

Enables a disabled VMware backup proxy.

Applies to

Platform: VMware

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Enable-VBRViProxy -Proxy <CViProxy[]>  [<CommonParameters>] |

Detailed Description

This cmdlet allows you to enable a VMware backup proxy.

Run the [Disable-VBRViProxy](disable-vbrviproxy.md) cmdlet to disable a VMware backup proxy.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Proxy | Specifies an array of VMware proxies you want to enable. | Accepts the CViProxy[] object. To get this object, run the [Get-VBRViProxy](get-vbrviproxy.md) cmdlet. | True | Named | True (ByValue, |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the CViProxy[] that contains an array of VMware backup proxy servers added to the backup infrastructure.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Enabling VMware Backup Proxy [Using Variable]

|  |  |
| --- | --- |
| This example shows how to enable the VMware backup proxy named Local Backup Repository.  |  | | --- | | $proxy = Get-VBRViProxy -Name "Local Backup Proxy"  Enable-VBRViProxy -Proxy $proxy |  Perform the following steps:   1. Run the [Get-VBRViProxy](get-vbrviproxy.md) cmdlet. Specify the Name parameter value. Save the result to the $proxy variable. 2. Run the Enable-VBRViProxy cmdlet. Set the $proxy variable as the Proxy parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Enabling VMware Backup Proxy [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to enable the VMware backup proxy named VMware Backup Proxy 01.  |  | | --- | | Get-VBRViProxy -Name "VMware Backup Proxy 01" | Enable-VBRViProxy |  Perform the following steps:   1. Run the [Get-VBRViProxy](get-vbrviproxy.md) cmdlet. Specify the Name parameter value. 2. Pipe the cmdlet output to the Enable-VBRViProxy cmdlet. |

Related Commands

[Get-VBRViProxy](get-vbrviproxy.md)


