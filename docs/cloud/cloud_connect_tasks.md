---
title: "Tasks with Cloud Repository"
product: "vbr"
doc_type: "cloud"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/cloud_connect_tasks.html"
last_updated: "2/2/2026"
product_version: "13.0.1.1071"
---

# Tasks with Cloud Repository


Tasks on Tenant Side

Tenants can perform the following data backup and recovery tasks in Veeam Backup & Replication against the cloud repository:

Data Backup

* VM backup

VM backup is supported for VMware vSphere and Microsoft Hyper-V platforms only. For other platforms, use backup copy.

* VMware Cloud Director backup (for VMware vSphere platform)
* Veeam Agent backup
* Backup copy

Backup copy is supported to a cloud repository only. Backup copy from a cloud repository is not supported.

For information about types of backups for which backup copy to the cloud repository is supported, see [Backup Copy to Cloud Repository](cc_backup_copy.md).

Data Recovery

Tenants can perform the following operations:

* Data restore

* Entire VM restore
* VMware Cloud Director restore (for VMware vSphere platform)
* VM files restore
* VM disks restore (for VMware vSphere platform)
* VM guest OS files restore (Microsoft Windows only. Multi-OS restore is not supported.)
* Application items restore
* Volume restore (for backups created with Veeam Agent for Microsoft Windows)
* Disk export (for backups created with Veeam Agent for Microsoft Windows)
* Guest OS files restore (for backups created with Veeam Agent for Microsoft Windows)
* Disk publishing

* Instant Recovery to [Nutanix AHV](https://helpcenter.veeam.com/docs/vbahv/userguide/overview.html?ver=9) (requires an additional plug-in)

* Backup export
* File copy (manual operations)

Tasks on SP Side

In addition to data restore operations performed by the tenant, the SP can perform the following operations:

* Instant Recovery
* Backup restore to Microsoft Azure
* Backup restore to Amazon EC2
* Disk restore (using Veeam PowerShell cmdlets only)
* Disk publishing (using Veeam PowerShell cmdlets only)

Related Topics

[Using Cloud Repositories](cloud_connect_use_cloud_repo.md)


