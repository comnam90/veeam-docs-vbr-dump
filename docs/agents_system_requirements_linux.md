---
title: "System Requirements for Linux Computers"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/agents_system_requirements_linux.html"
last_updated: "1/6/2026"
product_version: "13.0.1.1071"
---

# System Requirements for Linux Computers


You can use Veeam Backup & Replication to manage Veeam Agent for Linux that was installed using a package with the Veeam kernel module dependency or using a nosnap package without dependency on the Veeam kernel module. On IBM Power Systems, Veeam Agent for Linux can be installed using a special nosnap package — Veeam Agent for Linux on Power.

Veeam kernel module is used for creating system snapshots. The nosnap version of Veeam Agent for Linux leverages the native snapshot capabilities of the supported file systems. For information on system requirements for nosnap versions of Veeam Agent for Linux, see [System Requirements for Linux Computers (nosnap Veeam Agent)](agents_system_requirements_linux_nosnap.md).

|  |
| --- |
| NOTE |
| You can add computers with the nosnap version of Veeam Agent for Linux on Power installed only to the protection group for pre-installed Veeam Agents. |

Veeam Agent Computer (Veeam Kernel Module)

| Specification | Requirement |
| --- | --- |
| Hardware | IMPORTANT! Check [considerations and limitations](#limits_hw_val) that apply to the list of supported hardware.  CPU: x64.  Memory: 1 GB RAM or more. Memory consumption varies depending on the backup type and the total amount of backed-up data.  Disk Space: 500 MB for product installation. Required disk space varies depending on the Veeam Agent usage scenario.  Network: 10 Mbps or faster network connection to a backup target.  System firmware: BIOS or UEFI.  Disk layout: MBR or GPT.  For virtual machines: Only full virtualization type is supported. Oracle VM virtual machines are supported with [limitations](https://helpcenter.veeam.com/docs/agentforlinux/userguide/baremetal_volume_restore_byb.html). Virtual I/O (VirtIO) devices have [experimental support](https://www.veeam.com/kb2976) status. Other containers and paravirtualized instances are not supported. |
| OS | IMPORTANT! Check [considerations and limitations](#limits_os_val) that apply to the list of supported OSes.  Linux kernel version 3.10 to version 6.18 is supported.  Veeam Agent supports the 64-bit versions of the following distributions:   * Debian 11.0 – 13.21 * Ubuntu 16.04, 18.04, 20.04, 22.04 and 24.04  * RHEL 8.4 – 9.7, 10.0 and 10.1  * Oracle Linux 7 – 10.1 (RHCK) * Oracle Linux 7 (starting from UEK R4) – Oracle Linux 8 (up to UEK R6) * Oracle Linux 8 (UEK R7) — for information on installation, see [this Veeam KB article](https://www.veeam.com/kb4394). * Oracle Linux 9 (UEK R7 up to 5.15.0-315.196.5.2.el9uek.x86\_64)  * Oracle Linux 9 (UEK R8) – for information on installing Veeam Agent on Oracle Linux 9 with UEK R8, see [this Veeam KB article](https://www.veeam.com/kb4732). * Oracle Linux 10 (UEK R8)  * SLES 12 SP5, 15 SP3 – 15 SP7 and 16.0 * SLES for SAP 12 SP5, 15 SP3 – 15 SP7 and 16.0  * Rocky Linux 8.10, 9.4 – 9.7, 10.0 and 10.1 * AlmaLinux 8.10, 9.4 – 9.7, 10.0 and 10.1  * Amazon Linux 2 (starting from kernel version 5.10) and Amazon Linux 2023 — these distribution are supported for [cloud machines](agents_backup_cloud_machines.md) only and have an [experimental support](https://www.veeam.com/kb2976) status.   1 To install Veeam Agent on Debian 13, additional prerequisite [software](#deb13) is required. |
| File System | IMPORTANT! Check [considerations and limitations](#limits_fs_val) that apply to the list of supported file systems.  Veeam Agent for Linux supports consistent snapshot-based data backup for the following file systems:   * BTRFS (for OSes that run Linux kernel 3.16 or later) * Ext 2/3/4 * F2FS * FAT16 * FAT32 * HFS * HFS+ * JFS * NTFS * ReiserFS * XFS   The supported file system (except for BTRFS) can reside on a simple volume or LVM2 volume; volumes protected with encryption software such as dm-crypt are supported. BTRFS is supported only if it resides directly on a physical device with no additional abstraction layers (such as LVM, software RAID, dm-crypt and so on) below or above it.  Other file systems, file systems that are not located on logical volumes, as well as network file systems like NFS or SMB shares can be backed up using the snapshot-less mode only. For details, see the [Snapshot-Less File-Level Backup](https://helpcenter.veeam.com/docs/agentforlinux/userguide/file_backup_snapshotless.html) section in the Veeam Agent for Linux User Guide. |
| Software | IMPORTANT! Check [considerations and limitations](#software_lim) that apply to the list of required components.  Protected computer must have the following components installed:  Only for installing Veeam Agent using dkms packages:   * linux-headers (for Debian-based systems) * linux-headers-amd64 (for Debian 13. For package specifics, see [Considerations and Limitations](#software_lim)) * kernel-headers (for RHEL-based systems) * kernel-devel (for RHEL-based systems) * kernel-uek-devel (for Oracle Linux systems with UEK) * dkms * gcc * make * perl   For general operations, backup and restore:   * libudev (for managing devices during backup and restore) * libacl (for backup and restore of ACLs) * libattr (for backup and restore of extended file attributes) * lvm2 (for LVM snapshots and other LVM-related operations) * libfuse2 (FUSE libraries for Debian-based and SLES-based systems) * fuse-libs (FUSE libraries for RedHat-based systems) * libncurses5 (for rendering TUI on SLES 12) * libncurses6 (for rendering TUI on RHEL 8 – 10, SLES 15 and 16) * dmidecode (for managing Veeam Agent with Veeam Backup & Replication) * libmysqlclient (for processing MySQL database systems) * libpq5 (for processing PostgreSQL database systems) * python3 (for installing Veeam Agent on [some distributions](#python3) and other operations) * btrfs-progs (version 3.16 or later, for backup of BTRFS)  * wget (for downloading recovery ISO) * which (for deployment process)  * tar (for file system indexing, log export and rotation) * gzip (for file system indexing, log export and rotation)   For creating custom Veeam Recovery Media:   * efibootmgr (for UEFI-based systems) * isolinux (for Debian-based systems) * syslinux (for RHEL-based systems)  * mksquashfs * unsquashfs * xorriso (for custom Veeam Recovery Media with EFI support) |

Considerations and Limitations

Hardware

* For virtual machines, only full virtualization type is supported. Oracle VM virtual machines are supported with [limitations](https://helpcenter.veeam.com/docs/agentforlinux/userguide/baremetal_volume_restore_byb.html). Virtual I/O (VirtIO) devices have [experimental support](https://www.veeam.com/kb2976) status. Other containers and paravirtualized instances are not supported; backup of such devices may result in corruption of the source file system — for more information, see [this Veeam KB article](https://www.veeam.com/kb4428).

* Devices managed by Veritas Volume Manager are not supported.

OS

* Linux kernel version 3.10 to version 6.18 is supported as long as you use kernels supplied by your distribution.

* Only GA versions of the [supported distributions](#OS) that have been released before the current version of Veeam Agent for Linux are supported.

If a new version of a supported Linux distribution is released after the release of the current version of Veeam Agent, Veeam Agent may require a patch to support this new OS version. To learn more about Veeam Agent compatibility with Linux OS versions, see [this Veeam KB article](https://www.veeam.com/kb2804). Customers with a valid contract can request a patch from Veeam Support; for other customers, the support of the new Linux distribution will be provided with the next release of Veeam Agent.

* Veeam Agent supports the following versions of RHEL with Extended Update Support Add-On: 8.4, 8.6, 8.8, 8.10, 9.0, 9.2 and 9.4.

* To ensure proper functioning of the Veeam kernel module, verify that your system does not have any of the following modules installed: hcpdriver, snapapi26, snapapi, snapper, dattobd, dattobd-dkms, dkms-dattobd, cdr or cxbf.

* The Linux OS must be set up to receive software updates from the default repositories enabled in the OS after installation.
* For cloud-based installations that use customized kernels (such as Linux distributions deployed from AWS Marketplace or Azure Marketplace that are not in the [list of supported OSes](#OS)), the veeamsnap kernel module has an [experimental support](https://www.veeam.com/kb2976) status.
* For backups of cloud machines running Amazon Linux 2 and Amazon Linux 2023, only file-level restore is supported.

* Autmatic upgrade from Veeam backup console is not supported for manually deployed Veeam Agents.
* RHEL and Oracle Linux (RHCK) are supported up to certain kernel versions. To learn more, see [this Veeam KB article](https://www.veeam.com/kb2804).

* Ubuntu with Linux kernel for KVM (Kernel-based Virtual Machine) is not supported. For the list of linux-kvm kernels for Ubuntu, see [Ubuntu documentation](https://launchpad.net/ubuntu/%2Bsource/linux-kvm).

* You must not install Veeam Agent on servers that are used as [hardened repositories](https://helpcenter.veeam.com/docs/backup/vsphere/hardened_repository.html) in the Veeam Backup & Replication infrastructure.

* You must not install Veeam Agent on devices that are used as [deduplicating storage appliances](https://helpcenter.veeam.com/docs/backup/vsphere/deduplicating_storage_appliances.html?ver=120) in the Veeam Backup & Replication infrastructure.

* Do not use Veeam Agent managed by one Veeam Backup & Replication installation on a server that acts as a backup infrastructure component in another Veeam Backup & Replication installation. If this happens, both Veeam Backup & Replication installations can automatically update the Transport and Deployer components on the host server, which may lead to performance issues or errors in your backup infrastructure.

File System

* Veeam Agent for Linux does not back up volumes that reside on USB devices and SD cards.

* Veeam Agent for Linux does not back up LVM snapshots.
* File-level backup has the following limitations:

* Total size of all file systems must not exceed 216 TiB. This limitation applies to all file systems where files you plan to back up are located.
* Size of a file included in a file-level backup must not exceed 16 TiB.
* Name of a file must not be larger than 254 bytes.

Keep in mind that characters that you can use in the file name may be encoded in 2 bytes or more.

* To store volume snapshots, the blksnap kernel module requires an Ext4, BTRFS or XFS file system. Snapshot file cannot be stored on multi-device BTRFS.

* Veeam Agent for Linux supports backup of extended attributes with the following limitations:

* Veeam Agent for Linux backs up extended attributes only with the following public namespaces: system, security, trusted, and user.
* All extended attribute names and values of a file must not exceed 4096 bytes (size of a default ext4 file system block). Veeam Agent does not back up attributes exceeding the limit.

For the kernel version 4.13 or later, if a value of extended attribute exceeds the limit, Veeam Agent uses the ea\_inodes feature. Backups created using the ea\_inodes feature cannot be mounted on kernel versions up to 4.12.

* Backup of file and directory attributes (for example, a — append only, c — compressed, and so on) is not supported.

* Each volume included in a backup must have a unique UUID.
* The veeamsnap module provides RAM-based changed block tracking (CBT) mechanism. Every time the module is unloaded or Veeam Agent for Linux computer is rebooted, CBT data is reset. As a result, Veeam Agent reads the entire data added to the backup scope to detect what blocks have changed since the last job session, and incremental backup requires greater time.

* Consider the following about backup of computers that are used as cluster nodes:

* To back up data on local disks, you can use file-level or volume-level backup.
* Data on shared disks, clustered file systems or clustered LVM can be backed up only in the snapshot-less file-level backup mode.

* Backup of clustered file systems using a native file system snapshot, or a snapshot created with the help of custom pre-job or post-job scripts, is not supported.

For more information on backup modes, see the [Backup Types](https://helpcenter.veeam.com/docs/agentforlinux/userguide/backup_types.html) section in the Veeam Agent for Linux User Guide.

To protect data on computers that function as cluster nodes, you can also create backups using nosnap Veeam Agent for Linux. For more information, see [System Requirements for Linux Computers (nosnap Veeam Agent)](agents_system_requirements_linux_nosnap.md#cluster).

* Certain limitations for Dell PowerPath configuration apply. To learn more, see [this Veeam KB article](https://www.veeam.com/kb2771).

* BFQ I/O scheduler is not supported.
* Sparse files are not supported. Veeam Agent for Linux backs up and restores sparse files as regular files.

* Backup of pseudo file systems, such as /proc, /sys, tmpfs, devfs and others, is not supported.

* Backup of BTRFS volumes and subvolumes with enabled file-system compression is not supported.

* Backup of pseudo-RAID, or driver-level RAID, configurations is not supported. Only hardware RAID arrays managed by dedicated controllers and Linux native software RAID (mdadm) are supported.

Software

|  |
| --- |
| IMPORTANT |
| Linux user account used to work with Veeam Agent for Linux installed on the protected computer must have the /bin/bash shell set as the default shell. |

* [For Debian 13] Veeam Agent installs the latest version of linux-headers-amd64 with the matching kernel and its headers. This can cause the kernel to be upgraded, which might affect drivers or software that rely on a specific kernel version. After kernel upgrade, you may need to rebuild or reinstall any custom kernel modules that you have on the system.

* To install Veeam Agent for Linux packages on a target computer, Veeam Backup & Replication uses the default package manager of the Linux distribution running on this computer. During the installation process, the package manager checks whether all prerequisite software is available on the computer. If some of the required software components are missing, the package manager will attempt to install the missing packages from a software repository configured in the OS.
* Version of the following packages varies according to the Linux kernel version that you use:

* linux-headers (for Debian-based systems)
* kernel-headers (for RHEL-based systems)
* kernel-devel (for RHEL-based systems)

* kernel-uek-devel (for Oracle Linux systems with UEK)

* The dmidecode package is required for Veeam Agent management — a valid BIOS UUID must be obtainable either from dmidecode | grep -i uuid or from /sys/class/dmi/id/product\_uuid. Each Veeam Agent that consumes a license installed in Veeam Backup & Replication must have a unique BIOS UUID. If a valid UUID cannot be obtained, Veeam will generate it automatically.
* The libmysqlclient package version varies according to the MySQL database system version that you use.

* The python3 package or another RPM package providing a /usr/bin/python3 binary is required for RHEL 8.4 and later distributions if a pre-built binary kmod-veeamsnap package is to be installed.


