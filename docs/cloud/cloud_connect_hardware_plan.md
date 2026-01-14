---
title: "cloud_connect_hardware_plan"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/cloud_connect_hardware_plan.html"
last_updated: "12/4/2023"
product_version: "13.0.1.1071"
---


In this article

The hardware plan is a set of resources that the SP allocates in their Veeam Cloud Connect infrastructure to set up a target for tenant VM replicas. For a tenant, a hardware plan appears as a cloud host. A tenant can utilize a cloud host as a regular target host to perform VM replication and failover tasks.

A hardware plan comprises the following resources in the SP virtualization infrastructure:

* CPU — limit of CPU that can be used by all replicated VMs of a tenant subscribed to a hardware plan (amount of CPU on the tenant cloud host).
* Memory — limit of RAM that can be used by all replicated VMs of a tenant subscribed to a hardware plan (by all tenant VMs on the cloud host).
* Storage — a quota on a datastore (for VMware hardware plans) or a volume (for Hyper-V hardware plans) that a tenant can utilize for storing replicated VMs data.
* Network — specified number of networks to which tenant VM replicas can connect. When the SP subscribes a tenant to a hardware plan, Veeam Backup & Replication creates the same number of network adapters (vNICs) on the network extension appliance that is deployed on the SP side. To learn more, see [Network Extension Appliance](cloud_network_extension_appliance.md).

The SP can configure hardware plans for VMware vSphere and Microsoft Hyper-V platforms. Replication resources that will be provided to tenants through hardware plans can be allocated on standalone hosts and clusters.

If the SP configures a hardware plan using resources allocated on a cluster, Veeam Backup & Replication automatically distributes the workload between the components of the cluster:

* Selects a host on which to register a VM replica.
* Selects a datastore or volume on which to store VM replica files.

The SP can configure one or several hardware plans. For example, the SP may configure in advance multiple hardware plans for different categories of customers or create custom hardware plans that match production environment of particular tenants.

To let a tenant work with a cloud host based on the hardware plan, the SP must subscribe the tenant to this hardware plan. The SP can subscribe one or several tenants to the same hardware plan. Each tenant subscribed to the hardware plan can use the whole set of resources specified in the hardware plan. Tenants do not know about other tenants who work with cloud hosts, and have no access to their data. As a result, the SP can expose virtualization resources to several tenants and store tenants’ data in the cloud in an isolated and segregated way.

The SP can subscribe a tenant to one or several hardware plans that utilize resources on the same SP host or cluster or different hosts or clusters. When the SP subscribes a tenant to a hardware plan, the hardware plan appears in the tenant Veeam Backup & Replication infrastructure as a cloud host.

![Hardware Plan](images/hardware_plan.webp)

Cloud Hosts in SP Virtualization Environment

Replication resources allocated for tenant VM replicas appear in the SP virtualization environment differently depending on the virtualization platform: VMware vSphere or Microsoft Hyper-V.

When the SP configures the first VMware hardware plan, Veeam Backup & Replication creates on the host allocated for replication target a parent resource pool for Cloud Connect Replication resources. When the SP subscribes a tenant to a hardware plan, Veeam Backup & Replication creates in this parent resource pool a resource pool that represents a tenant cloud host. On the datastore that the SP exposes as a storage for tenant VM replicas, Veeam Backup & Replication creates for every tenant a folder in which VM replica files are stored.

For example, when the SP subscribes the tenant ABC Company to the hardware plan VMware Silver, the resource pool VMware\_Silver\_ABC will be created in the parent Cloud\_Connect\_Replication resource pool on the SP virtualization host where cloud replication resources are allocated. Tenant VM replicas will be created in the ABC Company folder on the selected datastore.

For Microsoft Hyper-V hardware plans, a tenant cloud host appears in the SP virtualization environment as a dedicated folder on the storage where tenant VM replicas are created.

Related Tasks

[Configuring Hardware Plans](cloud_connect_configure_hardware_plan.md)

Page updated 12/4/2023

Page content applies to build 13.0.1.1071
