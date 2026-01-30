---
title: "Updating Source File Share Path for Backup Jobs with Secondary Target"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/update_source_share_path.html"
last_updated: "8/19/2024"
product_version: "13.0.1.1071"
---

# Updating Source File Share Path for Backup Jobs with Secondary Target


Veeam Backup & Replication does not support auto mapping of the source file share path for the file backup copy when updating the source file share path for the main file backup job.

For example, you have a File Backup job protecting the file share located at \\shared\_server\documents. It has an associated backup copy job - File Backup (Copy) 1. The file backups are stored in the main\_storage repository, the file backup copies are stored in the copy\_storage repository. Then, you decide to update the protected file share name to \\share\_server\_new\documents.

To correctly update the file backup job protecting this file share, do the following:

1. Add a new file share \\share\_server\_new\documents in the inventory, as described in section [Adding File Share](adding_unstructured_data_source.md). Do not remove the old file share from the inventory yet as it is associated with the old file backup job.
2. Update the path to the source file share for the file backup:

|  |
| --- |
| $unstructuredbackup = Get-VBRUnstructuredBackup -Name "File Backup"  $sourceserver = Get-VBRUnstructuredServer -Backup $unstructuredbackup  $targetserver = Get-VBRUnstructuredServer -Name "\\share\_server\_new\documents"  Update-VBRUnstructuredBackupPath -Backup $unstructuredbackup -SourceUnstructuredServer $sourceserver -TargetUnstructuredServer $targetserver |

As a result, the backup will be moved from the Backups > Disk to Backups > Disk (Orphaned).

1. Update the path to the source file share for the file backup copy:

|  |
| --- |
| $unstructuredbackup = Get-VBRUnstructuredBackup -Name "File Backup (Copy) 1"  $sourceserver = Get-VBRUnstructuredServer -Backup $unstructuredbackup  $targetserver = Get-VBRUnstructuredServer -Name "\\share\_server\_new\documents"  Update-VBRUnstructuredBackupPath -Backup $unstructuredbackup -SourceUnstructuredServer $sourceserver -TargetUnstructuredServer $targetserver |

As a result, the backup copy will be moved from Backups > Disk (Copy) to Backups > Disk (Orphaned).

1. Edit settings of the File Backup job defining file backup properties:

1. Remove the old protected file share at \\shared\_server\documents and add the new file share at \\share\_server\_new\documents, as described in sections [Select Files and Folders to Back Up](file_share_backup_job_files_and_folders.md) of [Creating File Backup Jobs](file_share_backup_job.md).
2. Map the file backup job to the File Backup backup converted at step 2, as described in [step 4](file_share_backup_job_storage.md) of the [Creating File Backup Jobs](file_share_backup_job.md) procedure.
3. Remove the secondary target repository added at [step 7](file_share_backup_job_secondary_target.md) of [Creating File Backup Jobs](file_share_backup_job.md) procedure.
4. Ensure that the Run the job when I click Finish check box is not selected when you close the wizard, as described in [step 9](file_share_backup_job_summary.md) of the [Creating File Backup Jobs](file_share_backup_job.md) procedure.

1. Edit settings of the File Backup job defining file backup copy properties:

1. Enable creation of the file backup copy by selecting the Configure secondary destinations for this job check box, as described in [step 4](file_share_backup_job_storage.md) of the [Creating File Backup Jobs](file_share_backup_job.md) procedure.
2. Add the copy\_storage repository for storing backup copies, as described in [step 7](file_share_backup_job_secondary_target.md) of the [Creating File Backup Jobs](file_share_backup_job.md) procedure.

Veeam Backup & Replication will automatically map the existing file backup copy, which was previously located in Backups > Disk (Orphaned), to the file backup job.

1. Ensure that the Run the job when I click Finish check box is selected when you close the wizard, as described in [step 9](file_share_backup_job_summary.md) of the [Creating File Backup Jobs](file_share_backup_job.md) procedure.

As a result, if the job and its backups are updated correctly, the first session of the updated job will create not a full backup, but an incremental one.


