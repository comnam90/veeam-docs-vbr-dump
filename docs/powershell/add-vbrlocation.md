---
title: "Add-VBRLocation"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrlocation.html"
last_updated: "3/6/2024"
product_version: "13.0.1.1071"
---

# Add-VBRLocation

In this article

Short Description

Creates a geographic location in Veeam Backup & Replication.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Add-VBRLocation -Name <string>  [<CommonParameters>] |

Detailed Description

This cmdlet creates a geographic location in Veeam Backup & Replication.

Run the [Apply-VBRLocation](apply-vbrlocation.md) cmdlet to assign locations to the backup infrastructure components.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies the name you want to assign to the location.  The maximum length of the location name is 255 characters. | String | True | Named | True (ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRLocation object that contains the geographic location created.

Examples

Creating Geographic Location

This command creates a geographic location in Veeam Backup & Replication.

|  |
| --- |
| Add-VBRLocation -Name "ABC North" |

Related Commands

[Apply-VBRLocation](apply-vbrlocation.md)

Page updated 3/6/2024

Page content applies to build 13.0.1.1071
