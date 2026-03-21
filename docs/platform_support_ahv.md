---
title: "Nutanix AHV"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/platform_support_ahv.html"
last_updated: "3/20/2026"
product_version: "13.0.1.2067"
---

# Nutanix AHV


Nutanix AHV Virtual Infrastructure

Veeam Backup & Replication provides support for the following versions of the Nutanix AHV platform.

Nutanix AHV Virtual Infrastructure

| Specification | Requirement |
| Platform | Nutanix-certified hardware and Nutanix Cloud Clusters (NC2) running Nutanix AOS versions 6.8.1.6 and above |
| Hypervisor | AHV |
| Management Server | Prism Central version pc.2022.6–pc.2024.3.1.10, pc.7.3 and above except 7.3.1.2 and 7.5.0.0 |

Consider the following:

* An IP address of the cluster and the [iSCSI Data Service](https://portal.nutanix.com/page/documents/details?targetId=Web-Console-Guide-Prism-v7_3:wc-cluster-details-modify-wc-t.html) must be configured in Nutanix AHV cluster settings.
* [UEFI boot](https://portal.nutanix.com/page/documents/details?targetId=AHV-Admin-Guide-v6_8:vm-vm-uefi-support-c.html) must be supported in the Nutanix AHV environment.

Nutanix AHV VMs

Nutanix AHV VMs

| Specification | Requirement |
| Hardware | All types and versions of virtual hardware are supported |
| OS | All operating systems supported by Nutanix AHV. Guest processing is supported for OS versions released before the [Veeam Backup & Replication build release date](https://www.veeam.com/kb2680).   * Guest processing (which includes application-aware processing and indexing) is supported for the following Microsoft Windows operating systems except Nano Server:  * Microsoft Windows Server 2012 R2 SP1 or later * Microsoft Windows 10 22H2 for GA channel or later * Microsoft Windows 10 1507 for LTSB/LTSC channels or later * Microsoft Windows 11 22H2 or later  * Guest processing (which includes application-aware processing and indexing) is supported for 64-bit versions of the following Linux operating systems:  * Alma Linux 8.10 and 9.4 * Debian 11.0 to 13.1 * Oracle Linux 7 (UEK 3) to 9.6 (UEK 8) * Oracle Linux 7 to 9.6 (UEK/RHCK) * RHEL 8.4 to 10 * Rocky Linux 8.10, 9.4 and 9.6 * SLES 12 SP5 or later, 15 SP3 or later * Ubuntu: 16.04 LTS, 18.04 LTS, 20.04 LTS, 22.04 LTS, 24.04 LTS |
| Software | Nutanix Guest Tools (optional, not required for application-aware processing) |

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

The following table lists compatible versions of Veeam Backup & Replication and Veeam Plug-In for Nutanix AHV.

Version Compatibility

| Product Release | Veeam Plug-In for Nutanix AHV Build | Veeam Backup & Replication Build | Backup Appliance / Worker OS Version |
| 9 | 13.9.0.212 | 13.0.1.1071 | Veeam JeOS 9.2 |
| 8 | 13.8.0.582 | 13.0.0.4967 | Rocky Linux 8.10 |
| 7.1 | 12.7.1.12 | 12.3.1.1139 | Rocky Linux 8.10 |
| 7.0 | 12.7.0.172 | 12.3.0.310 |
| 6.1 | 12.6.1.15 | 12.2.0.334 |
| 6.0 | 12.6.0.632 | 12.2.0.334 |
| 5.1 | 12.5.1.8 | 12.1.0.2131 12.1.1.56 | Ubuntu 22.04 LTS |
| 5.0 | 12.5.0.465 | 12.0.0.1420 12.1.0.2131 |
| 4a | 12.1.4.5 | 12.0.0.1420 | Ubuntu 20.04 LTS |
| 4.0 | 12.0.4.1020 | 12.0.0.1420 |

Related Topics

* [Overview of Nutanix AHV Protection Functionality](nutanix_ahv.md)
* [Nutanix AHV Integration Architecture](ahv_infrastructure_components.md)


