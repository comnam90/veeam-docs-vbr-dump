---
title: "WAN Accelerator Sizing"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/wan_accelerator_sizing.html"
last_updated: "5/29/2024"
product_version: "13.0.1.1071"
---

# WAN Accelerator Sizing

In this article

To ensure correct work of remote jobs over WAN accelerators, you must provide enough free space for service data on source and target WAN accelerators.

When configuring WAN accelerators, note that there can be situations when WAN acceleration switches from the High bandwidth mode to the Low bandwidth mode: for example, the link to the remote location changes and you decide to disable the High bandwidth mode for one of the accelerators in the pair. If you disable the High bandwidth mode and start a job which utilizes this WAN accelerator, Veeam Backup & Replication deletes digest data that was used in the High bandwidth mode and recreates it for the Low bandwidth mode. Besides, Veeam Backup & Replication will also use the global cache at the target WAN accelerator.

To avoid problems caused by the lack of free space when switching from the High bandwidth mode to the Low bandwidth mode, we recommend that you configure WAN accelerators as if you planned to use them in the Low bandwidth mode.

Source WAN Accelerator

When you run a remote job over WAN accelerators, Veeam Backup & Replication analyses data blocks going to target and calculates digests for these data blocks. Digests data is stored on the source WAN accelerator, in the VeeamWAN folder on the disk that you select when you configure the WAN accelerator.

![WAN Accelerator Sizing](images/add_wan_accelerator_cache.webp)

You must make sure that there is enough disk space on the source WAN accelerator to store digest data.

The amount of disk space required for a source WAN accelerator operating in the Low bandwidth mode is calculated by the following formula:

|  |
| --- |
| Digest Size = 2% of Provisioned VM Size |

For example, if you plan to process 10 VMs whose provisioned size is 2 TB, you must allocate 40 GB of disk space for digest data on the source WAN accelerator operating in the Low bandwidth mode.

The amount of disk space required for a source WAN accelerator operating in the High bandwidth mode is calculated by the following formula:

|  |
| --- |
| Digest Size = 1% of Provisioned VM Size |

For example, if you plan to process 10 VMs whose provisioned size is 2 TB, you must allocate 20 GB of disk space for digest data on the source WAN accelerator operating in the High bandwidth mode.

You can increase the throughput by adjusting the number of upload streams. To learn how to configure them on the source WAN accelerator, see the [Choose Server](wan_server.md) step of the New WAN Accelerator wizard.

Target WAN Accelerator

You must make sure that you provide enough free space for the following data on the target WAN accelerator:

* [Global cache data](wan_accelerator_sizing.md#global_cache)
* [Digest data](wan_accelerator_sizing.md#digest)

|  |
| --- |
| Note |
| For the target WAN accelerator operating in the High bandwidth mode only, you must provide enough free space to generate [digest data](wan_accelerator_sizing.md#digest). Global cache data is not used in the High bandwidth mode.  When you enable the High bandwidth mode for an existing WAN accelerator, Veeam Backup & Replication does not automatically remove the global cache that was previously used for acceleration. If you are planning to use the High bandwidth mode for WAN acceleration and you do not need the global cache anymore, you can free the disk space by [manually removing the cache](wan_clear_cache.md). If you are planning to use WAN acceleration in the Low bandwidth mode in the future, we recommend that you keep the global cache. You can disable the High bandwidth mode and switch back to the Low bandwidth mode at any time. |

Global Cache Data

Global cache is stored on the target WAN accelerator, in the VeeamWAN folder on the disk that you select when you configure the WAN accelerator. The size of global cache is specified in the properties of the target WAN accelerator.

![WAN Accelerator Sizing](images/add_wan_accelerator_cache.webp)

You must provide enough free space for global cache data. It is recommended that you provide 10 GB per every type of OS on VMs that you plan to process. By default, Veeam Backup & Replication allocates 100 GB for the global cache size.

For example, you want to process the following VMs:

* 1 VM that runs Microsoft Windows 7
* 3 VMs that run Microsoft Windows Server 2008 R2
* 2 VMs that run Microsoft Windows Server 2012 R2

There are 3 types of OSes so you must allocate 30 GB for the global cache on the target WAN accelerator.

|  |
| --- |
| Note |
| Global cache is stored only on the target WAN accelerator. You do not have to provide space for global cache on the source WAN accelerator. |

Digest Data

In some cases, Veeam Backup & Replication may require more space on the target WAN accelerator than specified in the WAN accelerator properties. This can happen if digest data on the source WAN accelerator is missing or cannot be used. For example:

* You have performed the Clear Cache operation on the source WAN accelerator and it no longer contains digest data. For more information, see [Clearing Global Cache](wan_clear_cache.md).
* Veeam Backup & Replication has attempted to resume operation of backup data transfer, but the backup file was not prepared for the operation in a proper way. The digest data must be recalculated.

In such situations, the target WAN accelerator calculates digest data on its own, which requires additional space. After the digest data is calculated, the target WAN accelerator transfers it to the source WAN accelerator. After the transfer, the copy of the digest data is removed from the target WAN accelerator.

For safety reasons, it is recommended that you provide the following amount of space for digest data on the target WAN accelerator:

The amount of disk space required for digest data at a target WAN accelerator operating in the Low bandwidth mode is calculated by the following formula:

|  |
| --- |
| Digest Size = 2% of Provisioned VM Size |

The amount of disk space required for digest data at a target WAN accelerator operating in the High bandwidth mode is calculated by the following formula:

|  |
| --- |
| Digest Size = 1% of Provisioned VM Size |

This amount of space is required for digest data recalculation. If you do not provide this amount of space and a situation where Veeam Backup & Replication needs to recalculate digest data occurs, the job to the remote location will work in the limited mode. Veeam Backup & Replication will not deduplicate data against the previous restore points copied to target. For more information, see [Global Data Deduplication](wan_acceleration_sources.md).

|  |
| --- |
| Important |
| When you specify the global cache size for a target WAN accelerator, you do not allocate any space for storing digest data. To let Veeam Backup & Replication recalculate digest data, you must make sure that necessary amount of free space is available on the target WAN accelerator (in addition to the space allocated for the global cache). |

For example:

* You have allocated 100 GB for global cache on the target WAN accelerator operating in the Low bandwidth mode.
* Provisioned size of VMs to be processed is 2 TB.

In this case, the needed amount of free disk space for the global cache on the target WAN accelerator is:

|  |
| --- |
| 100 GB + 40 GB = 140 GB |

Many-to-One WAN Acceleration Scenario

Global cache size is calculated per 1 source WAN accelerator working with the target WAN accelerator. If you plan to use several source WAN accelerators with 1 target WAN accelerator, you must increase the size of the global cache proportionally. The cache data for every source WAN accelerator will be stored in a dedicated subfolder in the global cache folder of the target WAN accelerator. The global cache size is calculated by the following formula:

|  |
| --- |
| Total Global Cache Size = (# of Source WAN Accelerators) \* (Size of Global Cache Configured in Target WAN Accelerator Properties)  Total Free Disk Space to Provide = Total Global Cache Size + Digest Size |

For example:

* You have 4 source WAN accelerators in the source side working with 1 target WAN accelerator in the disaster recovery (DR) site.
* The global cache size configured in properties of the target WAN accelerator is 100 GB.
* The size of VMs to be processed is 2 TB.

In this case, the needed amount of free disk space for the global cache and digests on the target WAN accelerator is:

|  |
| --- |
| 4\*100 GB + 40 GB = 440 GB |

|  |
| --- |
| Note |
| For more information and recommendations on WAN accelerator cache sizing, see [this Veeam KB article](https://www.veeam.com/kb1877). |

Page updated 5/29/2024

Page content applies to build 13.0.1.1071
