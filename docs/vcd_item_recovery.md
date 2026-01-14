---
title: "Item Recovery"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vcd_item_recovery.html"
last_updated: "8/20/2025"
product_version: "13.0.1.1071"
---

# Item Recovery

In this article

Item recovery includes the following methods:

* VM file restore — to restore VM files (.VMX, .VMXF and so on) without restoring the entire VM.

The process of VM files restore for VMware Cloud Director VMs does not differ from that for regular VMware vSphere VMs. For more information, see [Restoring VM Files](performing_vmfile_restore.md).

* Restoring VM hard disks — to restore VM disks. When you restore disks, you extract them from backups to the production storage.

The process of VM hard disks restore for VMware Cloud Director VMs does not differ from that for regular VMware vSphere VMs. For more information, see [Restoring Virtual Disks](performing_disk_restore.md).

Veeam Backup & Replication provides the following platform-independent methods for item recovery:

* [Guest OS file restore](guest_file_recovery.md) — to restore individual guest OS files from Windows, Linux, Mac and other guest OS file systems. You can restore files and folders directly from a regular image-level backup, storage snapshot or replica.
* [Application items restore](restore_veeam_explorers.md) — to restore items from different applications such as Microsoft Active Directory, Microsoft SQL Server and so on. Application items are recovered directly from VM backups and replicas. To recover application items, Veeam Backup & Replication uses the capabilities of Veeam Explorers.

Page updated 8/20/2025

Page content applies to build 13.0.1.1071
