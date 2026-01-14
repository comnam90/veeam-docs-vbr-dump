---
title: "Set-VBRBackupCacheOptions"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrbackupcacheoptions.html"
last_updated: "10/21/2024"
product_version: "13.0.1.1071"
---

# Set-VBRBackupCacheOptions

In this article

Short Description

Modifies backup cache settings for Veeam Agent backup jobs.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRBackupCacheOptions -Options <VBRBackupCacheOptions> [-Enable] [-Type <VBRBackupCacheSelectionType> {Automatic | Manual}] [-LocalPath <string>] [-SizeLimit <int>] [-SizeUnit <VBRBackupCacheSizeUnit> {GB | TB}]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies backup cache settings that you can apply to Veeam Agent backup jobs.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Options | Specifies backup cache settings that you want to modify. | Accepts the VBRBackupCacheOptions object. To create this object, run the [New-VBRBackupCacheOptions](new-vbrbackupcacheoptions.md) cmdlet. | True | Named | True (ByValue) |
| Enable | Defines that the backup cache option is enabled.  If you provide this parameter, backup files will remain in the cache of the protected computers until these computers are able to connect to Veeam Backup & Replication. | SwitchParameter | False | Named | False |
| Type | Specifies how to choose the location to keep cached data. You can specify one of the following options:   * Automatic: use this option if you want Veeam Backup & Replication to define the cached data location automatically on every computer. * Manual: use this option if you want explicitly define the location to keep cached data on every computer. | VBRBackupCacheSelectionType | False | Named | False |
| LocalPath | For the Manual option of the Type parameter.  Specifies a path to the folder on a protected computer. The cmdlet will keep the cached data in the specified folder. | String | False | Named | False |
| SizeLimit | Specifies a size limit of a backup cache file in numbers. Veeam Backup & Replication will remove backup cache data from the folder when this limit is exceeded.  Provide the SizeUnit parameter to specify the unit of measure. | Int32 | False | Named | False |
| SizeUnit | For the SizeLimit option.  Specifies the unit of measure to keep backup cache files. You can specify either of the following units:   * GB * TB | VBRBackupCacheSizeUnit | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

This cmdlet returns the VBRBackupCacheOptions object that contains backup cache settings.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Modifying Location Option

|  |  |
| --- | --- |
| This example shows how to modify the location settings to keep cached data. The cmdlet will change the manual selection of location to the automatic selection.  |  | | --- | | $options = New-VBRBackupCacheOptions -Enable -Type Manual -LocalPath "C:\Backup" -SizeLimit 10 -SizeUnit TB  Set-VBRBackupCacheOptions -Options $options -Type Automatic |  Perform the following steps:   1. Run the [New-VBRBackupCacheOptions](new-vbrbackupcacheoptions.md) cmdlet. Provide the Enable parameter. Specify the Type, LocalPath, SizeLimit and SizeUnit parameter values. Save the result to the $options variable. 2. Run the Set-VBRBackupCacheOptions cmdlet. Set the $options variable as the Options parameter value. Set the Automatic option for the Type parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Modifying Size Limit of Backup Cache

|  |  |
| --- | --- |
| This example shows how to modify size limits for backup cache. The cmdlet will change size limits from 10 TB to 15 TB.  |  | | --- | | $options = New-VBRBackupCacheOptions -Enable -Type Manual -LocalPath "C:\Backup" -SizeLimit 10 -SizeUnit TB  Set-VBRBackupCacheOptions -Options $options -SizeLimit 15 |  Perform the following steps:   1. Run the [New-VBRBackupCacheOptions](new-vbrbackupcacheoptions.md) cmdlet. Provide the Enable parameter. Specify the Type, LocalPath, SizeLimit and SizeUnit parameter values. Save the result to the $options variable. 2. Run the Set-VBRBackupCacheOptions cmdlet. Set the $options variable as the Options parameter value. Specify the SizeLimit parameter value. |

Related Commands

[New-VBRBackupCacheOptions](new-vbrbackupcacheoptions.md)

Page updated 10/21/2024

Page content applies to build 13.0.1.1071
