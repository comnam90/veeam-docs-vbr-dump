---
title: "WAN Global Cache"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/wan_global_cache.html"
last_updated: "7/18/2024"
product_version: "13.0.1.1071"
---

# WAN Global Cache


From the technical point of view, the global cache is a folder on the target WAN accelerator. By default, global cache data is stored in the VeeamWAN folder on the disk with the most amount of space available. However, you can define any folder of your choice when you configure the target WAN accelerator.

|  |
| --- |
| Note |
| Global cache is not used if both WAN accelerators in the pair (the source one and the target one) operate in the High bandwidth mode. |

By default, the size of the global cache is 100 GB. You can increase the size or decrease it if necessary. The more space you allocate, the more repeating data blocks will be written to the global cache and the more efficient WAN acceleration will be. It is recommended that you allocate at least 40 GB to the global cache storage.

The global cache size is specified per source WAN accelerator. That is, if you plan to use one target WAN accelerator with several source WAN accelerators, the specified amount of space will be allocated for every source WAN accelerator that will be working with the target WAN accelerator and the size of the global cache will increase proportionally. For more information, see [WAN Accelerator Sizing](wan_accelerator_sizing.md).

The WAN global cache is a “library” that holds data blocks repeatedly going from the source side to the target side. The global cache is populated at the first cycle of a job to the remote location. The priority is given to data blocks of Windows-based OSes, other OSes like Linux/Unix, and Microsoft Exchange Server.

Veeam Backup & Replication constantly maintains the global cache in the actual state. To do that, it continuously monitors data blocks going over WAN and data blocks in the global cache.

* If some new data block is constantly sent over WAN, it is added to the global cache.
* If some data block in the global cache is not sent over WAN and are not re-used for some period of time, it is removed from the global cache to make room for new data blocks.

Veeam Backup & Replication also performs periodic consistency checks. If some data block in the global cache gets corrupted, Veeam Backup & Replication removes it from the global cache.

The efficiency of the WAN acceleration increases with every new backup copy interval in the backup copy job. During the first backup copy interval in the backup copy job, the WAN acceleration level is minimal. Veeam Backup & Replication populates the global cache. With every new job cycle, Veeam Backup & Replication updates the global cache to include the most “popular” data blocks and the WAN acceleration efficiency increases.

|  |
| --- |
| Note |
| You can populate the global cache before you run the job to the remote location for the first time. In this case, Veeam Backup & Replication will use the global cache starting from the first session of the job to the remote location, and the WAN traffic will be minimal. For more information, see [Manual Population of Global Cache](wan_population.md). |

Related Topics

* [Many to One WAN Acceleration](wan_acceleration_many.md)
* [Manual Population of Global Cache](wan_population.md)


