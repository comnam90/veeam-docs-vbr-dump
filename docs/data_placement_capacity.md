---
title: "Backup File Placement for Capacity Tier"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/data_placement_capacity.html"
last_updated: "2/28/2024"
product_version: "13.0.1.1071"
---

# Backup File Placement for Capacity Tier


Data distribution between capacity extents depends on whether it is the first or a subsequent move or copy of a backup chain. To select an extent for backup file placement, Veeam Backup & Replication checks the following conditions:

1. During the first job session, Veeam Backup & Replication checks availability of extents. In case, an extent is set to [Sealed](sobr_seal.md) or [Maintenance](sobr_maintenance.md) mode, these extents will be skipped from backup file placement.
2. After that, Veeam Backup & Replication checks the amount of backup chains in available extents and selects the extent with a minimal amount of backup chains.
3. If some extents have storage space limitations, Veeam Backup & Replication calculates the average storage of the backup chains located in all extents and select the extent that contains a minimum amount of backup chains. If all extents have the same number of backup chains, Veeam Backup & Replication selects the extent that has more free space.
4. During subsequent job sessions, Veeam Backup & Replication moves backup chains to the extent that was specified before.

|  |
| --- |
| Note |
| If an extent is set to Sealed mode or Maintenance mode, Veeam Backup & Replication will not move a backup chain to this extent. In this case, a new extent is selected and Veeam Backup & Replication follows the same algorithm as during the first job session. The backup chain located in an unavailable extent will be moved again to another extent. Veeam Backup & Replication will remove backup chains from the unavailable extents according to [retention policy](capacity_tier_retention.md). |


