---
title: "Sync-StoragePluginHost"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/sync-storagepluginhost.html"
last_updated: "3/4/2024"
product_version: "13.0.1.1071"
---

# Sync-StoragePluginHost

In this article

Short Description

Rescans Universal Storage API integrated systems.

Applies to

Platform: VMware

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Storage System: IBM Spectrum Virtualize, INFINIDAT InfiniBox, Pure Storage

Syntax

|  |
| --- |
| Sync-StoragePluginHost -Host <CPublicPluginHost>  [<CommonParameters>] |

Detailed Description

This cmdlet rescans Universal Storage API integrated systems. During rescan Veeam Backup & Replication retrieves information about the storage system topology and adds storage volumes to the backup infrastructure.

Run the [Sync-StoragePluginVolume](sync-storagepluginvolume.md) cmdlet to rescan Universal Storage API volumes added to the backup infrastructure.

|  |
| --- |
| ![Sync-StoragePluginHost](images/icon_note.webp) Note: |
| The cmdlet will not notify you in case Veeam Backup & Replication fails to perform a rescan. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Host | Specifies a storage system that you want to rescan. | Accepts the CPublicPluginHost object. To get this object, run the [Get-StoragePluginHost](get-storagepluginhost.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

Rescanning Universal Storage API Integrated System

This example shows to how to rescan Universal Storage API integrated system.

|  |
| --- |
| $storage = Get-StoragePluginHost -Name "IBM Spectrum"  Sync-StoragePluginHost -Host $storage |

Perform the following steps:

1. Run the [Get-StoragePluginHost](get-storagepluginhost.md) cmdlet. Specify the Name parameter value. Save the result to the $storage variable.
2. Run the Sync-StoragePluginHost cmdlet. Set the $storage variable as the Host parameter value.

Related Commands

[Get-StoragePluginHost](get-storagepluginhost.md)

Page updated 3/4/2024

Page content applies to build 13.0.1.1071
