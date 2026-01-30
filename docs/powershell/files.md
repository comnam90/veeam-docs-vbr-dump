---
title: "Managing Backups"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/files.html"
last_updated: "11/14/2025"
product_version: "13.0.1.1071"
---

# Managing Backups


You can use the cmdlet in this topic to perform the following operations:

| Cmdlet | Operation |
| --- | --- |
| [Get-VBRBackup](get-vbrbackup.md) | Returns backups. |
| [Get-VBRGoogleCloudBackup](get-vbrgooglecloudbackup.md) | Returns backups of Google Cloud VM instances. |
| [Get-VBRBackupFile](get-vbrbackupfile.md) | Returns backup files. |
| [Remove-VBRBackup](remove-vbrbackup.md) | Removes backup files. |
| [Remove-VBRBackupFile](remove-vbrbackupfile.md) | Removes missing backup files from the Veeam Backup & Replication configuration database. |
| [Import-VBRBackup](import-vbrbackup.md) | Imports backup files to Veeam Backup & Replication. |
| [Upgrade-VBRBackup](upgrade-vbrbackup.md) | Upgrades the backup chain format of backups from per-machine backup with single metadata file (legacy format) to per-machine backup with separate metadata files. |
| [Detach-VBRBackup](detach-vbrbackup.md) | Detaches backups from the job they belong to. |
| [Move-VBRBackup](move-vbrbackup.md) | Moves all backups of a job to another repository or specific workloads and their backups to another job. |
| [Copy-VBRBackup](copy-vbrbackup.md) | Copies backups to a repository or local or shared folder. |
| [Start-VBRDownloadBackupFile](start-vbrdownloadbackupfile.md) | Starts to download the backup files from the object storage. |
| [Start-VBROffloadBackupFile](start-vbroffloadbackupfile.md) | Starts to move the backup files to the object storage. |
| [Set-VBREncryptedBackupPassword](set-vbrencryptedbackuppassword.md) | Decrypts imported encrypted backups. |
| [Get-VBREncryptedBackup](get-vbrencryptedbackup.md) | Looks for imported encrypted backups. |
| [Remove-VBREncryptedBackup](remove-vbrencryptedbackup.md) | Removes selected encrypted backups. |
| [Get-VBREncryptedBackupHint](get-vbrencryptedbackuphint.md) | Looks for password hints for imported encrypted backups. |
| [Start-VBRDownloadTenantBackup](start-vbrdownloadtenantbackup.md) | Downloads tenant backups from capacity tier to performance tier. |
| [Get-VBRCloudUnavailableBackupFile](get-vbrcloudunavailablebackupfile.md) | Returns a list of backup files that are no longer available in the cloud repository. |
| [Forget-VBRCloudUnavailableBackupFile](forget-vbrcloudunavailablebackupfile.md) | Removes backup files that are no longer available from a cloud repository. |
| [Get-VBRDeletedArchivedBackupFile](get-vbrdeletedarchivedbackupfile.md) | Returns a list of backup files from insider protection. |
| [Download-VBRDeletedArchivedBackupFile](download-vbrdeletedarchivedbackupfile.md) | Retrieves backup files from insider protection. |
| [Get-VBRDeletedDehydratedBackupFile](get-vbrdeleteddehydratedbackupfile.md) | Returns a list of backup files from capacity tier. |
| [Rehydrate-VBRDeletedBackupFile](rehydrate-vbrdeletedbackupfile.md) | Retrieves backup files from capacity tier. |
| [Get-VBRCloudTenantBackup](get-vbrcloudtenantbackup.md) | Returns non-encrypted backups of AD tenants and tenants managed by the Service Provider. |
| [Remove-VBRCloudTenantBackup](remove-vbrcloudtenantbackup.md) | Removes selected backups of tenants from disk. |
| [Apply-VBRBackgroundRetention](apply-vbrbackgroundretention.md) | Performs background retention for backups. |
| [Enable-VBRBackgroundRetention](enable-vbrbackgroundretention.md) | Enables previously disabled background retention for backups. |
| [Disable-VBRBackgroundRetention](disable-vbrbackgroundretention.md) | Disables background retention for backups. |
| [Get-VBRSOBRObjectStorageBackup](get-vbrsobrobjectstoragebackup.md) | Returns backups available in archive extents and capacity extents of scale-out backup repositories. |


