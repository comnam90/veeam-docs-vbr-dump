---
title: "Proxmox VE"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/platform_support_proxmox.html"
last_updated: "3/2/2026"
product_version: "13.0.1.1071"
---

# Proxmox VE


Proxmox VE Virtual Infrastructure

Veeam Backup & Replication provides support for the following versions of the Proxmox VE platform.

Proxmox VE Virtual Infrastructure

| Specification | Requirement |
| Platform | Proxmox Virtual Environment versions 8.2–9.1 installed using the official ISO image provided by Proxmox |
| Hypervisor | KVM |
| Management Server | n/a |

Consider that at least one file-level storage configured in Proxmox Virtual Environment is required.

Proxmox VE VMs

Proxmox VE VMs

| Specification | Requirement |
| Hardware | All types and versions of virtual hardware are supported. |
| OS | All operating systems supported by Proxmox VE. Guest processing is supported for OS versions released before the [Veeam Backup & Replication build release date](https://www.veeam.com/kb2680).   * Guest processing (which includes application-aware processing and indexing) is supported for the following Microsoft Windows operating systems except Nano Server:  * Microsoft Windows Server 2012 R2 SP1 or later * Microsoft Windows 10 22H2 for GA channel or later * Microsoft Windows 10 1507 for LTSB/LTSC channels or later * Microsoft Windows 11 22H2 or later  * Guest processing (which includes application-aware processing and indexing) is supported for 64-bit versions of the following Linux operating systems:  * Alma Linux 8.10 and 9.4 * Debian 11.0 to 13.1 * Oracle Linux 7 (UEK 3) to 9.6 (UEK 8) * Oracle Linux 7 to 9.6 (UEK/RHCK) * RHEL 8.4 to 10 * Rocky Linux 8.10, 9.4 and 9.6 * SLES 12 SP5 or later, 15 SP3 or later * Ubuntu: 16.04 LTS, 18.04 LTS, 20.04 LTS, 22.04 LTS, 24.04 LTS |
| Software | [QEMU Guest Agent](https://pve.proxmox.com/wiki/Qemu-guest-agent) (optional, required for application-aware processing) |

Guest OS File Restore

File-level restore is supported for the following file systems, including Microsoft Windows LDM dynamic disks and Linux LVM:

Guest OS File Restore

| OS | Supported File Systems |
| Microsoft Windows | * FAT, FAT32 * NTFS * ReFS   Windows file-level restore to original location is supported for the following Microsoft Windows operating systems except Nano Server:   * Microsoft Windows Server 2012 R2 SP1 or later * Microsoft Windows 10 22H2 for GA channel or later * Microsoft Windows 10 1507 for LTSB/LTSC channels or later * Microsoft Windows 11 22H2 or later. |
| Linux | * ext2, ext3, ext4 * ReiserFS * JFS * XFS * Btrfs   DRBD (Distributed Replicated Block Devices) are not supported. |
| BSD | UFS, UFS2 |
| Mac | HFS, HFS+ (volumes up to 2 TB) |
| Solaris | * UFS * ZFS (except any pool versions of Oracle Solaris) |

For other requirements and limitations of guest OS file restore, see [Requirements and Limitations](guest_restore_before_you_begin.md).

Version Compatibility

The following table lists compatible versions of Veeam Backup & Replication and Veeam Plug-In for Proxmox VE.

Version Compatibility

| Product Release | Veeam Plug-In for Proxmox VE Build | Veeam Backup & Replication Build | Worker OS Version |
| 3 | 13.3.0.237 | 13.0.1.1071 | Rocky Linux 9.2 |
| 2 | 13.2.0.457 | 13.0.0.4967 | Rocky Linux 8.10 |
| 1.5 | 12.1.5.17 | 12.3.2.3617 |
| 1.3 | 12.1.3.217 | 12.3.2.3617  12.3.1.1139  12.3.0.310 |
| 1.1 | 12.1.1.1024 | 12.3.0.310  12.2.0.334 |

Related Topics

* [Overview of Proxmox VE Protection Functionality](proxmox_ve.md)
* [Proxmox VE Integration Architecture](pve_infrastructure_components.md)


