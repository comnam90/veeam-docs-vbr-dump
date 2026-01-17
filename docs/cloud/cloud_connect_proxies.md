---
title: "Backup Proxies"
product: "vbr"
doc_type: "cloud"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/cloud_connect_proxies.html"
last_updated: "11/18/2025"
product_version: "13.0.1.1071"
---

# Backup Proxies


A backup proxy is an architecture component that operates as a data mover and transfers data between source and target. Backup proxies in the Veeam Cloud Connect infrastructure run the same services and perform the same roles as backup proxies in the regular backup infrastructure.

In the Veeam Cloud Connect infrastructure, the SP and the tenant can use the following types of backup proxies:

* VMware Backup Proxy is used for backup, recovery and snapshot-based replication of VMware vSphere virtual machines. To learn more, see the [VMware Backup Proxies](https://helpcenter.veeam.com/docs/vbr/userguide/backup_proxy.html?ver=13) section in the Veeam Backup & Replication User Guide.
* CDP Proxy is used for continuous data protection of VMware vSphere virtual machines. To learn more about source and target CDP proxies, see [CDP Infrastructure in Veeam Cloud Connect](cloud_connect_cdp_infrastructure.md).
* Hyper-V Proxy is used for backup, recovery and replication of Hyper-V virtual machines. To learn more about Hyper-V proxies, see the [Backup Infrastructure Components](https://helpcenter.veeam.com/docs/vbr/userguide/components.html?ver=13) section in the Veeam Backup & Replication User Guide.

By default, the proxy role is assigned to the following components:

* The backup server itself for VMware Backup Proxy.
* The Hyper-V host for Hyper-V Proxy.

For large installations, it is recommended to deploy dedicated VMware proxies and off-host Hyper-V proxies to distribute the backup workload. The SPs and tenants configure backup proxies in the following way:

* The source proxy is configured on the tenant side.
* The target proxy is configured on the SP side.

The number of target backup proxies required in the SP infrastructure varies. At least one proxy must be deployed per hypervisor cluster, so that this proxy can access all available underlying storage and then write the received data to it.

It is recommended to deploy the VMware backup proxy as a virtual machine on the same ESXi host as the VMs to be backed up. In contrast to physical proxies, virtual proxies can use virtual appliance mode (also known as HotAdd mode), which is the most effective transport mode for a target-side proxy, especially in replication scenarios. To learn more, see the [Transport Modes](https://helpcenter.veeam.com/docs/vbr/userguide/transport_modes.html?ver=13) section in the Veeam Backup & Replication User Guide.

Veeam Backup & Replication does not apply the maximum concurrent task limit to backup proxies used in the Veeam Cloud Connect infrastructure. The maximum number of allowed concurrent tasks is defined per tenant in the properties of the tenant account. For optimal performance and to avoid overload, the maximum number of concurrent tasks specified in the tenant settings should not exceed the limits for backup proxies and backup repositories in the SP Veeam Cloud Connect infrastructure.

To ensure that the tenant has sufficient resources, the SP must consider the sizing and capacity of the backup proxies. The recommended ratio of available CPUs on a backup proxy server to the maximum number of concurrent tasks is one-to-one.


