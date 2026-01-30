---
title: "Transferring Backups to Performance Tier"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/data_transfer_to_performance_tier.html"
last_updated: "2/23/2024"
product_version: "13.0.1.1071"
---

# Transferring Backups to Performance Tier


Prior to Veeam Backup & Replication version 12, it was possible to keep data only on object storage repositories added as capacity extents of scale-out backup repository. Starting from Veeam Backup & Replication version 12, it is possible to add an object storage repository as a performance extent and back up data directly to this extent.

In case you have an object storage repository that is added as a capacity extent and want to use it as a performance extent, you can transfer existing backup from the capacity extent to the performance extent.

To do this, you must perform the followings steps:

1. Add a new object storage repository to the backup infrastructure.
2. Download a necessary backup chain to the existing backup repository added as a performance extent. For more information, see [Downloading Data from Capacity Tier](downloading_from_capacity_tier.md#download_single_chain).
3. Move backups from the backup repository to a new object storage repository. For more information, see [Moving Backups](move_backup.md).
4. Add the object storage as a performance extent to a new scale-out backup repository.


