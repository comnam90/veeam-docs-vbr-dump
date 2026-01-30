---
title: "New-VBRBackupCacheOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrbackupcacheoptions.html"
last_updated: "10/21/2024"
product_version: "13.0.1.1071"
---

# New-VBRBackupCacheOptions


Short Description

Defines backup cache settings for Veeam Agent for Microsoft Windows backup jobs.

Applies to:

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRBackupCacheOptions [-Enable] [-Type <VBRBackupCacheSelectionType> {Automatic | Manual}] [-LocalPath <string>] [-SizeLimit <int>] [-SizeUnit <VBRBackupCacheSizeUnit> {GB | TB}]  [<CommonParameters>] |

Detailed Description

This cmdlet creates the VBRBackupCacheOptions object. This object defines backup cache settings that you can apply to backup jobs created by Veeam Agent for Microsoft Windows.

|  |
| --- |
| ![New-VBRBackupCacheOptions](images/icon_important.webp) Important! |
| You can apply backup cache settings to Veeam Agent backup jobs that are targeted at the following types of backup location:   * Veeam backup repository. * Veeam Cloud Connect repository. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Enable | Defines that the backup cache option is enabled.  If you provide this parameter, backup files will remain in the cache of the protected computers until these computers are able to connect to Veeam Backup & Replication. | SwitchParameter | False | Named | False |
| Type | Specifies how to choose the location to keep cached data. You can specify one of the following options:   * Automatic: use this option if you want Veeam Agent automatically define location for the backup cache on on each computer added to the backup policy. * Manual: use this option if you want explicitly define the location to keep cached data on every computer.   Default: Automatic. | VBRBackupCacheSelectionType | False | Named | False |
| LocalPath | For the Manual option of the Type parameter.  Specifies a path to the folder on a protected computer. The cmdlet will keep the cached data in the specified folder. | String | False | Named | False |
| SizeLimit | Specifies a size limit of a backup cache file in numbers. Veeam Agent Backup jobs will not add new backup cache files when this limit is exceeded.  Provide the SizeUnit parameter to specify the unit of measure.  Default: 10.  Note: To run the script, you must provide this parameter. | Int32 | False | Named | False |
| SizeUnit | For the SizeLimit option.  Specifies the measure unit of a backup cache size limit. You can specify one of the following units:   * GB * TB   Default: GB.  Note: To run the script, you must provide this parameter. | VBRBackupCacheSizeUnit | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

This cmdlet returns the VBRBackupCacheOptions object that contains backup cache settings.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Defining Backup Cache Settings with Automatic Location Option

|  |  |
| --- | --- |
| This command defines the following backup cache settings:   * Veeam Backup & Replication will select the location to keep the backup cache automatically.  * Veeam Agent Backup jobs will not create backup cache files when the backup cache exceeds 5 GB.   |  | | --- | | New-VBRBackupCacheOptions -Enable -Type Automatic -SizeLimit 5 -SizeUnit GB | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Defining Backup Cache Settings with Manual Location Option

|  |  |
| --- | --- |
| This command defines the following backup cache settings:   * The location to keep backup cache is specified explicitly. * Veeam Backup & Replication will keep cache in the C:\Backup folder on the protected computer. * Veeam Agent Backup jobs will not create backup cache files when the backup cache exceeds 10 TB.   |  | | --- | | New-VBRBackupCacheOptions -Enable -Type Manual -LocalPath "C:\Backup" -SizeLimit 10 -SizeUnit TB | |


