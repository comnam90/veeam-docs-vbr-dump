---
title: "Get-VBRADForest"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbradforest.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Get-VBRADForest


Short Description

Returns Microsoft Active Directory forests in your infrastructure.

Applies to

Platform: VMware, Hyper-V

Product Edition: Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRADForest [<CommonParameters>] |

Detailed Description

This cmdlet returns all Microsoft Active Directory forests that are available for restore in your infrastructure.

Parameters

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the [VBRADForest](vbradforest.md)[] object that contains information about the Microsoft Active Directory forest.

Example

Getting All Microsoft Active Directory Forests

This command returns all Microsoft Active Directory forests in your infrastructure.

|  |
| --- |
| Get-VBRADForest |

Page updated 2026-07-28

