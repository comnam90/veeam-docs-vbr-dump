---
title: "Deleting Backups from Scale-Out Backup Repositories"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/deleting_backups_from_sobr_hv.html"
last_updated: "9/26/2025"
product_version: "13.0.1.1071"
---

# Deleting Backups from Scale-Out Backup Repositories

In this article

To delete a backup from a scale-out backup repository, do the following:

1. Open the Home view.
2. In the inventory pane, navigate to the Backups and select one of the following nodes:

* Select the Object Storage node if you want to delete a backup from the object storage repository added as a performance extent.

|  |
| --- |
| Important |
| Keep in mind that the Delete from disk operation will remove the backups not only from the performance tier but also from the capacity and archive tier. If you want to remove backups from the performance tier only, you should move those backups to the capacity tier instead. For details, see [Manually Moving Backups to Capacity Tier](moving_to_capacity_tier.md). |

* Select the Capacity Tier node if you want to delete a backup from the capacity tier.
* Select the Archive Tier node if you want to delete backups from the archive tier.

1. In the working area, select a backup or VM and click Delete from Disk on the ribbon. Alternatively, you can right-click a backup and select Delete from disk.

Related Topics

* [Capacity Tier](capacity_tier.md)
* [Object Storage Repositories](object_storage_repository.md)

Page updated 9/26/2025

Page content applies to build 13.0.1.1071
