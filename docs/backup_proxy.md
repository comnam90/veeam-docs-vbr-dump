---
title: "VMware Backup Proxies"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/backup_proxy.html"
last_updated: "8/26/2025"
product_version: "13.0.1.1071"
---

# VMware Backup Proxies

In this article

A VMware backup proxy is an architecture component that sits between the backup server and other components of the backup infrastructure. While the backup server administers tasks, the proxy processes jobs and delivers backup traffic.

Basic VMware backup proxy tasks include the following:

* Retrieving VM data from the production storage
* Compressing
* Deduplicating
* Encrypting
* Sending it to the backup repository (for example, if you run a backup job) or another VMware backup proxy (for example, if you run a replication job)

Usage Scenarios

A VMware backup proxy is used for backup, replication, Quick Migration and other features. For more information on the backup infrastructure components required for different features, see the relevant feature description.

VMware Backup Proxy Transport Modes

Depending on your backup architecture, a VMware backup proxy can use one of the following data transport modes:

* Direct storage access
* Virtual appliance
* Network

If the VM disks are located on the storage system and the storage system is added to the Veeam Backup & Replication console, the VMware backup proxy can also use the Backup from Storage Snapshots mode.

You can explicitly select the transport mode or let Veeam Backup & Replication automatically choose the mode. For details, see [Transport Modes](transport_modes.md) and [Configuring Backup Proxy for Storage Snapshots](storage_configure_proxy.md).

VMware Backup Proxy Deployment

By default, the role of the proxy is assigned to the backup server itself. However, this is sufficient only for small installations with low traffic load. For large installations, it is recommended to deploy dedicated backup proxies.

To optimize performance of several concurrent jobs, you can use several backup proxies. In this case, Veeam Backup & Replication will distribute the backup workload between available backup proxies. You can deploy backup proxies both in the primary site and in remote sites.

To deploy a proxy, you need to add a Windows-based or Linux-based server to Veeam Backup & Replication and assign the role of the VMware backup proxy to the added server. For requirements and limitations that backup proxies have, see [Requirements and Limitations for VMware Backup Proxies](backup_proxy_requirements.md).

VMware Backup Proxy Services and Components

Backup proxies run light-weight services that take a few seconds to deploy. Deployment is fully automated. Veeam Backup & Replication installs the following components and services:

* Veeam Installer Service is an auxiliary service that is installed and started on any Windows server once it is added to the list of managed servers in the Veeam Backup & Replication console. This service analyzes the system, installs and upgrades necessary components and services depending on the role selected for the server.
* Veeam Data Mover Service/Veeam Transport Service is a service that performs data processing tasks on behalf of Veeam Backup & Replication, such as retrieving source VM data, performing data deduplication and compression, and storing backed-up data on the target storage.

In This Section

* [Requirements and Limitations for VMware Backup Proxies](backup_proxy_requirements.md)
* [Transport Modes](transport_modes.md)
* [Adding VMware Backup Proxies](add_vmware_proxy.md)
* [Editing VMware Backup Proxy Settings](backup_proxy_edit.md)
* [Disabling and Removing VMware Backup Proxies](setup_manproxy.md)

Page updated 8/26/2025

Page content applies to build 13.0.1.1071
