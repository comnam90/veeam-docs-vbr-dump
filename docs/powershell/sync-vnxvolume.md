---
title: "Sync-VNXVolume"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/sync-vnxvolume.html"
last_updated: "2/16/2024"
product_version: "13.0.1.1071"
---

# Sync-VNXVolume

In this article

Short Description

Rescans Dell VNX storage volumes added to the backup infrastructure.

Applies to

Platform: VMware

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Storage System: Dell VNX

Syntax

|  |
| --- |
| Sync-VNXVolume -Volume <CSanVolume[]>  [<CommonParameters>] |

Detailed Description

This cmdlet rescans Dell VNX storage volumes from the backup infrastructure. Veeam Backup & Replication uses this process to synchronize the state of the backup server with storage systems state and to get information about new snapshots created on storage volumes.

Run the [Sync-VNXHost](sync-vnxhost.md) cmdlet to rescan an entire Dell VNX storage system.

|  |
| --- |
| Note: |
| The cmdlet will not notify you in case Veeam Backup & Replication fails to perform a rescan. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Volume | Specifies an array of storage volumes that you want to rescan. | Accepts the CSanVolume[] object. To get this object, run the [Get-VNXVolume](get-vnxvolume.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

Rescanning Dell VNX Storage Volume

This example shows how to rescan a Dell VNX storage volume added to the backup infrastructure.

|  |
| --- |
| $storage = Get-VNXHost -Name "VNX Storage"  $volume = Get-VNXVolume -Name "VOLUME1" -Host $storage  Sync-VNXVolume -Volume $volume |

Perform the following steps:

1. Run the [Get-VNXHost](get-vnxhost.md) cmdlet. Specify the Name parameter value. Save the result to the $storage variable.
2. Run the [Get-VNXVolume](get-vnxvolume.md) cmdlet. Specify the Name parameter value. Set the $storage variable as the Host parameter value. Save the result to the $volume variable.
3. Run the Sync-VNXVolume cmdlet. Set the $volume variable as the Volume parameter value.

Related Commands

* [Get-VNXHost](get-vnxhost.md)
* [Get-VNXVolume](get-vnxvolume.md)

Page updated 2/16/2024

Page content applies to build 13.0.1.1071
