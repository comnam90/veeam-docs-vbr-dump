---
title: "WORM Tapes"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/worm_tapes.html"
last_updated: "6/21/2023"
product_version: "13.0.1.1071"
---

# WORM Tapes

In this article

Veeam Backup & Replication supports WORM (Write Once Read Many) tapes for archiving backups to tape.

WORM Media Pools

As the WORM tapes cannot be overwritten, you need to treat them differently when using with Veeam Backup & Replication. These tapes cannot have retention period, and for this reason you cannot place them to the same media pool with the overwritable tapes.

For WORM tapes, you need to create separate media pools. In these media pools, only WORM tapes are used and they are not mixed with other tapes. The following media pools support the WORM media:

* WORM media pools
* WORM GFS media pools

In WORM media pools, retention settings are disabled. For more information, see [Media Pools](custom_media_pools.md) and [GFS Media Pools](gfs_media_pools.md).

You can append new data to the same WORM tape cartridge until it is full as long as the media set containing this media is open. For more information about cases when Veeam Backup & Replication closes the current media set and starts a new one, see [Media Sets](tape_media_sets.md).

Identifying WORM Tapes

Veeam Backup & Replication identifies WORM tapes and marks them as WORM in the Veeam database. WORM tapes are never mixed with standard tapes.

To identify WORM and standard tapes, run the inventory job against them. For more information, see [Inventorying Tapes](inventoring_tapes.md).

Requirements for WORM Tapes

Tape libraries must support reading/writing data on WORM tape cartridge memory chip.

Page updated 6/21/2023

Page content applies to build 13.0.1.1071
