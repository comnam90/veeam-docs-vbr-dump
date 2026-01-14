---
title: "How Downloading from Capacity Tier Works"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/capacity_tier_download.html"
last_updated: "8/2/2024"
product_version: "13.0.1.1071"
---

# How Downloading from Capacity Tier Works

In this article

To download data from the capacity extent back to the performance extents, Veeam Backup & Replication uses the SOBR Download job.

The SOBR Download job is triggered right after you select the Copy to performance tier option; it collects offloaded blocks of data from capacity extents and copies them back to the performance extents. For more information, see [Downloading Data from Capacity Tier](downloading_from_capacity_tier.md).

Consider the following:

* Veeam Backup & Replication copies all data blocks directly from object storage repositories added as extents to capacity tier.
* If a performance extent is unable to accommodate copied data due to lack of free storage space, Veeam Backup & Replication will find another extent in the associated scale-out backup repository that has sufficient storage capacity to receive the data. If your scale-out backup repository has no performance extents other than the one running out of space, the copy will not be possible.

* If you have removed any of the performance extents from a scale-out backup repository without evacuating backup files with metadata, the copy will not be possible until the files with metadata are downloaded back to the performance extents in the course of the rescan process. For more information on the rescan process, see [Rescanning Scale-Out Repositories](sobr_rescan.md).

Backup files with metadata are created as described in section [Moving Backups to Capacity Tier](capacity_tier_move.md).

* The SOBR download session results are saved to the configuration database and available for viewing, as described in section [Viewing Download Session Results](capacity_tier_download_results.md).

Related Topics

* [Downloading Data from Capacity Tier](downloading_from_capacity_tier.md)
* [Evacuating Backups from Extents](sobr_evacuate.md)
* [Copying Backups to Capacity Tier](capacity_tier_copy.md)
* [Moving Backups to Capacity Tier](capacity_tier_move.md)

Page updated 8/2/2024

Page content applies to build 13.0.1.1071
