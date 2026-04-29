---
title: "NAS Integration (Storage Systems)"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/nas_integration.html"
last_updated: "4/28/2026"
product_version: "13.0.1.2067"
---

# NAS Integration (Storage Systems)


Veeam Backup & Replication allows you to integrate your storage systems with NAS file shares residing on them into your infrastructure. For more information, see the [Adding Enterprise Storage System as NAS Filer](adding_nas_filer.md) section in the Veeam Backup & Replication User Guide.

To start working with storage systems, you must properly configure the backup infrastructure. For more information, see [Infrastructure Overview](storage_infrastructure.md). After that, you can use storage snapshots for data protection and disaster recovery operations.

|  |
| --- |
| Note |
| If only Veeam Agents or NAS backup processing is selected for a storage system, volumes with snapshots are not displayed under the Backups > Snapshots node. The storage system itself is still displayed in the Storage Infrastructure view, but no objects appear under the device. To manage NAS file shares backed up through this device, go to Inventory > File Shares. |

Supported Storage Systems

For the list of storage systems that support NAS integration, see [System Requirements](storage_system_requirements.md#nas).

Related Topics

* [Adding Enterprise Storage System as NAS Filer](adding_nas_filer.md)
* [Infrastructure Overview](storage_infrastructure.md)
* [NAS File Share Backup from Storage Snapshots](nas_backup_from_storage_snapshots.md)
* [Rescanning Storage Systems](storage_rescan.md)


