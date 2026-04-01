---
title: "Storage Integration Access"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/sia_transport.html"
last_updated: "3/23/2026"
product_version: "13.0.1.2067"
---

# Storage Integration Access


The Storage integration access transport mode is recommended for VMs whose disks are located on storage systems that are connected to ESXi hosts over any supported protocol. For more information on the protocols, see [Storage Systems System Requirements](system_requirements_storage_systems.md).

In the Storage integration access transport mode, Veeam Backup & Replication bypasses the ESXi host and reads data directly from or writes data directly to storage systems.

The Storage integration access transport mode can be used for the following features:

* [Backup from Storage Snapshots](backup_from_storage_snapshots.md)
* [Backup from Storage Snapshots with Snapshot Retention](snapshot_job_secondary.md)

Requirements and Limitations for the Storage Integration Access Mode

To use the Storage integration access transport mode, consider the following:

* Make sure that [general requirements for the VMware backup proxy](backup_proxy_requirements.md) plus [proxy requirements for the storage system snapshot integration](storage_configure_proxy.md) are met.
* For the correct configuration of the storage system integration feature, check [Storage System Snapshot Integration](storage_integration.md).


