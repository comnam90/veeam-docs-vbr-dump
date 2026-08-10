---
title: "Get-VBRNodeExporterOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrnodeexporteroptions.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Get-VBRNodeExporterOptions


Short Description

Returns node exporter metrics for Veeam Software Appliance.

Applies to

Product Edition: Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRNodeExporterOptions [<CommonParameters>] |

Detailed Description

This cmdlet returns the node exporter metrics for Veeam Software Appliance. These metrics contain current configuration details such as authentication type, TLS settings, and access credentials. Use it to monitor resource consumption or collect system events.

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRNodeExporterOptions object that contains node exporter metrics for Veeam Software Appliance.

Examples

Getting Node Exporter Metrics for Veeam Software Appliance

This command returns node exporter metrics for Veeam Software Appliance.

|  |
| --- |
| Get-VBRNodeExporterOptions |

Page updated 2026-06-24

