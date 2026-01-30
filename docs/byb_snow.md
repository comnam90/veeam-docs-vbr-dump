---
title: "Before You Begin"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/byb_snow.html"
last_updated: "9/25/2024"
product_version: "13.0.1.1071"
---

# Before You Begin


Before you add AWS Snowball Edge storage to the backup infrastructure, check the following prerequisites:

* To maintain the device performance, be sure to select 1 MB or 4 MB as the storage optimization option when you configure a backup job. For more information on the optimization, see [Storage Optimization](compression_deduplication.md#optimization).
* When you configure a scale-out backup repository with AWS Snowball Edge storage or [capacity tier](capacity_tier.md) in a scale-out backup repository, it is recommended to only use the copy policy. This way you keep copy of the data on your local storage which helps you reduce the risk of data loss if the device is damaged during shipping. It will also ensure that the backup data is available for restore operations while AWS Snowball Edge storage is in shipment.
* For information on FIPS status of AWS Snowball Edge storage, see Amazon official updates.
* You can add only one AWS Snowball Edge storage to a scale-out backup repository.
* Veeam Backup & Replication does not support Versioning and Object Lock for S3 buckets associated with AWS Snowball Edge storage.
* Veeam Cloud Connect service providers can use AWS Snowball Edge only as a capacity extent of a scale-out backup repository.

* You cannot back up data using Veeam Agent backup job or policy to AWS Snowball Edge devices.


