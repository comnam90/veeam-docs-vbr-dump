---
title: "Built-In Storage Systems"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/storage_configure_add_storage.html"
last_updated: "10/17/2025"
product_version: "13.0.1.1071"
---

# Built-In Storage Systems

In this article

To use storage snapshots for data protection and disaster recovery operations, you must add the storage system to the backup infrastructure. Before adding a storage system to the backup infrastructure, check [Planning and Preparation](storage_limitations.md). If you plan to work with secondary storage arrays, you must add them to the backup infrastructure as well.

The topology of the storage system added to the backup infrastructure is displayed in the Storage Infrastructure view in the Veeam Backup & Replication console. On the Home view, in the Backups > Snapshots node, you can see volumes with storage snapshots and VMs stored on these volumes.

|  |
| --- |
| Note |
| If only Veeam Agents or NAS backup processing is selected for a storage system, volumes with snapshots are not displayed under the Backups > Snapshots node. The storage system itself is still displayed in the Storage Infrastructure view. |

Supported Storage Systems

The supported built-in storage systems are listed in section [System Requirements](storage_system_requirements.md).

|  |
| --- |
| Tip |
| For information on how to add Universal Storage API integrated systems, see [Universal Storage API Integrated Systems](universal_storage_integration_api.md). |

Supported Integration Types

You can add different storage systems to your infrastructure depending on the integration type you use. To learn which storage systems are supported for which integrations, see [System Requirements](storage_system_requirements.md).

In This Section

* [Adding Cisco HyperFlex](cisco_add.md)
* [Adding Dell PowerScale (formerly Isilon)](dell_powerscale_add.md)
* [Adding Dell Unity XT, Unity](adding_dell_unity_vnx.md)
* [Adding Fujitsu ETERNUS HX/AX](fujitsu_add.md)
* [Adding HPE HPE Alletra 5000, 6000, Nimble](nimble_add.md)
* [Adding HPE HPE Alletra Storage MP B10000, 9000, Primera, 3PAR](hp_3par_add.md)
* [Adding Lenovo ThinkSystem DM/DG Series](lenovo_add.md)
* [Adding NetApp ONTAP](netapp_add.md)
* [Adding Nutanix Files Storage](nutanix_add.md)

Page updated 10/17/2025

Page content applies to build 13.0.1.1071
