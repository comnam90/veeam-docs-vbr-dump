---
title: "Sync-VBRNASBackupMetadata (obsolete)"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/sync-vbrnasbackupmetadata.html"
last_updated: "1/6/2025"
product_version: "13.0.1.1071"
---

# Sync-VBRNASBackupMetadata (obsolete)

In this article

Short Description

Downloads metadata of backup files from the long-term backup repository.

|  |
| --- |
| Note |
| This cmdlet is obsolete. Run the [Sync-VBRUnstructuredBackupMetadata](sync-vbrunstructuredbackupmetadata.md) cmdlet instead. |

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Sync-VBRNASBackupMetadata -SourceBackup <VBRNASBackup> -TargetRepository <CBackupRepository> [-RunAsync][<CommonParameters>] |

Detailed Description

This cmdlet downloads metadata of backup files from the long-term backup repository to the short-term repository. You can use this cmdlet to restore backup files that are located on the long-term repository but are no longer available on the short-term repository.

|  |
| --- |
| Important |
| Before downloading metadata from the long-term repository, you must run the [Sync-VBRBackupRepository](sync-vbrbackuprepository.md) cmdlet to rescan this repository. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| SourceBackup | Specifies a backup file. The cmdlet will download metadata of this backup file from the long-term repository. | Accepts the VBRNASBackup object. To get this object, run the [Get-VBRNASBackup](get-vbrnasbackup.md)cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| TargetRepository | Specifies the short-term backup repository. The cmdlet will download metadata of backup files to the specified short-term backup repository. | Accepts the CBackupRepository object. To get this object, run the [Get-VBRBackupRepository](get-vbrnasbackup.md) cmdlet. | True | Named | False |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Downloading Metadata to Short-term Repository

This example shows how to download data from the long-term repository to the short-term repository.

|  |
| --- |
| $backup = Get-VBRNASBackup  $repository = Get-VBRBackupRepository  Sync-VBRNASBackupMetadata -SourceBackup $backup -TargetRepository $repository |

Perform the following steps:

1. Run the [Get-VBRNASBackup](get-vbrnasbackup.md) cmdlet. Save the result to the $backup variable.
2. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Save the result to the $repository variable.
3. Run the Sync-VBRNASBackupMetadata cmdlet. Set the $backup variable as the SourceBackup parameter value. Set the $repository variable as the TargetRepository parameter value.

Related Commands

* [Get-VBRNASBackup](get-vbrnasbackup.md)
* [Get-VBRBackupRepository](get-vbrbackuprepository.md)

Page updated 1/6/2025

Page content applies to build 13.0.1.1071
