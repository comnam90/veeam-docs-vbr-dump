---
title: "Set-VBRVmBiosUuid"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrvmbiosuuid.html"
last_updated: "11/10/2025"
product_version: "13.0.1.1071"
---

# Set-VBRVmBiosUuid

In this article

Short Description

Collects MORef IDs.

Applies to

Platform: VMware

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRVmBiosUuid -VCenterName <String>  [<CommonParameters>] |

Detailed Description

This cmdlet modifies the BIOS UUIDs of existing VM entries within the Veeam Backup & Replication configuration database based on information from the specified vCenter.

BIOS UUIDs will not be modified if they are already up to date.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| VCenterName | Specifies VMware vCenter name which VMs MORef IDs you want to collect. | String | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns VMs MORef IDs of the specified VMware vCenter.

Examples

Collecting VMs MORef IDs

This example shows how to collect MORef IDs of VMs stored in VMware vCenter named vcenter70.

|  |
| --- |
| Set-VBRVmBiosUuid -VCenterName "vcenter70" |

Page updated 11/10/2025

Page content applies to build 13.0.1.1071
