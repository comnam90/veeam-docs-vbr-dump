---
title: "Immutability for Scale-Out Backup Repositories"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/immutability_sobr.html"
last_updated: "1/7/2025"
product_version: "13.0.1.1071"
---

# Immutability for Scale-Out Backup Repositories

In this article

Veeam Backup & Replication allows you to prohibit deletion of data from object storage repositories added as the extents of the scale-out backup repository by making that data temporarily immutable. It is done for increased security: immutability protects your data against loss as a result of attacks, malware activity or other injurious actions.

You can enable the immutability feature for any tier of scale-out backup repository.

To learn how immutability works with the performance tier of the scale-out backup repository, see [Immutability for Performance Tier](immutability_performance_tier.md).

To learn how immutability works with the capacity tier of the scale-out backup repository, see [Immutability for Capacity Tier](immutability_capacity_tier.md).

To learn how immutability works with the archive tier of the scale-out backup repository, see [Immutability for Archive Tier](immutability_archive_tier.md).

|  |
| --- |
| Note |
| Before you use an object storage repository as an immutable extent, you must configure immutability for this object storage beforehand. For more information, see [Enabling immutability for object storage repositories](immutability_os_enable.md). |

Related Topics

* [Immutability for Capacity Tier](immutability_capacity_tier.md)
* [Block Generation](block_gen.md)
* [Immutability for Archive Tier](immutability_archive_tier.md)
* [Considerations and Limitations](object_storage_repository_cal.md#cal_immutability)
* [Hardened Repository](hardened_repository.md)

In This Section

[GFS Backups Immutability Period](gfs_immutability_sobr.md)

Page updated 1/7/2025

Page content applies to build 13.0.1.1071
