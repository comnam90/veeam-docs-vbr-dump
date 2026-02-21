---
title: "Solution Architecture"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/sch_infrastructure_components.html"
last_updated: "2/20/2026"
product_version: "13.0.1.1071"
---

# Solution Architecture


The Veeam Plug-in for Scale Computing HyperCore architecture comprises the following set of components:

* [Scale Computing HyperCore cluster](#cluster)
* [Backup server](#server)
* [Plug-in](#plugin)
* [Backup repositories](#repositories)
* [Workers](#workers)

Scale Computing HyperCore Cluster

A Scale Computing HyperCore cluster is a cluster node containing one or more servers that run the Scale Computing HyperCore software. Veeam Plug-in for Scale Computing HyperCore uses the server to access such Scale Computing HyperCore resources as storage, networks and VMs while performing backup and restore operations.

Backup Server

A backup server is a physical or virtual machine on which Veeam Backup & Replication is installed. The backup server is the configuration, administration and management core of the backup infrastructure. It coordinates backup and restore operations, controls job scheduling and manages resource allocation.

Plug-in

Plug-in enables integration between the backup server and the Scale Computing HyperCore cluster. Plug-in also allows the backup server to deploy and manage workers.

Backup Repositories

A backup repository is a storage location where Veeam Plug-in for Scale Computing HyperCore stores backups of protected Scale Computing HyperCore VMs.

To communicate with backup repositories, Veeam Plug-in for Scale Computing HyperCore uses Veeam Data Mover — the service that is responsible for data processing and transfer. By default, Veeam Data Mover runs on the repositories themselves. If a repository cannot host Veeam Data Mover, it starts on a gateway server — a dedicated component that “bridges” the backup server and workers. For more information, see section [Gateway Server](gateway_server.md).

Workers

A worker is a Linux-based VM that resides on the Scale Computing HyperCore host and processes backup workloads when transferring data to and from backup repositories.

[![Architecture Overview](images/sch_infrastructure.webp)](images/sch_infrastructure.webp "Architecture Overview")


