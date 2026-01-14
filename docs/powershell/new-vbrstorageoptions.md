---
title: "New-VBRStorageOptions"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrstorageoptions.html"
last_updated: "11/18/2025"
product_version: "13.0.1.1071"
---

# New-VBRStorageOptions

In this article

Short Description

Defines storage optimization settings for backup jobs.

Applies to

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRStorageOptions -CompressionLevel <VBRCompressionLevel> {None | DedupeFriendly | Optimal | High | Extreme} -StorageOptimizationType <VBRStorageOptimizationType> {LocalTarget | LocalTargetHugeBackup | LANTarget | WANTarget} [-EnableEncryption] [-EncryptionKey <VBREncryptionKey>] [-KMSServer <VBRKMSServer>]  [<CommonParameters>] |

Detailed Description

This cmdlet creates the VBRStorageOptions object that contains the storage optimization settings that you can apply to Veeam Agent backup jobs. These settings allow you to modify the following options for the storage:

* Data compression options
* Data optimization options
* Encryption options

For more information about job storage settings, see the [Data Compression and Deduplication](https://helpcenter.veeam.com/docs/vbr/userguide/compression_deduplication.html?ver=13) section of the User Guide.

For more information about job encryption settings, see the [Storage Settings](https://helpcenter.veeam.com/docs/vbr/userguide/agent_job_advanced_storage.html?ver=13) section in the Veeam Agent Management Guide.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| CompressionLevel | Specifies the compression level of backups:   * None: use this option if you do not want to enable data compression. * Dedupe-friendly: use this option to set a dedupe-friendly compression level. * Optimal: use this option to set an optimal compression level. * High: use this option to set a high compression level. * Extreme: use this option to set an extreme compression level.   Default: Optimal. | VBRCompressionLevel | True | Named | False |
| StorageOptimizationType | Specifies the type of the storage that you plan to use as a backup target.   * LocalTarget: use this option for backup to SAN, DAS or local storage. * LocalTargetHugeBackup: use this option for Veeam Agent jobs that can produce backup files larger than 16 TB. * LANTarget: use this option for backup to NAS and for onsite backup. * WANTarget: use this option if you plan to use WAN for offsite backup.   Depending on the selected storage type, the job will use data blocks of different size to optimize the size of backup files.  Default: LocalTarget. | VBRStorageOptimizationType | True | Named | False |
| EnableEncryption | Enables the option for the Veeam Agent backup job to encrypt the backup data. | SwitchParameter | False | Named | False |
| EncryptionKey | For the EnableEncryption parameter.  Specifies the encryption key that you want to use to encrypt the data. | Accepts the VBREncryptionKey object. To create this object, run the [Add-VBREncryptionKey](add-vbrencryptionkey.md) cmdlet. | False | Named | False |
| KMSServer | Specifies KMS servers added to the Veeam Backup & Replication console. The cmdlet will decrypt data encrypted by this server. | Accepts the [VBRKMSServer](vbrkmsserver.md) object. To get this object, run the [Get-VBRKMSServer](get-vbrkmsserver.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

This cmdlet returns the VBRStorageOptions object that contains storage optimization settings for backup jobs.

Examples

Specifying Data Compression and Storage Optimization Settings

This example shows how to specify data compression and storage optimization settings that you can apply to a backup job. The job with these settings will run as follows:

* The backup job will encrypt the data and will apply the optimal compression level.
* The storage optimization type is set to keep backups larger than 16 TB on the local storage.

|  |
| --- |
| $key = Add-VBREncryptionKey -Description Mypass  New-VBRStorageOptions -CompressionLevel Optimal -StorageOptimizationType LocalTargetHugeBackup -EnableEncryption -EncryptionKey $key |

Perform the following steps:

1. Run the [Add-VBREncryptionKey](add-vbrencryptionkey.md) cmdlet. Specify the Description parameter value. Save the result to the $key variable.
2. Run the New-VBRStorageOptions cmdlet. Specify the following settings:

* Set the Optimal option for the CompressionLevel parameter.
* Set the LocalTargetHugeBackup option for the StorageOptimizationType parameter.
* Provide the EnableEncryption parameter.
* Set the $key variable as the EncryptionKey parameter value.

Related Commands

[Add-VBREncryptionKey](add-vbrencryptionkey.md)

Page updated 11/18/2025

Page content applies to build 13.0.1.1071
