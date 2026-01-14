---
title: "Storage System Snapshot Integration"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/storage_integration.html"
last_updated: "4/16/2025"
product_version: "13.0.1.1071"
---

# Storage System Snapshot Integration

In this article

Storage systems are designed to store and maintain data, and also protect data by means of snapshots. Veeam Backup & Replication allows using these snapshots to create backups which accelerates the backup process and minimizes the impact on the production site.

Integration Types

Veeam Backup & Replication provides the following types of snapshot integrations:

* [VMware integration](vmware_integration.md). Allows creating backups of VMware vSphere VMs and performing snapshot orchestration — build a snapshot chain on primary and secondary storage arrays. Also, Veeam Backup & Replication allows restoring data from storage snapshots.
* [NAS integration](nas_integration.md). Allows creating backups of NAS file shares.
* [Veeam Agent for Microsoft Windows integration](agent_integration.md). Allows creating Veeam Agent backups of Microsoft Windows computers.

|  |
| --- |
| Important |
| You cannot back up Hyper-V-based VMs with the help of the integration. |

After the backups are created from snapshots, you can perform different data recovery operations.

Configuring Infrastructure

Before you start working with storage systems in Veeam Backup & Replication, you must properly configure the backup infrastructure. For more information on configuring the backup infrastructure, see [Infrastructure Overview](storage_infrastructure.md).

Check the requirements for a specific storage system before you add this storage system to your backup infrastructure. For more information on storage requirements and limitations, see [Planning and Preparation](storage_limitations.md).

Related Topics

* [Infrastructure Overview](storage_infrastructure.md)
* [Planning and Preparation](storage_limitations.md)
* [Universal Storage API Integrated Systems](universal_storage_integration_api.md)
* [On-Demand Sandbox for Storage Snapshots](sandbox_storages_ebook.md)

Page updated 4/16/2025

Page content applies to build 13.0.1.1071
