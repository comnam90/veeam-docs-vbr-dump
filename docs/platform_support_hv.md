---
title: "Microsoft Hyper-V"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/platform_support_hv.html"
last_updated: "3/2/2026"
product_version: "13.0.1.1071"
---

# Microsoft Hyper-V


Hyper-V Virtual Infrastructure

Veeam Backup & Replication provides support for the following versions of the Microsoft Hyper-V platform.

Hyper-V Virtual Infrastructure

| Specification | Requirement |
| Platform | * Microsoft Windows Server 2025 * Microsoft Windows Server 2022 * Microsoft Windows Server 2019 * Microsoft Windows Server 2016 * Azure Stack HCI OS   For the supported versions, see [this Veeam KB article](https://www.veeam.com/kb4047).   * Microsoft Windows 111 * Microsoft Windows 101 |
| Hypervisor | * Windows Server Hyper-V 2025 * Windows Server Hyper-V 2022 * Windows Server Hyper-V 2019 * Windows Server Hyper-V 2016 * Azure Local (formerly Azure Stack HCI) * Microsoft Hyper-V Server (free hypervisor) is supported   Server Core installations are fully supported.  Microsoft Nano Server with Hyper-V role installed cannot be [added to the backup infrastructure as a managed server](setup_add_server.md) and no role can be assigned to it. However, you can back up and replicate such servers, but application-aware processing is not supported for them.  Note that you must keep your servers up-to-date. |
| Management Server (optional) | * Microsoft PowerShell Engine 2.0 or later (optional, enables networkless guest processing) * Microsoft System Center Virtual Machine Manager 2025 * Microsoft System Center Virtual Machine Manager 2022 * Microsoft System Center Virtual Machine Manager 2019 * Microsoft System Center Virtual Machine Manager 1807 * Microsoft System Center Virtual Machine Manager 1801 * Microsoft System Center Virtual Machine Manager 2016 |

1 Windows 10/11 is supported only as a target for Instant Recovery and as a host on which a [virtual lab](virtual_lab.md) for SureBackup jobs can be created.

Hyper-V VMs

Hyper-V VMs

| Specification | Requirement |
| Hardware | * Supported virtual hardware versions are 5.0 to 12.0 (valid for Hyper-V 2016 to 2025). * Both Generation 1 and 2 virtual machines are supported, including 64 TB VHDX disks. * Pass-through virtual disks and guest disks connected through in-guest FC or iSCSI initiators are not supported for VM backup. VMs with pass-through disks cannot be snapshotted, which prevents snapshot-based backup. In-guest connected disks are skipped from processing automatically. If backup of these VMs/disks is required, use Veeam Agent backup. * [For Hyper-V Server 1803 or later] Backup of VMs with VMPmemController is not supported. * [For Hyper-V 2016 and later] Veeam Backup & Replication does not support processing of VMs with shared VHDX disks. You must change the disk format to VHD Set (VHDS). * [For Hyper-V 2016 and later] VMs with pass-through virtual disks cannot be processed due to Hyper-V 2016 checkpoints limitation. * [For Hyper-V 2012 R2] Veeam Backup & Replication backs up shared VHDX disks in a crash-consistent state. * [For Hyper-V 2012 R2 and earlier] Backup and replication of VMs whose data resides on a Hyper-V host volume of 64 TB and larger is not supported. |
| OS | All operating systems supported by Hyper-V. Guest processing is supported for OS versions released before the [Veeam Backup & Replication build release date](https://www.veeam.com/kb2680).   * For Microsoft Windows OSes, guest processing (which includes application-aware processing and indexing) is supported for all OSes supported by Hyper-V. * For Linux OSes, guest processing is supported for the [same Linux OSes as for the VMware vSphere platform](platform_support_vm.md#lin_guest). This excludes any OSes that Hyper-V does not support.   Note: You can back up VMs of Hyper-V clusters in rolling upgrade. However, Veeam Backup & Replication does not use the [Resilient Changed Tracking](changed_block_tracking_hv.md#rct) mechanism in such scenario. To perform backup with RCT enabled, make sure your Microsoft Hyper-V environment meets [these requirements](changed_block_tracking.md#reqs). It is recommended to complete the rolling upgrade within four weeks. For more information, see [Microsoft Docs](https://docs.microsoft.com/en-us/windows-server/failover-clustering/cluster-operating-system-rolling-upgrade). |
| Software | Hyper-V integration components (optional, required for application-aware processing). |

Consider the following:

* [For Microsoft Windows 2003 and Nano Server] Application-aware processing is not supported due to the absence of VSS framework.
* [For Hyper-V 2016 and later] Application-aware processing for Microsoft Windows VMs with volumes larger than 64 TB is not supported, because Veeam Backup & Replication uses the Microsoft Software Shadow Copy Provider to create a volume shadow copy during the backup or replication. For more information, see [this Microsoft KB article](https://support.microsoft.com/en-us/help/2967756/usability-limit-for-volume-shadow-copy-service-vss-in-windows).

* [For Hyper-V 2016 and later] Veeam Backup & Replication cannot interact with the guest OS of a shielded VM and get information about its OS, IP address and so on. For this reason, the following operations are not supported for shielded VMs:

+ Application-aware image processing
+ Restore of VM guest OS files to the original location
+ Restore of application items to the original location

* [For Hyper-V 2016 and later] Shielded VMs can run only on trusted hosts guarded with the Host Guardian Service. Consider that when selecting a target host for VM replication or VM restore. If the target host is not guarded with the same Host Guardian Service as the source host, you will not be able to power on the replicated or restored VM.
* The two previous limitations also apply to Generation 1 of Microsoft Hyper-V VMs that use Key Storage Drive. For more information about Key Storage Drive, see [Microsoft Docs](https://technet.microsoft.com/en-us/windows-server-docs/compute/hyper-v/learn-more/Generation-1-virtual-machine-security-settings-for-Hyper-V).

Guest OS File Restore

File-level restore is supported for the following file systems, including Microsoft Windows LDM dynamic disks and Linux LVM:

Guest OS File Restore

| OS | Supported File Systems |
| Microsoft Windows | * FAT, FAT32 * NTFS * ReFS   Windows file-level restore to original location is supported for the following Microsoft Windows operating systems except Nano Server:   * Microsoft Windows Server 2012 R2 SP1 or later * Microsoft Windows 10 22H2 for GA channel or later * Microsoft Windows 10 1507 for LTSB/LTSC channels or later * Microsoft Windows 11 22H2 or later. |
| Linux | * ext2, ext3, ext4 * ReiserFS * JFS * XFS * Btrfs   DRBD (Distributed Replicated Block Devices) are not supported. |
| BSD | UFS, UFS2 |
| Mac | HFS, HFS+ (volumes up to 2 TB) |
| Solaris | * UFS * ZFS (except any pool versions of Oracle Solaris)   The helper appliance uses module ZFSonLinux version 0.7.0. For this reason, Veeam Backup & Replication supports only those versions of pools and features that are available in ZFSonLinux version 0.7.0. |

For other requirements and limitations of guest OS file restore, see [Requirements and Limitations](guest_restore_before_you_begin.md).


