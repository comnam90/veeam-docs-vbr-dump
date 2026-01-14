---
title: "Adding Amazon S3 Glacier Storage"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/osr_amazon_glacier_adding.html"
last_updated: "8/7/2025"
product_version: "13.0.1.1071"
---

# Adding Amazon S3 Glacier Storage

In this article

Veeam Backup & Replication uses Amazon S3 Glacier object storage with Amazon S3 service. For more information about Amazon S3 storage classes that you can use for this object storage repository, see [AWS Documentation](https://aws.amazon.com/s3/storage-classes/?nc1=h_ls#Archive).

|  |
| --- |
| Note |
| Consider the following:   * Veeam Backup & Replication does not create or use any S3 Glacier vaults in your AWS environment. Glacier vaults is an archive storage solution independent from AWS. It uses storage containers named vaults (opposed to S3 buckets) and its own set of APIs to upload and retrieve data. * Amazon S3 Glacier storage uses S3 APIs to manage data. It also uses S3 storage as a repository for metadata of the Glacier-stored objects. Veeam Backup & Replication assigns the added storage class to backups stored in the repository. That is why the archived backups remain in Amazon S3 and cannot be accessed directly through the Amazon S3 service. |

You can only use this repository as an archive extent of the scale-out backup repository. For more information, see [Archive Tier](archive_tier.md).

To add Amazon S3 Glacier object storage, use the New Object Storage Repository wizard.

1. [Launch the New Object Storage Repository wizard](glacier_repository_launch.md).
2. [Specify object storage name](glacier_repository_name.md).
3. [Specify object storage account](glacier_repository_account.md).
4. [Specify object storage settings](glacier_storage_details.md).
5. [Specify archiver appliance](glacier_archiver_appliance.md).
6. [Finish working with the wizard](glacier_finishing_wizard.md).

Page updated 8/7/2025

Page content applies to build 13.0.1.1071
