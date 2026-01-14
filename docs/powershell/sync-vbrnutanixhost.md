---
title: "Sync-VBRNutanixHost"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/sync-vbrnutanixhost.html"
last_updated: "2/16/2024"
product_version: "13.0.1.1071"
---

# Sync-VBRNutanixHost

In this article

Short Description

Rescans Nutanix Files storage systems.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Sync-VBRNutanixHost [-Host <CNutanixHost>]  [<CommonParameters>] |

Detailed Description

This cmdlet rescans Nutanix Files storage systems. During rescan Veeam Backup & Replication retrieves information about the storage system topology and adds storage volumes to the backup infrastructure.

Run the [Sync-VBRNutanixVolume](sync-vbrnutanixvolume.md) cmdlet to rescan Nutanix Files volumes added to the backup infrastructure.

|  |
| --- |
| Note |
| The cmdlet will not notify you in case Veeam Backup & Replication fails to perform a rescan. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Host | Specifies the storage system that you want to rescan. | Accepts the CNutanixHost object. To create this object, run the [Get-VBRNutanixHost](get-vbrnutanixhost.md) cmdlet. | False | Named | True (ByValue, |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

Returns the CBaseSession object that defines session properties.

Examples

Rescanning Nutanix Files Storage Systems

This example shows how to rescan Nutanix Files storage systems.

|  |
| --- |
| $storage = Get-VBRNutanixHost -Name "NetApp Store 01"  Sync-VBRNutanixHost -Host $storage |

Perform the following steps:

1. Run the [Get-VBRNutanixHost](get-vbrnutanixhost.md) cmdlet. Specify the Name parameter value. Save the result to the $storage variable.
2. Run the Sync-VBRNutanixHost cmdlet. Set the $storage variable as the Host parameter value.

Related Commands

[Get-VBRNutanixHost](get-vbrnutanixhost.md)

Page updated 2/16/2024

Page content applies to build 13.0.1.1071
