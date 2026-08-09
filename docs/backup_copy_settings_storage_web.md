---
title: "Storage Settings"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/backup_copy_settings_storage_web.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Storage Settings


To specify compression, deduplication and encryption settings for backup files stored in the target backup repository, do the following:

1. At the Target step of the wizard, click Advanced job settings.
2. Click the Storage tab.
3. Specify data compression and deduplication settings:

* By default, Veeam Backup & Replication performs deduplication before storing copied data in the target backup repository. To disable data deduplication, clear the Enable inline data deduplication check box.

For more information on deduplication, see [Deduplication](compression_deduplication.md#dedup).

* From the Compression level list, select a compression level.

For more information on data compression levels, see [Data Compression](compression_deduplication.md).

1. To encrypt backup files, select the Enable backup file encryption option. In the Password field, select the encryption method you want to use — a password that will generate secret keys or an external KMS server that will generate KMS keys. For more information about backup copy job encryption, see [Encrypting Backup Copy Jobs](encrypting_backup_copy_jobs.md).

If you have not created the password beforehand, click Add or use the Manage passwords link to specify a new password. For more information, see [Password Manager](password_manager.md).

If you do not use password loss protection, Veeam Backup & Replication will display a warning about it. For more information, see [Password Loss Protection](encryption_password_loss_protection.md).

1. If you want to save this set of settings as the default one, click Save as Default. When you create a new job, the saved settings will be offered as the default. This also applies to all users added to the backup server.

![Storage Settings](images/backup_copy_advanced_storage.webp)

Page updated 2026-07-27

