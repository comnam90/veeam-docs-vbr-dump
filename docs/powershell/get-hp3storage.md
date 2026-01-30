---
title: "Get-HP3Storage"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-hp3storage.html"
last_updated: "6/17/2024"
product_version: "13.0.1.1071"
---

# Get-HP3Storage


Short Description

Returns HPE 3PAR StoreServ storage systems.

Applies to

Platform: VMware

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Storage System: HPE 3PAR StoreServ

Syntax

|  |
| --- |
| Get-HP3Storage [-Name <string[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns HPE 3PAR StoreServ storages added to Veeam Backup & Replication.

You can get the list of all storages added to your virtual infrastructure or narrow down the output by storage name.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies the array of storage names. The cmdlet will return the storage systems with these names. | String[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All HPE 3PAR StoreServ Storage Systems

|  |  |
| --- | --- |
| This command returns all HPE 3PAR StoreServ storage systems.  |  | | --- | | Get-HP3Storage | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting HPE 3PAR StoreServ Storage System by Name

|  |  |
| --- | --- |
| This command returns an HPE 3PAR StoreServ storage by name.  |  | | --- | | Get-HP3Storage -Name "HPE 3PAR StoreServe Storage" | |


