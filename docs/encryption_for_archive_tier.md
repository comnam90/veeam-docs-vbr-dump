---
title: "Encryption for Archive Tier"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/encryption_for_archive_tier.html"
last_updated: "12/11/2024"
product_version: "13.0.1.1071"
---

# Encryption for Archive Tier


Veeam Backup & Replication allows you to encrypt archived data. This helps you protect the data from unauthorized access.

You can enable data encryption in the following ways:

* When you create a [backup or backup copy job](encryption_job.md).
* When you add an [archive extent](new_archive_tier.md) to your scale-out backup repository.

To get benefits of both encryption levels, you can use job-level and archive tier encryption within the same object storage. Both encryption levels prevents unauthorized access to your data, but the archive tier encryption allows you to encrypt backup chain metadata and restore points. After you enable encryption on the archive tier level, the archiving job encrypts the entire collection of blocks along with the metadata.

To encrypt data, Veeam Backup & Replication uses the following scheme:

1. The user specifies the password in the [archiving tier settings](new_archive_tier.md#encryption).
2. Veeam Backup & Replication generates an encryption key and uses the password to encrypt this key.
3. To encrypt the backups in the archive tier, Veeam Backup & Replication uses this encryption key.

To access the data in the archive extent you need to provide the password that is used to decrypt the encryption keys.

Encryption Scenarios

When data is moved to the archiving tier, Veeam Backup & Replication applies encryption on the archive tier level. Data encrypted by the backup job stays as is on the archive tier, Thus, this backup has 2 levels of encryption: on the job level an on the archive tier level.

Depending on the configuration of a scale-out backup repository, Veeam Backup & Replication will process backups according the following scenarios:

* If you use the performance tier, Veeam Backup & Replication encrypts data on the archive tier level.
* If you use the performance tier and the capacity tier with encryption, Veeam Backup & Replication decrypts the backups from the capacity tier and encrypts them on the archive tier level.
* If you do not apply encryption on the capacity tier level, Veeam Backup & Replication will encrypt backups on the archive tier level.
* If you apply encryption on the capacity tier level, but do not apply encryption on the archive tier level, Veeam Backup & Replication will decrypt these backups and will move them to the archiving tier unencrypted.

|  |
| --- |
| Important |
| When you disable encryption, the encryption key is added to the file system of your backup repository and all encrypted backups located on the archive tier become unencrypted. If you enable encryption again, Veeam Backup & Replication will encrypt only new backups with a new encryption key. |


