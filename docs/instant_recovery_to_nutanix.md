---
title: "Instant Recovery to Nutanix AHV"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/instant_recovery_to_nutanix.html"
last_updated: "11/13/2025"
product_version: "13.0.1.1071"
---

# Instant Recovery to Nutanix AHV


With Instant Recovery to Nutanix AHV, you can immediately recover different workloads as Nutanix AHV VMs. You can use Instant Recovery to Nutanix AHV to migrate the entire infrastructure or individual VMs to a Nutanix AHV cluster.

|  |
| --- |
| Important |
| To restore to Nutanix AHV, you must install Veeam Plug-In for Nutanix AHV on the backup server. To learn more, see the [Installation](https://helpcenter.veeam.com/docs/vbahv/userguide/install_ahv_services.html?ver=9) section in the Veeam Plug-In for Nutanix AHV User Guide. |

Supported Backup Types

To recover machines to a Nutanix AHV cluster, you can use the following backups:

* Backups of VMware vSphere virtual machines created by Veeam Backup & Replication
* Backups of VMware Cloud Director virtual machines created by Veeam Backup & Replication
* Backups of Microsoft Hyper-V virtual machines created by Veeam Backup & Replication

* Backups of virtual and physical machines created by [Veeam Agent for Microsoft Windows or Veeam Agent for Linux](agents_introduction.md)

* Backups of Nutanix AHV virtual machines created by [Veeam Plug-In for Nutanix AHV](https://helpcenter.veeam.com/docs/vbahv/userguide/overview.html?ver=9)
* Backups of Amazon EC2 instances created by [Veeam Backup for AWS](https://helpcenter.veeam.com/docs/vbaws/guide/overview.html?ver=10)
* Backups of Microsoft Azure virtual machines created by [Veeam Backup for Microsoft Azure](https://helpcenter.veeam.com/docs/vbazure/guide/overview.html?ver=8.1)
* Backups of Google Compute Engine VM instances created by [Veeam Backup for Google Cloud](https://helpcenter.veeam.com/docs/vbgc/guide/welcome.html?ver=7)\*

* Backups of oVirt VMs created by [Veeam Backup for OLVM and RHV](https://helpcenter.veeam.com/docs/vbrhv/userguide/overview.html?ver=7)\*
* Backups of Proxmox VE VMs created by [Veeam Plug-In for Proxmox VE](https://helpcenter.veeam.com/docs/vbproxmoxve/userguide/overview.html?ver=3)

* Backups of Scale Computing HyperCore VMs created by [Veeam Plug-In for Scale Computing HyperCore](https://helpcenter.veeam.com/docs/vpsch/userguide/overview.html?ver=2)

\* - Available on Microsoft Windows-based backup server.

Performing Instant Recovery to Nutanix AHV

The procedure of restore to Nutanix AHV practically does not differ from the procedure described in the [Performing Instant Recovery of Workloads to Nutanix AHV](https://helpcenter.veeam.com/docs/vbahv/userguide/instant_recovery_ahv.html?ver=9) section in the Veeam Plug-In for Nutanix AHV User Guide.

[![Launch Instant Recovery to Nutanix AHV](images/instant_recovery_to_nutanix.webp)](images/instant_recovery_to_nutanix.webp "Launch Instant Recovery to Nutanix AHV")


