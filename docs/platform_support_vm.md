---
title: "VMware vSphere"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/platform_support_vm.html"
last_updated: "2/25/2026"
product_version: "13.0.1.1071"
---

# VMware vSphere


VMware vSphere Virtual Infrastructure

Veeam Backup & Replication supports the following VMware vSphere platforms.

VMware vSphere Virtual Infrastructure

| Specification | Requirement |
| Platform | * vSphere 9.01 * vSphere 8.x * vSphere 7.x * VMware Cloud Foundation (VCF)   This platform is supported as individual VMware software components. VMware components listed on this page can be part of VCF. For the information on the correspondence of VMware components to the VCF version, see [this VMware KB article](https://kb.vmware.com/s/article/52520).   * Google Cloud VMware Engine (GCVE)   For more information on GCVE support, see [this Veeam KB article](https://www.veeam.com/kb3178).   * IBM Cloud for VMware Solutions   For more information on IBM Cloud for VMware Solutions support, see [this Veeam KB article](https://www.veeam.com/kb4006).   * Microsoft Azure VMware Solution (AVS)   For more information on AVS support, see [this Veeam KB article](https://www.veeam.com/kb4012).   * Oracle Cloud VMware Solution   For more information on Oracle Cloud VMware Solutions support, see [this Veeam KB article](https://www.veeam.com/kb4007).   * VMware Cloud on AWS   For more information on VMware Cloud on AWS support, see [this Veeam KB article](https://www.veeam.com/kb2414).   * VMware Cloud on Dell   1 Backup and restore of 4Kn drives is not supported. |
| Hypervisor | * vSphere 9.0  * ESXi 8.x * ESXi 7.x   Free ESXi is not supported. Veeam Backup & Replication leverages vSphere and vStorage APIs that are disabled by VMware in free ESXi. |
| Management Server | * vCenter Server or vCenter Server Appliance 9.0 (optional) * vCenter Server or vCenter Server Appliance 8.x (optional) * vCenter Server or vCenter Server Appliance 7.x (optional) |

Veeam Continuous Data Protection (CDP)

The following infrastructure requirements apply only when you protect VMs with Continuous Data Protection (CDP):

* VMware vSphere edition must be VMware vSphere Essentials Kits editions or higher.

* vCenter Server is required. Standalone ESXi hosts are not supported.
* Minimum 16GB RAM is required for source and target ESXi hosts.

* All hosts in a cluster must be of the same major version. For example, 7.x or 8.x (7.0.0, or 7.0.2, or a combination of 7.0.0 and 7.0.2 is supported).
* You can replicate data between vCenter Servers of different versions. However, if you replicate data within one vCenter Server, and this vCenter Server includes hosts of different versions (8 and 7), your CDP policy may fail. In this case, go to the vSphere Client and delete the Veeam CDP Replication VM storage policy applied to each VM included in the CDP policy. For more information on how to delete a VM storage policy, see [VMware Docs](https://knowledge.broadcom.com/external/article/375858/deleting-a-virtual-machine-storage-polic.html). Then, in the Veeam Backup & Replication console, relaunch the CDP policy.

* The maximum number of disks per ESXi host is 500.

* Backup server, CDP proxies, vCenter Server and ESXi hosts must be able to resolve each other DNS names.
* VMware Cloud on AWS is not supported.

For more information on Veeam CDP, its requirements and limitations, see [Continuous Data Protection (CDP)](cdp_replication.md).

VMware vSphere VMs

VMware vSphere VMs

| Specification | Requirement |
| Virtual Hardware | * All types and versions of virtual hardware are supported, including 62 TB VMDK. * Virtual machines with virtual NVDIMM devices, with virtual disks engaged in SCSI bus sharing or residing on PMem datastores are not supported for VM backup, because VMware does not support snapshotting such VMs. To protect such VMs, use Veeam Agent backup. * RDM virtual disks in physical mode, independent disks, and disks connected through in-guest iSCSI initiator are not supported for VM backup, and are skipped from processing automatically. If backup of these disks is required, use Veeam Agent backup.   Network shares and mount points targeted to 3rd party storage devices are also skipped as these volumes/disks are not visible in the VM configuration file.  RDM virtual disks in virtual mode are supported to create backups based on VMware Changed Block Tracking technology, although there are some restrictions on the virtual disk restore operation. To learn more about them, see [Restoring Virtual Disks](disk_restore_before_you_begin.md). |
| OS | * All operating systems supported by VMware. Guest processing is supported for OS versions released before the [Veeam Backup & Replication build release date](https://www.veeam.com/kb2680).  * Guest processing (which includes application-aware processing and indexing) is supported for the following Microsoft Windows operating systems except Nano Server:  * Microsoft Windows Server 2012 R2 SP1 or later * Microsoft Windows 10 22H2 for GA channel or later * Microsoft Windows 10 1507 for LTSB/LTSC channels or later * Microsoft Windows 11 22H2 or later.  * Guest processing (which includes application-aware processing and indexing) is supported for 64-bit versions of the following Linux operating systems:  * Alma Linux 8.10 and 9.4 * Debian 11.0 to 13.1 * Oracle Linux 7 (UEK 3) to 9.6 (UEK 8) * Oracle Linux 7 to 9.6 (UEK/RHCK) * RHEL 8.4 to 10 * Rocky Linux 8.10, 9.4 and 9.6 * SLES 12 SP5 or later, 15 SP3 or later * Ubuntu: 16.04 LTS, 18.04 LTS, 20.04 LTS, 22.04 LTS, 24.04 LTS |
| Software | * For Linux operating systems, GLIBC 2.16 or later. GLIBC is used for the following operations: application-aware processing, file-level restore to Linux guest OS, installing persistent agent components, and adding VM as a managed server. * VMware Tools (optional, recommended). VMware Tools are required for the following operations: application-aware processing, file-level restore from Microsoft Windows guest OS, and SureBackup testing functions. * Open VM Tools (OVT, optional). Open VM Tools are a set of services and modules used by VMware for interaction with VMs running Linux or other VMware supported Unix-like guest operating systems. * All latest OS service packs and patches (required for application-aware processing). |

Guest OS File Restore

File-level restore is supported for the following file systems, including Microsoft Windows Logical Disk Manager (LDM) dynamic disks and Linux Logical Volume Manager (LVM):

Guest OS File Restore

| OS | Supported File Systems |
| Microsoft Windows | * FAT, FAT32 * NTFS * ReFS   Windows file-level restore to original location is supported for the following Microsoft Windows operating systems except Nano Server:   * Microsoft Windows Server 2012 R2 SP1 or later * Microsoft Windows 10 22H2 for GA channel or later * Microsoft Windows 10 1507 for LTSB/LTSC channels or later * Microsoft Windows 11 22H2 or later. |
| Linux | * ext2, ext3, ext4 * ReiserFS * JFS * XFS * Btrfs * NTFS   DRBD (Distributed Replicated Block Devices) are not supported. |
| BSD | UFS, UFS2 |
| Mac | HFS, HFS+ (volumes up to 2 TB) |
| OpenText OES (formerly Micro Focus OES) | NSS  AD-enabled NSS volumes on Open Enterprise Server 2015 are supported. Besides restore of standard file and folder permissions, restore of NSS trustee rights on files and folders is supported.  File-level restore is supported for the following OSes:   * Open Enterprise Server (OES) versions 2015(SP1), 2018(SP1-SP3). Versions 2023, 24.1, 24.4 and 25.4 are supported with limitations. For more information, see [this Veeam KB article](https://www.veeam.com/kb4492). * NetWare 6.5 (only [restore to a new location](guest_restore_save.md#new) is supported) |
| Solaris | * UFS * ZFS (except any pool versions of Oracle Solaris)   The helper appliance uses module ZFSonLinux version 2.1.5. For this reason, Veeam Backup & Replication supports only those versions of pools and features that are available in ZFSonLinux version 2.1.5. |

For other requirements and limitations of guest OS file restore, see [Requirements and Limitations](guest_restore_before_you_begin.md).

VMware Cloud Director

VMware Cloud Director

| Specification | Requirement |
| VMware Cloud Director | VMware Cloud Director 10.4 to 10.6 |


