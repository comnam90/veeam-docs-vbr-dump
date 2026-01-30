---
title: "Set-VBRBackupCopyJobStorageOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrbackupcopyjobstorageoptions.html"
last_updated: "12/19/2024"
product_version: "13.0.1.1071"
---

# Set-VBRBackupCopyJobStorageOptions


Short Description

Modifies storage optimization settings for Veeam Agent backup copy jobs.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRBackupCopyJobStorageOptions -Options <VBRBackupCopyJobStorageOptions> [-EnableDataDeduplication] [-CompressionLevel {Auto | None | DedupeFriendly | Optimal | High | Extreme}] [-StorageOptimizationType {Automatic | LocalTarget | LocalTargetHugeBackup | LANTarget | WANTarget}] [-EnableEncryption] [-EncryptionKey <VBREncryptionKey>]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies storage optimization settings for Veeam Agent backup copy jobs.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Options | Specifies optimization settings for Veeam Agent backup copy jobs. The cmdlet will modify these settings. | Accepts the VBRBackupCopyJobStorageOptions object. To create this object, run the [Get-VBRJob](get-vbrjob.md) cmdlet. | True | Named | True (ByValue) |
| EnableDataDeduplication | Enables the data deduplication option for backup files created with a Veeam Agent backup copy job.  If you do not provide this parameter, Veeam Backup & Replication will not decrease the size of these backup files. | SwitchParameter | True | Named | False |
| CompressionLevel | Specifies a compression level of backup files created with a Veeam Agent backup copy job. You can specify either of the following compression level:   * Auto: use this option to set the same compression level as in the copied backup files. * None: use this option if you do not want to enable data compression. * DedupeFriendly: use this option to set a dedupe-friendly compression level. * Optimal: use this option to set an optimal compression level. * High: use this option to set a high compression level. * Extreme: use this option to set an extreme compression level.   Default: Auto. | VBRCompressionLevel | False | Named | False |
| StorageOptimizationType | Specifies data deduplication options.   * Automatic: use this option to set the same type of storage as in the copied backup files. * LocalTarget: use this option for backup to SAN, DAS or local storage. * LocalTargetHugeBackup: use this option for Veeam Agent jobs that can produce backup files larger than 16 TB. * LANTarget: use this option for backup to NAS and for onsite backup. * WANTarget: use this option if you plan to use WAN for offsite backup.   Depending on the selected storage type, the job will use data blocks of different size to optimize the size of backup files.  Default: LocalTarget. | VBRStorageOptimizationType | False | Named | False |
| EnableEncryption | Defines that the cmdlet will encrypt backup files created with a Veeam Agent backup copy job.  If you do not provide this parameter, Veeam Backup & Replication will not encrypt these backup files. | SwitchParameter | False | Named | False |
| EncryptionKey | For the encryption option.  Specifies an encryption key. Veeam Backup & Replication will use this key to encrypt backup files. | Accepts the VBREncryptionKey object. To get this object, run the [Get-VBREncryptionKey](get-vbrencryptionkey.md) cmdlet. | False | Named | False |
| KMSServer | Specifies the KMS server you want to use to encrypt the data. | Accepts the VBRKMSServer object.  To get this object, run the [Get-VBRKMSServer](get-vbrkmsserver.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRBackupCopyJobStorageOptions object that contains storage optimization settings for Veeam Agent backup copy jobs.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Enabling Data Deduplication for Storage Optimization Settings

|  |  |
| --- | --- |
| This example shows how to enable the data deduplication option for storage optimization settings of a Veeam Agent backup copy job.  |  | | --- | | $options = New-VBRBackupCopyJobStorageOptions -CompressionLevel Optimal -StorageOptimizationType LANTarget  Set-VBRBackupCopyJobStorageOptions -Options $options -EnableDataDeduplication |  Perform the following steps:   1. Run the [New-VBRBackupCopyJobStorageOptions](new-vbrbackupcopyjobstorageoptions.md) cmdlet. Specify the CompressionLevel and StorageOptimizationType parameter values. Save the result to the $options variable. 2. Run the Set-VBRBackupCopyJobStorageOptions cmdlet. Set the $options variable as the Options parameter value. Provide the EnableDataDeduplication parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Modifying Compression Level of Backup Files

|  |  |
| --- | --- |
| This example shows how to modify compression level of backup files or storage optimization settings of a Veeam Agent backup copy jobs. The cmdlet will change it from the dedupe-friendly to the extreme compression level.  |  | | --- | | $options = New-VBRBackupCopyJobStorageOptions -CompressionLevel DedupeFriendly -StorageOptimizationType LANTarget  Set-VBRBackupCopyJobStorageOptions -Options $options -CompressionLevel Extreme |  Perform the following steps:   1. Run the [New-VBRBackupCopyJobStorageOptions](new-vbrbackupcopyjobstorageoptions.md) cmdlet. Specify the CompressionLevel and StorageOptimizationType parameter values. Save the result to the $options variable. 2. Run the Set-VBRBackupCopyJobStorageOptions cmdlet. Set the $options variable as the Options parameter value. Set the Extreme option for the CompressionLevel parameter. |

Related Commands

* [New-VBRBackupCopyJobStorageOptions](new-vbrbackupcopyjobstorageoptions.md)
* [Get-VBREncryptionKey](get-vbrencryptionkey.md)


