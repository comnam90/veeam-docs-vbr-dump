---
title: "General Requirements and Limitations (Storage Systems)"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/storage_limitations_general.html"
last_updated: "1/6/2026"
product_version: "13.0.1.1071"
---

# General Requirements and Limitations (Storage Systems)

In this article

The following limitations apply to all storage systems supported by Veeam Backup & Replication.

Infrastructure

Backup infrastructure for storage snapshots has the following requirements and limitations:

* NVMe-oF protocol can be used with Linux-based proxies. For more information, see [NVMe-oF protocol](storage_configure_proxy.md#nvm).
* The following list applies to VMware and Veeam Agent integrations:

* Before you add a storage system to Veeam Backup & Replication, make sure SAN initiator groups for production ESXi hosts and for proxy hosts are isolated and snapshot clones will not be exported to production environment. Otherwise, you may encounter production infrastructure issues such as doubling of the root RGK4IT\_VMware\_Cluster\_Boot Volume to ESXi.

* CHAP authentication is not supported for storage systems working over iSCSI.

* SAS connections are not supported.

* Veeam Backup & Replication does not display volumes and snapshots with the '"VeeamAUX'" prefix in the storage hierarchy. Such volumes are used for service purposes and are filtered out.

IPv6 Support

IPv6 is supported for the following storage systems:

* Dell Unity (XT)
* Dell PowerStore
* Fujitsu ETERNUS HX/AX
* Fujitsu ETERNUS AF and DX Series (management connections only)
* Hitachi VSP/VSP One Block (data connections for VSP 5000; management and data connections for others)
* HPE Primera, HPE Alletra 9000
* HPE Alletra Storage MP B10000 (management connections only)
* HPE 3PAR StoreServ (management connections only)
* IBM FlashSystem (management connections only)
* Lenovo ThinkSystem DM/DG Series
* NEC Storage M Series (management connections only)
* NetApp ONTAP
* Pure Storage FlashArray

If only management IPv6 connection is supported for a storage system, you can add this storage system to backup infrastructure using IPv6 address. However, all data traffic will be transferred over IPv4.

|  |
| --- |
| Note |
| Temporary IPv6 addresses are not supported for backup infrastructure components and backed-up machines. For more information about using temporary addresses, see [this RFC section](https://www.rfc-editor.org/rfc/rfc4941#section-3.6). |

To use IPv6 addresses and resolve names using IPv6, configure IPv6 communication as described in the [IPv6 Support](ipv6.md) section in the Veeam Backup & Replication User Guide.

[VMware Integration] Backup from Storage Snapshots

Backup from storage snapshots has the following requirements and limitations:

* You must install the Enterprise Plus edition of Veeam Backup & Replication on the backup server.

* You must configure the backup infrastructure in the following way:

+ Add to the backup infrastructure a backup proxy that will be used for backup or replication, and properly configure this backup proxy. For more information, see [Configuring Backup Proxy](storage_configure_proxy.md).
+ Add to the backup infrastructure vCenter Server or ESXi hosts with VMs whose disks are hosted on the storage system.
+ Add the storage system to the backup infrastructure. If you plan to perform backup from snapshots on secondary storage arrays, also add the secondary storage array to the backup infrastructure.

* Backup from storage snapshots does not support vRDM disks. vRDM disks are skipped from processing.
* Backup from storage snapshots cannot be used:

* For VMs whose disks are located on VVol datastores.

* To back up VM templates.
* To back up encrypted VMs.

* Processing of VMs with VMware snapshots may take much longer to start compared to using the Direct SAN Access transport mode with iSCSI/FC SAN. In case these delays are unacceptable, we recommend to either delete the VMware snapshots or avoid using storage snapshots integration to protect such VMs.

* For storage systems working over NFS:

+ VMs that you plan to back up or replicate must not have VMware snapshots. VMs with snapshots are processed during regular backup job.
+ If you enable the Enable VMware tools quiescence option in the job settings, Veeam Backup & Replication will not use backup from storage snapshots to process running Microsoft Windows VMs that have VMware Tools installed.
+ Backup from storage snapshots is not supported for SLES operating systems working over IPv6.

* [For backup from secondary storage arrays] When you add storage arrays to the backup infrastructure, you must add to the rescan scope volumes and LUNs on which VM disks are located (both for primary and secondary storage arrays). For more information, see the description of the storage system wizard.

[VMware Integration] Snapshot Orchestration and Backup from Snapshots with Snapshot Retention

Snapshot jobs (snapshot-only jobs and backup jobs with storage snapshot retention) have the following requirements and limitations:

* If you remove or re-add a storage array that is already associated with a snapshot job, Veeam Backup & Replication will restart the retention cycle. You will need to manually remove old snapshots that are no longer needed.
* You cannot perform snapshot orchestration for VMs residing on a VMware datastore with multiple extents, typically due to the use of several LUNs. For such VMs, you can launch backup from storage snapshots. However, Veeam Backup & Replication will perform regular backup without creating a snapshot.

* Veeam Backup & Replication always creates snapshots of volumes that contain .VMX files of the VMs included in the job.

* The following applies to snapshot-only jobs:

+ If you exclude a VM disk from the job and this disk resides on the same volume as a non-excluded disk, Veeam Backup & Replication creates a snapshot of the entire volume, which includes the data of the excluded disk. If only the excluded disks reside on the volume, the volume snapshot is not created.
+ Veeam Backup & Replication does not support guest file indexing for snapshot-only jobs.
+ The ability to create snapshot-only jobs depends on the Veeam Backup & Replication license edition. For snapshot-only jobs on the primary storage arrays, you can use any license edition. For snapshot-only jobs on the secondary storage arrays, the license edition depends on the used storage system and replication feature. For more information, see [Storage Systems and Supported Features](vmware_integration.md#feature).

* The following applies to backup jobs with storage snapshot retention:

* You must configure the backup infrastructure in the following way:

+ Add to the backup infrastructure a backup proxy that will be used for backup or replication, and properly configure this backup proxy. For more information, see [Configuring Backup Proxy](storage_configure_proxy.md).
+ Add to the backup infrastructure vCenter Server or ESXi hosts with VMs whose disks are hosted on the storage system.
+ Add the storage system to the backup infrastructure. If you plan to perform backup from snapshots on secondary storage arrays, also add the secondary storage array to the backup infrastructure.

* You must install a license for Veeam Backup & Replication Enterprise Plus edition on the backup server.
* [For backup from secondary storage arrays] When you add storage arrays to the backup infrastructure, you must add to the rescan scope volumes and LUNs on which VM disks are located (both for primary and secondary storage arrays). For more information, see the description of the storage system wizard.

[VMware Integration] Data Recovery from Storage Snapshots

Data recovery from storage snapshots has the following requirements and limitations:

* You must add the storage system to the backup infrastructure.

* [For storage systems working over Fibre Channel] To let Veeam Backup & Replication present snapshots of LUNs to an ESXi host, you must register the ESXi host with a WWN ID on the storage system.

* During restore of VM guest OS files from storage snapshots, data is transferred over LAN through the Network Block Device protocol (NBD). Therefore, restore performance may not be optimal.

* You cannot perform any restore operations if a VMware datastore comprises several extents (usually due to the use of several LUNs).
* Restore is not supported for VMs whose disks are located on VVol datastores.
* For snapshots created by jobs, Veeam Backup & Replication supports multi-home restore (when VM disks are hosted on different VMware datastores).
* For snapshots created not by jobs, for example, native storage snapshots, consider the following:

* Veeam Backup & Replication supports restore operations and also restores only disks residing on the same datastore as the VMX file.
* You will not be able to restore VM disks that contain an absolute path in the VMX file.
* You will not be able to perform Instant Recovery and restore VM guest OS files to the original location from snapshots on secondary storage arrays.
* You cannot perform Instant Disk Restore for VMs if Veeam Backup & Replication cannot get information about them from the vCenter Server. This issue may occur if the vCenter Server or ESXi host is not added to the backup infrastructure, or if a secondary storage array is used for the restore.

* If you remove or re-add a storage array to the backup infrastructure, you will be able to restore data only from those VM disks that are hosted on the same datastore as the VMX file.
* You cannot restore data of a VM whose disks are hosted on storage systems of different storage vendors.
* [For Instant Recovery] If you recover a VM to the production network, make sure that the original VM is powered off to avoid conflicts.
* [For Instant Disk Recovery] If you recover a VM disk to the existing disk, this will delete the existing disk.

FAT, NTFS or ReFS Restore from Storage Snapshots

Before you restore VM guest OS files from Microsoft Windows file systems, check the following requirements:

* If you plan to restore VM guest OS files to their original location, you must make sure that VMware tools are installed on the target VM.
* If you plan to restore guest OS files from a VM running Microsoft Windows ReFS, the Veeam Backup & Replication console must be installed on a machine running Microsoft Windows Server 2012 or later.
* If you plan to restore files from a VM running Microsoft Windows Server 2012 or later, and data deduplication is enabled for some VM volumes, the Veeam Backup & Replication console must be installed on a machine running Microsoft Windows Server 2012 or later. Data deduplication must be enabled on this machine.

* If the original VM is removed from vSphere infrastructure or migrated to another datastore, you will not be able to perform VM guest OS files restore to the original location.

Linux, Unix and Other File Systems Restore from Storage Snapshots

Before you restore VM guest OS files from Linux, Unix or other file systems, check the following requirements:

* If you plan to restore VM guest OS files to their original location, make sure that VMware Tools are installed on the target VM.
* Veeam Backup & Replication restores ACL for recovered VM guest OS files. To let Veeam Backup & Replication detect the target Linux system architecture and kernel version, make sure that arch and uname are installed on the VM guest OS.
* Veeam Backup & Replication must have access to the guest OS of the target VM to be able to deploy a coordination process. The coordination process performs a number of administrative actions on the target VM guest OS, for example, collects information about mount points.
* The mount server, whether it is a helper host or a helper appliance, must have access over a network to a VM whose files you restore or direct access to vCenter or ESXi host where the VM resides. If the mount server is connected to a VM whose files you restore through VIX API/vSphere Web Services, you must use a root account for a target VM, otherwise the restore process will fail.

* You cannot restore files directly to the original location from backups of BSD, Mac and Solaris VMs. You cannot restore files directly to the original location from NSS filesystems. Use the Copy to option instead.

* If the original VM is removed from vSphere infrastructure or migrated to another datastore, you will not be able to perform VM guest OS files restore to the original location.

* For Linux target VM, consider the following:

+ If you want to restore files over network, make sure that the SSH daemon is configured and SCP utility is available on the target VM.
+ SELinux must be disabled on the target VM.
+ A range of ports that are used for data transfer must be open on the target VM.

For more information on configuring connection settings for Linux servers, see the [Specify Credentials and SSH Settings](linux_server_ssh.md) step of the New Linux Server wizard.

Page updated 1/6/2026

Page content applies to build 13.0.1.1071
