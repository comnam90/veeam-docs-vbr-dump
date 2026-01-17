---
title: "Connecting Source Virtualization Hosts"
product: "vbr"
doc_type: "cloud"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/cloud_connect_hypervisor_add.html"
last_updated: "11/11/2025"
product_version: "13.0.1.1071"
---

# Connecting Source Virtualization Hosts


You must connect to the Veeam backup server virtualization hosts on which VMs that you plan to back up or replicate to the cloud are located.

Veeam Backup & Replication lets you connect the following types of hosts:

* VMware vCenter Server
* Standalone ESXi host
* VMware Cloud Director server
* SCVMM
* Microsoft Hyper-V cluster
* Standalone Microsoft Hyper-V host

If a host is managed by VMware vCenter Server, SCVMM or is a part of a cluster, it is recommended that you connect servers or clusters, not a standalone host. If you move VMs between hosts, you will not have to re-configure jobs existing in Veeam Backup & Replication. Veeam Backup & Replication will automatically locate migrated VMs and continue processing them as usual.

|  |
| --- |
| Note |
| Veeam Cloud Connect does not support the scenario in which the SP and tenant connect the same host to Veeam backup servers deployed on the SP and tenant sides. You should not use the same host as a source host and target host for cloud backup and replication tasks (for example, for evaluation purposes). |

The host connection process in the Veeam Cloud Connect infrastructure is the same as the host connection process in a regular Veeam backup infrastructure. To learn more, see [Adding VMware vSphere Servers](https://helpcenter.veeam.com/docs/vbr/userguide/add_vmware_server.html?ver=13) and [Adding Microsoft Hyper-V Servers](https://helpcenter.veeam.com/docs/vbr/userguide/add_hyperv_server.html?ver=13) sections in the Veeam Backup & Replication User Guide.


