---
title: "Step 4. Specify NAS Access Options"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/dell_powerscale_add_options.html"
last_updated: "8/10/2023"
product_version: "13.0.1.1071"
---

# Step 4. Specify NAS Access Options


At the NAS Filer step of the wizard, specify options for accessing the storage system:

1. In the Protocol to use section, select check boxes next to protocols over which you want to work with the storage system.
2. During storage rescan, backup and restore operations, Veeam Backup & Replication automatically creates required NFS export rules on the storage system. If you do not want Veeam Backup & Replication to create export rules, clear the Create required export rules automatically check box.
3. If you plan to work with specific storage volumes, you can limit the storage rescan scope. In this case, Veeam Backup & Replication will rescan only the volumes that you select. Limiting the rescan scope reduces the amount of time required for the rescan operation.

To select volumes to rescan, click Choose to the right of the Volumes to scan field. In the Edit Volumes window, select volumes you want to rescan:

1. To exclude volumes from rescan, select All volumes except and click Add. Click From infrastructure to select volumes from your storage infrastructure, or By wildcard to select volumes using a wildcard character.
2. To rescan only specific volumes, select Only the following volumes and click Add. Click From infrastructure to select volumes from your storage infrastructure, or By wildcard to select volumes using a wildcard character.
3. If you leave All existing volumes check box selected, Veeam Backup & Replication will rescan all volumes in the storage hierarchy.

After you finish working with the wizard, you can change the rescan scope and start the rescan process manually at any time. For more information, see [Rescanning Storage Systems](storage_rescan.md).

1. To rescan storage systems and perform [backup from storage snapshots](backup_from_storage_snapshots.md), you must configure a proxy. On the right of the Backup proxies to use field, click Choose and define proxies.

+ Select Automatic selection to let Veeam Backup & Replication pick a proxy automatically. Veeam Backup & Replication will check which proxies have access to the storage system, and automatically assign an optimal proxy for rescan and backup from storage snapshots.
+ Select Use the selected backup proxy servers only to explicitly select a proxy that must be used for rescan and backup from storage snapshots. It is recommended that you select at least two proxies to ensure that rescan and backup from storage snapshot are performed if one of proxies fails or loses connection with the storage system.

![Step 4. Specify NAS Access Options](images/emc_isilon_add_options.webp)


