---
title: "HPE Morpheus VM Essentials"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/platform_support_hpe_vme.html"
last_updated: "3/2/2026"
product_version: "13.0.1.1071"
---

# HPE Morpheus VM Essentials


HPE Morpheus VM Essentials Virtual Infrastructure

Veeam Backup & Replication provides support for the following versions of the HPE Morpheus VM Essentials platform.

HPE Morpheus VM Essentials Virtual Infrastructure

| Specification | Requirement |
| Platform | HPE Morpheus VM Essentials Appliance versions 8.0.13 and 8.1 (host agent version 3.1.3 or later, morpheus-ws-node package version 3.3.19-1 or later, alletra plug-in version 1.8.1 or later) |
| Hypervisor | KVM |
| Management Server | HPE Morpheus VM Essentials Management Console |

Consider that at least one datastore of the Directory Pool, NFS Pool, GFS2 Pool type configured in the HPE Morpheus VM Essentials manager is required.

HPE Morpheus VM Essentials VMs

HPE Morpheus VM Essentials VMs

| Specification | Requirement |
| Hardware | All types and versions of virtual hardware are supported. |
| OS | All operating systems supported by HPE Morpheus VM Essentials. |
| Software | [QEMU Guest Agent](https://pve.proxmox.com/wiki/Qemu-guest-agent) (optional, required for QEMU Guest Agent quiescence) |

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

The following table lists compatible versions of Veeam Backup & Replication and Veeam Plug-in HPE Morpheus VM Essentials.

Version Compatibility

| Product Release | Veeam Plug-in HPE Morpheus VM Essentials Build | Veeam Backup & Replication Build | Worker OS Version |
| 1 | 13.1.0.271 | 13.0.1.1071 | Rocky Linux 9.2 |

Related Topics

* [Overview of HPE Morpheus VM Essentials Protection Functionality](proxmox_ve.md)
* [HPE Morpheus VM Essentials Integration Architecture](pve_infrastructure_components.md)


