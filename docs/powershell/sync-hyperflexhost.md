---
title: "Sync-HyperFlexHost"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/sync-hyperflexhost.html"
last_updated: "8/14/2024"
product_version: "13.0.1.1071"
---

# Sync-HyperFlexHost


Short Description

Rescans Cisco HyperFlex storage system.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Sync-HyperFlexHost [-Host <CCiscoHxHost>]  [<CommonParameters>] |

Detailed Description

This cmdlet rescans Cisco HyperFlex storage systems. During rescan Veeam Backup & Replication retrieves information about the storage system topology and adds storage volumes to the backup infrastructure.

|  |
| --- |
| Note |
| The cmdlet will not notify you in case Veeam Backup & Replication fails to perform a rescan. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Host | Specifies a storage system that you want to rescan. | Accepts the CCiscoHxHost object. To get this object, run the [Get-HyperFlexHost](get-hyperflexhost.md) cmdlet. | False | Named | True (ByValue, |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

Rescanning Cisco HyperFlexSystem

This example shows how to rescan the HX Storage Cisco HyperFlex storage system.

|  |
| --- |
| $storage = Get-HyperFlexHost -Name "HX Storage"  Sync-HyperFlexHost -Host $storage |

Perform the following steps:

1. Run the [Get-HyperFlexHost](get-hyperflexhost.md) cmdlet. Specify the Name parameter value. Save the result to the $storage variable.
2. Run the Sync-HyperFlexHost cmdlet. Set the $storage variable as the Host parameter value.

Related Commands

[Get-HyperFlexHost](get-hyperflexhost.md)


