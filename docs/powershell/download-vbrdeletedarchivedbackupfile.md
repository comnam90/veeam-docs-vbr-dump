---
title: "Download-VBRDeletedArchivedBackupFile"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/download-vbrdeletedarchivedbackupfile.html"
last_updated: "12/20/2024"
product_version: "13.0.1.1071"
---

# Download-VBRDeletedArchivedBackupFile

In this article

Short Description

Retrieves a backup file deleted from the archive tier and preserved by insider protection.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Retrieve backup files from Amazon S3 Glacier.

|  |
| --- |
| Download-VBRDeletedArchivedBackupFile -AmazonS3GlacierRetrievalPolicy {Expedited | Standard | Bulk} -BackupFile <VBRDeletedArchivedBackupFile> [-Overwrite] [-RunAsync]  [<CommonParameters>] |

* Retrieve backup files from Microsoft Azure Archive Storage.

|  |
| --- |
| Download-VBRDeletedArchivedBackupFile -AzureArchiveRetrievalPolicy {StandardPriority | HighPriority} -BackupFile <VBRDeletedArchivedBackupFile> [-Overwrite] [-RunAsync]  [<CommonParameters>] |

Detailed Description

This cmdlet retrieves a backup file deleted from the archive tier preserved by insider protection and uploads them to the performance tier.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| BackupFile | Specifies an array of deleted backup files that you want to retrieve. | Accepts the VBRDeletedArchivedBackupFile[] object. To get this object, run the [Get-VBRDeletedArchivedBackupFile](get-vbrdeletedarchivedbackupfile.md) cmdlet. | True | Named | True |
| AmazonS3GlacierRetrievalPolicy | Defines the method of data retrieval for Amazon S3 Glacier object storage. You can retrieve data using one of the following method:   * Expedited: Use this method to retrieve archived data within 1-5 minutes. * Standard: Use this method to retrieve archived data within 3-5 hours. * Bulk: Use this method to retrieve archived data within 5-12 hours. | VBRAmazonS3GlacierRetrievalPolicy | True | Named | False |
| AzureArchiveRetrievalPolicy | Defines the method of data retrieval for Azure Archive storage. You can retrieve data using one of the following method:   * StandardPriority: Use this method to retrieve archived data within 15 hours. * HighPriority: Use this method to retrieve archived data within an hour. | VBRAzureArchiveRestrievalPolicy | True | Named | False |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |
| Overwrite | Defines that the cmdlet will overwrite an existing object with the downloaded one. | SwitchParameter | False | Named | False |

Output Object

None.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Retrieving Backup Files from Amazon S3 Glacier

|  |  |
| --- | --- |
| This example shows how to retrieve backup files from Amazon S3 Glacier.  |  | | --- | | $backupfile = Get-VBRDeletedArchivedBackupFile  Download-VBRDeletedArchivedBackupFile -BackupFile $backupfile[0] -AmazonS3GlacierRetrievalPolicy Standard -Overwrite |  Perform the following steps:   1. Run the [Get-VBRDeletedArchivedBackupFile](get-vbrdeletedarchivedbackupfile.md) cmdlet. Save the result to the $backupfile variable.   The [Get-VBRDeletedArchivedBackupFile](get-vbrdeletedarchivedbackupfile.md) cmdlet will return an array of deleted backup files. Mind the ordinal number of the necessary backup file (in our example, it is the first backup file in the array).   1. Run the Download-VBRDeletedArchivedBackupFile cmdlet. Set the $backupfile[0] variable as the BackupFile parameter value. Specify the AmazonS3GlacierRetrievalPolicy parameter value. Provide the Overwrite parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Retrieving Backup Files from Microsoft Azure Archive Storage

|  |  |
| --- | --- |
| This example shows how to retrieve backup files from Microsoft Azure Archive Storage.  |  | | --- | | $backupfile = Get-VBRDeletedArchivedBackupFile  Download-VBRDeletedArchivedBackupFile -BackupFile $backupfile[0] -AzureArchiveRetrievalPolicy StandardPriority -Overwrite |  Perform the following steps:   1. Run the [Get-VBRDeletedArchivedBackupFile](get-vbrdeletedarchivedbackupfile.md) cmdlet. Save the result to the $backupfile variable.   The [Get-VBRDeletedArchivedBackupFile](get-vbrdeletedarchivedbackupfile.md) cmdlet will return an array of deleted backup files. Mind the ordinal number of the necessary backup file (in our example, it is the first backup file in the array).   1. Run the Download-VBRDeletedArchivedBackupFile cmdlet. Set the $backupfile[0] variable as the BackupFile parameter value. Specify the AzureArchiveRetrievalPolicy parameter value. Provide the Overwrite parameter. |

Related Commands

[Get-VBRDeletedArchivedBackupFile](get-vbrdeletedarchivedbackupfile.md)

Page updated 12/20/2024

Page content applies to build 13.0.1.1071
