---
title: "Connect-VBRHvVirtualLab"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/connect-vbrhvvirtuallab.html"
last_updated: "3/1/2024"
product_version: "13.0.1.1071"
---

# Connect-VBRHvVirtualLab

In this article

Short Description

Adds VMs to Veeam Backup & Replication.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Connect-VBRViVirtualLab -VM <CHvVmItem>  [<CommonParameters>] |

Detailed Description

This cmdlet adds VMs created on Hyper-V to Veeam Backup & Replication.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| VM | Specifies a VM that you want to add to Veeam Backup & Replication. | Accepts the CHvVmItem object. To get this object, run the [Find-VBRHvEntity](find-vbrhventity.md) cmdlet. | True | 0 | True (ByValue, |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

Adding VM to Virtual Lab

This example shows how to add the srv99 VM into Veeam Backup & Replication infrastructure.

|  |
| --- |
| $vm = Find-VBRHvEntity -Name "srv99"  Connect-VBRHvVirtualLab -VM $vm |

Perform the following steps:

1. Run the [Find-VBRHvEntity](find-vbrhventity.md) cmdlet. Specify the Name parameter value. Save the result to the $vm variable.
2. Run the Connect-VBRHvVirtualLab cmdlet. Set the $vm variable as the VM parameter value.

Related Commands

[Find-VBRHvEntity](find-vbrhventity.md)

Page updated 3/1/2024

Page content applies to build 13.0.1.1071
