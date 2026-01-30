---
title: "Sync-NimbleHost"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/sync-nimblehost.html"
last_updated: "4/22/2024"
product_version: "13.0.1.1071"
---

# Sync-NimbleHost


Short Description

Rescans HPE Nimble storage systems.

Applies to

Platform: VMware

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Sync-NimbleHost -Host <CNimbleHost>  [<CommonParameters>] |

Detailed Description

This cmdlet rescans HPE Nimble storage systems. During rescan Veeam Backup & Replication retrieves information about the storage system topology and adds storage volumes to the backup infrastructure.

Run the [Sync-NimbleVolume](sync-nimblevolume.md) cmdlet to rescan Dell VNX volumes added to the backup infrastructure.

|  |
| --- |
| Note |
| The cmdlet will not notify you in case Veeam Backup & Replication fails to perform a rescan. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Host | Specifies a storage system that you want to rescan. | Accepts the CNimbleHost object. To get this object, run the [Get-NimbleHost](get-nimblehost.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

Rescanning HPE Nimble Storage System

This example shows how to rescan a HPE Nimble storage system.

1. Run the [Get-NimbleHost](get-nimblehost.md) cmdlet. Specify the Name parameter value. Save the result to the $storage variable.
2. Run the Sync-NimbleHost cmdlet. Set the $storage variable as the Storage parameter value.

|  |
| --- |
| $storage = Get-NimbleHost -Name "HPE Nimble-FC"  Sync-NimbleHost -Host $storage |

Related Commands

[Get-NimbleHost](get-nimblehost.md)


