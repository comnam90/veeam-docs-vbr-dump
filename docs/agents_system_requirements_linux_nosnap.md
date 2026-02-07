---
title: "System Requirements for Linux Computers with Nosnap Veeam Agent"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/agents_system_requirements_linux_nosnap.html"
last_updated: "2/6/2026"
product_version: "13.0.1.1071"
---

# System Requirements for Linux Computers with Nosnap Veeam Agent


If you plan to use a nosnap package to install Veeam Agent, the protected Linux computer must meet the following system requirements:

| Specification | Requirement |
| --- | --- |
| Hardware | [For nosnap Veeam Agent for Linux] CPU: x64.  [For nosnap Veeam Agent for Linux on Power] CPU: IBM POWER9 or POWER10.  Memory: 1 GB RAM or more. Memory consumption varies depending on the backup type and the total amount of backed-up data.  Disk Space: 300 MB free disk space for product installation.  Network: 10 Mbps or faster network connection to a backup target.  Disk layout: MBR or GPT. |
| OS | Important! Check [considerations and limitations](#os_limits) that apply to the list of supported OSes.  Nosnap Veeam Agent for Linux supports the following distributions:   * Debian 11.0 – 13.2 * Ubuntu 16.04, 18.04, 20.04, 22.04 and 24.04  * RHEL 8.4 – 9.7, 10.0 and 10.1  * Oracle Linux 7 – 10.1 (RHCK) * Oracle Linux 7 (starting from UEK R4) – Oracle Linux 9 (up to 6.12.0-106.55.4.2.el9uek.x86\_64) * Oracle Linux 10 (UEK R8)  * SLES 12 SP5, 15 SP3 – 15 SP7 and 16.0 * SLES for SAP 12 SP5, 15 SP3 – 15 SP7 and 16.0  * Rocky Linux 8.10, 9.4 – 9.7, 10.0 and 10.1 * AlmaLinux 8.10, 9.4 – 9.7, 10.0 and 10.1   Nosnap Veeam Agent for Linux on Power supports little endian versions of the following Linux distributions for IBM Power:   * SLES 15 SP3 – 15 SP7 and 16.0 * SLES for SAP 12 SP5, 15 SP3 – 15 SP7 and 16.0  * RHEL 8.4, 8.6, 8.8, 8.10, 9.0, 9.2, 9.4, 9.6 and 10.0  * RHEL for SAP 8.4, 8.6, 8.8, 8.10, 9.0, 9.2, 9.4, 9.6 and 10.0 |
| File System | Important! Check [considerations and limitations](#file_sys_lim) that apply to the list of supported file systems.  Veeam Agent for Linux supports consistent snapshot-based data backup for the following file systems:   * All [supported file systems](agents_system_requirements_linux.md#filesystem) that are built on top of LVM logical volumes.  * BTRFS (for OSes that run Linux kernel 3.16 or later)   [For nosnap Veeam Agent for Linux] BTRFS is supported only if it resides directly on a physical device with no additional abstraction layers (such as LVM, software RAID, dm-crypt and so on) below or above it.  [For nosnap Veeam Agent for Linux on Power] If BTRFS has additional abstraction layers (such as LVM, software RAID, dm-crypt and so on) above it, only file-level restore operations are supported. Instant Recovery, restore verification (SureBackup), bare metal recovery and volume-level restore are not supported.  Supported file systems that are not located on logical volumes, other file systems and network file systems like NFS or SMB shares can be backed up using the snapshot-less mode only. For details, see the [Snapshot-Less File-Level Backup](https://helpcenter.veeam.com/docs/agentforlinux/userguide/file_backup_snapshotless.html) section in the Veeam Agent for Linux User Guide. |
| Software | Important! Check [considerations and limitations](#software_lim) that apply to the list of supported components.  Protected computer must have the following components installed:  For general operations, backup and restore:   * libacl (for backup and restore of ACLs) * libattr (for backup and restore of extended file attributes) * lvm2 (for LVM snapshots and other LVM-related operations)  * libfuse2 (FUSE libraries for Debian-based and SLES-based systems) * fuse-libs (FUSE libraries for RedHat-based systems)  * dmidecode (for managing Veeam Agent with Veeam Backup & Replication, not required for Veeam Agent for Linux on Power) * btrfs-progs (version 3.16 or later, for backup of BTRFS) * wget (for downloading recovery ISO)  * which (for deployment process)  * tar (for file system indexing, log export and rotation) * gzip (for file system indexing, log export and rotation)   For creating custom Veeam Recovery Media (not required for Veeam Agent for Linux on Power):   * efibootmgr (for UEFI-based systems) * isolinux (for Debian-based systems) * syslinux (for RedHat-based systems) * mksquashfs * unsquashfs * xorriso (for custom Veeam Recovery Media with EFI support) |

Considerations and Limitations

OS

* Only GA versions of the [supported distributions](#OS) that have been released before the current version of Veeam Agent for Linux are supported.

If a new version of a supported Linux distribution is released after the release of the current version of Veeam Agent, Veeam Agent may require a patch to support this new OS version. For details on Veeam Agent compatibility with Linux OS versions, see [this Veeam KB article](https://www.veeam.com/kb2804). Customers with a valid contract can request a patch from Veeam Support; for other customers, the support of the new Linux distribution will be provided with the next release of Veeam Agent.

* The Linux OS must be set up to receive software updates from the default repositories enabled in the OS after installation.

* [For nosnap Veeam Agent for Linux] Veeam Agent supports the following versions of RHEL with Extended Update Support Add-On: 8.4, 8.6, 8.8, 8.10, 9.0, 9.2 and 9.4.
* [For nosnap Veeam Agent for Linux on Power] Veeam Agent supports the following versions of RHEL with Extended Update Support Add-On: 8.4, 8.6, 8.8, 8.10 and 9.4.

* Do not install Veeam Agent on servers that are used as components of the Veeam Backup & Replication infrastructure. This includes Veeam backup servers, backup repositories, proxy servers, mount servers, distribution servers, gateway and helper appliance servers, and any other backup infrastructure component that has the Veeam Mount Service deployed.

* Do not use Veeam Agent managed by one Veeam Backup & Replication installation on a server that acts as a backup infrastructure component in another Veeam Backup & Replication installation. If this happens, both Veeam Backup & Replication installations can automatically update the Transport and Deployer components on the host server, which may lead to performance issues or errors in your backup infrastructure.

File System

* Veeam Agent for Linux does not back up volumes that reside on USB devices and SD cards.

* LVM volumes encrypted with dm-crypt software are not supported.

* Total size of all file systems must not exceed 216 TiB. This limitation applies to all file systems where files you plan to back up are located.

* Size of a file included in a file-level backup must not exceed 16 TiB.
* Name of a file must not be larger than 254 bytes.

Keep in mind that characters that you can use in the file name may be encoded in 2 bytes or more.

* The amount of space required for LVM snapshots largely depends on the IO intensity. Generally, from 10% to 20% of the system’s occupied space should be enough for storing an LVM snapshot.

* Veeam Agent supports backup of extended attributes with the following limitations:

* Veeam Agent backs up extended attributes only with the following public namespaces: system, security, trusted, and user.
* All extended attribute names and values of a file must not exceed 4096 bytes (size of a default ext4 file system block). Veeam Agent does not back up attributes exceeding the limit.

For the kernel version 4.13 or later, if a value of extended attribute exceeds the limit, Veeam Agent uses the ea\_inodes feature. Backups created using the ea\_inodes feature cannot be mounted on kernel versions up to 4.12.

* Backup of file and directory attributes (for example, a — append only, c — compressed, and so on) is not supported.

* Each volume included in a backup must have a unique UUID.

* Consider the following about the backup of machines used as cluster nodes:

* To back up data on local LVM volumes and BTRFS subvolumes, you can use [file-level](https://helpcenter.veeam.com/docs/agentforlinux/userguide/file_backup.html) or [volume-level](https://helpcenter.veeam.com/docs/agentforlinux/userguide/volume_backup.html) backup.

|  |
| --- |
| NOTE |
| Consider the following about backup of LVM volumes:   * During volume-level backup, data from shared disks, clustered file systems or clustered LVM will not be backed up. * To perform volume-level backup, Veeam Agent for Linux will create an LVM snapshot, which can cause instability of the cluster or cluster software. This can happen due to the failover conditions configured for the cluster. However, if the cluster instability is caused by creation of an LVM snapshot only during backup, contact Veeam support for assistance. |

* Backup of clustered file systems using a native file system snapshot is not supported. This includes snapshots created with the help of custom pre-job or post-job scripts.
* The following objects can be backed up only by [snapshot-less file-level backup](https://helpcenter.veeam.com/docs/agentforlinux/userguide/file_backup_snapshotless.html):

* Files on shared disks, clustered file systems or clustered LVM.

* Files on local file systems that are not hosted by LVM or BTRFS.

* Certain limitations for Dell PowerPath configuration apply. To learn more, see [this Veeam KB article](https://www.veeam.com/kb2771).

* Sparse files are not supported. Veeam Agent backs up and restores sparse files as regular files.

* Backup of pseudo file systems, such as /proc, /sys, tmpfs, devfs and others, is not supported.

* Backup of BTRFS volumes and subvolumes with enabled file-system compression is not supported.

* Backup of pseudo-RAID, or driver-level RAID, configurations is not supported. Only hardware RAID arrays managed by dedicated controllers and Linux native software RAID (mdadm) are supported.

Software

|  |
| --- |
| IMPORTANT |
| Linux user account used to work with Veeam Agent for Linux must have the /bin/bash set as the default shell. |

* [For nosnap Veeam Agent for Linux] The dmidecode package is required for Veeam Agent management — a valid BIOS UUID must be obtainable either from dmidecode | grep -i uuid or from /sys/class/dmi/id/product\_uuid. Each Veeam Agent that consumes a license installed in Veeam Backup & Replication must have a unique BIOS UUID. If a valid UUID cannot be obtained, Veeam will generate it automatically.


