---
title: "New-VBRBackupCopyJobStorageOptions"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrbackupcopyjobstorageoptions.html"
last_updated: "11/18/2025"
product_version: "13.0.1.1071"
---

# New-VBRBackupCopyJobStorageOptions

In this article

Short Description

Defines storage settings for Veeam Agent backup copy jobs.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRBackupCopyJobStorageOptions -CompressionLevel {Auto | None | DedupeFriendly | Optimal | High | Extreme} -StorageOptimizationType {Automatic | LocalTarget | LocalTargetHugeBackup | LANTarget | WANTarget} [-EnableDataDeduplication] [-EnableEncryption] [-EncryptionKey <VBREncryptionKey>] [-KMSServer <VBRKMSServer>]  [<CommonParameters>] |

Detailed Description

This cmdlet creates the VBRBackupCopyJobStorageOptions object that contains storage settings for Veeam Agent backup copy jobs. These settings allow you to modify the following options for the storage:

* Data compression options
* Data deduplication options

* Encryption options

For more information about job storage settings, see the [Data Compression and Deduplication](https://helpcenter.veeam.com/docs/vbr/userguide/compression_deduplication.html?ver=13) section of User Guide.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| CompressionLevel | Specifies a compression level of backup files created with a Veeam Agent backup copy job. You can specify either of the following compression level:   * Auto: use this option to set the same compression level as in the copied backup files. * None: use this option if you do not want to enable data compression. * DedupeFriendly: use this option to set a dedupe-friendly compression level. * Optimal: use this option to set an optimal compression level. * High: use this option to set a high compression level. * Extreme: use this option to set an extreme compression level.   Default: Auto. | VBRCompressionLevel | True | Named | False |
| StorageOptimizationType | Specifies data deduplication options.   * Automatic: use this option to set the same type of storage as in the copied backup files. * LocalTarget: use this option for backup to SAN, DAS or local storage. * LocalTargetHugeBackup: use this option for Veeam Agent jobs that can produce backup files larger than 16 TB. * LANTarget: use this option for backup to NAS and for onsite backup. * WANTarget: use this option if you plan to use WAN for offsite backup.   Depending on the selected storage type, the job will use data blocks of different size to optimize the size of backup files.  Default: LocalTarget. | VBRStorageOptimizationType | True | Named | False |
| EnableDataDeduplication | Defines that the cmdlet will enable the data deduplication option for backup files created with a Veeam Agent backup copy job.  If you do not provide this parameter, Veeam Backup & Replication will not decrease the size of these backup files. | SwitchParameter | False | Named | False |
| EnableEncryption | Defines that the cmdlet will encrypt backup files created with a Veeam Agent backup copy job.  If you do not provide this parameter, Veeam Backup & Replication will not encrypt these backup files. | SwitchParameter | False | Named | False |
| EncryptionKey | For the encryption option.  Specifies an encryption key. Veeam Backup & Replication will use this key to encrypt backup files. | Accepts the VBREncryptionKey object. To get this object, run the [Get-VBREncryptionKey](get-vbrencryptionkey.md) cmdlet. | False | Named | False |
| KMSServer | Specifies the KMS server you want to use to encrypt the data. | Accepts the VBRKMSServer object.  To get this object, run the [Get-VBRKMSServer](get-vbrkmsserver.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRBackupCopyJobStorageOptions object that contains storage optimization settings for Veeam Agent backup copy jobs.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Defining Storage Optimization Settings for Veeam Agent Backup Copy Job

|  |  |
| --- | --- |
| This command defines storage optimization settings for a Veeam Agent backup copy jobs. These settings are defined with the following options:   * The compression level is set to Optimal. * The storage optimization type is set to back up to NAS.     |  | | --- | | New-VBRBackupCopyJobStorageOptions -CompressionLevel Optimal -StorageOptimizationType LANTarget | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Defining Storage Optimization Settings with Data Deduplication

|  |  |
| --- | --- |
| This command defines storage optimization settings for a Veeam Agent backup copy job. These settings are defined with the following options:   * The compression level is set to dedupe-friendly. * The storage optimization type is set to back up to local storage. * Data deduplication is enabled.     |  | | --- | | New-VBRBackupCopyJobStorageOptions -CompressionLevel DedupeFriendly -StorageOptimizationType LANTarget -EnableDataDeduplication | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Defining Storage Optimization Settings with Encryption Option

|  |  |
| --- | --- |
| This example shows how to define storage optimization settings with the encryption option.  |  | | --- | | $plainpassword = "VeeamPassword"  $securepassword = $plainpassword | ConvertTo-SecureString -AsPlainText -Force  $key = Add-VBREncryptionKey -Password $securepassword -Description "Veeam Administrator"  New-VBRBackupCopyJobStorageOptions -CompressionLevel Optimal -StorageOptimizationType LocalTargetHugeBackup -EnableEncryption -EncryptionKey $key |  Perform the following steps:   1. Create the secure password:  1. Add the $plainpassword variable and set it to the VeeamPassword value. 2. Convert the $plainpassword variable to the secure string. Provide the ConvertTo-SecureString, AsPlainText and Force parameters. Save the result to the $securepassword variable. 3. Run the [Add-VBREncryptionKey](add-vbrencryptionkey.md) cmdlet. Set the $securepassword variable as the Password parameter value. Specify the Description parameter value. Save the result to the $key variable.  1. Run the New-VBRBackupCopyJobStorageOptions cmdlet. Specify the following settings:  * Set the Optimal option for the CompressionLevel parameter. * Set the LocalTargetHugeBackup option for the StorageOptimizationType parameter. * Provide the EnableEncryption parameter. * Set the $key variable as the EncryptionKey parameter value. |

Related Commands

[Add-VBREncryptionKey](add-vbrencryptionkey.md)

Page updated 11/18/2025

Page content applies to build 13.0.1.1071
