---
title: "Universal Hypervisors"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/platform_support_uhapi.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Universal Hypervisors


Universal Hypervisors Virtual Infrastructure

Veeam Backup & Replication provides support for the following hypervisors:

Universal Hypervisors Virtual Infrastructure

| Specification | Requirement |
| Platform | * Platform9 version 2026.4 or later. * VergeOS version 26.1.7 or later. |
| Hypervisor | KVM |

Universal Hypervisor VMs

Universal Hypervisor VMs

| Specification | Requirement |
| Hardware | All types and versions of virtual hardware are supported. |
| OS | All operating systems supported by universal hypervisors. |
| Software | n/a |

Guest OS File Restore

File-level restore is supported for the following file systems, including Microsoft Windows LDM dynamic disks and Linux LVM:

Guest OS File Restore

| OS | Supported File Systems |
| Microsoft Windows | * FAT, FAT32 * NTFS * ReFS   Windows file-level restore to original location is supported for the following Microsoft Windows operating systems except Nano Server:   * Microsoft Windows Server 2012 R2 SP1 or later * Microsoft Windows 10 22H2 for GA channel or later * Microsoft Windows 10 1507 for LTSB/LTSC channels or later * Microsoft Windows 11 22H2 or later |
| Linux | * ext2, ext3, ext4 * ReiserFS * JFS * XFS * Btrfs   DRBD (Distributed Replicated Block Devices) are not supported. |
| BSD | UFS, UFS2 |
| Mac | HFS, HFS+ (volumes up to 2 TB) |
| Solaris | * UFS * ZFS (except any pool versions of Oracle Solaris) |

For other requirements and limitations of guest OS file restore, see [Requirements and Limitations](guest_restore_before_you_begin.md).

Version Compatibility

The following table lists compatible versions of Veeam Backup & Replication and Veeam Plug-in for Universal Hypervisor API.

Version Compatibility

| Product Release | Veeam Plug-in for Universal Hypervisor API Build | Veeam Backup & Replication Build | Worker OS Version |
| 1 | 13.1.0.191 | 13.1.0.411 | Veeam JeOS 9.6 |

Related Topics

* [Overview of Universal Hypervisor Protection Functionality](universal_hypervisors.md)
* [Universal Hypervisor Integration Architecture](uh_infrastructure_components.md)

Page updated 2026-07-30

