---
title: "Restore to Nutanix AHV"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/restore_ahv.html"
last_updated: "11/13/2025"
product_version: "13.0.1.1071"
---

# Restore to Nutanix AHV

In this article

Veeam Backup & Replication allows you to recover different workloads as Nutanix AHV VMs.

Supported Backup Types

To recover workloads to a Nutanix AHV cluster, you can use the following backups:

* Backups of VMware vSphere virtual machines created by Veeam Backup & Replication
* Backups of VMware Cloud Director virtual machines created by Veeam Backup & Replication
* Backups of Microsoft Hyper-V virtual machines created by Veeam Backup & Replication

* Backups of virtual and physical machines created by [Veeam Agent for Microsoft Windows or Veeam Agent for Linux](agents_introduction.md)

* Backups of Nutanix AHV virtual machines, snapshots of Nutanix AHV PDs, snapshots of Nutanix AHV virtual machines created by [Veeam Plug-In for Nutanix AHV](https://helpcenter.veeam.com/docs/vbahv/userguide/overview.html?ver=9)
* Backups of Amazon EC2 instances created by [Veeam Backup for AWS](https://helpcenter.veeam.com/docs/vbaws/guide/overview.html?ver=10)
* Backups of Microsoft Azure virtual machines created by [Veeam Backup for Microsoft Azure](https://helpcenter.veeam.com/docs/vbazure/guide/overview.html?ver=8.1)
* Backups of Google Compute Engine VM instances created by [Veeam Backup for Google Cloud](https://helpcenter.veeam.com/docs/vbgc/guide/welcome.html?ver=7)\*

* Backups of oVirt VMs created by [Veeam Backup for OLVM and RHV](https://helpcenter.veeam.com/docs/vbrhv/userguide/overview.html?ver=7)\*
* Backups of Proxmox VE VMs created by [Veeam Plug-In for Proxmox VE](https://helpcenter.veeam.com/docs/vbproxmoxve/userguide/overview.html?ver=3)

* Backups of Scale Computing HyperCore VMs created by [Veeam Plug-In for Scale Computing HyperCore](https://helpcenter.veeam.com/docs/vpsch/userguide/overview.html?ver=2).

Performing Restore to Nutanix AHV

The restore procedure of entire workloads to Nutanix AHV practically does not differ from the procedure described in the [Performing VM Restore](https://helpcenter.veeam.com/docs/vbahv/userguide/restore_to_ahv.html?ver=9) section in the Veeam Plug-In for Nutanix AHV User Guide.

[![Restore to Nutanix AHV](images/restore_ahv.webp)](images/restore_ahv.webp)

Page updated 11/13/2025

Page content applies to build 13.0.1.1071
