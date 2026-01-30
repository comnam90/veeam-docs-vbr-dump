---
title: "HPE StoreOnce Supported Features"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/storeonce_supported_features.html"
last_updated: "11/13/2025"
product_version: "13.0.1.1071"
---

# HPE StoreOnce Supported Features


The HPE StoreOnce Catalyst technology offers a set of features for advanced data processing. Veeam Backup & Replication supports the following features.

Synthetic Full Backups

HPE StoreOnce Catalyst improves synthetic full backup file creation and transformation performance. When Veeam Backup & Replication creates or transforms a synthetic full backup, HPE StoreOnce does not physically copy data between the existing backup chain and the target full backup file. Instead, it performs a metadata-only operation — updates pointers to existing data blocks on the storage device. As a result, the operation completes much faster. This mechanism helps improve performance of primary backup jobs and backup copy jobs that are scheduled to create periodic archive full backups (GFS).

Accelerated vPower-Enabled Operations

[For VMware vSphere environments] If HPE StoreOnce Catalyst is integrated with Veeam Backup & Replication, it helps to benefit from improved performance of vPower-enabled operations — Instant Recovery, SureBackup and On-Demand Sandbox — from backups residing on HPE StoreOnce. To get the maximum vPower performance, HPE StoreOnce must be running firmware version 3.15.1 or later.

Accelerated Data Recovery

Integration with HPE StoreOnce improves data recovery performance for different restore scenarios: Instant Recovery, file-level recovery and application items recovery with Veeam Explorers.

WAN-based Catalyst Store Support

Veeam Backup & Replication provides advanced support for WAN-based HPE Catalyst stores. If a WAN connection to HPE StoreOnce is weak, you can instruct Veeam Backup & Replication to compress VM data and calculate checksums for data blocks going from the source side to HPE StoreOnce.

HPE StoreOnce Replication

HPE StoreOnce replication improves copying data between two HPE StoreOnce backup repositories. For more information on copying, see [Creating Backup Copy Jobs for HPE StoreOnce Repositories](backup_copy_hpe_storeonce.md).

Independent Software Vendor (ISV) Controlled Data Immutability (ISV-DI)

Together with HPE StoreOnce Independent Software Vendor (ISV) Controlled Data Immutability (ISV-DI), Veeam Backup & Replication allows you to prohibit deletion of data from the HPE StoreOnce deduplicating storage appliances by making that data temporarily immutable. This is required for improved security: immutability protects your data from loss as a result of malware activity or unplanned actions.

You can enable the immutability feature and specify the immutable period when adding or editing the HPE StoreOnce backup repository. For more information, see [Configure Backup Repository Settings](dsa_repository_repository.md). Once imposed, immutability prohibits deletion of data from the deduplicating storage appliance until the immutability expiration date comes. Note that if you enable immutability and Veeam Backup & Replication does not start a new backup chain and still continues the chain, the whole backup chain is marked as immutable. Once you disable immutability, newly created backups are not marked as immutable.

In many respects, HPE StoreOnce with enabled immutability works similarly to the hardened repository. For more information on how repositories with immutability operate as a part of a scale-out backup repository, see [Hardened Repository as Performance Extent](hardened_repository_sobr.md#sobr). For more information on how retention periods set in jobs correlate with retention periods set in the deduplicating storage appliance, see [How Immutability Works](hardened_repository_immutability.md).

Fixed Block Chunking

Together with fixed block chunking, Veeam Backup & Replication improves performance when creating incremental and synthetic full backup files. Fixed block chunking improves performance up to 4-5 times compared to variable chunking,

Veeam Backup & Replication supports fixed block chunking functionality for HPE StoreOnce software version 4.3.2 or later. To be able to use this functionality in Veeam Backup & Replication, check that the [Align backup file data blocks](dsa_repository_repository.md) option is enabled in the repository settings.

Fixed block chunking is supported for the following types of backups:

* Backups of VMware vSphere virtual machines created by Veeam Backup & Replication
* Backups of Microsoft Hyper-V virtual machines created by Veeam Backup & Replication

* Backups of virtual and physical machines created by [Veeam Agent for Microsoft Windows, Veeam Agent for Linux, Veeam Agent for Oracle Solaris or Veeam Agent for IBM AIX](agents_introduction.md)

* Backups of Nutanix AHV virtual machines created by [Veeam Plug-In for Nutanix AHV](https://helpcenter.veeam.com/docs/vbahv/userguide/overview.html?ver=9)

* Backups of oVirt VMs created by [Veeam Backup for OLVM and RHV](https://helpcenter.veeam.com/docs/vbrhv/userguide/overview.html?ver=7)\*

* Backups of Proxmox VE VMs created by [Veeam Plug-In for Proxmox VE](https://helpcenter.veeam.com/docs/vbproxmoxve/userguide/overview.html?ver=3)
* Backups of Scale Computing HyperCore VMs created by [Veeam Plug-In for Scale Computing HyperCore](https://helpcenter.veeam.com/docs/vpsch/userguide/overview.html?ver=2)

\* - Available on Microsoft Windows-based backup server.

For more information on issue that can occur, see [this Veeam KB article](https://www.veeam.com/kb4364).

Cloud Bank Storage

Veeam Backup & Replication supports HPE Cloud Bank Storage for HPE StoreOnce software version 4.3.2 or later. HPE Cloud Bank Storage is an extension of HPE StoreOnce Catalyst that uses external object storage to store backup data. It is possible to use HPE Cloud Bank Storage as a target for [backup copy jobs for HPE StoreOnce repositories](backup_copy_hpe_storeonce.md). This helps to reduce long-term retention costs.

Veeam Backup & Replication can also use HPE Cloud Bank Storage located on HPE Alletra Storage MP X10000 as the target for backup jobs and backup copy jobs. The following list shows the supported platforms, products and operations:

* Backup and backup copy: [VMware vSphere](vmware_vsphere.md), [Microsoft Hyper-V](ms_hyperv.md).
* Experimental support for backup copy: [VMware Cloud Director](vcloud_director.md) , [Kasten](https://helpcenter.veeam.com/docs/vbr/kasten_integration/overview.html?ver=13), [MongoDB](mongo_backup.md), [Veeam Backup for OLVM and RHV](https://helpcenter.veeam.com/docs/vbrhv/userguide/overview.html?ver=7)\*, [Nutanix AHV](https://helpcenter.veeam.com/docs/vbahv/userguide/overview.html?ver=9), [Proxmox VE](https://helpcenter.veeam.com/docs/vbproxmoxve/userguide/overview.html?ver=3), [Veeam Agents](protect_comp.md).
* Experimental support for backup and backup copy: [Veeam Plug-Ins for Enterprise Applications](protect_applications.md) (except for MongoDB Backup).

\*This feature is available for Microsoft Windows-based backup servers.

Related Topics

* [HPE StoreOnce](deduplicating_appliance_storeonce.md)
* [Operational Modes](deduplicating_appliance_storeonce_modes.md)
* [Adding Deduplicating Storage Appliances](dsa_repository_add.md)


