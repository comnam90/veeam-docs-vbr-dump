---
title: "Get-VBRWANAccelerator"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrwanaccelerator.html"
last_updated: "5/7/2024"
product_version: "13.0.1.1071"
---

# Get-VBRWANAccelerator

In this article

Short Description

Returns WAN accelerators.

Applies to

Platform: VMware, Hyper-V

Product Edition: Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRWANAccelerator [-Name <String[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet gets WAN accelerators managed by Veeam Backup & Replication.

WAN accelerator is an architecture component that optimizes file transfer via WAN by means of data deduplication. The role of a WAN accelerator can be assigned to a dedicated Windows-based machine (physical or virtual). For best performance you should set a WAN accelerator on both source and target sides.

You can get the list of all WAN accelerators, or search for instances directly by name.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies the array of WAN accelerator names. The cmdlet will return WAN accelerators with these names. | String[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[CwanAccelerator](cwanaccelerator.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All WAN Accelerators

|  |  |
| --- | --- |
| This command looks for the list of all WAN accelerators.  |  | | --- | | Get-VBRWANAccelerator | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting WAN Accelerator by Name

|  |  |
| --- | --- |
| This command looks for WAN accelerators with the names starting with WAN.  |  | | --- | | Get-VBRWANAccelerator -Name WAN\* | |

Page updated 5/7/2024

Page content applies to build 13.0.1.1071
