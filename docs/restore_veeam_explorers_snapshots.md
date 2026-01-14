---
title: "Application Item Restore from Storage Snapshots"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/restore_veeam_explorers_snapshots.html"
last_updated: "10/8/2025"
product_version: "13.0.1.1071"
---

# Application Item Restore from Storage Snapshots

In this article

Veeam Backup & Replication allows you to restore different application items from a storage snapshot.

Supported Applications

Veeam Backup & Replication integrates with Veeam Explorers to let you restore items from the following applications:

* Microsoft Active Directory
* Microsoft Exchange
* Microsoft SharePoint
* Microsoft SQL Server
* Oracle
* PostgreSQL

When you perform application item restore, Veeam Backup & Replication automatically extracts the application databases from a storage snapshot and opens them in Veeam Explorer.

How Restore Works

As part of this procedure, Veeam Backup & Replication performs the following actions:

1. Veeam Backup & Replication creates a clone/virtual copy of a storage snapshot and mounts the clone/virtual copy to an ESXi host.
2. Veeam Backup & Replication accesses the configuration file of the virtualized application server (VMX) on the snapshot clone/virtual copy and uses this configuration file to register a temporary VM on the ESXi host.
3. Veeam Backup & Replication mounts disks of the application server to the temporary VM.
4. Veeam Backup & Replication locates the application databases and opens them in Veeam Explorer.

Requirements for Application Item Restore

Before you perform backup from storage snapshots, check requirements specific for data recovery in [Data Recovery from Storage Snapshots Requirements and Limitations](storage_limitations_general.md#boss).

Performing Application Item Restore

For information on performing application item restore, see the [Launching Veeam Explorer](restoring_veeam_explorers.md) section in the Veeam Backup & Replication User Guide.

Page updated 10/8/2025

Page content applies to build 13.0.1.1071
