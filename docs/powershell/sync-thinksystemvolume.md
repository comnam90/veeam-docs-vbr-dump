---
title: "Sync-ThinkSystemVolume"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/sync-thinksystemvolume.html"
last_updated: "2/16/2024"
product_version: "13.0.1.1071"
---

# Sync-ThinkSystemVolume


Short Description

Rescans ThinkSystem storage volumes added to the backup infrastructure.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Sync-ThinkSystemVolume -Volume <CSanVolume[]>  [<CommonParameters>] |

Detailed Description

This cmdlet rescans ThinkSystem storage volumes from the backup infrastructure. Veeam Backup & Replication uses this process to synchronize the state of the backup server with storage systems state and to get information about new snapshots created on storage volumes.

Run the [Sync-ThinkSystemHost](sync-thinksystemhost.md) cmdlet to rescan an entire ThinkSystem storage system.

|  |
| --- |
| ![Sync-ThinkSystemVolume](images/icon_note.webp) Note: |
| The cmdlet will not notify you in case Veeam Backup & Replication fails to perform a rescan. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Volume | Specifies an array of storage volumes that you want to rescan. | Accepts the CSanVolume object. To create this object, run the [Get-ThinkSystemVolume](get-thinksystemvolume.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

Rescanning ThinkSystem Storage Volume

This example shows how to rescan a ThinkSystem storage volume added to the backup infrastructure.

|  |
| --- |
| $volume = Get-ThinkSystemVolume -Name "VOL01"  Sync-ThinkSystemVolume -Volume $volume |

Perform the following steps:

1. Run the [Get-ThinkSystemVolume](get-thinksystemvolume.md) cmdlet. Specify the Name parameter value. Save the result to the $volume variable.
2. Run the Sync-ThinkSystemVolume cmdlet. Set the $volume variable as the Volume parameter value.

Related Commands

[Get-ThinkSystemVolume](get-thinksystemvolume.md)


