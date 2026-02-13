---
title: "Disk Publishing (Data Integration API)"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/data_integration_api.html"
last_updated: "2/12/2026"
product_version: "13.0.1.1071"
---

# Disk Publishing (Data Integration API)


Disk publishing allows you to save time by getting backup content of one or multiple disks instead of all disks from a backup. This technology gives read-only access to data and helps if you want to analyze data of your backup. For example, look for specific documents or usage patterns, or perform antivirus scan of backed-up data.

You can publish a disk from different types of backups. The disk can have a Microsoft Windows file system or Linux, Unix or other file system. For the full list of supported file systems, see [Supported Platforms, Applications and Workloads](platform_support.md#flr). To present the backed-up disk to the target server, Veeam Backup & Replication uses the iSCSI protocol when publishing disks to the Microsoft Windows-based server or the FUSE protocol when publishing disks to the Linux-server or Unix-based server. After the publishing, the target server can access the backup content using the iSCSI initiator or FUSE protocol, and read the necessary data from the disk.

Supported Backup Types

You can publish disks from the following types of backups:

* Backups of VMware vSphere virtual machines created by Veeam Backup & Replication

* Backups of Microsoft Hyper-V virtual machines created by Veeam Backup & Replication

* Backups of VMware Cloud Director virtual machines created by Veeam Backup & Replication

* Backups of oVirt VMs created by [Veeam Backup for OLVM and RHV](https://helpcenter.veeam.com/docs/vbrhv/userguide/overview.html?ver=7)\*

* Backups of virtual and physical machines created by [Veeam Agent for Microsoft Windows, Veeam Agent for Linux, Veeam Agent for Mac, Veeam Agent for Oracle Solaris or Veeam Agent for IBM AIX](agents_introduction.md)

* Backups of Nutanix AHV virtual machines created by [Veeam Plug-In for Nutanix AHV](https://helpcenter.veeam.com/docs/vbahv/userguide/overview.html?ver=9)
* Backups of Amazon EC2 instances created by [Veeam Backup for AWS](https://helpcenter.veeam.com/docs/vbaws/guide/overview.html?ver=10)
* Backups of Microsoft Azure virtual machines created by [Veeam Backup for Microsoft Azure](https://helpcenter.veeam.com/docs/vbazure/guide/overview.html?ver=8.1)
* Backups of Google instances created by [Veeam Backup for Google Cloud](https://helpcenter.veeam.com/docs/vbgc/guide/welcome.html?ver=7)\*

* Backups exported by [Kasten policies](https://helpcenter.veeam.com/docs/vbr/kasten_integration/overview.html?ver=13)

* Backups of Proxmox VE VMs created by [Veeam Plug-In for Proxmox VE](https://helpcenter.veeam.com/docs/vbproxmoxve/userguide/overview.html?ver=3)
* Backups of Scale Computing HyperCore VMs created by [Veeam Plug-In for Scale Computing HyperCore](https://helpcenter.veeam.com/docs/vpsch/userguide/overview.html?ver=2)

\* - Available on Microsoft Windows-based backup server.​

|  |
| --- |
| Note |
| You cannot publish disks from replicas using UI. To do that, use the [Publish-VBRBackupContent](https://helpcenter.veeam.com/docs/vbr/powershell/publish-vbrbackupcontent.html?ver=13) cmdlet. |

Considerations and Limitations

Disk publishing has the following requirements and limitations:

* The necessary ports must be opened on the target server. For more information, see [Ports](used_ports.md#guest_os_recovery_connections).
* The file system of a workload whose disks you plan to restore must be supported. For details, see the [File-Level Restore](platform_support.md#flr).
* To restore disks that have file system other than Microsoft Windows, you can use only a Linux-based server as the target server.

* The 32-bit version of a Linux-based server is not supported as the target server.
* The target server must support the file system of the disk that you plan to publish.
* A server on which a hardened repository is configured cannot be used as the target server.
* [For Microsoft Windows-based backup server] Disk publishing is not available for Linux, Unix, macOS (and other) workload backups stored on Veeam Cloud Connect Repositories. For more information on Veeam Cloud Connect repositories, see the [Cloud Repository](https://helpcenter.veeam.com/docs/vbr/cloud/cloud_connect_repository.html?ver=13) section in the Veeam Cloud Connect Guide.
* Basic disks, Linux LVM (Logical Volume Manager) and ZFS pools can be published. Encrypted, RAID1 and mirrored LVM volumes are not supported.
* RAID disks publish for Linux workloads is not supported.

* The target server must support the same ReFS version or later than the version used on the workload from which you plan to restore files. For more information on which OSes support which ReFS, see [ReFS versions and compatibility matrix](https://gist.github.com/0xbadfca11/da0598e47dd643d933dc#mountability).
* If data deduplication is enabled for some disks in a backup, data deduplication must be enabled on the target server.
* You cannot publish disks from a backup created in the reverse incremental mode if the backup job is being performed. If the backup is created in the incremental backup mode and the backup job is being performed, you can publish disks from any available restore point.
* You can publish disks from Novell Storage Services (NSS) file system. The target host must differ from the backed-up workload.
* Mounting of LVM snapshots is not supported. LVM snapshots are skipped from processing.
* You can publish disks with ZFS FS if the zfsutils-linux package is installed on the specified target host. The zfs-fuse package is not supported.
* If you want to publish a Btrfs disk and select the original server as the target server, the mount of the Btrfs disk will fail. The issue occurs due to restriction of mounting two Btrfs disks with identical IDs to the same machine. To avoid this issue, use another target server. However, note that Btrfs disks can be restored for backups created by Veeam Agent for Linux. During the backup process, Veeam Agent for Linux changes disk IDs in the backup file.

How Publishing Works for Microsoft Windows File Systems

After you start the publishing session for disks with Microsoft Windows file system, the following applies:

1. Veeam Backup & Replication connects to the backup repository where the backup locates and to the mount server associated with this repository.
2. Veeam Backup & Replication starts the following agents and services in the infrastructure:

* The repository agent. This agent runs on the backup repository or on the gateway server associated with this repository.
* The mount agent. This agent runs on the mount server. The agent configures the iSCSI Target Server on the mount server and triggers the repository agent to read the backup data.
* Veeam Installer Service. This service is installed and runs on the target server and remains on it after the publishing finishes.

1. Veeam Backup & Replication accesses the target server and configures the iSCSI initiator on this server.
2. After Veeam Backup & Replication adds the target server to the iSCSI Target Server settings, the target server can access disk content. The disk content is available in the C:\VeeamFLR\ folder on the target server. Note that disk data is read-only.

After that, you can browse the disks and perform data analysis operations with them. The published disks are available while the mount server is up and running. Even if you turn off the backup server, you will be able to access the published disks.

After you finish working with the disks, you should stop publishing them as described in [Managing Published Disks](publishing_disks_manage.md).

How Publishing Works for Linux, Unix and Other File Systems

After you start the publishing session for disks with Linux, Unix or other file system, the following applies:

1. Veeam Backup & Replication connects to the backup repository where the backup locates and to the mount server associated with this repository.
2. Veeam Backup & Replication starts the following agents in the infrastructure:

* The repository agent. This agent runs on the backup repository or on the gateway server associated with this repository.
* A temporary agent. This agent runs on the target server and is removed after the publishing session finishes.

1. Veeam Backup & Replication uses the FUSE protocol to publish the content of the backup automatically.

The published disk images are available in the /tmp/Veeam.Mount.Disks location. The disk content is available in the /tmp/Veeam.Mount.FS location. Note that disk data is read-only.

After that, you can browse the disks and perform data analysis operations with them.

After you finish working with the disks, you should stop mounting them as described in [Managing Published Disks](publishing_disks_manage.md).

Mount Modes

When you publish disks with Microsoft Windows file system from the UI, Veeam Backup & Replication automatically configures the iSCSI session and gives the target server (iSCSI initiator) access to the published disks. To manually start the iSCSI session from any server that has access to the iSCSI Target Server, you can use the [Publish-VBRBackupContent](https://helpcenter.veeam.com/docs/vbr/powershell/publish-vbrbackupcontent.html?ver=13) cmdlet.


