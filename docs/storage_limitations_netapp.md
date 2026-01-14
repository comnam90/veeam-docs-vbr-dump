---
title: "NetApp ONTAP, Fujitsu ETERNUS HX/AX, Lenovo ThinkSystem DM/DG"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/storage_limitations_netapp.html"
last_updated: "11/19/2025"
product_version: "13.0.1.1071"
---

# NetApp ONTAP, Fujitsu ETERNUS HX/AX, Lenovo ThinkSystem DM/DG

In this article

If you plan to perform operations with NetApp ONTAP, Fujitsu ETERNUS HX/AX, Lenovo ThinkSystem DM/DG storage snapshots, consider the following:

* ONTAP integration requires ONTAPI (ZAPI). For information on ONTAPI (ZAPI) availability, see this [NetApp KB article](https://kb.netapp.com/on-prem/ontap/DM/REST-API/REST_API_KBs/FAQs_on_ZAPI_to_ONTAP_REST_API_transformation_for_CPC_Customer_Product_Communiques_notification).
* Volumes with NetApp SnapLock enabled are not supported.

* Veeam Backup & Replication does not support the listed replication features of the secondary storage arrays. However, you can use volumes with these configured features as sources for backup or snapshot-only jobs.

* MetroCluster
* SVM-DR
* Synchronous SnapMirror
* SnapMirror Active-Sync (formerly SnapMirror Business Continuity (SM-BC))

It is recommended to add only one Storage Virtual Machine (SVM) from the SnapMirror Active-Sync pair to Veeam Backup & Replication. If you add both SVMs, Veeam Backup & Replication may select either SVM as a source for backup jobs, since both are active. This can result in backup inconsistencies.

* ONTAP application-aware data management is not supported.
* [For ONTAP SnapMirror] The Number of snapshot copies to retain option is not applicable to ONTAP SnapMirror. On this secondary storage system, Veeam Backup & Replication maintains the same number of storage snapshots as on primary storage systems. MirrorAndVault Relationships will be identified by Veeam Backup & Replication as SnapVault. For more information on the Number of snapshot copies to retain option, see [Configuring Backup from Snapshots on Secondary Storage Arrays](storage_secondary_backup_perform.md#number) and [Configuring Snapshot-Only Jobs](snapshot_only_job_perform.md#number).
* You may need additional licenses for the following operations:

+ [For VMware integration] [Storage system rescan](netapp_limitations_rescan.md)
+ [For VMware, NAS, Veeam Agent integration] [Backup from storage snapshots](backup_from_storage_snapshots_hiw_netapp.md)
+ [For VMware integration] [Restore from storage snapshots](restore_storage_snapshots_hiw_netapp.md)

For these operations, Veeam Backup & Replication uses different technologies depending on the protocol type and operating mode of the storage system. You need to install one license, even if several technologies can be used for snapshot clone creation. For more information, see [Required Licenses for NetApp](restore_storage_snapshots_hiw_netapp.md).

* The following applies to VMware and NAS integrations:

* The snapshot directory must be visible in the NFS or SMB shares. To learn more about making the snapshot directory visible, see [NFS and SMB (CIFS) Protocols](storage_backup_netapp_nfs.md).
* NetApp FlexGroups are supported, but with a limitation: if you add a new FlexVol to an existing FlexGroup, you will not be able to recover data from existing Snapshots of that FlexGroup.

* [For VMware, Veeam Agent integration] When the storage is added as a specific SVM, and not as a whole cluster, you must set up Aggregation List for vServer so that FlexClone Volume will work properly. Otherwise, errors like this will arise: "Cannot create volume. Reason: aggregate aggr1 is not in aggr-list of Vserver svm-dr-nfs".
* The following applies to VMware integration:

* Multi-home restore is not supported for SnapMirror Target Snapshots with NFS or iSCSI/FC protocol.
* The configuration with several ONTAP SnapMirror or SnapVault relationships configured for one source volume is not supported. Backup jobs from storage snapshots with secondary target will fail. Snapshot-only jobs will accumulate storage snapshots on the target storage systems.
* [For backup from secondary storage arrays and backup with storage snapshot retention] You must configure volume ONTAP SnapMirror or SnapVault relationships between the primary and secondary storage arrays. MirrorAndVault Relationships will be identified by Veeam Backup & Replication as SnapVault. For more information, see the NetApp documentation.
* [For backup from secondary storage arrays and backup with storage snapshot retention] You must install a license for storage snapshot export on ONTAP SnapMirror or SnapVault. For more information, see [Required Licenses for NetApp](restore_storage_snapshots_hiw_netapp.md).
* [For backup from secondary storage arrays] SVM/volumes must have different names between primary and secondary storage arrays. Otherwise, Veeam Backup & Replication may fail to perform backup from secondary storage arrays.
* [For Kerberos authentication] The [Create required export rules automatically](netapp_add_options.md) option must be disabled.

* [For NAS integration] Veeam Backup & Replication uses NetApp SnapDiff for changed files tracking (CBT):

* [For Microsoft Windows-based backup server] NetApp SnapDiff v1 is required and must be enabled. Note that it is not supported for NetApp ONTAP versions from 9.10.1 to 9.10.1P10 and for NetApp ONTAP FlexGroup volumes.
* [For Linux-based backup server] NetApp SnapDiff v3 is required and must be enabled. For information on how to enable SnapDiff v3, see NetApp KB article, see [NetApp KB article](https://kb.netapp.com/on-prem/ontap/DP/SnapDiff/SnapDiff-KBs/How_to_enable_SnapDiff_in_ONTAP).

In This Section

* [Rescan of NetApp Storage Systems](netapp_limitations_rescan.md)
* [Backup from Storage Snapshots](backup_from_storage_snapshots_hiw_netapp.md)
* [Restore from Storage Snapshots](restore_storage_snapshots_hiw_netapp.md)

Page updated 11/19/2025

Page content applies to build 13.0.1.1071
