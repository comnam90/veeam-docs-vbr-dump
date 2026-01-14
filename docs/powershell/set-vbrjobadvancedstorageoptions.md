---
title: "Set-VBRJobAdvancedStorageOptions"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrjobadvancedstorageoptions.html"
last_updated: "11/18/2025"
product_version: "13.0.1.1071"
---

# Set-VBRJobAdvancedStorageOptions

In this article

Short Description

Customizes advanced job storage settings.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRJobAdvancedStorageOptions -Job <CBackupJob[]> [-EnableDeduplication <Boolean>] [-CompressionLevel <Int32>] [-StorageBlockSize <EKbBlockSize>] [-EnableEncryption <Boolean>] [-EncryptionKey <PSCryptoKey>] [-KMSServer <VBRKMSServer>]  [<CommonParameters>] |

Detailed Description

This cmdlet sets storage options for the selected job.

You can enable backup data deduplication and customize data units compression level and size.

Read more about job storage settings in [Veeam Backup & Replication User Guide](https://helpcenter.veeam.com/docs/vbr/userguide/backup_job_advanced_storage_vm.html?ver=13).

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameters values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies the array of jobs. The cmdlet will modify advanced storage options of these jobs. | Accepts the CBackupJob[] object. To create this object, run the [Get-VBRJob](get-vbrjob.md) cmdlet. | True | Named | True (ByProperty Name, ByValue) |
| EnableDeduplication | Defines whether the job will deduplicate.   * True: the data will be deduplicated during the backup job run (recommended). * False: no data will be checked for duplication. | Bool | False | Named | False |
| CompressionLevel | Specifies the compression level for the created backup:   * Auto = -1 * None = 0 * Dedupe-friendly = 4 * Optimal = 5 * High = 6 * Extreme = 9   Default: Optimal. | Int32 | False | Named | False |
| StorageBlockSize | Specifies the integer defining the data blocks size. Larger sized blocks provide faster procession but lower deduplication level.   * KbBlockSize256 (former WAN Target) = 0. * KbBlockSize512 (former LAN target) = 1. * KbBlockSize1024 (former Local Target) = 3. * KbBlockSize2048 = 4. * KbBlockSize4096 (former Local Target (large blocks))= 5. * KbBlockSize8192 = 6. * Automatic (Defines the best block size depending on the target type)  = 7.   Default: KbBlockSize1024. | EKbBlockSize | False | Named | False |
| EnableEncryption | Defines whether the job must use encryption. Use the EncryptionKey parameter to specify the encryption key. | Bool | False | Named | False |
| EncryptionKey | Used to specify the encryption key for the EnableEncryption parameter. | Accepts the [PSCryptoKey](pscryptokey.md) object. To create this object, run the [Get-VBREncryptionKey](get-vbrencryptionkey.md) cmdlet. | False | Named | False |
| KMSServer | Specifies KMS servers added to the Veeam Backup & Replication console. The cmdlet will decrypt data encrypted by this server. | Accepts the [VBRKMSServer](vbrkmsserver.md) object. To create this object, run the [Get-VBRKMSServer](get-vbrkmsserver.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Editing Advanced Storage Settings for Backup Job [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to edit advanced storage settings for the Backup Job 01 and Backup Job 02 backup jobs.   * The EnableDeduplication parameter is set to enable data deduplication. * The compression level is set to none (0). * The storage blocks size is set to Automatic.   |  | | --- | | Get-VBRJob -Name "Backup Job 01", "Backup Job 02" | Set-VBRJobAdvancedStorageOptions -EnableDeduplication $True -CompressionLevel 0 -StorageBlockSize 7 |  Perform the following steps:   1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. 2. Pipe the cmdlet output to the Set-VBRJobAdvancedStorageOptions cmdlet. Specify the following settings:  * Provide the $True value for the EnableDeduplication parameter. * Specify the CompressionLevel parameter value. * Specify the StorageBlockSize parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Applying Optimal Compression Level to all Jobs [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to apply the optimal compression level (=5) to all jobs.  |  | | --- | | Get-VBRJob | Set-VBRJobAdvancedStorageOptions -CompressionLevel 5 |  Perform the following steps:   1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. 2. Pipe the cmdlet output to the Set-VBRJobAdvancedStorageOptions cmdlet. Specify the CompressionLevel parameter value. |

Related Commands

* [Get-VBRJob](get-vbrjob.md)
* [Get-VBREncryptionKey](get-vbrencryptionkey.md)

Page updated 11/18/2025

Page content applies to build 13.0.1.1071
