---
title: "Clear-VBRWANCache"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/clear-vbrwancache.html"
last_updated: "5/7/2024"
product_version: "13.0.1.1071"
---

# Clear-VBRWANCache


Short Description

Removes data from WAN accelerator global cache.

Applies to

Platform: VMware, Hyper-V

Product Edition: Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Clear-VBRWANCache -Accelerator <CWanAccelerator>  [<CommonParameters>] |

Detailed Description

This cmdlet clears WAN accelerator global cache.

You may need to clear the global cache, for example, if the data gets corrupted.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Accelerator | Specifies the WAN accelerator. The cmdlet will clear cache of this accelerator. | Accepts the CWanAccelerator object. To get this object, run the [Get-VBRWANAccelerator](get-vbrwanaccelerator.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Creating WAN Accelerator [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to clear cache of the WAN 01 WAN accelerator.  |  | | --- | | Get-VBRWANAccelerator -Name "WAN 01" | Clear-VBRWANCache |  Perform the following steps:   1. Run the [Get-VBRWANAccelerator](get-vbrwanaccelerator.md) cmdlet. Specify the Name parameter value. 2. Pipe the cmdlet output to the Clear-VBRWANCache cmdlet. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Creating WAN Accelerator [Using Variable]

|  |  |
| --- | --- |
| This example shows how to clear cache of the WAN 01 WAN accelerator.  |  | | --- | | $accelerator01 = Get-VBRWANAccelerator -Name "WAN 01"  Clear-VBRWANCache -Accelerator $accelerator01 |  Perform the following steps:   1. Run the [Get-VBRWANAccelerator](get-vbrwanaccelerator.md) cmdlet. Specify the Name parameter value. Save the result to the $accelerator01 variable. 2. Run the Clear-VBRWANCache cmdlet. Set the $accelerator01 variable as the Accelerator parameter value. |

Related Commands

[Get-VBRWANAccelerator](get-vbrwanaccelerator.md)


