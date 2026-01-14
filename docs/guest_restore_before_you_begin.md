---
title: "Microsoft Windows File Recovery"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/guest_restore_before_you_begin.html"
last_updated: "11/19/2025"
product_version: "13.0.1.1071"
---

# Microsoft Windows File Recovery

In this article

This section lists considerations and limitations that apply to recovery from Microsoft Windows workloads.

Licensing

[Restore changes functionality](guest_restore_save.md#changed) is included in the Veeam Universal License. When using a legacy socket-based license, the Enterprise or Enterprise Plus editions of Veeam Backup & Replication are required.

Infrastructure Components

* The account that you use to start the Veeam Backup & Replication console and to connect to the backup server must have permissions and privileges described in section [Veeam Backup & Replication Console Permissions](required_permissions.md#rpvbr).

* You can recover files from basic disks and dynamic disks (including simple, mirrored, striped, spanned and RAID5 volumes).
* [For recovery to another workload, to original location, or permissions only] If the target workload uses the gMSA account and you recover files from a backup, you must also [install this account](using_gmsa.md#install) on the mount server associated with the backup repository on which the backup resides. If you recover from a replica, you must install the gMSA account on the backup server.

* [For vSphere recovery to original location] The mount server must have access to the guest OS (if recovery is performed over the network) or vCenter Server and ESXi host where the target workload runs (if recovery is performed over VIX API/vSphere Web Services).
* [For Hyper-V recovery to original location] Guest OS must be accessible from the backup server over the network, or over PowerShell Direct (for VMs that reside on Microsoft Hyper-V Server 2016 or later).

Mount Server

If the antivirus software installed on the mount server blocks or deletes from the mounted disk the objects you are trying to recover, Veeam Backup & Replication will not be able to access these objects. In this case, the restore session will be finished with the Failed state. To avoid such issues, you can add the C:\VeeamFLR folder to the antivirus exclusions.

Recovery using Linux Server as Mount Server

You can recover files and folders of Microsoft Windows workloads using a Linux server (Linux-based mount server or Linux helper host). In this case, the following considerations and limitations apply:

* You can recover files and folders only from NTFS disks.
* Symbolic links and reparse points cannot be recovered.
* Recovery of files and folders from dynamic disks is not supported.
* The backup server, mount server and the target Microsoft Windows workload must be in the same domain, or the [Deployment Kit](deployment_kit.md) must be installed on the target workload.
* Recovery is available only over the network. Recovery over VIX API/vSphere Web Services or PowerShell Direct is not available.
* Besides the file or folder content, Veeam Backup & Replication recovers only basic attributes: Date Created, Date Modified, Read-Only, and Hidden.
* You will need to specify the path for recovery.
* [For Microsoft Windows-based backup server] The following operations are available to finalize recovery: recovery to the original location (Restore), recovery to another location (Restore to) and copy (Copy to).

The Restore to option is not available for restoring from backups created by Veeam Agent for Microsoft Windows.

* Recovery is not supported for workloads with data deduplication enabled.
* When backup of a Microsoft Windows workload is mounted on a Linux-based mount server, the original volume name or drive letter cannot be determined. Linux does not support access to Windows registry data, which stores this information. As a result, the server displays volumes with random IDs instead of their original names or drive letters.

Source for Data Recovery

* You can recover guest OS files from disks that use either the GPT or MBR partitioning scheme. Recovery from disks without a partitioning scheme is not supported.

* You cannot recover pipes and other file system objects. Guest OS file restore supports recovery of files and folders only.

* You cannot recover guest OS files encrypted with Windows EFS.
* You cannot recover and browse guest OS files on disks encrypted by BitLocker.

* Processing of reparse points is supported only for NTFS. Note that reparse points with reparse tag values other than IO\_REPARSE\_TAG\_MOUNT\_POINT, IO\_REPARSE\_TAG\_SYMLINK and IO\_REPARSE\_TAG\_DEDUP may be processed and recovered incorrectly.
* [For recovery to original location] You cannot recover guest OS files if you have excluded the system disk from the backup used for recovery and the [volume GUID](https://docs.microsoft.com/en-us/windows/win32/fileio/naming-a-volume) of the system disk was changed after the backup creation.

* [For [comparison functionality](guest_restore_save.md#compare) and recovery of permissions only] Check that VMware Tools or [Hyper-V integration services](https://learn.microsoft.com/en-us/virtualization/hyper-v-on-windows/reference/integration-services) are installed on the original machine and the machine is accessible over the network.
* You cannot use the [comparison functionality](guest_restore_save.md#compare) if the [Group Managed Service Account (gMSA) account](using_gmsa.md) is used for the workload whose files you plan to recover.

* The [comparison functionality](guest_restore_save.md#compare) is not available for backups created by [Veeam Backup for OLVM and RHV](https://helpcenter.veeam.com/docs/vbrhv/userguide/overview.html?ver=7), for backups exported with Kasten policies and for backups stored in external repositories (for example, backups created by Veeam Backup for AWS, Veeam Backup for Microsoft Azure, and so on).

* [For permission recovery] Permissions can be recovered only for files and folders that are still present on the original workloads. If files and folders are missing, recovery fails.

* The comparison functionality uses Veeam Deployer Service, which is a 32-bit service. During the comparison, the service converts some 64-bit objects into 32-bit objects. That is why such objects are shown as deleted in the Veeam Backup browser, for example, some objects in the Windows folder.

Target for Data Recovery

* [For recovery to original location] VMware Tools must be installed on the target VM. Application-aware processing must be supported for the Microsoft Windows OS of the original machine. If this is not possible, you can use 1-click file-level restore or copy files to the selected folder and then move them to their original location.

* [For [recovery to another workload](guest_restore_save.md#new_vm)] You can recover items only to Microsoft Windows-based workloads. You can select a workload only within the same virtual infrastructure where the original workload resides. For example, if the original workload resides in VMware vSphere, you can select a workload that resides in VMware vSphere only.
* [For permission recovery] Veeam Backup & Replication recovers only permissions. If you recover a folder, permissions are recovered for all subfolders and nested files. Attributes such as Read-only and Encrypted are not recovered.

ReFS

* The mount server must run Microsoft Windows Server 2016 or later.
* The mount server must support the same ReFS version or later than the version used on the workload from which you plan to recover files. For more information on which OSes support which ReFS, see [ReFS versions and compatibility matrix](https://gist.github.com/XenoPanther/15d8fad49fbd51c6bd946f2974084ef8#mountability).

Data Deduplication

If you plan to recover files from a workload running Microsoft Windows Server 2016 or later and data deduplication is enabled for some volumes, consider the following:

* The mount server must run Microsoft Windows Server 2016 or later.
* The mount server must run Microsoft Windows Server of the same version or later than the guest OS of a workload from which you plan to recover files.
* Data deduplication must be enabled on the mount server.

Recovery Finalization

* The following operations are available for recovering from a Microsoft Windows workload: recovery to original location (Restore), recovery to another location (Restore to), copy (Copy to), compare files and folders (Compare), recover only changed files and folders (Restore changed only), recover permissions only (Permissions only), application item restore (Application items), and open files in Microsoft Windows File Explorer.
* The following operations are available for files and folders in the non-comparison state: recovery to original location (Restore), recovery to another location (Restore to), and copy (Copy to).

* When recovering symbolic links to the original location or to another machine, Veeam Backup & Replication recovers only the links, not the content to which they point. However, when copying symbolic links, Veeam Backup & Replication copies the content that the links point to.
* Veeam Backup & Replication recovers junction points as folders with the content they refer to. If a junction point refers to the folder in which it resides or to the parent folder, recovery will fail. For more information, see [this Veeam KB article](https://www.veeam.com/kb4672).
* Hard links are displayed and recovered as files.
* The following applies to the Copy to operation:

* The Copy to operation does not use the comparison states and copies all selected files and folders.
* If the Veeam Backup & Replication console is launched on the backup server, the Copy to operation does not allow copying files to the backup server. You can only copy files to a network shared folder.
* [For Hyper-V VMs] You can restore files and folders to components of the Veeam Backup & Replication infrastructure available over the network.

Page updated 11/19/2025

Page content applies to build 13.0.1.1071
