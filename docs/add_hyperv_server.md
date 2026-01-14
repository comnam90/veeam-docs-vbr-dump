---
title: "Adding Microsoft Hyper-V Servers"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/add_hyperv_server.html"
last_updated: "9/23/2025"
product_version: "13.0.1.1071"
---

# Adding Microsoft Hyper-V Servers

In this article

You must add to the backup infrastructure Microsoft Hyper-V hosts that you plan to use as source and target for backup, replication and other activities.

You can connect standalone Hyper-V hosts, Hyper-V clusters or SCVMM servers. If a Hyper-V host is a part of a cluster or SCVMM, it is recommended that you add to the backup infrastructure a cluster or SCVMM, not a standalone Hyper-V host.

If you plan to migrate VMs between hosts in the cluster or SCVMM, you will not have to reconfigure jobs in Veeam Backup & Replication. Veeam Backup & Replication will automatically locate migrated VMs and continue processing them as usual. If you migrate VMs between standalone hosts that are not a part of one cluster or SCVMM server registered in Veeam Backup & Replication, you will have to reconfigure jobs to include the migrated VMs. After that, Veeam Backup & Replication will create full backups for these VMs. If you do not reconfigure the jobs, they will fail.

On every connected Microsoft Hyper-V host, Veeam Backup & Replication deploys a set of components:

* Veeam Installer Service
* Veeam Data Mover Service/Veeam Transport Service
* Veeam Hyper-V Integration Service
* Guest Interaction Proxy Service

|  |
| --- |
| Important |
| By default, these services run under the LocalSystem account. For security purposes, it is not recommended to change the default account. |

Related Topics

* [Adding Microsoft Hyper‑V Servers Using Console](add_hyperv_server_console.md)
* [Adding Microsoft Hyper‑V Servers Using Web UI](add_hyperv_server_web.md)

Page updated 9/23/2025

Page content applies to build 13.0.1.1071
