---
title: "Rescanning Storage Systems"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/storage_rescan.html"
last_updated: "4/29/2025"
product_version: "13.0.1.1071"
---

# Rescanning Storage Systems


You can rescan a storage system added to the backup infrastructure. Storage system rescan gets and updates the information that is necessary for the backup, replication and restore processes. Storage system rescan may be required, for example, if you create or delete snapshots manually on the storage system, not using Veeam Backup & Replication. It also updates a storage system hierarchy in the Veeam Backup & Replication console. For more information about the storage system rescan process, see [Rescan (Storage Discovery) Process](storage_discovery_process.md).

Storage system rescan can be performed automatically or manually.

|  |
| --- |
| Note |
| Consider the following:   * Before you start a storage rescan, make sure that you have a properly configured proxy in the backup infrastructure. * Veeam Backup & Replication does not perform rescan on VMs whose disks are located on VVol datastores. |

Limiting Rescan Scope

Rescan of the whole storage system hierarchy can take much time. To minimize the rescan time, you can instruct Veeam Backup & Replication to rescan only specific volumes.

To limit the rescan scope, open the storage system connection settings and navigate to the VMware/NAS/Veeam Agent Access Options step of the wizard. Select the volumes you want to rescan.

For more information, see the Specify VMware/NAS/Veeam Agent Access Options step of the relevant Add Storage wizard.


