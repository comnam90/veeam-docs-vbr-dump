---
title: "Encrypting VeeamZIP Backups"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/encrypting_veeam_zip.html"
last_updated: "1/31/2025"
product_version: "13.0.1.1071"
---

# Encrypting VeeamZIP Backups


The encryption process for a VeeamZIP session includes the following steps:

1. Encryption is configured in the [VeeamZIP session options](create_veeamzip.md). When you enable the encryption option, you need to enter a password or select a KMS server.
2. If you enter a password, Veeam Backup & Replication generates a secret key. If you select a KMS server, Veeam Backup & Replication asks the KMS server to generate an asymmetric KMS key. A secret key or a KMS key will be used to encrypt data encryption keys during the job.  For more information, see [How Backup Data Encryption Works](encryption_hiw.md).
3. When you start a job, Veeam Backup & Replication encrypts backup files with data encryption keys. By default, this operation is performed on the backup proxy.
4. Encrypted data is passed to the target backup repository and stored to a resulting backup file.

[![Encrypting VeeamZIP Backups](images/backup_job_encryption.webp)](images/backup_job_encryption.webp)

|  |
| --- |
| Note |
| If you plan to store backups in [Veeam Data Cloud Vault](osr_adding_veeam_data_cloud_vault.md), you must enable encryption for VeeamZIP backup. |


