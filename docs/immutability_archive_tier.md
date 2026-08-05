---
title: "Immutability for Archive Tier"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/immutability_archive_tier.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Immutability for Archive Tier


Veeam Backup & Replication allows you to prohibit deletion of data from the archive extent by making that data temporarily immutable. Immutability protects your data from loss as a result of attacks, malware activity or any other injurious actions.

You can enable immutability for data stored in the following repositories when they are used as archive extents of the scale-out backup repository:

* Amazon S3 Glacier.
* S3-compatible with data archiving.
* Microsoft Azure Archive Storage.

After you enable immutability, Veeam Backup & Replication prohibits data deletion from the archive extent until the immutability period expires. The duration of the immutability period depends on the immutability mode configured for the archive extent.

|  |
| --- |
| Notes |
| Consider the following:   * When you enable immutability for the archive tier, only the settings of the archive extent are taken into account. The settings of the capacity extents and of the original data blocks are ignored. * The immutability period for backups with GFS flags depends on multiple settings of a scale-out backup repository. For more information, see [GFS Backups Immutability Period](gfs_immutability_sobr.md). |

Immutability Modes

You can select one of the following immutability mode for the archive extent, when you add the object storage repository to the backup infrastructure:

* For the entire duration of their retention policy — in this case, the immutability period depends on the GFS retention of the backup:

* If the GFS retention period is shorter than the minimum immutability period configured for the repository, the minimum immutability period applies.
* If the GFS retention period is longer, the backup is kept for the entire GFS period.

* Minimum immutability — the immutability period always equals the minimum immutability period configured for the repository, ignoring the GFS retention of the backup.

For Amazon S3 Glacier, S3-compatible with data archiving, Veeam Data Cloud Vault Archive and Microsoft Azure Archive Storage, all types of files that are suitable for archive storage can be made immutable:

* Backup files with GFS flags assigned. If GFS retention is extended in the backup job or backup copy job settings, the immutability period for existing backup files will be prolonged at the end of the archiving session. For more information on GFS retention policy, see [Long-Term Retention Policy (GFS)](gfs_retention_policy.md).
* VeeamZIP backup files with specified retention (deletion date). For more information, see [Creating VeeamZIP Backups](create_veeamzip.md).
* Exported backup files with specified retention (deletion date). For more information, see [Exporting Backups](exporting_backups.md).

Enabling Immutability

To enable immutability, you must do the following:

1. Configure the necessary settings when you create an S3 bucket or an Azure container.

For more information, see [Enabling Immutability](immutability_os_enable.md).

1. Enable the immutability option when you add an object storage repository to the backup infrastructure at the Container step (for Azure object storage repository) or Bucket step (for Amazon S3 or S3 compatible object storage repositories) of the new Object Storage Repository wizard.

Related Topics

* [Immutability for Scale-Out Backup Repositories](immutability_sobr.md)
* [Adding Amazon S3 Glacier Storage](osr_amazon_glacier_adding.md)
* [Adding Azure Archive Storage](osr_adding_blob_storage_archive_tier.md)
* [Adding Veeam Data Cloud Vault Archive](veeam_data_cloud_vault_archive.md)
* [Adding S3 Compatible with Data Archiving](compatible_glacier_add.md)
* [GFS Backups Immutability Period](gfs_immutability_sobr.md)

Page updated 2026-07-23

