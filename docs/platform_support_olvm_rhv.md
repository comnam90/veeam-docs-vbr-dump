---
title: "oVirt KVM"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/platform_support_olvm_rhv.html"
last_updated: "3/2/2026"
product_version: "13.0.1.1071"
---

# oVirt KVM


oVirt KVM Virtual Infrastructure

Veeam Backup & Replication provides support for the following versions of the oVirt KVM platform.

oVirt KVM Virtual Infrastructure

| Specification | Requirement |
| Platform | * Oracle Linux Virtualization node operating version 4.5 and cluster compatibility version 4.7 * Red Hat Virtualization node operating version 4.5 and cluster compatibility version 4.7 |
| Hypervisor | KVM |
| Management Server | * Red Hat Virtualization Manager version 4.5.0 or later * Oracle Linux Virtualization Manager version 4.5.5 or later |

Consider that at least one file-level storage configured in Proxmox Virtual Environment is required.

oVirt KVM VMs

oVirt KVM VMs

| Specification | Requirement |
| Hardware | All types and versions of virtual hardware are supported. |
| OS | All operating systems supported by oVirt KVM. |
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

The following table lists compatible versions of Veeam Backup & Replication and Veeam Plug-In for oVirt KVM.

Version Compatibility

| Product Release | Veeam Plug-In for oVirt KVM Build | Veeam Backup & Replication Build |
| 7 | 13.7.0.473 | 13.0.1.1071 |
| 6.2 | 12.6.2.6 | 12.3.2.3617 |
| 6.1 | 12.6.1.4 | 12.3.1.1139 |
| 6.0 | 12.6.0.166 | 12.3.0.310 |
| 5.0 | 12.5.0.299 | 12.2.0.334 |
| 4.1 | 12.4.1.45 | 12.1.2.172 |
| 4.0 | 12.4.0.385 | 12.1.0.2131 |
| 3b | 12.2.3.19 | 12.0.0.1420 |
| 3a | 12.1.3.431 |
| 3.0 | 12.0.3.412 |

Related Topics

* [Overview of Oracle Linux Virtualization Manager Protection Functionality](olvm_rhv.md)
* [Oracle Linux Virtualization Manager Integration Architecture](ovirt_infrastructure_components.md)


