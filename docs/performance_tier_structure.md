---
title: "Extent Structure of Performance Tier with Object Storage Repositories"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/performance_tier_structure.html"
last_updated: "4/29/2025"
product_version: "13.0.1.1071"
---

# Extent Structure of Performance Tier with Object Storage Repositories


If your performance tier consists of object storage repositories, Veeam Backup & Replication creates and maintains the following structure of directories after backups are moved to the performance tier extents.

![Extent Structure of Performance Tier with Object Storage Repositories ](images/object_storage_structure.webp)

| Directory | Description |
| --- | --- |
| Veeam/Backup/ | Standard folders created by Veeam Backup & Replication. |
| Repository\_folder\_name | Contains information on the repository name and the repository ID. |
| Clients | Contains backups. |
| Client catalogue | Contains information on solutions that create backups to this repository. |
| Backup catalogue | Contains backup ID. |
| CloudStg | Contains data blocks. |
| MetaData | Contains metadata. |
| Config | Contains information on the object storage repository infrastructure. |
| Owner | Contains information on a repository owner. |
| Repository | Contains information on a repository. |


