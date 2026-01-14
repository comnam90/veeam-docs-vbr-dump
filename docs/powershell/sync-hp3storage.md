---
title: "Sync-HP3Storage"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/sync-hp3storage.html"
last_updated: "2/16/2024"
product_version: "13.0.1.1071"
---

# Sync-HP3Storage

In this article

Short Description

Rescans HPE 3PAR StoreServ storage systems.

Applies to

Platform: VMware

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Storage System: HPE 3PAR StoreServ

Syntax

|  |
| --- |
| Sync-HP3Storage [-Storage <CHp3PARHost>]  [<CommonParameters>] |

Detailed Description

This cmdlet rescans HPE 3PAR StoreServ storage systems. During rescan Veeam Backup & Replication retrieves information about the storage system topology and adds storage volumes to the backup infrastructure.

Run the [Sync-HP3Volume](sync-hp3volume.md) cmdlet to rescan HPE 3PAR StoreServ volumes added to the backup infrastructure.

|  |
| --- |
| ![Sync-HP3Storage](images/icon_note.webp) Note: |
| The cmdlet will not notify you in case Veeam Backup & Replication fails to perform a rescan. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Storage | Specifies a storage system that you want to rescan. | Accepts the CHp3PARHost object. To get this object, run the [Get-HP3Storage](get-hp3storage.md) cmdlet. | False | Named | True (ByValue, ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

Rescanning HPE 3PAR StoreServ Storage System

This example shows how to rescan an HPE 3PAR StoreServ storage system.

|  |
| --- |
| Get-HP3Storage -Name "HPE Store 01"  Sync-HP3Storage -Storage $storage |

Perform the following steps:

1. Run the [Get-HP3Storage](get-hp3storage.md) cmdlet. Specify the Name parameter value. Save the result to the $storage variable.
2. Run the Sync-HP3Storage cmdlet. Set the $storage variable as the Storage parameter value.

Related Commands

[Get-HP3Storage](get-hp3storage.md)

Page updated 2/16/2024

Page content applies to build 13.0.1.1071
