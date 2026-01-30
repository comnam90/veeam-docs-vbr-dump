---
title: "GFS Media Pools"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/gfs_media_pools.html"
last_updated: "5/20/2025"
product_version: "13.0.1.1071"
---

# GFS Media Pools


The GFS media pools are special media pools that store data to tape according to the GFS, or Grandfather-Father-Son rotation scheme. The GFS media pools are targets for GFS tape jobs. For more information, see [GFS Backup to Tape](gfs_jobs.md).

Tapes for GFS Media Pools

For writing data, you can use rewritable tapes or WORM (Write Once Read Many) tapes. For more information, see [WORM Tapes](worm_tapes.md). For using WORM tapes, you need to create separate media pools. The following types of media pools are available:

* GFS media pools.
* WORM GFS media pools.

For more information on creating WORM media pools, see [Creating GFS Media Pools](creating_gfs_media_pools.md).

GFS Media Sets

GFS media pool keeps five predefined media sets for storing the machine backups with a tiered retention policy scheme:

* Daily
* Weekly
* Monthly
* Quarterly
* Yearly

You can disable a media set or sets if you do not need them.

GFS Tape Jobs

A GFS media pool can be target for unlimited number of GFS tape jobs.

Related Topics

* [Creating GFS Media Pools](creating_gfs_media_pools.md)
* [Moving Tapes to Another Media Pool](moving_tapes_to_custom_pool.md)
* [Modifying Media Pools](modifying_media_pools.md)
* [Removing Media Pools](deleting_media_pools.md)


