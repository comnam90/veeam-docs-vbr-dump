---
title: "Importing Encrypted Backups"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/import_encrypted_hv.html"
last_updated: "1/22/2026"
product_version: "13.0.1.1071"
---

# Importing Encrypted Backups


You can import backups that were encrypted on this backup server or on another backup server.

To import an encrypted backup file:

1. On the Home tab, click Import Backup.
2. From the Location list, select the host on which the backup you want to import is stored.
3. Click Browse and select the VBM or VBK file.
4. Click OK. The encrypted backup will appear under the Backups > Disk (encrypted) node in the [inventory pane](vbr_ui.md).
5. In the working area, select the imported backup and click Specify Password on the ribbon or right-click the backup and select Specify password.
6. In the Password field, enter the password for the backup file.

If you changed the password one or several times while the backup chain was created, you must enter passwords in the following manner:

+ If you select a VBM file for import, you must specify the latest password that was used to encrypt files in the backup chain.
+ If you select a VBK file for import, you must specify the whole set of passwords that were used to encrypt files in the backup chain.

If you enter the correct passwords, Veeam Backup & Replication will decrypt the backup file. The backup will be moved under the Backups > Disk (Imported) node in the inventory pane.

|  |
| --- |
| Note |
| You can recover data from encrypted backups even if the password is lost. The availability of restoring data without a password depends on the license you use. For more details about licensing support, see [Veeam Data Platform Feature Comparison](https://www.veeam.com/veeam_data_platform_feature_comparison_ds.pdf). Also, your backup server must be connected to Veeam Backup Enterprise Manager. For more information, see [Decrypting Backups With Enterprise Manager Keys](decrypt_without_pass.md). |

![Importing Encrypted Backups](images/decrypt_file.webp)

Related Topics

[Creating Encrypted Configuration Backups](config_backup_encrypted.md)


