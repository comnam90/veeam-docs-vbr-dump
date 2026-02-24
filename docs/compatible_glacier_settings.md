---
title: "Step 4. Specify Object Storage Settings"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/compatible_glacier_settings.html"
last_updated: "2/23/2026"
product_version: "13.0.1.1071"
---

# Step 4. Specify Object Storage Settings


At the Bucket step of the wizard, specify the bucket and folder where you will store data, and define storage limits and immutability settings that Veeam Backup & Replication will apply to data in the object storage.

1. In the Bucket field, enter a name of the bucket or click Browse to get the necessary bucket.

Note that you must create the bucket where you want to store your backup data beforehand.

1. In the Folder field, enter a cloud folder name to which you want to map your S3 compatible object storage with data archive. Alternatively, click Browse and either select an existing folder or click New Folder.
2. To prohibit deletion of blocks of data from object storage, select the Make backups immutable for the entire duration of their retention policy check box. The immutability period will be equal to the retention period (if any) of the data blocks. All the types of files that are eligible for archive storage can be made immutable. For more information on the immutability feature and the retention policy for each file type, see [Immutability for Archive Tier](immutability_archive_tier.md).

![Step 4. Specify Object Storage Settings](images/compatible_glacier_bucket.webp)


