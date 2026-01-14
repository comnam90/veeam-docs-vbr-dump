---
title: "Set-VBRStorageOptions"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrstorageoptions.html"
last_updated: "10/21/2024"
product_version: "13.0.1.1071"
---

# Set-VBRStorageOptions

In this article

Short Description

Modifies storage optimization settings for Veeam Agent backup jobs.

Applies to

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRStorageOptions -Options <VBRStorageOptions> [-CompressionLevel <VBRCompressionLevel> {None | DedupeFriendly | Optimal | High | Extreme}] [-StorageOptimizationType <VBRStorageOptimizationType> {LocalTarget | LocalTargetHugeBackup | LANTarget | WANTarget}] [-EnableEncryption] [-EncryptionKey <VBREncryptionKey>] [-KMSServer <VBRKMSServer>]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies storage optimization settings that you can apply to Veeam Agent backup jobs. You can modify the following settings for the storage:

* Data compression settings
* Data optimization settings
* Encryption settings

Veeam Backup & Replication will apply the settings to new backups during the next Veeam Agent backup job run. The new settings will not modify previously created backups.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Options | Specifies storage options that you want to modify. | Accepts VBRStorageOptions type. | True | Named | True (ByValue) |
| CompressionLevel | Specifies the compression level for the backup:   * None: use this option if you do not want to enable data compression.  * Dedupe-friendly: use this option to set a dedupe-friendly compression level. * Optimal: use this option to set an optimal compression level. * High: use this option to set a high compression level. * Extreme: use this option to set an extreme compression level. | VBRCompressionLevel | False | Named | False |
| StorageOptimizationType | Specifies the type of the storage that you plan to use as a backup target.   * LocalTarget: use this option for backup to SAN, DAS or local storage. * LocalTargetHugeBackup: use this option for Veeam Agent jobs that can produce backup files larger than 16 TB. * LANTarget: use this option for backup to NAS and for onsite backup. * WANTarget: use this option if you plan to use WAN for offsite backup.   Depending on the selected storage type, the job will use data blocks of different size to optimize the size of backup files. | VBRStorageOptimizationType | False | Named | False |
| EnableEncryption | Enables the option for the Veeam Agent backup job to encrypt the backup data. | SwitchParameter | False | Named | False |
| EncryptionKey | For the EnableEncryption option.  Specifies the encryption key that you want to use to encrypt the data. | Accepts the [VBREncryptionKey](vbrencryptionoptions.md) object. To create this object, run the [Add-VBREncryptionKey](add-vbrencryptionkey.md) cmdlet. | False | Named | False |
| KMSServer | Specifies KMS servers added to the Veeam Backup & Replication console. The cmdlet will decrypt data encrypted by this server. | Accepts the [VBRKMSServer](vbrkmsserver.md) object. To get this object, run the [Get-VBRKMSServer](get-vbrkmsserver.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

This cmdlet returns the VBRStorageOptions object that contains storage optimization settings for backup jobs.

Examples

Changing Data Compression and Storage Optimization Settings

This example shows how to specify data compression and storage optimization settings for a Veeam Agent backup job. The job with these settings will run as follows:

* Veeam Backup & Replication will change the optimization type to use WAN for offsite backup.
* Veeam Backup & Replication will change the compression level to dedupe-friendly.

|  |
| --- |
| $job = Get-VBRComputerBackupJob -Name "AgentBackupJob"  $options = New-VBRStorageOptions -CompressionLevel Optimal -StorageOptimizationType LocalTargetHugeBackup  $newoptions = Set-VBRStorageOptions -Options $options -CompressionLevel DedupeFriendly -StorageOptimizationType WANTarget  Set-VBRComputerBackupJob -Job $job -StorageOptions $newoptions |

Perform the following steps:

1. Run the [Get-VBRComputerBackupJob](get-vbrcomputerbackupjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable.
2. Run the [New-VBRStorageOptions](new-vbrstorageoptions.md) cmdlet. Specify the CompressionLevel and StorageOptimizationType parameter values. Save the result to the $options variable.
3. Run the Set-VBRStorageOptions cmdlet. Set the $options variable as the Options parameter value. Specify the CompressionLevel and StorageOptimizationType parameter values. Save the result to the $newoptions variable.
4. Run the [Set-VBRComputerBackupJob](set-vbrcomputerbackupjob.md) cmdlet. Set the $job variable as the Job parameter value. Set the $newoptions variable as the StorageOptions parameter value.

Related Commands

* [Get-VBRComputerBackupJob](get-vbrcomputerbackupjob.md)
* [New-VBRStorageOptions](new-vbrstorageoptions.md)
* [Set-VBRComputerBackupJob](set-vbrcomputerbackupjob.md)

Page updated 10/21/2024

Page content applies to build 13.0.1.1071
