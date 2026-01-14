---
title: "Encryption"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/external_repository_encryption.html"
last_updated: "10/20/2025"
product_version: "13.0.1.1071"
---

# Encryption

In this article

Backups that reside in Amazon S3 buckets, Google Cloud storage\* and Azure Blob storage can be encrypted by [Veeam Backup for AWS](https://helpcenter.veeam.com/docs/vbaws/guide/overview.html?ver=10), [Veeam Backup for Google Cloud](https://helpcenter.veeam.com/docs/vbgc/guide/welcome.html?ver=7)\* and [Veeam Backup for Microsoft Azure](https://helpcenter.veeam.com/docs/vbazure/guide/overview.html?ver=8.1). Moreover, password for such encrypted backups may change on a daily basis. For example, there is a backup chain in Amazon S3 bucket that consists of 10 restore points, each of which was encrypted with different password. Therefore, there are 10 different passwords in total that have been used.

To be able to decrypt each restore point in such a backup chain without having to provide each previously used password separately, Veeam Backup & Replication implements the ability of backward hierarchical decryption.

Backward hierarchical decryption requires you to provide only the latest password so that all the previously created restore points can be decrypted as well. For example, there are three restore points: A, B, and C. The point A was encrypted with password 1, B with password 2, and C with password 3. Therefore, you will only need to know the password of the C point to decrypt points C, B, and A.

If you plan to perform data recovery operations with encrypted backups, you must provide a password for these backups in the External Repository wizard:

* [For Veeam Backup for AWS] At the [Encryption](external_repository_s3_encryption.md) step of the wizard.
* [For Veeam Backup for Microsoft Azure] At the [Encryption](external_azure_encryption.md) step of the wizard.
* [For Google Cloud\*] At the [Bucket](external_google_cloud_details.md) step of the wizard.

\*This feature is available for Microsoft Windows-based backup servers.

Page updated 10/20/2025

Page content applies to build 13.0.1.1071
