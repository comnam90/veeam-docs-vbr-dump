---
title: "Decrypting Tapes with KMS Keys"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/tape_decrypt_kms.html"
last_updated: "1/9/2026"
product_version: "13.0.1.1071"
---

# Decrypting Tapes with KMS Keys

In this article

Tapes can be decrypted automatically or manually.

Decrypting Tapes Automatically

If you encrypt data encryption keys with KMS keys, tapes are decrypted automatically when you import them. Decrypted backup files appear under the Backups > Tape node in the inventory pane. After that, you can perform restore operations for data archived to tape as usual.

Decrypting Tapes Manually

In the following situations, you need to decrypt tapes manually:

* You perform tape catalogization on a new Veeam Backup & Replication installation that is not connected to the KMS server yet.
* On a new Veeam Backup & Replication installation, you run separate catalog jobs for tapes encrypted with the KMS solution and tapes encrypted with password-based keys.

To decrypt tapes manually, do the following:

1. Insert encrypted tapes into the tape library.
2. Catalog the tapes. Encrypted tapes will be marked with the key icon and displayed under the Media Pools > Imported node in the tape library.
3. In the working area, select the imported tape and click Specify Password on the ribbon. Alternatively, you can right-click the tape and select Specify password.

[![Decrypting Tapes with KMS Keys](images/decrypt_tapes.webp)](images/decrypt_tapes.webp)

1. Check the encryption key ID and selected KMS server, and click OK. Veeam Backup & Replication will decrypt the tape media.

![Decrypting Tapes with KMS Keys](images/kms_decrypt_backups.webp)

Consider the following:

* If you import a backup file that was encrypted twice, you will need to subsequently do the following:

* To decrypt the tape, specify a KMS key for the initial media pool used as a target in the backup to tape job. Backup files from the tape will be displayed under the Backup > Tape (Encrypted) node in the inventory pane.
* Specify a KMS key for the initial backup job to decrypt the backup and get access to its content.

For more information, see [How Double Data Encryption Works](encryption_tape.md#double_encryption_hiw).

* If a KMS key has changed several times or you have switched between encryption methods, you will need to do the following:

+ If you catalog all tapes in the media pool including the last tape at a time, you must specify only the latest KMS key that was used to encrypt data encryption keys. It will decrypt all tapes regardless of the previously used KMS keys.
+ If you catalog specific tapes in the media pool, you must specify the KMS key that was used to encrypt data encryption keys for this specific tape.

* If you cannot use KMS keys due to a KMS server failure, you can issue a request to Veeam Backup Enterprise Manager and restore data from encrypted tapes using Enterprise Manager keys. This option works only if the password loss protection is enabled. For more information, see [Decrypting Tapes With Enterprise Manager Keys](tape_decrypt_no_password.md).
* If the imported tape is a part of a backup set but is not the last tape in this set, after you decrypt the type media, perform catalogization once again.

Page updated 1/9/2026

Page content applies to build 13.0.1.1071
