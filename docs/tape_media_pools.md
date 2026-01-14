---
title: "Media Pools"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/tape_media_pools.html"
last_updated: "5/27/2024"
product_version: "13.0.1.1071"
---

# Media Pools

In this article

Media pools are logical containers created in Veeam Backup & Replication to organize and administer tapes.

Veeam Backup & Replication has the following types of media pools:

* [Service Media Pools](service_media_pools.md) are created automatically and are used for automatic tape administration.
* [Media Pools](custom_media_pools.md) are created by user and contain tapes for backups.
* [GFS Media Pools](gfs_media_pools.md) are created by user and contain tapes for GFS backups.

All Veeam media pools are global. They span tapes that belong to multiple libraries. In a global media pool, you can move tapes between the libraries without need to catalog them.

|  |
| --- |
| Note |
| Consider the hardware encryption. If the tapes are encrypted by native hardware means of a tape library, you cannot read them at tape device with another encryption standard or with hardware encryption turned off. |

Placing Tapes to Media Pools

Veeam Backup & Replication works only with tapes that are placed to a media pool. To introduce tapes to Veeam Backup & Replication, you need to run importing procedure against all new tapes you load to your tape devices. Importing registers tapes in the Veeam Backup database after which Veeam Backup & Replication places tapes to one of the media pools. For more information, see [Loading Tapes](import_tapes.md).

Related Topics

* [Media Sets](tape_media_sets.md)
* [Tape Parallel Processing](parallel_processing.md)
* [Backup Sets](tape_backup_sets.md)
* [Service Media Pools](service_media_pools.md)
* [Media Pools](custom_media_pools.md)
* [GFS Media Pools](gfs_media_pools.md)
* [Moving Tapes to Another Media Pool](moving_tapes_to_custom_pool.md)
* [Modifying Media Pools](modifying_media_pools.md)
* [Removing Media Pools](deleting_media_pools.md)

Page updated 5/27/2024

Page content applies to build 13.0.1.1071
