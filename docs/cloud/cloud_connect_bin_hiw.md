---
title: "How Insider Protection Works"
product: "vbr"
doc_type: "cloud"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/cloud_connect_bin_hiw.html"
last_updated: "3/14/2024"
product_version: "13.0.1.1071"
---


In this article

Veeam Backup & Replication performs protection of tenant backup files against accidental or intentional deletion in the following way:

1. The SP enables the Keep deleted backup files for <N> days option in the properties of the tenant account.
2. The tenant creates a backup in the cloud repository in one of the following ways:

* In Veeam Backup & Replication, runs a VM backup job, Veeam Agent backup job or backup copy job targeted at the cloud repository.
* In Veeam Agent for Microsoft Windows or Veeam Agent for Linux, runs a Veeam Agent backup job targeted at the cloud repository.

1. When a backup or restore point is deleted from the cloud repository, Veeam Backup & Replication moves the backup files to the \_RecycleBin folder on the SP backup repository whose storage resources are exposed to tenants as cloud repositories. Veeam Backup & Replication performs this operation in the following cases:

* When the tenant performs the Delete from disk operation with a backup on a cloud repository.

In this case, Veeam Backup & Replication performs the following operations:

1. On the tenant side, Veeam Backup & Replication removes the backup from the tenant Veeam Backup & Replication console and database.
2. On the SP side, Veeam Backup & Replication moves backup files pertaining to the deleted backup to the "recycle bin".

* When the tenant performs the Delete operation with a backup file on a cloud repository in the Files node of the Veeam Backup & Replication console.

* When one or more backup files are automatically deleted from the backup chain in a cloud repository according to the retention policy defined in the job settings. This includes deletion of obsolete backup files within a backup or backup copy job session, or by a background retention job. This does not include incremental backup files of forever forward incremental backup chains that are merged to a full backup file during backup chain transform.

Veeam Backup & Replication moves to the "recycle bin" only backup files of the VBK, VIB and VRB types. VBM backup files are deleted from disk immediately.

For backups created by backup copy jobs, Veeam Backup & Replication does not move transaction log backup files to the "recycle bin".

|  |
| --- |
| Note |
| Consider the following:   * If the tenant plans to create off-site backups with a backup copy job, they should enable GFS retention settings in the job properties. This way, Veeam Backup & Replication will be able to protect backups created with the job against an attack when a hacker reduces the job retention policy and creates a few incremental backups to remove backed-up data from the backup chain.   With GFS retention settings enabled, the backup chain will contain a sequence of full backups that will not merge according to a retention policy. After such a backup is moved to the "recycle bin", the tenant will be able to use it for data restore.  If the tenant does not enable GFS retention settings for the backup copy job, the job will complete with a warning. In the job statistics window, Veeam Backup & Replication will display a notification advising to use the GFS retention scheme for the job.   * If the SP uses the capacity tier or archive tier functionality, insider protection processes backup files differently depending on the way the backup files were offloaded to object storage. For more information, see [Insider Protection and Capacity Tier](#tier). |

1. Veeam Cloud Connect Service running on the SP backup server checks the configuration database to get the date when the backup file was moved to the "recycle bin" and compares it to the current date. This operation is performed regularly with an interval of 20 minutes.
2. When the time interval between the date when the backup file was moved to the "recycle bin" and the current date exceeds the number of days specified in the Keep deleted backup files for <N> days setting, Veeam Backup & Replication deletes the backup file from the \_RecycleBin folder.

Insider Protection and Capacity Tier

The SP can use insider protection along with the capacity tier functionality. In this scenario, when a tenant backup whose data was offloaded to capacity tier is deleted from the cloud repository, Veeam Backup & Replication processes backup files in one of the following ways:

* If the tenant data was copied to capacity tier, Veeam Backup & Replication moves backup files that reside in performance tier to the "recycle bin". After that, Veeam Backup & Replication deletes backup files that reside in capacity tier from the object storage.

Backup files are kept in the "recycle bin" for the number of days specified in the properties of the tenant account. After that, Veeam Backup & Replication removes backup files from the "recycle bin".

* If the tenant data was moved to capacity tier, Veeam Backup & Replication does not move the actual backup files to the "recycle bin". Instead, Veeam Backup & Replication marks the backup files as moved to the "recycle bin". This information is saved in the configuration database on the SP backup server.

Information about backups in insider protection is kept in the database for the number of days specified in the properties of the tenant account. After that, Veeam Backup & Replication removes backup files from capacity tier.

In case the tenant needs to restore data from deleted backups whose files reside in capacity tier (that is, backups whose data was moved to capacity tier), the SP must download the necessary backup files from capacity tier. This operation is performed using Windows PowerShell scripts. For details, contact [Veeam Customer Support](https://www.veeam.com/support.html).

When the SP downloads deleted backups from capacity tier, Veeam Backup & Replication performs the following operations:

1. Downloads backup files from capacity tier and saves them to the "recycle bin" in performance tier.
2. Removes backup files from capacity tier.

The same mechanism applies to tenant backups that were offloaded to archive tier in the scenario where the SP uses insider protection along with the archive tier functionality.

|  |
| --- |
| Note |
| If the tenant uses data deduplication, backup files in object storage that are marked as moved to the "recycle bin" share data blocks with other backup files in object storage. |

Page updated 3/14/2024

Page content applies to build 13.0.1.1071
