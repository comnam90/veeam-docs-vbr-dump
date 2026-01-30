---
title: "Remove-VBRHighAvailabilityCluster"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/remove-vbrhighavailabilitycluster.html"
last_updated: "10/20/2025"
product_version: "13.0.1.1071"
---

# Remove-VBRHighAvailabilityCluster


Short Description

Disassembles an HA cluster.

Applies to

Product Edition: Premium

Syntax

|  |
| --- |
| Remove-VBRHighAvailabilityCluster [-RunAsync]  [<CommonParameters>] |

Detailed Description

This cmdlet disassembles an HA cluster.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Disassembling HA cluster

This command disassembles the HA cluster.

|  |
| --- |
| Remove-VBRHighAvailabilityCluster -RunAsync |


