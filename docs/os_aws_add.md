---
title: "Adding Amazon S3 Object Storage"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/os_aws_add.html"
last_updated: "11/7/2023"
product_version: "13.0.1.1071"
---

# Adding Amazon S3 Object Storage

In this article

Before you add an Amazon S3 object storage to the inventory of the virtual infrastructure, consider the following:

* The object storage meets requirements and limitations listed in the [Platform Support](https://helpcenter.veeam.com/docs/backup/vsphere/platform_support.html?ver=120#nas-backup-support) section.

* If you plan to use dedicated proxy servers, make sure these components are added in the [Backup Infrastructure](https://helpcenter.veeam.com/docs/backup/vsphere/unstructured_data_backup_infrastructure.html?ver=120).

To add an Amazon S3 object storage as a source of unstructured data, do the following:

1. [Launch the New Object Storage wizard](os_s3_aws_launch.md).
2. [Specify account settings](os_s3_aws_account.md).
3. [Specify object storage processing settings](os_s3_aws_processing.md).
4. [Apply object storage settings](os_s3_aws_apply.md).
5. [Finish working with the wizard](os_s3_aws_finish.md).

Page updated 11/7/2023

Page content applies to build 13.0.1.1071
