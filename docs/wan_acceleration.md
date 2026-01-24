---
title: "WAN Acceleration"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/wan_acceleration.html"
last_updated: "1/22/2026"
product_version: "13.0.1.1071"
---

# WAN Acceleration


WAN acceleration is a Veeam technology that optimizes data transfer to remote locations. It is specific for off-site backup copy jobs and replication jobs.

To enable WAN acceleration and data deduplication technologies, you must deploy a pair of WAN accelerators in your backup infrastructure. For more information, see [WAN Accelerators](wan_accelerator.md).

|  |
| --- |
| Note |
| The availability of the feature depends on the license you use. For more details about licensing support, see [Veeam Data Platform Feature Comparison](https://www.veeam.com/veeam_data_platform_feature_comparison_ds.pdf). |

Off-site backup copy and replication always involve moving large volumes of data between remote sites. The most common problems that backup administrators encounter during off-site backup and replication are insufficient network bandwidth to support VM data traffic and transmission of redundant data. To solve these problems, Veeam Backup & Replication offers the WAN acceleration technology that combines:

* Network traffic compression
* Multistreaming upload
* Global data deduplication
* Variable block size deduplication

These technologies help optimize the data transfer and reduce the amount of data going over WAN.

High Bandwidth Mode

We recommend using the High bandwidth mode for WAN connections faster than 100 Mbps. If compared with the Low bandwidth mode, it does not leverage the global cache, but utilizes a faster compression method, optimized digests processing and an alternative deduplication mechanism. As a result, the new mode provides better performance and higher speed of data transfer.

Note that to use the High bandwidth mode, you must enable this option for WAN accelerators at both sites of the data transfer: the source and the target. If the target WAN accelerator has the High bandwidth mode enabled, different source accelerators can parallelly interact with it in different modes, depending on the mode selected for each source WAN accelerator.

In This Section

* [How WAN Acceleration Works](wan_hiw.md)
* [Global Data Deduplication](wan_acceleration_sources.md)
* [Data Block Verification](wan_crc.md)
* [Data Transport on WAN Disconnect](resume_disconnect_wan.md)


