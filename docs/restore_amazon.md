---
title: "Restore to Amazon EC2"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/restore_amazon.html"
last_updated: "1/7/2026"
product_version: "13.0.1.1071"
---

# Restore to Amazon EC2


Veeam Backup & Replication allows you to restore different workloads (VMs, Google VM instances, physical servers and so on) to Amazon Elastic Compute Cloud (Amazon EC2) as EC2 instances. An EC2 instance is a virtual machine in Amazon EC2 with a preconfigured combination of computing resources.

You can use Veeam Backup & Replication to perform the following operations:

* Restore workloads to Amazon EC2 from backups.
* Migrate workloads from the on-premises infrastructure to the cloud.
* Create a test environment in the cloud for troubleshooting, testing patches and updates, and so on.

Supported Backup Types

You can restore workloads from the following types of backups:

* Backups of VMware vSphere or VMware Cloud Director virtual machines created by Veeam Backup & Replication.
* Backups of Microsoft Hyper-V virtual machines created by Veeam Backup & Replication.
* Backups of virtual and physical machines created by [Veeam Agent for Microsoft Windows or Veeam Agent for Linux](agents_introduction.md).

Backups must be created at the entire machine level or volume level.

* Backups of Amazon EC2 instances created by [Veeam Backup for AWS](https://helpcenter.veeam.com/docs/vbaws/guide/overview.html?ver=10).

* Backups of Microsoft Azure virtual machines created by [Veeam Backup for Microsoft Azure](https://helpcenter.veeam.com/docs/vbazure/guide/overview.html?ver=8.1).
* Backups of Google Compute Engine VM instances created by [Veeam Backup for Google Cloud](https://helpcenter.veeam.com/docs/vbgc/guide/welcome.html?ver=7)\*.

* Backups of Nutanix AHV virtual machines created by [Veeam Plug-In for Nutanix AHV](https://helpcenter.veeam.com/docs/vbahv/userguide/overview.html?ver=9).

* Backups of oVirt VMs created by [Veeam Backup for OLVM and RHV](https://helpcenter.veeam.com/docs/vbrhv/userguide/overview.html?ver=7)\*.
* Backups of Proxmox VE VMs created by [Veeam Plug-In for Proxmox VE](https://helpcenter.veeam.com/docs/vbproxmoxve/userguide/overview.html?ver=3).

* Backups of Scale Computing HyperCore VMs created by [Veeam Plug-In for Scale Computing HyperCore](https://helpcenter.veeam.com/docs/vpsch/userguide/overview.html?ver=2)

\* - Available on Microsoft Windows-based backup server.

In This Section

* [How Restore to Amazon EC2 Works](restore_amazon_hiw.md)
* [AWS IAM User Permissions](restore_amazon_permissions.md)
* [Performing Restore to Amazon EC2](restore_amazon_process.md)


