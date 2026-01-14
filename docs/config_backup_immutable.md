---
title: "Creating Immutable Configuration Backups"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/config_backup_immutable.html"
last_updated: "11/9/2025"
product_version: "13.0.1.1071"
---

# Creating Immutable Configuration Backups

In this article

Veeam Backup & Replication allows you to keep configuration backups on object storage repositories that support immutability. Immutability makes data temporarily immutable and prohibits deletion of configuration backups from object storage repositories. Therefore, it protects your data against loss as a result of attacks, malware activity or any other injurious actions.

Retention Policy for Immutable Configuration Backups

By default, object storage repositories keeps the number of restore points that you define in the configuration backup settings. In case, a total number of restore point exceeds the retention policy settings, Veeam Backup & Replication deletes the oldest restore point. If you keep configuration backups on immutable object storage repositories, Veeam Backup & Replication will not delete the older restore points. Instead, it will mark them as immutable and will keep them on object storage repositories until immutability period passes.

Creating Immutable Configuration Backups

To make configurations backups immutable, perform the following steps:

1. Configure an object storage repository where you will keep configuration backups. For more information, see [Immutability for Object Storage Repositories](immutability_object_storage_repositories.md).
2. From the main menu, select Configuration Backup.
3. Make sure that the Enable configuration backup to the following repository check box is selected.
4. From the Backup repository list, choose an object storage repository on which the configuration backup must be stored.
5. In the Restore points to keep field, specify the number of restore points that you want to maintain in the object storage repository.
6. To create an encrypted backup, select the Enable backup file encryption check box. From the Password field, select a password you want to use for encryption. If you have not created a password beforehand, click Add or use the Manage passwords link to specify a new password. For more information, see [Creating Encrypted Configuration Backups](config_backup_encrypted.md).
7. Click Backup now.

![Creating Immutable Configuration Backups](images/immutable_config_backup.webp)

Page updated 11/9/2025

Page content applies to build 13.0.1.1071
