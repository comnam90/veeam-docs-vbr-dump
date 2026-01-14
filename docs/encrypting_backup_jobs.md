---
title: "Encrypting Backup Jobs"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/encrypting_backup_jobs.html"
last_updated: "2/10/2025"
product_version: "13.0.1.1071"
---

# Encrypting Backup Jobs

In this article

The encryption process for a backup job includes the following steps:

1. Job encryption is configured in the [advanced job settings](backup_job_advanced_storage_vm.md). When you enable the encryption option, you need to enter a password or select a KMS server.
2. If you enter a password, Veeam Backup & Replication generates a secret key. If you select a KMS server, Veeam Backup & Replication asks the KMS server to generate an asymmetric KMS key. A secret key or a KMS key will be used to encrypt data encryption keys during the job.  For more information, see [How Backup Data Encryption Works](encryption_hiw.md).
3. When you start a job, Veeam Backup & Replication encrypts backup files with data encryption keys. By default, this operation is performed on the backup proxy.
4. Encrypted data is passed to the target backup repository and stored to a resulting backup file.

![Encrypting Backup Jobs](images/backup_job_encryption.webp)

|  |
| --- |
| Note |
| If you plan to store backups in [Adding Veeam Data Cloud Vault](osr_adding_veeam_data_cloud_vault.md), you must enable job encryption. |

If you update encryption settings for an existing backup job, consider the following:

* If you enable encryption, during the next job session Veeam Backup & Replication will automatically create a full backup file. The created full backup file and subsequent incremental backup files in the backup chain will be encrypted with the specified password or KMS key.

Note that Veeam Backup & Replication does not encrypt the previous backup chain created by this job. If you want to start a new chain so that the unencrypted previous chain can be separated from the encrypted new chain, follow [this Veeam KB article](https://www.veeam.com/kb1885).

* If you change the password or start using KMS keys for the already encrypted job, during the next job session Veeam Backup & Replication will create a new incremental backup file. The created backup file and subsequent backup files in the backup chain will be encrypted with the new password or KMS key.
* If you disable encryption, during the next job session Veeam Backup & Replication will automatically create a full backup file.

Page updated 2/10/2025

Page content applies to build 13.0.1.1071
