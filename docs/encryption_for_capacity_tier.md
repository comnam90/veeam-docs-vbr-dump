---
title: "Encryption for Capacity Tier"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/encryption_for_capacity_tier.html"
last_updated: "5/6/2025"
product_version: "13.0.1.1071"
---

# Encryption for Capacity Tier


Veeam Backup & Replication allows you to encrypt archived data. This helps you protect the data from unauthorized access.

You can enable data encryption in the following ways:

* When you create a [backup or backup copy job](encryption_job.md).
* When you add a [capacity extent](new_capacity_tier.md) to your scale-out backup repository.

To get benefits of both encryption levels, you can use job-level and the capacity tier encryption within the same object storage. Both encryption levels prevents unauthorized access to your data, but the capacity tier encryption allows you to encrypt backup chain metadata and restore points. After you enable encryption on the capacity tier level, Veeam Backup & Replication encrypts the entire collection of blocks along with the metadata. Data encrypted by the backup job stays as is on the capacity tier, Thus, this backup has 2 levels of encryption: on the job level an on the capacity tier level.

To encrypt data, Veeam Backup & Replication uses the following scheme:

1. The user specifies the password in the [archiving tier settings](new_archive_tier.md#encryption).
2. Veeam Backup & Replication generates an encryption key and uses the password to encrypt this key.
3. To encrypt the backups in the capacity tier, Veeam Backup & Replication uses this encryption key.

To access the data in the archive extent you need to provide the password that is used to decrypt the encryption keys.

|  |
| --- |
| Important |
| Consider the following:   * When you disable encryption, the encryption key is added to the file system of your backup repository and all encrypted backups located on the capacity tier become unencrypted. If you enable encryption again, Veeam Backup & Replication will encrypt only new data with a new encryption key. * If you enable encryption for the capacity extent that already contains backups, it will not automatically encrypt these backups. If a backup job creates an active full or synthetic full backup, it will consist of encrypted and unencrypted data blocks after offload to the capacity tier. This backup will remain in the capacity tier in this state until new encrypted data blocks completely replace the unencrypted blocks. * If you enable encryption after you have already offloaded data to capacity tier, Veeam Backup & Replication will not encrypt previously offloaded backup chains. |


