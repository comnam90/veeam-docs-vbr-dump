---
title: "Replication for VMware Cloud Director"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vcloud_director_replication.html"
last_updated: "7/18/2024"
product_version: "13.0.1.1071"
---

# Replication for VMware Cloud Director

In this article

VMware Cloud Director replication is a technology that allows you to replicate VM containers between production and disaster recovery VMware Cloud Director environments, to the source organization VDC or to another organization VDC added to a different VMware Cloud Director. Using the VMware Cloud Director replication you can replicate the following VM containers:

* vApps
* Cloud Director organizations
* Cloud Director organization VDC
* VMware Cloud Director instances

The VMware Cloud Director replication technology utilizes the same mechanisms as the [VM replica](replication.md) and follows the same recovery scenarios. The main differences from VM replica are the following:

* The VMware Cloud Director replica target is an organization VDC and it must be set up beforehand in your VMware Cloud Director infrastructure.
* A minimal unit of a VMware Cloud Director replication is a vApp, you cannot replicate a single VM that is added to a vApp.
* The VMware Cloud Director replica snapshots are created on the VMs that are added to the target vApp.
* A single restore point of the VMware Cloud Director replica contains snapshots of all VMs added to a vApp.
* Veeam Backup & Replication assigns a new CLOUD.UUID to the replicated VMs when a VMware Cloud Director replication job runs.

The VMware Cloud Director replication technology supports functionality similar to normal VM replication: you can create VMware Cloud Director replication jobs, perform failover and failback operations with replicated VM containers and manage these VM containers.

Related Topics

* [Creating Cloud Director Replication Job](creating_vcd_replication_job.md)
* [Managing Cloud Director Replication Jobs](replication_job_manage_vcd.md)
* [Managing Cloud Director Replicas](managing_vcd_replicas.md)
* [Failover and Failback for Cloud Director](vcd_failover_failback.md)

Page updated 7/18/2024

Page content applies to build 13.0.1.1071
