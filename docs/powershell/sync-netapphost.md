---
title: "Sync-NetAppHost"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/sync-netapphost.html"
last_updated: "5/12/2025"
product_version: "13.0.1.1071"
---

# Sync-NetAppHost

In this article

Short Description

Rescans NetApp storage systems.

Applies to

Platform: VMware

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Sync-NetAppHost [-Host <CNaHost>]  [<CommonParameters>] |

Detailed Description

This cmdlet rescans NetApp storage systems. During a rescan Veeam Backup & Replication, retrieves information about the storage system topology and adds storage volumes to the backup infrastructure.

Run the [Sync-NetAppVolume](sync-netappvolume.md) cmdlet to rescan NetApp volumes added to the backup infrastructure.

|  |
| --- |
| ![Sync-NetAppHost](images/icon_note.webp) Note: |
| The cmdlet will not notify you in case Veeam Backup & Replication fails to perform a rescan. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Host | Specifies a storage system that you want to rescan. | Accepts the CNaHost object. To get this object, run the [Get-NetAppHost](get-netapphost.md) cmdlet. | False | Named | True (ByValue, ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

Rescanning NetApp Storage Systems

This example shows how to rescan NetApp storage systems.

|  |
| --- |
| $storage = Get-NetAppHost -Name "NetApp Store 01"  Sync-NetAppHost -Host $storage |

Perform the following steps:

1. Run the [Get-NetAppHost](get-netapphost.md) cmdlet. Specify the Name parameter value. Save the result to the $storage variable.
2. Run the Sync-NetAppHost cmdlet. Set the $storage variable as the Host parameter value.

Related Commands

[Get-NetAppHost](get-netapphost.md)

Page updated 5/12/2025

Page content applies to build 13.0.1.1071
