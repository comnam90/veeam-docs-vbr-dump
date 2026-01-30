---
title: "General-Purpose Backup Proxies"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/backup_proxy_general.html"
last_updated: "8/26/2025"
product_version: "13.0.1.1071"
---

# General-Purpose Backup Proxies


A general-purpose backup proxy is a component that operates as a data mover. The backup proxy processes jobs and delivers backup and restore traffic.

Usage Scenarios

General-purpose backup proxies can be used for the following operations:

* [Unstructured Data Backup](unstructured_data_backup.md). In this case, proxies transfer data between an unstructured data source and a backup repository.
* [Veeam Agent and storage system snapshot integration](agents_storage_systems.md). In this case, proxies transfer data between a storage system and a backup repository.

For more information on the backup infrastructure components required for different features, see feature descriptions.

General-Purpose Backup Proxy Deployment

By default, the role of the general-purpose backup proxy is assigned to the backup server itself. However, this option is sufficient only for small installations where all components are located in the same network segment. For larger installations with larger workload, assign the role of a backup proxy to a dedicated server, as described in the [Adding General-Purpose Backup Proxies](file_share_backup_add_file_proxy.md) section.

To optimize performance of several concurrent tasks, you can use several backup proxies. In this case, Veeam Backup & Replication will distribute the backup or restore workload between available backup proxies on per-task basis, taking into account proxy connectivity and their current load.

To minimize the network load during backup, locate the backup proxy closer to the source file share or storage in the computer network: at the best they should be one hop away from each other.

Backup Proxy Services and Components

General-purpose backup proxies run light-weight services that take a few seconds to deploy. Deployment is fully automated. Veeam Backup & Replication installs the following components and services:

* Veeam Backup VSS Integration is a service that manages Microsoft VSS snapshots. Used for file backup.
* Veeam VSS Hardware Snapshot Provider is a service that extends Microsoft VSS and enables backups from storage snapshots. Used for Veeam Agents.
* Veeam Installer Service is an auxiliary service that is installed and started on any Windows server once it is added to the list of managed servers in the Veeam Backup & Replication console. This service analyzes the system, installs and upgrades necessary components and services depending on the role selected for the server.

Requirements for General-Purpose Backup Proxy

Before you add a backup proxy to the inventory of the virtual infrastructure, check the following requirements and limitations:

* The backup proxy must meet the system requirements. For more information, see [System Requirements](system_requirements.md#file_proxy).
* The role of a backup proxy for unstructured data backup and file to tape backup can be assigned to a Microsoft Windows or Linux server.
* For Veeam Agent backup from storage system snapshots, the role of a backup proxy must be assigned to a Microsoft Windows server. For more information on the limitations, see the [Storage Snapshots Support](agents_storage_systems.md) section in  Veeam Agent Backup.


