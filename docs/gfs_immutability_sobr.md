---
title: "GFS Backups Immutability Period"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/gfs_immutability_sobr.html"
last_updated: "1/8/2026"
product_version: "13.0.1.1071"
---

# GFS Backups Immutability Period

In this article

The immutability period for backups with GFS flags depends on multiple settings of a scale-out backup repository. The following table shows how the immutability period is counted depending on the scale-out backup repository configuration.

| Scale-Out backup Repository Settings | Performance Tier Immutable | Capacity Tier Immutable | Archive Tier Immutable |
| --- | --- | --- | --- |
| Performance Tier Only | The immutability period depends on the settings of an object storage repository:   * For the entire duration of their retention policy. In this case, the immutability period is the same as the GFS retention period + [Block Generation](object_storage_block_generation.md). * For the minimum immutability period only. In this case, the immutability period is the same as the immutability period of an object storage repository + [Block Generation](object_storage_block_generation.md). | — | — |
| Performance Tier + Capacity Tier with Copy Policy | The immutability period depends on the settings of an object storage repository:   * For the entire duration of their retention policy. In this case, the immutability period is the same as the GFS retention period + [Block Generation](object_storage_block_generation.md). * For the minimum immutability period only. In this case, the immutability period is the same as the immutability period of an object storage repository + [Block Generation](object_storage_block_generation.md). | The immutability period is the same as the immutability period of an object storage repository set as the capacity extent. | — |
| Performance Tier + Capacity Tier with Move Policy | The immutability period is the same as the immutability period of an object storage repository set as the performance extent. | The immutability period is the same as the immutability period of an object storage repository set as the capacity extent. | — |
| Performance Tier + Capacity Tier with Copy Policy + Archive Tier | The immutability period is the same as the immutability period of an object storage repository set as the performance extent. | The immutability period is the same as the immutability period of an object storage repository set as the capacity extent. | The immutability period is the same as the GFS retention period1. |
| Performance Tier + Capacity Tier with Move Policy + Archive Tier | The immutability period is the same as the immutability period of an object storage repository set as the performance extent. | The immutability period is the same as the immutability period of an object storage repository set as the capacity extent. | The immutability period is the same as the GFS retention period1. |
| Performance Tier + Archive Tier | The immutability period is the same as the immutability period of an object storage repository set as the performance extent. | — | The immutability period is the same as the GFS retention period1. |

1 Valid only in case the GFS retention period is longer than the immutability period for object storage repository.

Page updated 1/8/2026

Page content applies to build 13.0.1.1071
