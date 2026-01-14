---
title: "Managing Unstructured Data Backups"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/unstructured_backups_manage.html"
last_updated: "1/7/2025"
product_version: "13.0.1.1071"
---

# Managing Unstructured Data Backups

In this article

You can use the cmdlets in this topic to perform the following operations.

| Cmdlet | Operation |
| --- | --- |
| [Get-VBRUnstructuredBackup](get-vbrunstructuredbackup.md) | Returns backup files created by file backup jobs and object storage backup jobs. |
| [Remove-VBRUnstructuredBackup](remove-vbrunstructuredbackup.md) | Removes backup files created by the file backup jobs and object storage backup jobs. |
| [Copy-VBRUnstructuredBackup](copy-vbrunstructuredbackup.md) | Copies backups created by file backup jobs and object storage backup jobs to another location. |
| [Get-VBRNASObjectStorageTransformThreshold](get-vbrnasobjectstoragetransformthreshold.md) | Returns the blob transformation threshold defined for an object storage repository that stores file backups. |
| [Set-VBRNASObjectStorageTransformThreshold](set-vbrnasobjectstoragetransformthreshold.md) | Modifies the blob transformation threshold for an object storage repository that stores file backups. |
| [Convert-VBRNASBackupRootFormat](convert-vbrnasbackuprootformat.md) | Converts backups created by one file backup job for separate non-root shared folders residing on the same server into the backup created for the server single root folder. |
| [Convert-VBRNASBackupSANFormat](convert-vbrnasbackupsanformat.md) | Converts backups created for SMB or NFS file shares residing on an enterprise NAS system into the format of a NAS filer share on the same storage system. |
| [Convert-VBRNASBackupStorageFormat](convert-vbrnasbackupstorageformat.md) | Converts format of baskets used for storing backups created with file backup and file backup copy jobs. |

Page updated 1/7/2025

Page content applies to build 13.0.1.1071
