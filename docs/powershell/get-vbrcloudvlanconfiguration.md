---
title: "Get-VBRCloudVLANConfiguration"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrcloudvlanconfiguration.html"
last_updated: "9/7/2023"
product_version: "13.0.1.1071"
---

# Get-VBRCloudVLANConfiguration

In this article

Short Description

Returns reserved VLAN ranges.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Requires a VCP license.

Syntax

|  |
| --- |
| Get-VBRCloudVLANConfiguration  [<CommonParameters>] |

Detailed Description

This cmdlet returns the array of the [VBRCloudVLANConfiguration](vbrcloudvlanconfiguration.md) objects. These objects contain VLAN ranges reserved for Veeam Backup & Replication.

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRCloudVLANConfiguration](vbrcloudvlanconfiguration.md)

Examples

Getting All Configured VLANs

This command returns all configured VLANs.

|  |
| --- |
| Get-VBRCloudVLANConfiguration |

Page updated 9/7/2023

Page content applies to build 13.0.1.1071
