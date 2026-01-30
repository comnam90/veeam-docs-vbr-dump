---
title: "Viewing Offload Session Results"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/capacity_tier_offload_results.html"
last_updated: "8/2/2024"
product_version: "13.0.1.1071"
---

# Viewing Offload Session Results


To review offload session results, do the following:

1. Open the History view.
2. In the [inventory pane](vbr_ui.md), select the Storage management node.
3. In the working area, right-click an offload session and select Statistics.

For more information, see [Moving Backups to Capacity Tier](capacity_tier_move.md).

[![Viewing Offload Session Results](images/offload_statistics.webp)](images/offload_statistics.webp)

Veeam Backup & Replication displays offload job session statistics for the following counters:

* The Job progress bar shows percentage of the offload session completion.
* The Summary box shows general information about the offload session:

+ Duration — duration of the offload session.
+ Processing rate — average speed of VM data processing. This counter is a ratio between the amount of data that has actually been read and the offload session duration.
+ Bottleneck — bottleneck in the data transmission process. To learn more about bottlenecks, see [Performance Bottlenecks](detecting_bottlenecks.md).

* The Data box shows information about processed data:

+ Processed — total size of all VM disks processed by the offload session.
+ Read — the amount of data read from from the performance tier to the capacity tier.
+ Transferred — the amount of data transferred from performance tier to capacity tier.

* The Status box shows information about the job results. This box informs how many tasks have completed with the Success, Warning and Error statuses (1 task per 1 VM).
* The pane in the lower-left corner shows a list of objects processed by the offload session.
* The pane in the lower-right corner shows a list of operations performed during the session. To see a list of operations for a specific object, click the object in the pane on the left. To see a list of operations for the whole offload session, click anywhere on the blank area in the left pane.

Related Topics

* [Viewing Copy Session Results](capacity_tier_copy_results.md)
* [Viewing Download Session Results](capacity_tier_download_results.md)


