---
title: "Hardened Repository as Performance Extent"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/hardened_repository_sobr.html"
last_updated: "8/1/2024"
product_version: "13.0.1.1071"
---

# Hardened Repository as Performance Extent

In this article

You can add a hardened repository to your scale-out backup repository as a performance extent. For more information, see [Scale-Out Backup Repository](backup_repository_sobr.md) and [Add Performance Extents](sobr_add_extents.md).

Immutability Limitations

* Mutable and immutable extents must not be mixed within one scale-out backup repository.
* If your scale-out backup repository includes hardened repositories and deduplicating storage appliances with enabled immutability (StoreOnce, Dell Data Domain), consider the following:

* The immutability time period must be the same on all extents added to this scale-out repository. If you want to change the immutability period on any extent, a new value will be applied to all extents.
* If you want to upgrade to the latest Veeam Backup & Replication version, before starting the operation, you must specify the same immutability period for all extents added to this scale-out repository.

Using Capacity Tiers and Hardened Repositories

If you use the capacity tier with move option, note that having a hardened repository as a performance extent will affect the capacity tier behavior. You will not be able to move immutable backup files, because they cannot be deleted from the performance extent. Veeam Backup & Replication will copy such backup files to the capacity tier. When the immutability time period is over, Veeam Backup & Replication will delete these files from the performance extent. For more information on copy and move policies, see [Copying Backups to Capacity Tier](capacity_tier_copy.md) and [Moving Backups to Capacity Tier](capacity_tier_move.md).

If a hardened repository is a part of a scale-out backup repository with the capacity tier added and the move policy enabled, Veeam Backup & Replication ignores the GFS retention policy. The immutability time period for full backup files equals the period specified in the setting of a hardened repository.

Evacuating Immutable Backups

If you evacuate your backups from an immutable performance extent, Veeam Backup & Replication will copy them instead of moving. When the immutability time period is over, you will need to delete these files manually. If the target extent is also immutable, the immutability of the target extent will apply to copied backup files. For more information on evacuating backups, see [Evacuating Backups from Extents](sobr_evacuate.md).

When you evacuate backups to the hardened Linux extent, the immutability period of the full chain will be chosen as maximum between the following values:

* The immutability period determined for the original chain.
* The time of creation of the last restore point in the chain plus the immutability period determined for the target extent.

Page updated 8/1/2024

Page content applies to build 13.0.1.1071
