---
title: "Sync-StoragePluginVolume"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/sync-storagepluginvolume.html"
last_updated: "2/16/2024"
product_version: "13.0.1.1071"
---

# Sync-StoragePluginVolume


Short Description

Rescans volumes of Universal Storage API integrated systems.

Applies to

Platform: VMware

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Storage System: IBM Spectrum Virtualize, INFINIDAT InfiniBox, Pure Storage

Syntax

|  |
| --- |
| Sync-StoragePluginVolume -Volume <CSanVolume[]>  [<CommonParameters>] |

Detailed Description

This cmdlet rescans volumes of Universal Storage API integrated systems added to the backup infrastructure. Veeam Backup & Replication uses this process to synchronize the state of the backup server with storage systems state and to get information about new snapshots created on storage volumes.

Run the [Sync-StoragePluginHost](sync-storagepluginhost.md) cmdlet to rescan an Universal Storage API integrated systems.

|  |
| --- |
| ![Sync-StoragePluginVolume](images/icon_note.webp) Note: |
| The cmdlet will not notify you in case Veeam Backup & Replication fails to perform a rescan. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Volume | Specifies an array of storage volumes that you want to rescan. | Accepts the CSanVolume[] object. To get this object, run the Get-StoragePluginVolume cmdlet. | True | Named | True (ByValue, ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

Rescanning Universal Storage API Integrated System Volume

This example shows how to rescan a Universal Storage API integrated systems volume added to the backup infrastructure.

|  |
| --- |
| $volume = Get-StoragePluginVolume -Name "VOLUME-01"  Sync-StoragePluginVolume -Volume $volume |

Perform the following steps:

1. Run the [Get-StoragePluginVolume](get-storagepluginvolume.md) cmdlet. Specify the Name parameter value. Save the result to the $volume variable.
2. Run the Sync-StoragePluginVolume cmdlet. Set the $volume variable as the Volume parameter value.

Related Commands

[Get-StoragePluginVolume](get-storagepluginvolume.md)


