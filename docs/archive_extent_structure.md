---
title: "Archive Extent Structure"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/archive_extent_structure.html"
last_updated: "2/28/2024"
product_version: "13.0.1.1071"
---

# Archive Extent Structure


When data is transferred to the archive extent, Veeam Backup & Replication creates and maintains the following structure of directories:

![Archive Extent Structure](images/archive_extent_structure.webp)

| Directory | Description | Misc |
| --- | --- | --- |
| <bucket\_name> or <container\_name> | A bucket or container name.  Buckets and containers must be created in advance. | N/A |
| Veeam/LongTerm/ | Standard folders created by Veeam Backup & Replication. |
| <repository\_folder\_name> | A repository folder that you create when adding a new archive extent. |
| <backup\_id> | Contains objects in a backup. | These folders are automatically removed during data removal. |
| <objects\_in\_backup\_id> | An identifier of an object in a backup. |
| IndexDescr | Contains size of a backup. |
| BlobStore | Contains data blobs created by the archiving session, as described in section [Archive Tier Data Transfer](archive_data_transfer.md). |
| Checkpoints | Contains meta information about the state of archived backup chains. Such meta information is updated upon each successful archiving session. |
| Objects | Contains meta information and other auxiliary data. |  |
| Storages | Contains a replicated version of archived backup files with metadata. |  |


