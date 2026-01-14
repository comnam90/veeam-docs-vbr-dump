---
title: "Get-StoragePluginHost"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-storagepluginhost.html"
last_updated: "4/23/2024"
product_version: "13.0.1.1071"
---

# Get-StoragePluginHost

In this article

Short Description

Returns Universal Storage API integrated systems.

Applies to

Platform: VMware

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Storage System: IBM Spectrum Virtualize, INFINIDAT InfiniBox, Pure Storage

Syntax

|  |
| --- |
| Get-StoragePluginHost [-Name <String[]>] [-PluginType <String>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns Veeam Universal Storage API integrated storages added to Veeam Backup & Replication.

You can get the list of all storages or narrow down the output by storage name or storage plugin.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies the array of storage names. The cmdlet will return storage systems with these names. | String[] | False | Named | False |
| PluginType | Specifies the storage Plug-in. The cmdlet will return storage systems added to Veeam Backup & Replication over this Plug-in. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All Storage Systems

|  |  |
| --- | --- |
| This command returns all storage systems added to Veeam Backup & Replication.  |  | | --- | | Get-StoragePluginHost | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Storage Systems by Name

|  |  |
| --- | --- |
| This command returns storage systems by name.  |  | | --- | | Get-StoragePluginHost -Name "IBM Spectrum" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting All Storage Systems by Associated Storage Plug-in

|  |  |
| --- | --- |
| This command returns storage systems by the associated storage plug-in.  |  | | --- | | Get-StoragePluginHost -PluginType "Ibm" | |

Page updated 4/23/2024

Page content applies to build 13.0.1.1071
