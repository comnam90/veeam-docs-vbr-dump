---
title: "How Backup Data Decryption Works"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/decryption_hiw.html"
last_updated: "12/22/2025"
product_version: "13.0.1.1071"
---

# How Backup Data Decryption Works


To perform operations with backup files, you need to decrypt them first. Backup files can be decrypted automatically or manually:

* If you encrypt data encryption keys with KMS keys, backup files are decrypted automatically when you import them. In some cases, you need to decrypt backup files manually. For more information, see [How KMS Works](kms_how_it_works.md).
* If you encrypt data encryption keys with secret keys, backup files are decrypted automatically only when the following conditions are met:

* You encrypt and decrypt the backup file on the same backup server that uses the same configuration database.
* The backup is not removed from the Veeam Backup & Replication console.

In other cases, you need to enter a password you specified in the encryption options.

|  |
| --- |
| Note |
| To decrypt backup files, a desktop version of the Veeam Backup & Replication console is required. The feature is not supported in the Veeam Backup & Replication web UI. |

Veeam Backup & Replication transfers encrypted data to the source side and performs data decryption. Decrypted files appear under the Backups > Disk (Imported) node in the inventory pane.

For more information on how to decrypt backups, see [Decrypting Backups](decrypt_with_pass.md). If you want to restore data from encrypted backups, see the following sections:

* [Restoring Data from Encrypted Backups](restore_encrypted.md)
* [Restoring Data from Encrypted Tapes](tapes_restore_encrypted.md)


