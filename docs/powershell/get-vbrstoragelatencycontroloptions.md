---
title: "Get-VBRStorageLatencyControlOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrstoragelatencycontroloptions.html"
last_updated: "12/18/2023"
product_version: "13.0.1.1071"
---

# Get-VBRStorageLatencyControlOptions


Short Description

Returns storage latency control settings on the production datastores.

Applies to

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRStorageLatencyControlOptions  [<CommonParameters>] |

Detailed Description

This cmdlet returns settings of the storage latency control on the production datastores.

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRLatencyControlOptions object that contains settings of the storage latency control on the production datastores.

Examples

Getting Settings of Storage Latency Control on Production Datastore

This command returns settings of the storage latency control on the production datastore. The cmdlet output will contain the following details on the storage latency control: Enable, LatencyLimitMs, ThrottlingIOLimitMs and AdvancedOptions.

|  |
| --- |
| Get-VBRStorageLatencyControlOptions  Enabled LatencyLimitMs ThrottlingIOLimitMs AdvancedOptions  ------- -------------- ------------------- ---------------   False             20                  30 {} |


