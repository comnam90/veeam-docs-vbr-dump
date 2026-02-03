---
title: "Connecting Proxmox VE Server"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/pve_connecting_manager.html"
last_updated: "1/26/2026"
product_version: "13.0.1.1071"
---

# Connecting Proxmox VE Server


A Proxmox VE server is a Proxmox VE standalone host or cluster that allows the backup server to access Proxmox VE resources such as VMs, storage and networks. After you add a Proxmox VE server to the backup infrastructure, you will be able to deploy workers and to manage data protection tasks for Proxmox VE VMs.

|  |
| --- |
| Important |
| If you want to add a Proxmox VE cluster to the backup infrastructure, consider the following:   * Each node of the cluster must be added to the backup infrastructure separately.  * The name of the cluster must not be changed in the Proxmox VE environment after you add it to the backup infrastructure. * The type of the Proxmox VE server (standalone host or cluster) must not be changed in the Proxmox VE environment after you add it to the backup infrastructure.   If you want to add the host that was already connected to the backup server as a node to a Proxmox VE cluster, first remove the host from the backup infrastructure and then add it again. Keep in mind that Veeam Backup & Replication will treat it as a new sever and will start new backup chains for VMs. |

In This Section

* [Adding Proxmox VE Server to Backup Infrastructure](pve_sever_add.md)
* [Editing Proxmox VE Server Properties](pve_server_edit.md)
* [Rescanning Proxmox VE Server](pve_server_rescan.md)
* [Removing Proxmox VE Server](pve_server_remove.md)


