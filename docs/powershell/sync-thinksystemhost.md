---
title: "Sync-ThinkSystemHost"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/sync-thinksystemhost.html"
last_updated: "2/16/2024"
product_version: "13.0.1.1071"
---

# Sync-ThinkSystemHost


Short Description

Rescans ThinkSystem storage systems.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Sync-ThinkSystemHost [-Host <CNaHost>]  [<CommonParameters>] |

Detailed Description

This cmdlet rescans ThinkSystem storage systems. During a rescan Veeam Backup & Replication, retrieves information about the storage system topology and adds storage volumes to the backup infrastructure.

Run the [Sync-ThinkSystemVolume](sync-thinksystemvolume.md) cmdlet to rescan ThinkSystem volumes added to the backup infrastructure.

|  |
| --- |
| ![Sync-ThinkSystemHost](images/icon_note.webp) Note: |
| The cmdlet will not notify you in case Veeam Backup & Replication fails to perform a rescan. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Host | Specifies a storage system that you want to rescan. | Accepts the CNaHost object. To create this object, run the [Get-ThinkSystemHost](get-thinksystemhost.md) cmdlet | False | Named | True (ByValue, ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

Rescanning ThinkSystem Storage Systems

This example shows how to rescan ThinkSystem storage systems.

|  |
| --- |
| $storage = Get-ThinkSystemHost -Name "ThinkSystem Store 01"  Sync-ThinkSystemHost -Host $storage |

Perform the following steps:

1. Run the [Get-ThinkSystemHost](get-thinksystemhost.md) cmdlet. Specify the Name parameter value.  Save the result to the $storage variable.
2. Run the Sync-ThinkSystemHost cmdlet. Set the $storage variable as the Host parameter value.

Related Commands

[Get-ThinkSystemHost](get-thinksystemhost.md)


