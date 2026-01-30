---
title: "Sync-VBRIsilonVolume"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/sync-vbrisilonvolume.html"
last_updated: "2/9/2024"
product_version: "13.0.1.1071"
---

# Sync-VBRIsilonVolume


Short Description

Rescans Dell PowerScale (formerly Isilon) storage volumes added to the backup infrastructure.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Sync-VBRIsilonVolume -Volume <CSanVolume[]>  [<CommonParameters>] |

Detailed Description

This cmdlet rescans Dell PowerScale storage volumes from the backup infrastructure. Veeam Backup & Replication uses this process to synchronize the state of the backup server with storage systems state and to get information about new snapshots created on storage volumes.

Run the [Sync-VBRIsilonHost](sync-vbrisilonhost.md) cmdlet to rescan an entire Dell PowerScale storage system.

|  |
| --- |
| ![Sync-VBRIsilonVolume](images/icon_note.webp) Note: |
| The cmdlet will not notify you in case Veeam Backup & Replication fails to perform a rescan. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Volume | Specifies an array of storage volumes that you want to rescan. | Accepts the CSanVolume[] object. To get this object, run the [Get-VBRIsilonHost](get-vbrisilonhost.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

Rescanning Dell PowerScale Storage Volume Added to Backup Infrastructure

This example shows how to rescan a Dell PowerScale storage volume added to the backup infrastructure.

|  |
| --- |
| $storage = Get-VBRIsilonHost -Name "Isilon Storage"  $volume = Get-VBRIsilonVolume -Name "VOLUME1" -Host $storage  Sync-VBRIsilonVolume -Volume $volume |

Perform the following steps:

1. Run the [Get-VBRIsilonHost](get-vbrisilonhost.md) cmdlet. Specify the Name parameter value. Save the result to the $storage variable.
2. Run the [Get-VBRIsilonVolume](get-vbrisilonvolume.md) cmdlet. Specify the Name and Host parameter values. Save the result to the $volume variable.
3. Run the Sync-VBRIsilonVolume cmdlet. Set the $volume variable as the Volume parameter value.

Related Commands

* [Get-VBRIsilonHost](get-vbrisilonhost.md)
* [Get-VBRIsilonVolume](get-vbrisilonvolume.md)


