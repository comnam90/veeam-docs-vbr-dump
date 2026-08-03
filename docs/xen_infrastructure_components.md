---
title: "Solution Architecture"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/xen_infrastructure_components.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Solution Architecture


Since Veeam Plug-in for Xen is integrated with Veeam Backup & Replication, the solution architecture comprises the following set of components:

* [Xen Pool Coordinator](xen_infrastructure_components.md#cluster)
* [Backup server](#server)
* [Veeam Plug-in for Xen](#plugin)
* [Backup repositories](#repositories)
* [Workers](#workers)

Xen Pool Coordinator

Xen pool coordinator host provides a centralized interface for managing other hosts in a Xen pool. Veeam Plug-in for Xen uses the pool coordinator to access such resources as storage, networks and VMs while performing backup and restore operations.

Backup Server

A backup server is either a Windows-based or Linux-based physical or virtual machine on which Veeam Backup & Replication is installed. The backup server is the configuration, administration and management core of the backup infrastructure. It coordinates backup and restore operations, controls job scheduling and manages resource allocation.

Veeam Plug-In for Xen

Veeam Plug-in for Xen is an architecture component that enables integration between the backup server and other components of the backup infrastructure. Veeam Plug-in for Xen allows Veeam Backup & Replication to connect to the Xen pool, and to perform data protection and disaster recovery tasks with Xen resources.

Backup Repositories

A backup repository is a storage location where Veeam Backup & Replication stores backups of protected Xen VMs.

To communicate with backup repositories, Veeam Backup & Replication uses Veeam Data Mover — the service that is responsible for data processing and transfer. By default, Veeam Data Mover runs on the repositories themselves. If a repository cannot host Veeam Data Mover, it starts on a gateway server — a dedicated component that “bridges” the backup server and workers. For more information, see [Gateway Servers](gateway_server.md).

Workers

A worker is a Linux-based VM that resides on the Xen host and processes backup workloads when transferring data to and from backup repositories.

[![Architecture Overview](images/xen_infrastructure_components.webp)](images/xen_infrastructure_components.webp "Architecture Overview")

Page updated 2026-07-30

