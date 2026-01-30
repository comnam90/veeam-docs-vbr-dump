---
title: "Converting Backups from Non-Root to Root Shared Folders"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/convert_backups_nonroot_to_root.html"
last_updated: "6/3/2024"
product_version: "13.0.1.1071"
---

# Converting Backups from Non-Root to Root Shared Folders


Veeam Backup & Replication allows adding a server root folder as a source for file backup jobs. In this case, all changes to separate shared folders residing on this server will be reflected in the file backup job where the root shared folder of this server is added. You can even add shared root folders using different protocols to one file backup job and thus protect all file shares that are or will be added on the server.

If you previously had several separate non-root shared folders residing on the same server and want to switch to using a single root shared folder to cover the same shares, you do not have to run full backups to update data of protected shares. Instead, you can convert existing backups and update existing file backup jobs to protect single root shared folders comprising all other non-root shared folders residing on the same server. Perform the conversion with extreme caution.

To convert backups from non-root to root shared folders, do the following:

1. Disable file backup jobs protecting file shares, for which you want to convert backups. To do that, right-click the required job in the Jobs node of the inventory pane in the Home view and select Disable. Alternatively, you can click Disable on the ribbon.
2. Make sure that your backup infrastructure has a root share (for example, NFS or SMB) added for the whole server or storage system where existing non-root shares reside. These shares must reside on the same server or storage system. The correspondence of the shares must be full except for the host name.
3. Run the Convert-VBRNASBackupRootFormat PowerShell cmdlet to convert backups created by one file backup job for separate non-root shared folders residing on the same server into the backup created for the server single root folder with all the non-root shared folders of the same type under it. For more information, see the description of the Convert-VBRNASBackupRootFormat cmdlet in the [Veeam PowerShell Reference](https://helpcenter.veeam.com/docs/vbr/powershell/convert-vbrnasbackuprootformat.html?ver=13).

As a result, the backup will be moved from Backups > Disk node to Backups > Disk (Orphaned) node in the inventory pane of the Home view.

At this step, you can check if the cmdlet has correctly converted the backup. To do that, check if backup object names in the Disk (Orphaned) node have changed and now show the path to the server root folder. If object names have not changed and show the paths to multiple separate non-root shared folders as before, continuing the conversion process can lead to the unwanted result. For example, when you enable the backup job for the converted backup, it will back up all shared folders under root folder not with an incremental run, but with a full run instead, which may lead to extra costs.

1. Use the [Edit File Backup Job](file_share_backup_job.md) wizard to edit the file backup job that protects the file shares:

1. At the [Files and Folders](file_share_backup_job_files_and_folders.md) step of the wizard, remove the existing non-root shared folders from the job and add the server root folder instead.
2. At the [Backup Repository](file_share_backup_job_storage.md) step of the wizard, map the job to the backup that was converted at step 2.

1. Enable file backup jobs protecting file shares, for which you converted backups. To do that, right-click the required job from the Jobs node of the inventory pane in the Home view and clear selection Disable. Alternatively, you can click Disable on the ribbon.


