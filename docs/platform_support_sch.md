---
title: "Scale Computing HyperCore"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/platform_support_sch.html"
last_updated: "3/2/2026"
product_version: "13.0.1.1071"
---

# Scale Computing HyperCore


Virtual Infrastructure

Veeam Backup & Replication provides support for the following versions of the Scale Computing HyperCore platform.

Virtual Infrastructure

| Specification | Requirement |
| Platform | Scale Computing Platform |
| Hypervisor | The following Scale Computing HyperCore versions are supported:   * 9.4.x starting from 9.4.32.218226 * 9.5.x |

VMs

VMs

| Specification | Requirement |
| Hardware | All types and versions of virtual hardware are supported |
| OS | All operating systems compatible with the Scale Computing HyperCore version in use are supported. |

Guest OS File Restore

File-level restore is supported for the following file systems, including Microsoft Windows LDM dynamic disks and Linux LVM:

Guest OS File Restore

| OS | Supported File Systems |
| Microsoft Windows | * FAT, FAT32 * NTFS * ReFS   Windows file-level restore to original location is supported for the following Microsoft Windows operating systems except Nano Server:   * Microsoft Windows Server 2012 R2 SP1 or later * Microsoft Windows 10 22H2 for GA channel or later * Microsoft Windows 10 1507 for LTSB/LTSC channels or later * Microsoft Windows 11 22H2 or later |
| Linux | * ext2, ext3, ext4 * ReiserFS * JFS * XFS * Btrfs   DRBD (Distributed Replicated Block Devices) are not supported |
| BSD | UFS, UFS2 |
| Mac | HFS, HFS+ (volumes up to 2 TB) |
| Solaris | * UFS * ZFS (except any pool versions of Oracle Solaris) |

For other requirements and limitations of guest OS file restore, see [Requirements and Limitations](guest_restore_before_you_begin.md).

Version Compatibility

Version Compatibility

| Product Release | Veeam Plug-in for Scale Computing HyperCore Build | Veeam Backup & Replication Build |
| 2 | 13.2.0.245 | 13.0.1.180 |
| 1.1 | 12.1.1.4 | 12.3.2.3617 |


