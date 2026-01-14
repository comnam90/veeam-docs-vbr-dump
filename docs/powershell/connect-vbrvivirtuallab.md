---
title: "Connect-VBRViVirtualLab"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/connect-vbrvivirtuallab.html"
last_updated: "3/1/2024"
product_version: "13.0.1.1071"
---

# Connect-VBRViVirtualLab

In this article

Short Description

Adds VMs to Veeam Backup & Replication.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Connect-VBRViVirtualLab -VM <CViVmItem>  [<CommonParameters>] |

Detailed Description

This cmdlet adds VMs created on VMware to Veeam Backup & Replication.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| VM | Specifies a VM that you want to add to Veeam Backup & Replication. | Accepts the CViVmItem object. To get this object, run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. | True | 0 | True (ByValue, |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

Adding VM to Virtual Lab

This example shows how to add the Oracle05 VM created on VMware into Veeam Backup & Replication infrastructure.

|  |
| --- |
| $vm = Find-VBRViEntity -Name "Oracle05"  Connect-VBRViVirtualLab -VM $vm |

Perform the following steps:

1. Run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. Specify the Name parameter value. Save the result to the $vm variable.
2. Run the Connect-VBRViVirtualLab cmdlet. Set the $vm variable as the VM parameter value.

Related Commands

[Find-VBRViEntity](find-vbrvientity.md)

Page updated 3/1/2024

Page content applies to build 13.0.1.1071
