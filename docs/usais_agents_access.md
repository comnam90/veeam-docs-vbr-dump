---
title: "Step 5. Specify Veeam Agent Access Options"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/usais_agents_access.html"
last_updated: "8/4/2023"
product_version: "13.0.1.1071"
---

# Step 5. Specify Veeam Agent Access Options

In this article

[This step is available if you have selected the Block storage for Microsoft Windows servers check box at the [Specify Storage Name or Address and Storage Role](usais_add_name.md) step of the wizard.]

At the Server Storage step of the wizard, specify options for accessing the storage system.

1. In the Protocol to use section, select check boxes next to protocols over which you want to work with the storage system.
2. If you plan to work with specific storage volumes, you can limit the storage rescan scope. In this case, Veeam Backup & Replication will rescan only the volumes that you select. Limiting the rescan scope reduces the amount of time required for the rescan operation.

To select volumes to rescan, click Choose to the right of the Volumes to scan field. In the Edit Volumes window, select volumes you want to rescan:

* To exclude volumes from rescan, select All volumes except and click Add. Click From infrastructure to select volumes from your storage infrastructure, or By wildcard to select volumes using a wildcard character.
* To rescan only specific volumes, select Only the following volumes and click Add. Click From infrastructure to select volumes from your storage infrastructure, or By wildcard to select volumes using a wildcard character.
* If you leave All existing volumes check box selected, Veeam Backup & Replication will rescan all volumes in the storage hierarchy.

After you finish working with the wizard, you can change the rescan scope and start the rescan process manually at any time. For more information, see [Rescanning Storage Systems](storage_rescan.md).

|  |
| --- |
| Important |
| [For VMware integration] If you plan to use [backup from storage snapshots](backup_from_storage_snapshots.md), you need to make sure that you include in the rescan scope the volumes on which the protected machine disks reside. |

1. To rescan storage systems and perform backup from storage snapshots, you need to configure a proxy. On the right of the Backup proxies to use field, click Choose and define proxies that you want to use for these operations.

+ Select Automatic selection to let Veeam Backup & Replication pick a proxy automatically. Veeam Backup & Replication will check which proxies have access to the storage system, and automatically assign an optimal proxy for rescan and backup from storage snapshots.
+ Select Use the selected backup proxy servers only to explicitly select a proxy that must be used for rescan and backup from storage snapshots. It is recommended that you select at least two proxies to ensure that rescan and backup from storage snapshot are performed if one of proxies fails or loses its connectivity to the storage system.

|  |
| --- |
| Note |
| [For VMware integration] If you select proxies explicitly, you must make sure that you also select these proxies in settings of backup and replication jobs for which you plan to use backup from storage snapshots. If a proxy selected for the job is not added to the list of proxies in the storage system connection settings and the Failover to standard backup option is disabled in the job settings, the job will fail. |

![Step 6. Specify Agents Access Options](images/inf_add_agents.webp)

Page updated 8/4/2023

Page content applies to build 13.0.1.1071
