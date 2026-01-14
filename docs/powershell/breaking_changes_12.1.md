---
title: "Breaking Changes"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/breaking_changes_12.1.html"
last_updated: "8/21/2025"
product_version: "13.0.1.1071"
---

# Breaking Changes

In this article

This section contains information on breaking changes in Veeam PowerShell v12.1. These changes cause Veeam PowerShell v12.1 to function differently and could affect the code.

Backup Infrastructure Components

Object Storage Repositories

In this version, you can no longer enable immutability for an already configured object storage repository since it may result in data loss. Therefore, the EnableBackupImmutability parameter is removed from the following cmdlets:

* [Set-VBRAmazonS3CompatibleRepository](set-vbramazons3compatiblerepository.md)
* [Set-VBRAmazonS3GlacierRepository](set-vbramazons3glacierrepository.md)
* [Set-VBRS3GlacierCompatibleRepository](set-vbrs3glaciercompatiblerepository.md)
* [Set-VBRAzureBlobRepository](set-vbrazureblobrepository.md)
* [Set-VBRAzureArchiveRepository](set-vbrazurearchiverepository.md)

File Backup

In this version, Veeam PowerShell covers functionality related to the unstructured data backup. This feature allows you to back up and restore unstructured data: content of various file shares and object storage repositories. To support this functionality, the following changes have been done for cmdlets related to file backup jobs:

* A number of cmdelts that were used to work with file backup jobs are deprecated. For more information, see [Deprecated Cmdlets](deprecated_cmdlets.md).
* The following parameter types have been changed for the [Add-VBRNASBackupJob](add-vbrnasbackupjob.md) and [Set-VBRNASBackupJob](set-vbrnasbackupjob.md) cmdlets:

| Parameter | Old Type | New Type |
| --- | --- | --- |
| LongTermArchivalOptions | VBRNASBackupArchivalOptions | VBRUnstructuredBackupArchivalOptions |
| ShortTermRetentionType | VBRNASBackupShortTermRetentionType | VBRUnstructuredBackupShortTermRetentionType |
| LongTermRetentionType | VBRNASBackupLongTermRetentionType | VBRUnstructuredBackupLongTermRetentionType |
| VersionRetentionOptions | VBRNASBackupVersionRetentionOptions | VBRUnstructuredBackupVersionRetentionOptions |
| SecondaryTarget | VBRNASBackupSecondaryTarget[] | VBRUnstructuredBackupSecondaryTarget[] |

SureBackup

In this version, the type for the Job parameter is changed from the VBRSureBackupJob to VBRSureBackupJobBase for the following cmdlets:

* [Enable-VBRSureBackupJob](enable-vbrsurebackupjob.md)
* [Disable-VBRSureBackupJob](disable-vbrsurebackupjob.md)
* [Start-VBRSureBackupJob](start-vbrsurebackupjob.md)
* [Stop-VBRSureBackupJob](stop-vbrsurebackupjob.md)
* [Remove-VBRSureBackupJob](remove-vbrsurebackupjob.md)

Page updated 8/21/2025

Page content applies to build 13.0.1.1071
