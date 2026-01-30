---
title: "Remove-VBRAdvancedLatencyOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/remove-vbradvancedlatencyoptions.html"
last_updated: "2/14/2024"
product_version: "13.0.1.1071"
---

# Remove-VBRAdvancedLatencyOptions


Short Description

Removes datastore latency settings from Veeam Backup & Replication settings.

Applies to

Product Edition: Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Remove-VBRAdvancedLatencyOptions -Options <VBRAdvancedLatencyOptions>  [<CommonParameters>] |

Detailed Description

This cmdlet removes datastore latency settings from Veeam Backup & Replication general settings.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Options | Specifies the datastore latency settings that you want to remove. | Accepts the VBRAdvancedLatencyOptions object. To create this object, run the [Get-VBRAdvancedLatencyOptions](get-vbradvancedlatencyoptions.md) cmdlet. | True | Named | True (ByValue, |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Removing Datastore Latency Settings

This example shows how to remove datastore latency settings from Veeam Backup & Replication general settings.

|  |
| --- |
| $latency = Get-VBRAdvancedLatencyOptions  Remove-VBRAdvancedLatencyOptions -Options $latency |

Perform the following steps:

1. Run the [Get-VBRAdvancedLatencyOptions](get-vbradvancedlatencyoptions.md) cmdlet. Save the result to the $latency variable.
2. Run the Remove-VBRAdvancedLatencyOptions cmdlet. Set the $latency variable as the Options parameter value.

Related Commands

[Get-VBRAdvancedLatencyOptions](get-vbradvancedlatencyoptions.md)


