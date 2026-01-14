---
title: "Find-VBRObject (obsolete)"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/find-vbrobject.html"
last_updated: "3/11/2024"
product_version: "13.0.1.1071"
---

# Find-VBRObject (obsolete)

In this article

Short Description

Returns a list of all VMs and VM containers on the specified ESXi host.

|  |
| --- |
| Note |
| This cmdlet is obsolete. The cmdlet still works, but it is recommended to rewrite your scripts using the [Find-VBRViEntity](find-vbrvientity.md) and [Find-VBRHvEntity](find-vbrhventity.md) cmdlets. |

Applies to

Platform: VMware

Syntax

|  |
| --- |
| Find-VBRObject -Server <CHost> [-Name <String[]>] [-WarningAction <ActionPreference>] [-WarningVariable <String>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns a list of all VMs and VM containers on the specified ESXi host.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Server | Specifies the host you want to look for objects on. | Accepts the CHost object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | True | 1 | True (ByValue, ByProperty Name) |
| Name | Specifies the name of the object you want to get, or search conditions.  You can specify multiple names separated by commas. | String[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All Objects on ServerBackup File to Specific Folder

|  |  |
| --- | --- |
| This example shows how to look for all objects registered on the VMwareHost server.  |  | | --- | | Get-VBRBackup -Name "VMwareHost" | Find-VBRObject |  Perform the following steps:   1. Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. 2. Pipe the cmdlet output to the Find-VBRObject cmdlet. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting All Objects on ServerBackup File to Specific Folder

|  |  |
| --- | --- |
| This example shows how to look for all objects registered on the VMwareHost server.  |  | | --- | | $server = Get-VBRServer -Name "srv001"  Find-VBRObject -Server $server -Name "VM01", "VM03" |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 2. Run the Find-VBRObject cmdlet. Set the $server variable as the Server parameter value. Specify the Name parameter value. |

Related Commands

[Get-VBRServer](get-vbrserver.md)

Page updated 3/11/2024

Page content applies to build 13.0.1.1071
