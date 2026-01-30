---
title: "Get-VBRFiler"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrfiler.html"
last_updated: "4/29/2024"
product_version: "13.0.1.1071"
---

# Get-VBRFiler


Short Description

Returns enterprise NAS systems added as file shares to the inventory.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get all enterprise NAS systems added to the inventory.

|  |
| --- |
| Get-VBRFiler  [<CommonParameters>] |

* Get enterprise NAS systems by the NAS system name.

|  |
| --- |
| Get-VBRFiler -Name <string[]>  [<CommonParameters>] |

* Get enterprise NAS systems by the NAS system ID.

|  |
| --- |
| Get-VBRFiler -Id <guid[]>  [<CommonParameters>] |

Detailed Description

This cmdlet returns an array of enterprise NAS systems added to the inventory.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies an array of names of enterprise NAS systems. The cmdlet will return an array of the enterprise NAS systems with the specified name. | String[] | True | Named | False |
| Id | Specifies an array of IDs of enterprise NAS systems. The cmdlet will return an array of the NAS filers with the specified ID. | Guid[] | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRFiler object that defines the settings of the enterprise NAS system added as a file share to the inventory.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All Enterprise NAS Systems Added to Veeam Backup & Replication Infrastructure

|  |  |
| --- | --- |
| This example shows how to get all enterprise NAS systems added to the inventory. The cmdlet output will contain the following details on enterprise NAS systems: Server, AccessCredentials, Name, EnableSnapDiff, Id, CacheRepository, BackupIOControlLevel.  |  | | --- | | Get-VBRFiler | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Enterprise NAS System by Name

|  |  |
| --- | --- |
| This example shows how to get enterprise NAS systems added to the inventory by specifying their names. The cmdlet output will contain the following details on the enterprise NAS systems: Server, AccessCredentials, Name, EnableSnapDiff, Id, CacheRepository, BackupIOControlLevel.  |  | | --- | | Get-VBRFiler -Name "ontap-2"  Server               : Veeam.Backup.Core.Common.CHost AccessCredentials    : Name                 : ontap-2 EnableSnapDiff       : False Id                   : 7f149320-59c5-49f3-9133-0c5ac04c245d CacheRepository      : Veeam.Backup.Core.CBackupRepository BackupIOControlLevel : Medium | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting Enterprise NAS System by ID

|  |  |
| --- | --- |
| This example shows how to get enterprise NAS systems added to the inventory by specifying their IDs. The cmdlet output will contain the following details on the enterprise NAS systems: Server, AccessCredentials, Name, EnableSnapDiff, Id, CacheRepository, BackupIOControlLevel.  |  | | --- | | Get-VBRFiler -Id 'f804cc0c-e959-46c4-8515-47925ab5b77d'  Server               : Veeam.Backup.Core.Common.CHost AccessCredentials    : administrator Name                 : 7mode-01 EnableSnapDiff       : False Id                   : f804cc0c-e959-46c4-8515-47925ab5b77d CacheRepository      : Veeam.Backup.Core.CBackupRepository BackupIOControlLevel : Medium | |


