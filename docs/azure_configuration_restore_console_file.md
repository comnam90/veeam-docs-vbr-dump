---
title: "Step 2. Choose Backup File"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_configuration_restore_console_file.html"
last_updated: "2025"
product_version: "13.1.0.411"
---

# Step 2. Choose Backup File


At the Configuration backup step of the wizard, do the following:

1. From the Backup Repository list, select a backup repository where the configuration backup file is stored.

For a repository to be displayed in the list of available repositories, it must be added to the backup infrastructure as described [Adding Backup Repositories](repo_add.md).

1. Click Browse and select the necessary file.

|  |
| --- |
| Note |
| If the selected configuration backup file is not stored on the backup server, Veeam Backup & Replication will copy the file to a temporary folder on the server and automatically delete it from the folder as soon as the restore process completes. |

![Step 2. Choose Backup File](images/azure_restore_config_backup.webp)

Page updated 2025-08-20

