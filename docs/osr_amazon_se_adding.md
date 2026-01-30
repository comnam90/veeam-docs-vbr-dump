---
title: "Adding AWS Snowball Edge Storage"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/osr_amazon_se_adding.html"
last_updated: "8/8/2024"
product_version: "13.0.1.1071"
---

# Adding AWS Snowball Edge Storage


[AWS Snowball Edge](https://docs.aws.amazon.com/snowball/latest/developer-guide/whatisedge.html) is a physical device which you can request for a short period of time from Amazon. You can temporarily attach it to the backup infrastructure and use as an object storage repository. For more information about ordering AWS Snowball Edge and preparing to use it, see [this Amazon article](https://docs.aws.amazon.com/snowball/latest/developer-guide/getting-started.html).

This device may become useful when you need to offload a significant number of backup files occupying storage space on your extents, as offloading data to the AWS Snowball Edge device is much faster than transferring the same amount of data directly to Amazon object storage. Once you have offloaded backups to AWS Snowball Edge, you need to ship the device back to Amazon for further data synchronization with your storage account, as described in section [Seeding Backups to Amazon S3 Storage](amazon_se_seeding.md).

To add AWS Snowball Edge storage, do the following:

1. [Check prerequisites](byb_snow.md).
2. [Launch the New Object Storage Repository wizard](amazon_se_repository_launch.md).
3. [Specify object storage name](amazon_se_repository_name.md).
4. [Specify object storage account](amazon_se_repository_account.md).
5. [Specify object storage settings](amazon_se_storage_details.md).
6. [Finish working with the wizard](amazon_se_finishing_wizard.md).


