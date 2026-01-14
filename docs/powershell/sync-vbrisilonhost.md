---
title: "Sync-VBRIsilonHost"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/sync-vbrisilonhost.html"
last_updated: "2/19/2024"
product_version: "13.0.1.1071"
---

# Sync-VBRIsilonHost

In this article

Short Description

Rescans Dell PowerScale (formerly Isilon) storage system.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Sync-VBRIsilonHost [-Host <CIsilonHost>]  [<CommonParameters>] |

Detailed Description

This cmdlet rescans Dell PowerScale storage systems. During rescan Veeam Backup & Replication retrieves information about the storage system topology and adds storage volumes to the backup infrastructure.

Run the [Sync-VBRIsilonVolume](sync-vbrisilonvolume.md) cmdlet to rescan Dell PowerScale volumes added to the backup infrastructure.

|  |
| --- |
| ![Sync-VBRIsilonHost](images/icon_note.webp) Note: |
| The cmdlet will not notify you in case Veeam Backup & Replication fails to perform a rescan. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Host | Specifies a storage system that you want to rescan. | Accepts the CIsilonHost object. To create this object, run the [Get-VBRIsilonHost](get-vbrisilonhost.md) cmdlet. | False | Named | True (ByValue, ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

Rescanning Dell PowerScale Storage System

This example shows how to rescan a Dell PowerScale storage system.

|  |
| --- |
| $storage = Get-VBRIsilonHost -Name "Isilon Storage"  Sync-VBRIsilonHost -Host $storage |

Perform the following steps:

1. Run the [Get-VBRIsilonHost](get-vbrisilonhost.md) cmdlet. Specify the Name parameter value. Save the result to the $storage variable.
2. Run the Sync-VBRIsilonHost cmdlet. Set the $storage variable as the Host parameter value.

Related Commands

* [Get-VBRIsilonHost](get-vnxhost.md)
* [Sync-VBRIsilonVolume](sync-vbrisilonvolume.md)

Page updated 2/19/2024

Page content applies to build 13.0.1.1071
