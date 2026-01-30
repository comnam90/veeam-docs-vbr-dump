---
title: "Find-VBRResourcePool (obsolete)"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/find-vbrresourcepool.html"
last_updated: "3/11/2024"
product_version: "13.0.1.1071"
---

# Find-VBRResourcePool (obsolete)


Short Description

Looks for VMware resource pools.

|  |
| --- |
| Note |
| This cmdlet is obsolete. The cmdlet still works, but it is recommended to rewrite your scripts using the [Find-VBRViResourcePool](find-vbrviresourcepool.md) cmdlet. |

Applies to

Platform: VMware

Syntax

|  |
| --- |
| Find-VBRResourcePool -Server <CHost> [-Name <String[]>] [-WarningAction <ActionPreference>] [-WarningVariable <String>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns a list of all VMware resource pools on the specified ESXi host.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Server | Specifies the host you want to look for resource pool on. | Accepts the CHost object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | True | 1 | True (ByValue, ByProperty Name) |
| Name | Specifies the name of the resource pool you want to get, or search conditions.  You can specify multiple names separated by commas. | String[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Related Commands

[Get-VBRServer](get-vbrserver.md)


