---
title: "Sync-VNXHost"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/sync-vnxhost.html"
last_updated: "2/16/2024"
product_version: "13.0.1.1071"
---

# Sync-VNXHost


Short Description

Rescans Dell VNX storage system.

Applies to

Platform: VMware

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Storage System: Dell VNX

Syntax

|  |
| --- |
| Sync-VNXHost -Host <CVnxHost>  [<CommonParameters>] |

Detailed Description

This cmdlet rescans Dell VNX storage systems. During rescan Veeam Backup & Replication retrieves information about the storage system topology and adds storage volumes to the backup infrastructure.

Run the [Sync-VNXVolume](sync-vnxvolume.md) cmdlet to rescan Dell VNX volumes added to the backup infrastructure.

|  |
| --- |
| ![Sync-VNXHost](images/icon_note.webp) Note: |
| The cmdlet will not notify you in case Veeam Backup & Replication fails to perform a rescan. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Storage | Specifies a storage system that you want to rescan. | Accepts the CVnxHost object. To get this object, run the [Get-VNXHost](get-vnxhost.md) cmdlet | True | Named | True (ByValue, ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

Rescanning Dell VNX Storage System

This example shows how to rescan a Dell VNX storage system.

|  |
| --- |
| $storage = Get-VNXHost -Name "VNX Storage"  Sync-VNXHost -Storage $storage |

Perform the following steps:

1. Run the [Get-VNXHost](get-vnxhost.md) cmdlet. Specify the Name parameter value. Save the result to the $storage variable.
2. Run the Sync-VNXHost cmdlet. Set the $storage variable as the Storage parameter value.

Related Commands

[Get-VNXHost](get-vnxhost.md)


