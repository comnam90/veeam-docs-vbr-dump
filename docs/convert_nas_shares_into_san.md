---
title: "Converting Backups from SMB or NFS Shares to NAS Filer Shares"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/convert_nas_shares_into_san.html"
last_updated: "9/19/2025"
product_version: "13.0.1.1071"
---

# Converting Backups from SMB or NFS Shares to NAS Filer Shares


You can use enterprise storage systems integrated with Veeam Backup & Replication both to host simple SMB or NFS shares and to act as NAS filer shares.

|  |
| --- |
| Note |
| You cannot convert backups stored on a root server or shares from the root server. |

To use all the advantages of NAS filer shares, for example the native file change tracking technology, you can convert backups created for existing SMB or NFS shares into the format of NAS filer shares. After that you can continue to protect the file shares as NAS filer shares by running existing file backup jobs and by using existing backup files. Perform the conversion with extreme caution.

To convert SMB or NFS shares into NAS filer shares, do the following:

1. Disable file backup jobs protecting SMB or NFS shares, for which you want to convert backups. To do that, right-click the required job in the Jobs node of the inventory pane in the Home view and select Disable. Alternatively, you can click Disable on the ribbon.
2. Make sure that you have created NAS filer, which corresponds to existing SMB or NFS shares, added to the Veeam Backup & Replication inventory. The NAS filer and these shares must reside on the same storage system. The correspondence of the shares must be full except for the host name.
3. Run the Convert-VBRNASBackupSANFormat PowerShell cmdlet to convert the format of the file share backup to provide support of NAS filer shares. The following example shows how to convert file shares residing on a NetApp storage system:

|  |
| --- |
| $nasbackup = Get-VBRNASBackup -name "File Backup Job 1"  $netapp = Get-NetAppHost -name "pdc-ontap-1"  $netapp\_filer = Get-VBRNASServer -SANEntity $netapp  Convert-VBRNASBackupSANFormat -Backup $nasbackup -Server $netapp\_filer |

For more information, see the description of the Convert-VBRNASBackupSANFormat cmdlet in the [Veeam PowerShell Reference](https://helpcenter.veeam.com/docs/vbr/powershell/convert-vbrnasbackupsanformat.html?ver=13).

As a result, the backup will be moved from Backups > Disk node to Backups > Disk (Orphaned) node in the inventory pane of the Home view.

At this step, you can check if the cmdlet has correctly converted the backup. To do that, check if backup object names in the Disk (Orphaned) node have changed and now show the path to the NAS filer share. If object names have not changed and show the path to the SMB or NFS share as before, continuing the conversion process can lead to the unwanted result. For example, when you enable the backup job for the converted backup, it will back up the NAS filer share not with an incremental run, but with a full run instead, which may lead to extra costs.

1. Use the [Edit File Backup Job](file_share_backup_job.md) wizard to edit the file backup job that protects the file shares:

1. At the [Files and Folders](file_share_backup_job_files_and_folders.md) step of the wizard, remove the existing SMB and NFS shares from the job and add NAS filer shares instead.
2. At the [Backup Repository](file_share_backup_job_storage.md) step of the wizard, map the job to the backup that was converted at step 2.

1. Enable file backup jobs protecting file shares, for which you converted backups. To do that, right-click the required job from the Jobs node of the inventory pane in the Home view and clear selection of Disable. Alternatively, you can click Disable on the ribbon.

Veeam Backup & Replication supports conversion of backups created by backup copy jobs. To continue the old backup chain created by the backup copy job, do the following:

1. Disable file backup jobs protecting SMB or NFS shares, for which you want to convert backups. To do that, right-click the required job in the Jobs node of the inventory pane in the Home view and select Disable. Alternatively, you can click Disable on the ribbon.
2. Make sure that you have created NAS filer, which corresponds to existing SMB or NFS shares, added to the Veeam Backup & Replication inventory. The NAS filer and these shares must reside on the same storage system. The correspondence of the shares must be full except for the host name.
3. Run the Convert-VBRNASBackupSANFormat PowerShell cmdlet to convert the format of the file share backup to provide support of NAS filer shares. The following example shows how to convert the backup format of the file shares residing on a NetApp storage system:

|  |
| --- |
| $backup\_copy = Get-VBRNASBackup -name "File Backup Job 1 (Copy)"  $netapp = Get-NetAppHost -name "pdc-ontap-1"  $netapp\_filer = Get-VBRNASServer -SANEntity $netapp  Convert-VBRNASBackupSANFormat -Backup $backup\_copy -Server $netapp\_filer |

For more information, see the description of the Convert-VBRNASBackupSANFormat cmdlet in the [Veeam PowerShell Reference](https://helpcenter.veeam.com/docs/vbr/powershell/convert-vbrnasbackupsanformat.html?ver=13).

1. Use the [Edit File Backup Job](file_share_backup_job.md) wizard to remove the secondary target storage for the file backup job that protects the file shares:

1. At the [Secondary Target](file_share_backup_job_secondary_target.md) step of the wizard, remove the required repository selected as a secondary target for the file backup job.
2. Go through all the wizard steps without running the job. Click Finish.

1. Use the [Edit File Backup Job](file_share_backup_job.md) wizard to add the secondary target storage back for the file backup job that protects the file shares:

1. At the [Secondary Target](file_share_backup_job_secondary_target.md) step of the wizard, add the required repository as a secondary target for the file backup job.
2. Go through all the wizard steps. Click Finish.

1. Enable file backup jobs protecting file shares, for which you converted backups. To do that, right-click the required job from the Jobs node of the inventory pane in the Home view and clear selection of Disable. Alternatively, you can click Disable on the ribbon.

File share backup copy will automatically map to the file backup copy job. After that, the backup copy job will back up new points of the main file backup job if they were created.


