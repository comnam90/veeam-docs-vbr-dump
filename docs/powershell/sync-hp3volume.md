---
title: "Sync-HP3Volume"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/sync-hp3volume.html"
last_updated: "2/16/2024"
product_version: "13.0.1.1071"
---

# Sync-HP3Volume

In this article

Short Description

Rescans HPE 3PAR StoreServ storage volumes added to the backup infrastructure.

Applies to

Platform: VMware

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Storage System: HPE 3PAR StoreServ

Syntax

|  |
| --- |
| Sync-HP3Volume -Volume <CSanVolume[]>  [<CommonParameters>] |

Detailed Description

This cmdlet rescans HPE 3PAR StoreServ storage volumes from the backup infrastructure. Veeam Backup & Replication uses this process to synchronize the state of the backup server with storage systems state and to get information about new snapshots created on storage volumes.

Run the [Sync-HP3Storage](sync-hp3storage.md) cmdlet to rescan an entire HPE 3PAR StoreServ storage system.

|  |
| --- |
| ![Sync-HP3Volume](images/icon_note.webp) Note: |
| The cmdlet will not notify you in case Veeam Backup & Replication fails to perform a rescan. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Volume | Specifies an array of storage volumes that you want to rescan. | Accepts the CSanVolume[] object. To get this object, run the [Get-HP3Volume](get-hp3volume.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

Rescanning HPE 3PAR StoreServ Storage Volume

This example shows how to rescan an HPE 3PAR StoreServ storage volume added to the backup infrastructure.

|  |
| --- |
| $storage = Get-HP3Storage -Name "HPE 3PAR StoreServe Storage"  $volume = Get-HP3Volume -Storage $storage  Sync-HP3Volume -Volume $volume |

Perform the following steps:

1. Run the [Get-HP3Storage](get-hp3storage.md) cmdlet. Specify the Name parameter value. Save the result to the $storage variable.
2. Run the [Get-HP3Volume](get-hp3volume.md) cmdlet. Set the $storage variable as the Storage parameter value. Save the result to the $volume variable.
3. Run the Sync-HP3Volume cmdlet. Set the $volume variable as the Volume parameter value.

Related Commands

* [Get-HP3Storage](get-hp3storage.md)
* [Get-HP3Volume](get-hp3volume.md)

Page updated 2/16/2024

Page content applies to build 13.0.1.1071
