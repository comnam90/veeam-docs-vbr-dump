---
title: "Step 3. Choose Backup Destination"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/restore_backup_from_tape_target.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 3. Choose Backup Destination


At the Destination step of the wizard, select where the backup files for the selected objects should be restored:

* To restore backup files to a repository, select the Backup repository option and choose the necessary repository from the list.

|  |
| --- |
| Note |
| Restoring machine backups from tapes to object storage repositories is not supported. |

* [For VM and physical machine restore] To restore backup files to the Veeam backup server, shared folder or to any Microsoft or Linux server connected to Veeam backup server, select the Server option. Choose the necessary server from the list and specify path to the target folder in the Path to folder field.

If you choose to restore files to a shared folder, make sure that the account under which Veeam Backup Service runs has write permissions to the target folder. If the account does not have sufficient permissions, Veeam Backup & Replication will prompt you to enter credentials for the account that can be used for writing to the target folder.

|  |
| --- |
| Important |
| The Server option is not available for restoring Veeam Plug-In backups from tape. You can restore Veeam Plug-In backups only to backup repositories added to the backup infrastructure. |

![Step 3. Choose Backup Destination](images/restore_backup_from_tape_target.webp)

Page updated 2026-07-16

