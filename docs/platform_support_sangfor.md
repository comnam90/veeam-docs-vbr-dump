---
title: "Sangfor aSV"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/platform_support_sangfor.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Sangfor aSV


Sangfor aSV Virtual Infrastructure

Sangfor aSV Virtual Infrastructure

| Specification | Requirement |
| Platform | Sangfor HCI versions starting from 6.11.3 |
| Hypervisor | Sangfor aSV |
| Management Server | Sangfor Cloud Platform |

Sangfor aSV VMs

Sangfor aSV VMs

| Specification | Requirement |
| Hardware | All types and versions of virtual hardware are supported. |
| OS | All operating systems supported by Sangfor aSV are supported. |

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

The following table lists compatible versions of Veeam Backup & Replication and Veeam Plug-in for Sangfor aSV.

Version Compatibility

| Product Release | Veeam Plug-in for Sangfor aSV Build | Veeam Backup & Replication Build |
| 1 | 13.1.0.358 | 13.1.0.411 |

Related Topics

* [Overview of Sangfor aSV Protection Functionality](sangfor_overview.md)
* [Sangfor aSV Integration Architecture](sangfor_infrastructure_components.md)

Page updated 2026-07-28

