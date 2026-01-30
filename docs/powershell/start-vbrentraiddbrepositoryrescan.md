---
title: "Start-VBREntraIDDBRepositoryRescan"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/start-vbrentraiddbrepositoryrescan.html"
last_updated: "12/19/2024"
product_version: "13.0.1.1071"
---

# Start-VBREntraIDDBRepositoryRescan


Short Description

Starts rescan of the repository where the Microsoft Entra ID tenant backups are stored.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Start-VBREntraIDDBRepositoryRescan  [<CommonParameters>] |

Detailed Description

This cmdlet rescans the repository where the Entra ID tenant backups are stored.

Parameters

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

This cmdlet returns the VBRSession object that defines properties of the rescan session.

Examples

Rescanning Repository with Tenant Backups

This example shows how to rescan the repository where the tenant backups are stored.

|  |
| --- |
| Start-VBREntraIDDBRepositoryRescan |


