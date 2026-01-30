---
title: "Get-NetAppHost"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-netapphost.html"
last_updated: "6/17/2024"
product_version: "13.0.1.1071"
---

# Get-NetAppHost


Short Description

Returns NetApp storage systems added to Veeam Backup & Replication.

Applies to

Platform: VMware

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-NetAppHost [-Name <String[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns NetApp storages added to Veeam Backup & Replication. You can get the list of all NetApp storage systems added to your virtual infrastructure or narrow down the output by storage name.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies an array of storage names. The cmdlet will return storage systems with these names. | String[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All NetApp Storage Systems

|  |  |
| --- | --- |
| This command returns all NetApp storage systems.  |  | | --- | | Get-NetAppHost | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting NetApp Storage System by Name

|  |  |
| --- | --- |
| This command returns a NetApp storage by name.  |  | | --- | | Get-NetAppHost -Name "NetApp Store" | |


