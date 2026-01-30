---
title: "Immutability for Archive Tier"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/immutability_archive_tier.html"
last_updated: "12/23/2025"
product_version: "13.0.1.1071"
---

# Immutability for Archive Tier


Veeam Backup & Replication allows you to prohibit deletion of data from the archive extent by making that data temporarily immutable. It is done for increased security: immutability protects your data from loss as a result of attacks, malware activity or any other injurious actions.

You can enable immutability for data stored in Amazon S3 Glacier, S3-compatible with data archiving and Microsoft Azure Archive Storage repositories used as archive extents of the scale-out backup repository. After you enable immutability, Veeam Backup & Replication will prohibit data deletion from the archive tier until the immutability expiration date comes.

|  |
| --- |
| Note |
| Consider the following:   * When you enable immutability for the archive tier, keep in mind that only the settings of the archive extents will be taken into account. The settings of the capacity extents and of the original data blocks will be ignored. * The immutability period for backups with GFS flags depends on multiple settings of a scale-out backup repository. For more information, see the [GFS Backups Immutability Period](gfs_immutability_sobr.md) section. |

For Amazon S3 Glacier, S3-compatible with data archiving and Microsoft Azure Archive Storage, all the types of files that are suitable for archive storage can be made immutable:

* Backup files with GFS flags assigned: in case GFS retention is extended in the backup job or backup copy job settings, the immutability period for existing backup files will be prolonged at the end of the archiving session. For more information about GFS retention policy, see [Long-Term Retention Policy (GFS)](gfs_retention_policy.md).
* VeeamZIP backup files with specified retention (deletion date). For more information, see [Creating VeeamZIP Backups](create_veeamzip.md).
* Exported backup files with specified retention (deletion date). For more information, see [Exporting Backups](exporting_backups.md).

The immutability period of a backup file will be equal to its retention period at the moment of archiving. If the retention period is not specified for VeeamZIP backup files or exported backup files, such files will not be made immutable.

Enabling Immutability

To enable immutability, you must do the following:

1. Configure the necessary settings when you create an S3 bucket or an Azure container.

For more information, see [Enabling Immutability](immutability_os_enable.md).

1. Enable the immutability option when you add an object storage repository to the backup infrastructure at the Container step (for Azure object storage repository) or Bucket step (for Amazon S3 or S3 compatible object storage repositories) of the new Object Storage Repository wizard.

Related Topics

* [Immutability for Scale-Out Backup Repositories](immutability_sobr.md)
* [Adding Amazon S3 Glacier Storage](osr_amazon_glacier_adding.md)


