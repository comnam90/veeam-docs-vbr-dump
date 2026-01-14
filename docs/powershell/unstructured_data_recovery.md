---
title: "Unstructured Data Recovery"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/unstructured_data_recovery.html"
last_updated: "8/21/2025"
product_version: "13.0.1.1071"
---

# Unstructured Data Recovery

In this article

You can use the cmdlets in this topic to perform the following operations.

| Cmdlet | Operation |
| --- | --- |
| [Start-VBRNasBackupRestore](start-vbrnasbackuprestore.md) | Starts restore of backups created by the file backup job. |
| [New-VBRNASInstantRecoveryMountOptions](new-vbrnasinstantrecoverymountoptions.md) | Creates a mapping configuration for instant restore of file backups. |
| [New-VBRNASPermissionSet](new-vbrnaspermissionset.md) | Creates a permission set for instant restore of file share backups that will be used if the file share backup does not contain security information. |
| [Start-VBRNASInstantRecovery](start-vbrnasinstantrecovery.md) | Starts an instant restore of backups created by the file backup job. |
| [Get-VBRNASInstantRecovery](get-vbrnasinstantrecovery.md) | Returns active instant restore sessions started to recover backups created by file backup jobs. |
| [Stop-VBRNASInstantRecovery](stop-vbrnasinstantrecovery.md) | Stops an instant restore of backups created by the file backup job. |
| [Get-VBRUnstructuredBackupRestorePoint](get-vbrunstructuredbackuprestorepoint.md) | Returns restore points created by file backup jobs and object storage backup jobs. |
| [Start-VBRUnstructuredBackupFLRSession](start-vbrunstructuredbackupflrsession.md) | Starts a restore session to explore objects backed-up by file backup jobs and object storage backup jobs. |
| [Get-VBRUnstructuredBackupFLRSession](get-vbrunstructuredbackupflrsession.md) | Returns restore sessions started to recover backups created by file backup jobs and object storage backup jobs. |
| [Stop-VBRUnstructuredBackupFLRSession](stop-vbrunstructuredbackupflrsession.md) | Stops restore sessions started to recover backups created by file backup jobs or object storage backup jobs. |
| [Get-VBRUnstructuredBackupFLRItem](get-vbrunstructuredbackupflritem.md) | Returns backed-up objects created by file backup jobs or object storage backup jobs. |
| [Get-VBRUnstructuredBackupFLRItemVersion](get-vbrunstructuredbackupflritemversion.md) | Returns versions of objects backed-up by file backup jobs or object storage backup jobs. |
| [Restore-VBRUnstructuredBackupFLRItem](restore-vbrunstructuredbackupflritem.md) | Restores objects backed up by file backup jobs or object storage backup jobs to original file shares or object storage. |
| [Start-VBRObjectStorageBackupRestore](start-vbrobjectstoragebackuprestore.md) | Starts restore of backups created by an object storage backup job. |
| [Save-VBRUnstructuredBackupFLRItem](save-vbrunstructuredbackupflritem.md) | Restores objects backed up by file backup jobs or object storage backup jobs to the specified file shares or object storage. |
| [Start-VBRUnstructuredBackupHealthCheck](start-vbrunstructuredbackuphealthcheck.md) | Performs a health check of the latest restore point created by file backup jobs and object storage backup jobs and their repair if necessary. |
| [Sync-VBRUnstructuredBackupMetadata](sync-vbrunstructuredbackupmetadata.md) | Downloads metadata of backup files from the long-term backup repository. |
| [Compare-VBRUnstructuredBackupFLRItem](compare-vbrunstructuredbackupflritem.md) | Compares backed-up objects with objects on production file share or object storage. |
| [Compare-VBRUnstructuredBackupFLRItemAttributes](compare-vbrunstructuredbackupflritemattributes.md) | Compares attributes of backed-up objects with objects on production file share or object storage. |
| [Stop-VBRUnstructuredBackupFLRItemComparison](stop-vbrunstructuredbackupflritemcomparison.md) | Stops sessions that are running to compare backed-up objects with objects on production file share or object storage. |

Page updated 8/21/2025

Page content applies to build 13.0.1.1071
