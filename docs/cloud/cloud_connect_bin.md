---
title: "Insider Protection"
product: "vbr"
doc_type: "cloud"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/cloud_connect_bin.html"
last_updated: "1/26/2024"
product_version: "13.0.1.1071"
---

# Insider Protection


In some situations, keeping primary or additional backups in a cloud repository may be not enough to ensure data security for a tenant. The backed-up data may become unavailable because of an insider attack. For example, a hacker can gain access to the tenant Veeam Backup & Replication console and delete all tenant backups, including off-site backups stored in the cloud repository. Or a backup administrator on the tenant side can accidentally or intentionally delete backups from a cloud repository. Veeam Backup & Replication allows the SP to protect tenant data against attacks of this kind.

Veeam Backup & Replication offers the insider protection functionality for the following types of tenant backups:

* VM backups and Veeam Agent backups created by backup jobs configured in Veeam Backup & Replication
* Backups of physical or virtual machines created by Veeam Agent backup jobs configured in Veeam Agent for Microsoft Windows or Veeam Agent for Linux
* Backup copies of VM backups or Veeam Agent backups created by backup copy jobs configured in Veeam Backup & Replication

The SP can enable the insider protection option individually for a specific tenant. To enable the option, the SP must select the Keep deleted backup files for <N> days check box in the properties of the tenant account. With this option enabled, when a backup or a specific restore point in the backup chain is deleted from the cloud repository, Veeam Backup & Replication does not immediately delete the actual backup files. Instead, Veeam Backup & Replication moves backup files to the "recycle bin".

Technically, a "recycle bin" is a folder on the backup repository in the SP backup infrastructure whose storage resources are exposed to tenants as cloud repositories. Veeam Backup & Replication automatically creates this folder at the time when a tenant backup file is moved to the "recycle bin" for the first time.

Backup files in the "recycle bin" do not consume the tenant quota. However, these backup files consume disk space on the SP storage where the cloud repository is configured. Thus, if the SP plans to offer insider protection to tenants, they should consider allocating sufficient storage resources in the Veeam Cloud Connect infrastructure.

For the tenant, backup files moved to the "recycle bin" appear as actually deleted. The tenant cannot access backup files in the "recycle bin" and perform operations with them. If a tenant needs to restore data from a deleted backup whose backup files still reside in a "recycle bin", the tenant must contact the SP to obtain the necessary backup files. To learn more, see [Data Restore from Deleted Backups](cloud_connect_bin_restore.md).

|  |
| --- |
| Note |
| Consider the following:   * If a tenant renames a job targeted at the cloud repository, and then deletes a backup, Veeam Backup & Replication will move the backup files to a folder with the initial name of the job. As a result, it may become difficult for the SP to find the necessary backup files in case the tenant needs to restore data from backup files in the "recycle bin". To overcome such situations, the SP should recommend tenants who use the insider protection functionality to avoid renaming jobs targeted at the cloud repository of the SP. * After the SP enables insider protection for the tenant account, the tenant can use the Files view in the Veeam Backup & Replication console only to delete backup files from the cloud repository. Other operations with backup files in the Files node are unavailable. * The insider protection functionality is not supported for tenant backups if an object storage repository is assigned to the tenant as a cloud repository. After the SP assigns such a cloud repository to the tenant, backups in other repositories are no longer covered by insider protection. |

Veeam Backup & Replication keeps tenant backup files in the "recycle bin" for a specific number of days defined by the SP. After this period expires, Veeam Backup & Replication completely deletes tenant backup files from the "recycle bin".

Related Topics

* [How Insider Protection Works](cloud_connect_bin_hiw.md)
* [Data Restore from Deleted Backups](cloud_connect_bin_restore.md)


