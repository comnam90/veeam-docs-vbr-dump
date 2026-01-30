---
title: "Disk Export"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/disk_export.html"
last_updated: "12/15/2025"
product_version: "13.0.1.1071"
---

# Disk Export


Veeam Backup & Replication allows you to export disks, that is, restore disks from backups of physical or virtual machines and convert them to the VMDK, VHD or VHDX formats.

During disk export, Veeam Backup & Replication creates the following files that can be used by VMware vSphere and Microsoft Hyper-V VMs:

* When you export a disk in the VMDK format, Veeam Backup & Replication creates a pair of files that make up the VM virtual disk: a descriptor file and file with the virtual disk content.
* When you export a disk in the VHD/VHDX format, Veeam Backup & Replication creates a file of the VHD or VHDX format.

You can save the exported disks to different servers added to the backup infrastructure or place disks on a datastore connected to a host.

Veeam Backup & Replication supports batch disk export. For example, if you choose to export 2 disks, Veeam Backup & Replication will convert them to 2 virtual disks and store these disks in the specified location.

Supported Backup Types

You can restore disks from the following backups:

* Backups of VMware vSphere virtual machines created by Veeam Backup & Replication
* Backups of VMware Cloud Director virtual machines created by Veeam Backup & Replication
* Backups of Microsoft Hyper-V virtual machines created by Veeam Backup & Replication

* Backups of virtual and physical machines created by [Veeam Agent for Microsoft Windows, Veeam Agent for Linux, Veeam Agent for Mac, Veeam Agent for Oracle Solaris or Veeam Agent for IBM AIX](agents_introduction.md)

* Backups of EC2 instances created by [Veeam Backup for AWS](https://helpcenter.veeam.com/docs/vbaws/guide/overview.html?ver=10)
* Backups of Azure VMs created by [Veeam Backup for Microsoft Azure](https://helpcenter.veeam.com/docs/vbazure/guide/overview.html?ver=8.1)
* Backups of Nutanix AHV virtual machines created by [Veeam Plug-In for Nutanix AHV](https://helpcenter.veeam.com/docs/vbahv/userguide/overview.html?ver=9)
* Backups of Google VM instances created by [Veeam Backup for Google Cloud](https://helpcenter.veeam.com/docs/vbgc/guide/welcome.html?ver=7)\*
* Backups of oVirt VMs created by [Veeam Backup for OLVM and RHV](https://helpcenter.veeam.com/docs/vbrhv/userguide/overview.html?ver=7)\*
* Backups exported by [Kasten policies](https://helpcenter.veeam.com/docs/vbr/kasten_integration/overview.html?ver=13)

* Backups of Proxmox VE VMs created by [Veeam Plug-In for Proxmox VE](https://helpcenter.veeam.com/docs/vbproxmoxve/userguide/overview.html?ver=3)

* Backups of Scale Computing HyperCore VMs created by [Veeam Plug-In for Scale Computing HyperCore](https://helpcenter.veeam.com/docs/vpsch/userguide/overview.html?ver=2)

\* - Available on Microsoft Windows-based backup server.

Related Topics

* [Exporting Disks](exporting_disks.md)
* [Restoring Volumes from Veeam Agent Backups](integration_volume_restore.md)


