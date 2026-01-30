---
title: "Sync-VBRNutanixVolume"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/sync-vbrnutanixvolume.html"
last_updated: "2/16/2024"
product_version: "13.0.1.1071"
---

# Sync-VBRNutanixVolume


Short Description

Rescans Nutanix Files volumes added to the backup infrastructure.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Sync-VBRNutanixVolume -Volume <CSanVolume[]>  [<CommonParameters>] |

Detailed Description

This cmdlet rescans Nutanix Files volumes added to the backup infrastructure. Veeam Backup & Replication uses this process to synchronize the state of the backup server with storage systems state and to get information about new snapshots created on the volumes.

Run the [Sync-VBRNutanixHost](sync-vbrnutanixhost.md) cmdlet to rescan the entire Nutanix Files storage system.

|  |
| --- |
| Note |
| The cmdlet will not notify you in case Veeam Backup & Replication fails to perform rescan. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Volume | Specifies an array of storage volumes that you want to rescan. | Accepts the CSanVolume[] object. To create this object, run the [Get-VBRNutanixVolume](get-vbrnutanixvolume.md) cmdlet. | True | Named | True (ByValue, |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

Returns the CBaseSession[] objects that define session properties.

Examples

Rescanning Nutanix Files Storage Volume

This example shows how to rescan a Nutanix Files storage volume added to the backup infrastructure.

|  |
| --- |
| $volume = Get-VBRNutanixVolume -Name "VOL01"  Sync-VBRNutanixVolume -Volume $volume |

Perform the following steps:

1. Run the [Get-VBRNutanixVolume](get-vbrnutanixvolume.md) cmdlet. Specify the Name parameter value. Save the result to the $volume variable.
2. Run the Sync-VBRNutanixVolume cmdlet. Set the $volume variable as the Volume parameter value.

Related Commands

[Get-VBRNutanixVolume](get-vbrnutanixvolume.md)


