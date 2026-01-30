---
title: "New-VBRPluginCopyJobStorageOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrplugincopyjobstorageoptions.html"
last_updated: "11/18/2025"
product_version: "13.0.1.1071"
---

# New-VBRPluginCopyJobStorageOptions


Short Description

Defines storage optimization settings for plug-in backup copy jobs.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRPluginCopyJobStorageOptions -CompressionLevel {Auto | None | DedupeFriendly | Optimal | High | Extreme} -StorageOptimizationType {Automatic | LocalTarget | LocalTargetHugeBackup | LANTarget | WANTarget} [-EnableDataDeduplication] [-EnableEncryption] [-EncryptionKey <VBREncryptionKey>] [-KMSServer <VBRKMSServer>]  [<CommonParameters>] |

Detailed Description

This cmdlet creates the VBRPluginCopyJobStorageOptions object. This object contains storage optimization settings for plug-in backup copy jobs. These settings allow you to modify the following options for the storage:

* Data compression options
* Data optimization options

For more information about job storage settings, see the [Data Compression and Deduplication](https://helpcenter.veeam.com/docs/vbr/userguide/compression_deduplication.html?ver=13) section of User Guide for VMware vSphere.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| CompressionLevel | Specifies a compression level of backup files created with a plug-in backup copy job. You can specify either of the following compression levels:   * Auto: use this option to set the same compression level as in the copied backup files. * None: use this option if you do not want to enable data compression. * Dedupe-friendly: use this option to set a dedupe-friendly compression level. * Optimal: use this option to set an optimal compression level. * High: use this option to set a high compression level. * Extreme: use this option to set an extreme compression level.   Default: Auto. | VBRCompressionLevel | True | Named | False |
| StorageOptimizationType | Specifies the type of storage that you plan to use as a backup target.   * Automatic: use this option to set the same type of storage as in the copied backup files. * LocalTarget: use this option for backup to SAN, DAS or local storage. * LocalTargetHugeBackup: use this option for Veeam Agent jobs that can produce backup files larger than 16 TB. * LANTarget: use this option for backup to NAS and for onsite backup. * WANTarget: use this option if you plan to use WAN for offsite backup.   Depending on the selected storage type, the job will use data blocks of different sizes to optimize the size of backup files.  Default: LocalTarget. | VBRStorageOptimizationType | True | Named | False |
| EnableDataDeduplication | Defines that the cmdlet will enable the data deduplication option for backup files created with a plug-in backup copy job.  If you do not provide this parameter, Veeam Backup & Replication will not decrease the size of these backup files. | SwitchParameter | False | Named | False |
| EnableEncryption | Enables encryption for a specific application backup policy. Veeam Backup & Replication will encrypt the data that is passed between backup infrastructure components on the source and target side. | SwitchParameter | False | Named | False |
| EncryptionKey | Creates an encryption key for the specified application backup policy. | Accepts the VBREncryptionKey object. To define this object, run the [Get-VBREncryptionKey](get-vbrencryptionkey.md) cmdlet. | False | Named | False |
| KMSServer | Specifies KMS servers added to the Veeam Backup & Replication console. The cmdlet will decrypt data encrypted by this server. | Accepts the VBRKMSServer object. To create this object, run the [Get-VBRKMSServer](get-vbrkmsserver.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRPluginCopyJobStorageOptions object that contains optimization settings for plug-in backup copy jobs.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Defining Storage Optimization Settings for Plug-In Backup Copy Job

|  |  |
| --- | --- |
| This command defines storage optimization settings for a plug-in backup copy job. These settings are defined with the following options:   * The compression level is set to Optimal. * The storage optimization type is set to back up to NAS.     |  | | --- | | New-VBRPluginCopyJobStorageOptions -CompressionLevel Optimal -StorageOptimizationType LANTarget | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Defining Storage Optimization Settings with Data Deduplication for Plug-In Backup Copy Job

|  |  |
| --- | --- |
| This command defines storage optimization settings for a plug-in backup copy job. These settings are defined with the following options:   * The compression level is set to dedupe-friendly. * The storage optimization type is set to back up to local storage. * Data deduplication is enabled.     |  | | --- | | New-VBRPluginCopyJobStorageOptions -CompressionLevel DedupeFriendly -StorageOptimizationType LANTarget -EnableDataDeduplication | |


