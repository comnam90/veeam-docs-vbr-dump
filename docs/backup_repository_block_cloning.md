---
title: "Fast Clone"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/backup_repository_block_cloning.html"
last_updated: "10/20/2025"
product_version: "13.0.1.1071"
---

# Fast Clone


Fast Clone is the Veeam Backup & Replication technology that helps create quick file copies. Fast Clone increases the speed of synthetic backup creation and transformation, reduces disk space requirements and decreases the load on storage devices.

With this technology, Veeam Backup & Replication references existing data blocks on volumes instead of copying data blocks between files. Data blocks are copied only when files are modified.

Veeam Backup & Replication supports Fast Clone for the following types of backup repositories:

* Linux server
* Microsoft Windows server
* SMB share
* Dell Data Domain
* ExaGrid
* Fujitsu ETERNUS CS800
* HPE StoreOnce
* Infinidat InfiniGuard
* Quantum DXi

Depending on the repository type, Fast Clone uses different technologies and has different requirements and limitations. For more information, see [Fast Clone for Deduplicating Storage Appliances](#dedup), [Fast Clone for Linux Repositories](#linux) and [Fast Clone for Microsoft Windows and SMB Repositories](#microsoft_smb).

Fast Clone requires that the starting and ending file offsets are aligned to cluster boundaries. For this reason, Veeam Backup & Replication automatically enables the Align backup file data blocks option for backup repositories that support Fast Clone.

Veeam Backup & Replication uses Fast Clone for the following operations:

* In backup jobs: to merge backup files, create synthetic full backups (including GFS backups), transform reverse incremental backups and compact full backup files.
* In backup copy jobs: to merge backup files, create GFS backups (synthetic method) and compact full backup files.
* To [migrate (evacuate) backups between performance extents](sobr_evacuate.md).
* To [migrate (evacuate) Veeam Cloud Connect tenant backups between performance extents](https://helpcenter.veeam.com/docs/vbr/powershell/start-vbrcloudtenantbackupevacuation.html?ver=13).
* To [rebalance SOBR extents](sobr_rebalance.md).
* To [download backups from capacity extents](downloading_from_capacity_tier.md).
* To [move backups to another repository](move_backup.md).
* To [copy backups to another repository](copy_backup.md).
* To [export backups into standalone .VBK files](exporting_backups.md).
* To [upgrade the backup chain format](backup_copy_change_type.md#periodic_copy_mode) for backup copies created in the periodic copy mode.\*

\*This feature is available for Microsoft Windows-based backup servers.

Fast Clone for Deduplicating Storage Appliances

For deduplicating storage appliances (ExaGrid, Quantum DXi and so on), Fast Clone is based on the reflink technology and must be supported by vendors.

Fast Clone for Linux Repositories

For Linux-based backup repositories, Fast Clone is based on the reflink technology.

Requirements for Linux Repositories

To use Fast Clone, Veeam Backup & Replication requires that Linux-based backup repositories meet the following conditions:

* File system is XFS.
* The Linux distribution is supported. For more information, see [Backup Repository](system_requirements.md#repo) (XFS integration).
* The Linux kernel supports reflinks.
* Cyclic redundancy check (CRC) is enabled.
* The minimum supported data block size is 1 KB. The maximum supported block size is 4KB.

Configuring a Linux Repository

To configure a Linux-based backup repository for work with Fast Clone, perform the following steps:

1. Format the disk where backups will be stored using the following XFS volume format string:

|  |
| --- |
| mkfs.xfs -b size=4096 -m reflink=1,crc=1 /dev/sda1 |

Consider that:

* size=4096 sets file system block size to 4096 bytes.
* reflink=1 enables reflinking for the XFS instance (disabled by default).
* crc=1 enables checksums, required for reflink=1 (enabled by default).

1. Mount the disk to a specific directory:

|  |
| --- |
| mkdir /backups  mount /dev/sda1 /backups |

1. Run the following command to ensure that the disk is properly configured:

|  |
| --- |
| df -hT |

1. To permanently mount the disk, add the entry to the /etc/fstab configuration file. It is recommended to use the UUID to specify the disk.

|  |
| --- |
| # <file system>    <mount point>       <type>   <options>   <dump> <pass>  UUID=<UUID>        /backups            xfs      defaults    0       0 |

To get the UUID, run the following command:

|  |
| --- |
| blkid /dev/sda1 |

Limitations

If you have manually moved backup chains to a Linux-based backup repository with Fast Clone support, you must create active full backups for these chains after the move to activate Fast Clone. You can also schedule the backup file compact operation instead of active full backup. Note that creation of active full backups is not required if you use the Veeam [copy](copy_backup.md) or [move](backup_moving.md) features.

Fast Clone for Microsoft Windows and SMB Repositories

For Microsoft Windows and SMB backup repositories, Fast Clone is based on ReFS block cloning technology of Microsoft. For more information on block cloning, see [Microsoft Docs](https://docs.microsoft.com/en-us/windows/desktop/FileIO/block-cloning).

By default, Veeam Backup & Replication uses Fast Clone for all Microsoft Windows and SMB backup repositories that meet the requirements. You can disable this option in the in the configuration file on the Linux-based backup server or with a registry value on the Microsoft Windows-based backup server. For more information, contact Veeam Customer Support.

Requirements for Microsoft Windows and SMB Repositories

Microsoft Windows Backup Repository

To use Fast Clone, Veeam Backup & Replication requires that Microsoft Windows-based backup repositories meet the following conditions:

* OS is Microsoft Windows Server 2016 (or later) or Microsoft Windows 10 Pro for Workstations (or later).
* File system is ReFS 3.1 (or later).

|  |
| --- |
| Note |
| All ReFS supported configurations must use [Windows Server Catalog](https://www.WindowsServerCatalog.com) certified hardware. For other requirements, limitations and known issues, see [this Veeam KB article.](https://www.veeam.com/kb2792) |

Shared Folder Backup Repository

To use Fast Clone, Veeam Backup & Replication requires that SMB backup repositories support [FSCTL\_DUPLICATE\_EXTENTS\_TO\_FILE](https://msdn.microsoft.com/en-us/library/windows/desktop/mt590823%28v%3Dvs.85%29.aspx) and [FSCTL\_SET\_INTEGRITY\_INFORMATION](https://msdn.microsoft.com/en-us/library/windows/desktop/hh965609%28v%3Dvs.85%29.aspx). SMB shares configured on Microsoft Windows machines must also support the SMB 3.1.1 protocol and the ReFS 3.1 (or later) file system.

Depending on the type of the performed job, Veeam Backup & Replication also imposes the following requirements on backup infrastructure components.

| Type of Job | Requirements for backup infrastructure components |
| --- | --- |
| Backup job | Protocol: SMB 3.1.1  OS: Microsoft Windows Server 2016 (or later) or Microsoft Windows 10 Pro for Workstations (or later) on the following backup infrastructure components:   * If a gateway is selected manually: Gateway server. * If a gateway is selected automatically:  * [For VMware vSphere environments] Mount server associated with the backup repository, or backup server. For reverse incremental backup chains, Microsoft Windows Server 2016 (or later) or Windows 10 Pro for Workstations (or later) must additionally be installed on backup proxies assigned for the job. * [For Microsoft Hyper-V environments] For forward incremental chains, mount server associated with the backup repository, or backup server. |
| Backup copy job | Protocol: SMB 3.1.1  OS: Microsoft Windows Server 2016 (or later) or Microsoft Windows 10 Pro for Workstations (or later) on the following backup infrastructure components:   * If a gateway is selected manually: Gateway server. * If a gateway is selected automatically: |

Limitations

The following limitations apply when Veeam Backup & Replication uses Fast Clone for Microsoft Windows or SMB backup repositories:

* Veeam Backup & Replication does not use Fast Clone for backup repositories configured with Veeam Backup & Replication 9.5 or an earlier version. After upgrade, such backup repositories will work as backup repositories without Fast Clone support. To leverage Fast Clone, [edit settings](backup_repo_edit.md) of such backup repositories and complete the Edit Backup Repository wizard without changing settings.
* After you have enabled Fast Clone for existing repositories as described in the previous paragraph or have manually moved backup chains to backup repositories with Fast Clone support, you must create active full backups for backup chains stored in / moved to the repositories to activate Fast Clone. You can also schedule the backup file compact operation instead of performing active full backup.

* Due to Microsoft limitations, the source and destination files must be stored on the same ReFS volume. For more information, see Restrictions and Remarks at [Microsoft Docs](https://msdn.microsoft.com/en-us/library/windows/desktop/mt590820%28v%3Dvs.85%29.aspx).

If you add a backup repository with Fast Clone support as an extent to a scale-out backup repository, make sure that you enable the Data Locality placement policy for this scale-out backup repository. If backup files are stored on different extents, Fast Clone will not be used.

* Veeam Backup & Replication automatically aligns data blocks at a 4KB or 64 KB block boundary depending on the volume configuration or SMB share used storage.

We recommend that you use ReFS volume formatted with 64 KB cluster size to provide better performance with large data volumes.

* When you copy data from a ReFS volume to another location, the file system downloads cloned data blocks. For this reason, copied data occupy more space in the target location than it used to occupy in the source location. This can happen, for example, if you evacuate an extent that supports block cloning from a scale-out backup repository and migrate VM backup data to another extent: copied data will require more space than it originally took.
* If you plan to assign the role of a backup repository to Microsoft Windows Server 2016 version 1709 (or later) or Microsoft Windows 10 Pro for Workstations (or later), consider the following limitations:

* Fast Clone and Windows data deduplication cannot be used simultaneously. Thus, if you target a backup job to a repository supporting Fast Clone and enable Windows data deduplication, the Fast Clone technology will not be used for this job.
* If you target a backup job to an SMB (CIFS) ReFS repository and enable Windows data deduplication, the job will fail. Veeam Backup & Replication does not support such scenario.

Related Topics

[Backup File Placement for Performance Tier](backup_repository_sobr_placement.md)


