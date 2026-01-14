---
title: "Sync-NimbleVolume"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/sync-nimblevolume.html"
last_updated: "2/16/2024"
product_version: "13.0.1.1071"
---

# Sync-NimbleVolume

In this article

Short Description

Rescans HPE Nimble storage volumes added to the backup infrastructure.

Applies to

Platform: VMware

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Sync-NimbleVolume -Volume <CSanVolume[]>  [<CommonParameters>] |

Detailed Description

This cmdlet rescans HPE Nimble storage volumes from the backup infrastructure. Veeam Backup & Replication uses this process to synchronize the state of the backup server with storage systems state and to get information about new snapshots created on storage volumes.

Run the [Sync-NimbleHost](sync-nimblehost.md) cmdlet to rescan an entire HPE Nimble storage system.

|  |
| --- |
| ![Sync-NimbleVolume](images/icon_note.webp) Note: |
| The cmdlet will not notify you in case Veeam Backup & Replication fails to perform a rescan. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Volume | Specifies an array of storage volumes that you want to rescan. | Accepts the CSanVolume[] object. To get this object, run the [Get-NimbleVolume](get-nimblevolume.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

Rescanning HPE Nimble Storage Volume

This example shows how to rescan an HPE Nimble storage volume added to the backup infrastructure.

|  |
| --- |
| $volume = Get-NimbleVolume -Name "VOL01"  Sync-NimbleVolume -Volume $volume |

Perform the following steps:

1. Run the [Get-NimbleVolume](get-nimblevolume.md) cmdlet. Specify the Name parameter value Save the result to the $volume variable.
2. Run the Sync-NimbleVolume cmdlet. Set the $volume variable as the Volume parameter value.

Related Commands

[Get-NimbleVolume](get-nimblevolume.md)

Page updated 2/16/2024

Page content applies to build 13.0.1.1071
