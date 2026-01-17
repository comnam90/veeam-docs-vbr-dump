---
title: "Adding Amazon S3 Object Storage"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/os_aws_add.html"
last_updated: "1/12/2026"
product_version: "13.0.1.1071"
---

# Adding Amazon S3 Object Storage

In this article

Before you add an Amazon S3 object storage to the inventory of the virtual infrastructure, consider the following:

* Veeam Backup & Replication does not support backup from and restore to AWS Snowball Edge Storage.
* If you plan to use dedicated proxy servers, make sure these components are added in the [Backup Infrastructure](unstructured_data_backup_infrastructure.md).

To add an Amazon S3 object storage as a source of unstructured data, do the following:

1. [Launch the New Object Storage wizard](os_s3_aws_launch.md).
2. [Specify account settings](os_s3_aws_account.md).
3. [Specify object storage processing settings](os_s3_aws_processing.md).
4. [Apply object storage settings](os_s3_aws_apply.md).
5. [Finish working with the wizard](os_s3_aws_finish.md).

Page updated 1/12/2026

Page content applies to build 13.0.1.1071
