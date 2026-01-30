---
title: "Restore to Google Compute Engine"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/restore_google.html"
last_updated: "12/30/2025"
product_version: "13.0.1.1071"
---

# Restore to Google Compute Engine


Veeam Backup & Replication allows you to restore different workloads (VMs, Google VM instances, physical servers and so on) to Google Compute Engine as VM instances. A VM instance is a virtual machine in Google Compute Engine with a preconfigured combination of computing resources.

You can use Veeam Backup & Replication to perform the following operations:

* Restore machines to Google Compute Engine from backups.
* Migrate machines from the on-premises infrastructure to the cloud.
* Create a test environment in the cloud for troubleshooting, testing patches and updates, and so on.

Supported Backup Types

You can restore machines from the backups of the following types:

* Backups of VMware vSphere or VMware Cloud Director VMs created by Veeam Backup & Replication.
* Backups of Microsoft Hyper-V VMs created by Veeam Backup & Replication.
* Backups of virtual and physical machines created by [Veeam Agent for Microsoft Windows or Veeam Agent for Linux](agents_introduction.md).

Backups must be created at the entire machine level or volume level.

* Backups of Google Compute Engine VM instances created by [Veeam Backup for Google Cloud](https://helpcenter.veeam.com/docs/vbgc/guide/welcome.html?ver=7)\*.
* Backups of Amazon EC2 VM instances created by [Veeam Backup for AWS](https://helpcenter.veeam.com/docs/vbaws/guide/overview.html?ver=10).

* Backups of Microsoft Azure VMs created by [Veeam Backup for Microsoft Azure](https://helpcenter.veeam.com/docs/vbazure/guide/overview.html?ver=8.1).

* Backups of Nutanix AHV VMs created by [Veeam Plug-In for Nutanix AHV](https://helpcenter.veeam.com/docs/vbahv/userguide/overview.html?ver=9).
* Backups of oVirt VMs created by [Veeam Backup for OLVM and RHV](https://helpcenter.veeam.com/docs/vbrhv/userguide/overview.html?ver=7)\*.
* Backups of Proxmox VE VMs created by [Veeam Plug-In for Proxmox VE](https://helpcenter.veeam.com/docs/vbproxmoxve/userguide/overview.html?ver=3).

* Backups of Scale Computing HyperCore VMs created by [Veeam Plug-In for Scale Computing HyperCore](https://helpcenter.veeam.com/docs/vpsch/userguide/overview.html?ver=2).

\* - Available on Microsoft Windows-based backup server.

In This Section

* [How Restore to Google Compute Engine Works](restore_google_hiw.md)
* [Google Compute Engine IAM User Permissions](gcp_iam_permissions.md)
* [Restoring Machines](restore_google_process.md)


