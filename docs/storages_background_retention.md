---
title: "Background Retention"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/storages_background_retention.html"
last_updated: "10/13/2025"
product_version: "13.0.1.1071"
---

# Background Retention


In addition to applying a retention policy ([short-term retention policy](retention_policy.md) and [long-term retention policy](gfs_retention_policy.md)) to backups and snapshots within a job session, Veeam Backup & Replication performs background retention for backups and snapshots. The background retention aims mostly at backups and snapshots that are no longer processed by jobs (orphaned backups are shown under Orphaned node in the inventory pane; orphaned snapshots are shown in the Snapshots node). However, this retention can also be helpful for standard backups and snapshots, in case backups and snapshots are created by jobs without a schedule, the job retention has not been applied yet or failed for some reason, and so on.

To learn more, see [Background Retention](background_retention_job.md).


